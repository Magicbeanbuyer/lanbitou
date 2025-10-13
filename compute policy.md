#databricks 

Only used by classic [[databricks compute|compute]], not serverless compute.
- [ ] is compute policy used for classic sql warehouse too?
Databricks recommends using compute policies to limit the ability to configure clusters based on a set of rules. 

Compute policies let you restrict access to only **create clusters which are [[Unity Catalog]]-enabled**. 

Using compute policies reduces available choices, which will greatly simplify the cluster creation process for users. 

Compute policies also enable you to control cost by limiting per cluster maximum cost.

To enforce the use of specific custom [[Databricks tag|tags]], use `custom_tags.<tag-name>`. 