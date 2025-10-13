#databricks 
Catalogs are the highest level in the data hierarchy (catalog > schema > table/view/volume) managed by the Unity Catalog metastore. 

They are intended as the primary unit of **data isolation** in a typical Databricks data governance model.

Catalogs represent a logical grouping of schemas, usually bounded by data access requirements. Catalogs often mirror **organizational units** or **software development lifecycle** scopes. You may choose, for example, to have a catalog for **production** data and a catalog for **development** data, or a catalog for **non-customer** data and one for **sensitive customer** data.

You must specify a storage location (e.g. S3 bucket) when you create a catalog.

If the catalog is the primary unit of data isolation in the Databricks data governance model, the workspace is the primary environment for working with data assets. Metastore admins and catalog owners can manage access to catalogs independently of workspaces, or they can bind catalogs to specific workspaces to ensure that certain kinds of data are processed only in those workspaces. You might want separate production and development workspaces, for example, or a separate workspace for processing personal data.

By default, access permissions for a securable object are inherited by the children of that object, with catalogs at the top of the hierarchy. This makes it easier to set up default access rules for your data and to specify different rules at each level of the hierarchy only where you need them.

Reading list:
[Isolation of Environments on the Databricks Data I... - Databricks Community - 56737](https://community.databricks.com/t5/technical-blog/isolation-of-environments-on-the-databricks-data-intelligence/ba-p/56737)
[5 Best Practices for Databricks Workspaces - The Databricks Blog](https://www.databricks.com/blog/2022/03/10/functional-workspace-organization-on-databricks.html)