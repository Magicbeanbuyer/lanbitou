#clickhouse 

[[clickhouse]]
![[Screenshot 2023-02-14 at 20.23.20.png]]




Clickhouse inserts data ASAP, and merge the files in the background.

When you `INSERT` a bunch of data into `MergeTree`, that bunch is sorted by primary key order and forms a new part. There are background threads that periodically select some parts and merge them into a single sorted part to keep the number of parts relatively low. That’s why it is called `MergeTree`.