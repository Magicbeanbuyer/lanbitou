---
tags:
  - snowflake
---
Each virtual warehouse is an MPP compute cluster composed of multiple compute nodes allocated by Snowflake from a cloud provider.
When a warehouse is running, even if there is no query running, it costs credits.
Warehouse are on-demand clusters. 

How long does it take for a warehouse to start?

resizing a warehouse can enable limited scaling for query concurrency and queuing; however, warehouse resizing is primarily intended for improving query performance.
To enable fully automated scaling for concurrency, Snowflake recommends [multi-cluster warehouses](https://docs.snowflake.com/en/user-guide/warehouses-multicluster)


When a [[session]] is initiated in Snowflake, the session does not, by default, have a warehouse associated with it.

multi-cluster run one query quicker or more queries at once?
what is considered memory intensive workload for a snowpark warehouse?
table primary key?
is iceberg table loaded into snowflake managed storage and cost money?