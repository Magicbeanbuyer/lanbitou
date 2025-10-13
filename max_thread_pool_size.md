#clickhouse 
ClickHouse uses threads from the [[global thread pool]] to process queries. 

If there is no [[idle thread]] to process a query, then a new thread is created in the pool. 

`max_thread_pool_size` limits the maximum number of threads in the global thread pool.

The maximum number of threads that could be allocated from the OS and used for query execution and background operations like [[merge]]s and [[mutation]]s.

should be equal to [[thread_pool_queue_size]]