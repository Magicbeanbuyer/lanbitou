#databricks 
A metastore is the top-level container of objects in [[unity catalog]].

Metastores manage data assets (tables, views, and volumes) and the permissions that govern access to them. Databricks account admins can create one metastore for each **region** in which they operate, and **assign them to multiple Databricks workspaces in the same region**. 

Metastores provide **regional isolation** but are not intended as units of data isolation. Data isolation should begin at the [[catalog]] level.
