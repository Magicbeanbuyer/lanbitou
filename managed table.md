#databricks 
Unity Catalog manages the **lifecycle** and **file layout** for these securables. You should not use tools outside of Databricks to manipulate files in managed tables or volumes directly.

- [ ] why not use tools outside of Databricks to manipulate files in managed tables or volumes directly?

Managed tables and volumes are stored in _managed storage_.

**Managed tables always use the Delta table format.** ❌
	you can now read and write Managed Iceberg tables using Databricks or external Iceberg engines via Unity Catalog’s Iceberg REST Catalog API.

All Managed Tables automatically deliver best-in-class read performance and storage optimization using [[Predictive Optimization]].