#clickhouse 
[[async_insert]]
Enables or disables waiting for processing of asynchronous insertion. If enabled, server will return `OK` only after the data is inserted. Otherwise, it will return `OK` even if the data wasn't inserted.

With the wait_for_async_insert setting
- an acknowledgment either immediately after the data got inserted into the buffer (wait_for_async_insert = 0) 
- or by default, after the data got written to a part after flushing from buffer (wait_for_async_insert = 1).