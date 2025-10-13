#clickhouse 

clickHouse takes the right-hand side table and creates a hash table for it in RAM, it is more memory efficient to place the smaller table on the right-hand side of the JOIN.

The `memory_usage` metric in `system.query_log` counts the overall memory reserved for the hash table, though it may not be completely filled.

The fill stage for the hash table runs in a single thread because it is not thread safe.