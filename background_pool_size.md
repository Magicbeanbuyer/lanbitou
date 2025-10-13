#clickhouse 

Sets the number of threads performing background merges and [[mutation]]s for tables with [[MergeTree]] engines. 

You can only increase the number of threads at runtime. To lower the number of threads you have to restart the server. 

By adjusting this setting, you manage CPU and disk load. 

Smaller pool size utilizes less CPU and disk resources, but background processes advance slower which might eventually impact query performance.

Before changing it, please also take a look at related MergeTree settings:
- [[number_of_free_entries_in_pool_to_lower_max_size_of_merge]]
- [[number_of_free_entries_in_pool_to_execute_mutation]]