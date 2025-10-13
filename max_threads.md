#clickhouse 

The maximum number of [[thread]]s that perform the same stages of the query processing pipeline in parallel ([[parallelism]]). 

It excludes threads for retrieving data from remote servers (see the [[max_distributed_connections]] parameter).

For example, when reading from a table, if it is possible to evaluate expressions with functions, filter with WHERE and pre-aggregate for GROUP BY in parallel using at least ‘max_threads’ number of threads, then ‘max_threads’ are used.

Default value: the number of physical [[CPU]] cores.

For queries that are completed quickly because of a LIMIT, you can set a lower ‘max_threads’. For example, if the necessary number of entries are located in every block and max_threads = 8, then 8 blocks are retrieved, although it would have been enough to read just one.

The smaller the max_threads value, the[]() less memory is consumed.

See also:
- [[merge_tree_min_rows_for_concurrent_read]]