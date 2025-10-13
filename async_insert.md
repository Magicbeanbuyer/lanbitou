#clickhouse 
By default, ClickHouse is writing data synchronously. Each insert sent to ClickHouse causes ClickHouse to immediately create a [[part]] containing the data from the insert.

By setting async_insert to 1, ClickHouse first stores the incoming inserts into an in-memory buffer before flushing them regularly to disk.[]()

- buffer size has reached N KB in size (N is configurable via [async_insert_max_data_size](https://clickhouse.com/docs/en/operations/settings/settings#async-insert-max-data-size))
- at least N ms has passed since the last buffer flush (N is configurable via [async_insert_busy_timeout_ms](https://clickhouse.com/docs/en/operations/settings/settings#async-insert-busy-timeout-ms))

Manual batching has the advantage that it supports the [built-in automatic deduplication](https://clickhouse.com/docs/en/engines/table-engines/mergetree-family/replication) of table data if (exactly) the same insert statement is sent multiple times to ClickHouse, for example, because of an automatic retry in client software because of some temporary network connection issues.

Generally, we recommend inserting data in fairly large batches of at least 1,000 rows at a time, and ideally between 10,000 to 100,000 rows.

To achieve this, consider implementing a buffer mechanism such as using the [Buffer table Engine](https://clickhouse.com/docs/en/engines/table-engines/special/buffer) to enable batch inserts, or use asynchronous inserts.

And, if a single insert query contains more than 1 million rows, ClickHouse will create more than one new part for the query’s data. 

- [ ] why break inserts into multiple batches?
