#databricks 
![[Pasted image 20250808110421.png]]
[[Metastore]]
[[catalog]]
[[Schema]]
Tables:
- [[managed table]] 
- [[External table]]

Views: 
A view is a read-only object derived from one or more tables and views in a metastore.

Rows and columns:
Row and column-level access, along with data masking, is granted using either **dynamic views or row filters and column masks**. Dynamic views are read-only.

Volumes:
Volumes reside in the third layer of Unity Catalog's three-level namespace. They manage **non-tabular** data. You can use volumes to store, organize, and access files in any format, including structured, semi-structured, and **unstructured data**. **Files in volumes cannot be registered as tables.**

Models and functions:
Although they are not, strictly speaking, data assets, registered models and user-defined functions can also be managed in Unity Catalog and reside at the lowest level in the object hierarchy. See Manage model lifecycle in Unity Catalog and User-defined functions (UDFs) in Unity Catalog.

## Plan your data isolation model

Users can only gain access to data based on specified access rules​.
Access to this type of information is typically tightly controlled and **audited** periodically.

In the **centralized** governance model, your governance administrators are owners of the metastore.

In a **distributed** governance model, **the catalog or a set of catalogs is the data domain**. The owner of that catalog can create and own all assets and manage governance within that domain.

Regardless, Databricks strongly recommends that you set a group as the **metastore admin or catalog owner**.

Unity Catalog gives the ability to configure **storage locations at the metastore, catalog, or schema level** to satisfy such requirements.

If such a storage isolation is not required, you can set a storage location at the metastore level. The result is that this location serves as a default location for storing managed tables and volumes across catalogs and schemas in the metastore.  In most scenarios, Databricks recommends storing managed data at the **catalog level.**

If you choose to create a metastore-level managed location, you must ensure that **no users have direct access to it** (that is, through the cloud account that contains it). Giving access to this storage location could allow a user to bypass access controls in a Unity Catalog metastore and disrupt auditability.

- [ ] how to check if a metastore location is configured?

The system evaluates the hierarchy of storage locations from schema to catalog to metastore.

For example, if a table `myCatalog.mySchema.myTable` is created in `my-region-metastore`, the table storage location is determined according to the following rule:

1. If a location has been provided for `mySchema`, it will be stored there.
2. If not, and a location has been provided on `myCatalog`, it will be stored there.
3. Finally, if no location has been provided on `myCatalog`, it will be stored in the location associated with the `my-region-metastore`.

![Unity Catalog storage hierarchy](https://docs.databricks.com/aws/en/assets/images/managed-storage-0fe299ce1b4c32afce5845652093c124.png)

Unity Catalog lets metastore admins, catalog owners, and users with the `MANAGE` permission assign, or **“bind,” catalogs to specific workspaces**. These environment-aware bindings give you the ability to ensure that only certain catalogs are available within a workspace, regardless of the specific privileges on data objects granted to a user.

**Metastore** must be in the same region as the **workspaces** you want to use to access the data. Make sure that this matches the region of the storage **bucket** you created earlier.
## Configure access control

Securable objects in Unity Catalog are hierarchical and privileges are inherited downward. **This means that granting a privilege on a catalog or schema automatically grants the privilege to all current and future objects within the catalog or schema**. 

In order to read data from a table or view a user must have the following privileges:
- SELECT on the table or view
- USE SCHEMA on the schema that owns the table
- USE CATALOG on the catalog that owns the schema

A common scenario is to set up a schema per team where only that team has USE SCHEMA and CREATE on the schema. This means that any tables produced by team members can only be shared within the team.

```sql
GRANT USE CATALOG ON CATALOG < catalog > TO < group >;
GRANT USE SCHEMA ON SCHEMA < catalog >.< schema > TO < group >;
GRANT SELECT ON < catalog >.< schema >.< table_name > TO < group >;
```
You can secure access to columns using a dynamic view in a secondary schema as shown in the following SQL syntax:
```sql
CREATE VIEW < catalog >.< schema >.< view_name > as
SELECT
  id,
  CASE WHEN is_account_group_member(< group >) THEN email ELSE 'REDACTED' END AS email,
  country,
  product,
  total
FROM < catalog >.< schema >.< table_name >;
GRANT USE CATALOG ON CATALOG < catalog > TO < group >;
-- grant on a VIEW!!!???
GRANT USE SCHEMA ON SCHEMA < catalog >.< schema >.< view_name > TO < group >;
GRANT SELECT ON < catalog >.< schema >.< view_name > TO < group >;
```

Compute policies let you restrict access to only create clusters which are Unity Catalog-enabled.

a cluster's access mode [[compute policy]]


[Compute requirements](https://docs.databricks.com/aws/en/data-governance/unity-catalog/#cluster-security-mode)
[Compute configuration reference | Databricks Documentation](https://docs.databricks.com/aws/en/compute/configure#access-mode)
[Audit log system table reference](https://docs.databricks.com/aws/en/admin/system-tables/audit-logs)
[Monitoring Your Databricks Lakehouse Platform with Audit Logs](https://www.databricks.com/blog/2022/05/02/monitoring-your-databricks-lakehouse-platform-with-audit-logs.html)
