#clickhouse 
You can also free up resources if your server has a lot of [[idle thread]]s - using the `max_thread_pool_free_size` setting. The default is 1,000, which means your Global Thread pool will never have more than 1,000 idle threads.

see also
[[max_thread_pool_size]]