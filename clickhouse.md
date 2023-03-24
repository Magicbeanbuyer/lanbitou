- C++ binary
- [[shared nothing]]
- [[vectorized query execution]]

### part

Each part is one folder
within each part (a file) data is ordered by order key

The files consist of compressed blocks. Each block is usually from 64 KB to 1 MB of uncompressed data.

ACID
The [[database transaction]] unit in [[clickhouse]] is a part,  individual parts are written atomically
There is no row level operation, when deleting data, the file has to be deleted and rewritten.

### column
![[Screenshot 2023-02-14 at 20.41.56.png]]

Columns are ordered and compressed
each column has **two files**
`column_name.mrk` 
contains an array of pointers
the pointers/marks are corresponding to the primary key
Each mark is a pair: the offset in the file to the beginning of the compressed block, and the offset in the decompressed block to the beginning of data.
data for `column.mrk` files is cached.

`column_name.bin` 
each mark is pointing to a segment in the `.bin` file (a compressed block) 


### granule
![](https://clickhouse.com/docs/assets/images/sparse-primary-indexes-02-f6b524b73c2747c0c26aaf8a8a06a89e.png)
distance between two indices, granule is the smallest data unit clickhouse processes, 8,192

Default maximum size of a granule is 10Mb.

### Block
A `Block` is a container that represents a subset (chunk) of a table in memory. It is just a set of triples: `(IColumn, IDataType, column name)`. During query execution, data is processed by `Block`s.

The files consist of compressed blocks. Each block is usually from 64 KB to 1 MB of uncompressed data, depending on the average value size.


### primary index

The primary index is created based on the granules. This index is an uncompressed flat array file `primary.idx`, containing so-called numerical index marks starting at 0.

`primary.idx` stores the primary key column values for each first row for each granule. Or in other words: the primary index stores the primary key column values from each 8192nd row of the table.

The primary index file is completely loaded into the main memory.

The sparse primary index allows it to quickly (via a binary search over index entries) identify granules that could possibly match the query. The located granules are then in parallel streamed into the ClickHouse engine in order to find the matches.

### sorting key and primary key
Because the primary key is sparse, it is not unique: it cannot check the existence of the key in the table at INSERT time.

- If you only specify the sorting key (via ORDER BY ...), then the primary key is implicitly equal to the sorting key.
- If you only specify the primary key (via PRIMARY KEY ...), then the sorting key is implicitly equal to the primary key.
- If you specify explicitly both a sorting key and a primary key, then the primary key needs to be a prefix of the sorting key, for example the sorting key can be (col1, col2, col3, col4) and the primary key can be (col1, col2). This can make sense because the primary index is based on the primary key, and the primary index needs to be loaded into the main memory. Therefore it makes sense to only use columns that are really required for speeding up queries. Whereas the sorting key is used for the physical order of the rows on disk, and it is good for compression ratio if data per column file is sorted.

### parallelism
thread = CPU core

you can increase/decrease the amount of threads/cpu cores used for a query processing.
The more threads, the more data is processed in parallel, and the more RAM is used. The setting is called `max_threads`.
Here is a video showing the effects https://youtu.be/hP6G2Nlz_cA

### compression and encoding
`LowCardniality`: dictionary encoding 
`delta` encoding: encode by the diff in the steps
double `delta` encoding: diff in the slope in the steps

numerical encoding for time series data is significant 


### Replication and Sharding
![[Screenshot 2023-02-14 at 22.09.58.png]]
shards have different data
only shard when data cannot fit on one machine
shards are not aware of other shards of the same table

replicas have the same data, there is always a leader replica
![[Screenshot 2023-02-14 at 22.14.34.png]]
Data is inserted on the server where the query is run, and then it is copied to the other servers.

### distributed table
![[Screenshot 2023-02-14 at 22.24.31.png]]

Local join is possible when the join keys align on the same node (as the drawing on the left)
Otherwise a  `global` join is required.

### materialized views
chain views as data pipelines
last point query: for example, reads the latest data in a time series
change sorting

### kafka table engine
Use kafka topic as a logical/external table
Then a materialized view reads from the topic at intervals and write the data out to clickhouse under the materialized view

### questions
A sparse index allows extra data to be read. When reading a single range of the primary key, up to `index_granularity * 2` extra rows in each data block can be read.

For each `INSERT` query, approximately ten entries are added to ZooKeeper through several transactions. (To be more precise, this is for each inserted block of data; an INSERT query contains one block or one block per `max_insert_block_size = 1048576` rows.) This leads to slightly longer latencies for `INSERT` compared to non-replicated tables. But if you follow the recommendations to insert data in batches of no more than one `INSERT` per second, it does not create any problems. The entire ClickHouse cluster used for coordinating one ZooKeeper cluster has a total of several hundred `INSERTs` per second. The throughput on data inserts (the number of rows per second) is just as high as for non-replicated data.

The key for partitioning by month allows reading only those data blocks which contain dates from the proper range. In this case, the data block may contain data for many dates (up to an entire month). Within a block, data is sorted by primary key, which might not contain the date as the first column. Because of this, using a query with only a date condition that does not specify the primary key prefix will cause more data to be read than for a single date.

Usually, compressed blocks are aligned by marks, and the offset in the decompressed block is zero.