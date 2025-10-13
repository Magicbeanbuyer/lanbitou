 #databricks
 tables whose data lifecycle and file layout are managed using your cloud provider and other data platforms, not [[Unity Catalog]]. 
 
 Typically you use external tables to register **large amounts of your existing data**, or if you also require **write access to the data using tools outside of Databricks** clusters and Databricks SQL warehouses. 
 
 Once an external table is registered in a Unity Catalog metastore, you can manage and audit Databricks access to it just like you can with managed tables.

![External locations](https://docs.databricks.com/aws/en/assets/images/external-locations-eeb842410decae15aa122f90957f1ad2.png)

Databricks recommends giving the CREATE EXTERNAL LOCATION permission only to an administrator who is tasked with setting up connections between Unity Catalog and cloud storage. 

To provide other users with more granular access, Databricks recommends **registering external tables or volumes on top of [[external location|external locations]]** and granting users access to data using volumes or tables. Since tables and volumes are children of a catalog and schema, catalog or schema administrators have the ultimate control over access permissions.

Don't grant general READ FILES or WRITE FILES permissions on external locations to end users. With the availability of [[volume]]s, users shouldn't use external locations for path-based access.

Explore existing files in cloud storage before you create an external table or volume at a specific prefix. The READ FILES privilege is a precondition.

Avoid path overlap conflicts: **never create external volumes or tables at the root of an external location.** If you do create external volumes or tables at the external location root, you can't create any additional external volumes or tables on the external location. 

Databricks recommends that you create external tables using **one external location per schema**.
- [ ] why create external tables using **one external location per schema**?

Databricks strongly recommends against registering a table as an external table in more than one metastore due to the risk of consistency issues. For example, a change to the schema in one metastore will not register in the second metastore. 
