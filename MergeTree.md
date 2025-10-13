#clickhouse 

[[clickhouse]]
![[Screenshot 2023-02-14 at 20.23.20.png]]




Clickhouse inserts data ASAP, and merge the files in the background.

When you `INSERT` a bunch of data into `MergeTree`, that bunch is sorted by primary key order and forms a new [[part]]. There are background threads ([[background_pool_size]]) that periodically select some parts and merge them into a single sorted part to keep the number of parts relatively low. That’s why it is called `MergeTree`.

In the background, for incrementally optimizing the data for reads, ClickHouse is continuously merging data parts into larger parts. The merged parts are marked as inactive and finally deleted after a configurable number of minutes.

data is sorted and compressed when a new part is written. When parts are merged, the data needs to be **decompressed** and **merge-sorted**. Also, table engine specific optimizations are applied **before** the merged data is compressed and written to storage again.

And, if a single insert query contains more than 1 million rows, ClickHouse will create more than one new part for the query’s data.