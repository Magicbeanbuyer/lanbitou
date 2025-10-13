#databricks

# account admin
- create metastores
- create metastore admins
- create workspaces
- user management
- cloud resources
- account usage monitoring
- Manage identities - sync the identity provider with Databricks

# [[workspace]] admin
You must be a workspace admin to create [[serverless budget policy|serverless budget policies]]. Non-admins can manage policies if they are assigned `Serverless budget policy: Manager` permissions. 
Workspace admins can manage and view serverless budget policies they created or the ones they have explicit permissions on. To view and manage all policies for a given account, the workspace admin must additionally have the [[#Billing admin]] account-level role.
## Manage workspace identities
If your workspace is enabled for [[Unity Catalog]], identities should be added at the **account** level. 
Workspace admins can then assign users, groups, and service principals to their workspace.
## Manage workspace access control
Limit workspace users' cluster creation options with [[cluster policies]].
Databricks recommends managing all init scripts as cluster-scoped init scripts.
- [ ] what is cluster-scoped init scripts and global init scripts? 
Instead of using global init scripts, manage init scipts using cluster policies.
## Manage workspace settings and features 


# [[metastore]] admin
- Change ownership of catalogs
- Manage and delegate permissions on the init script and jar allowlist.
- Delegate the ability to create catalogs and other top-level permissions to non-workspace admins.
- Receive shared data through Delta Sharing.
- Use clean rooms.
- Remove default workspace admin permissions.
- Add managed storage to the metastore, if it has none
- Manage privileges and ownership for all securable objects within a [[Unity Catalog]] [[metastore]]
- [ ] what is managed storage to an existing metastore?

[]()# Billing admin
![[Screenshot 2025-08-08 at 10.58.51.png]]
[Manage users, service principals, and groups | Databricks Documentation](https://docs.databricks.com/aws/en/admin/users-groups/)
[Compute configuration reference | Databricks Documentation](https://docs.databricks.com/aws/en/compute/configure#access-mode)