#clickhouse 
It defines the minimum number of rows a single query execution thread should read.

If at least as many lines are read from one file, the reading can be parallelized.

If the number of rows to be read from a file of a [[MergeTree]] table exceeds merge_tree_min_rows_for_concurrent_read then ClickHouse tries to perform a concurrent reading from this file on several [[thread]]s.

