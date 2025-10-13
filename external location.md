#databricks 
External locations =  a path to cloud storage + a storage credential that can be used to access that location.

By default, an external location is accessible from **all of the workspaces in the metastore**. This means that if a user has been granted a privilege (such as `READ FILES`) on that external location, they can exercise that privilege from **any workspace** attached to the metastore. If you use workspaces to isolate user data access, you might want to allow access to an external location only from specific workspaces. This feature is known as **workspace binding** or **external location isolation**.

You can use external locations to register **external tables** and **external volumes** in Unity Catalog.

A **storage credential** encapsulates a long-term cloud credential that provides access to cloud storage. For example, in AWS you can configure an IAM role to access S3 buckets.
