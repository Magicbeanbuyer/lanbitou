#databricks 

> As files are discovered, their metadata is persisted in a scalable key-value store (RocksDB) in the _checkpoint location_ of your Auto Loader pipeline.
Streaming table is [[Apache Spark|Spark]] Structured Streaming under the hood.

```sql
CREATE OR REFRESH STREAMING TABLE sales
  SCHEDULE EVERY 1 hour
  AS SELECT product, price FROM STREAM raw_data;
```

When you create a streaming table using the `CREATE OR REFRESH STREAMING TABLE` statement, the initial data refresh and population begin **immediately**. These operations do not consume DBSQL warehouse compute. Instead, streaming table rely on **serverless pipelines** for both creation and refresh. A dedicated serverless pipeline is automatically created and managed by the system for each streaming table.

Note the pipeline cannot be stopped in the pipeline UI, I suspect one can only stop it by deleting the stream table.

A streaming table could be loading data from another table or from an object storage (e.g. S3), but [[auto loader]] is just for loading data from object storage.

```sql
describe extended `agent-development`.`agent-shared`.`datalake_streaming`
```
ran for 1.5 min, wonder why it is so slow

streaming table vs [[materialized view]]
Materialized view does full refresh and streaming table only appends.
Materialized view can join and streaming table cannot.