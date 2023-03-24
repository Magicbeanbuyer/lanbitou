#spark #clickhouse

### Spark
![[Vectorized Query Execution in Apache Spark at Facebook Chen Yang Facebook 13-9 screenshot.png]]

### CockroachDB
If vectorized execution is enabled, the physical plan is sent to nodes to be processed by the vectorized execution engine.

Upon receiving the physical plan, the vectorized engine reads batches of table data from disk and converts the data from row format to columnar format. These batches of column data are stored in memory so the engine can access them quickly during execution.

The vectorized engine uses specialized, precompiled functions that quickly iterate over the type-specific arrays of column data. The columnar output from the functions is stored in memory as the engine processes each column of data.

After processing all columns of data in the input buffer, the engine converts the columnar output back to row format, and then returns the processed rows to the SQL interface. After a batch of table data has been fully processed, the engine reads the following batch of table data for processing, until the query has been executed.