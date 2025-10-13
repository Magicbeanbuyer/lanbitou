#databricks
Tag data can be replicated globally. Do not use tag names or values that could compromise the security of your resources. For example, do not use tag names that contain personal or sensitive information.

## compute tag
Cost attribution can be done for all compute [[stock keeping unit|SKUs]] with a tagging strategy, whether for a classic or serverless [[databricks compute|compute]] model. 

Classic compute (workflows, Declarative Pipelines, SQL Warehouse, etc.) inherits tags on the cluster definition, while serverless adheres to [[Serverless Budget Policy|Serverless Budget Policies]]. 
Note: Serverless SQL warehouse inherits tags on the cluster definition and doesn't use Serverless Budget Policies.

To enforce the use of specific custom tags, for classic compute use [[compute policy|compute policies]]; for serverless compute, use serverless budget policies.

To ensure that certain tags are always populated when compute resources are created across a workspace, you can apply a specific IAM policy to your workspace's primary IAM role (the one created during workspace setup; contact your AWS administrator if you need access). The IAM policy should include explicit Deny statements for mandatory tag keys and optional values. Cluster creation will fail if required tags with one of the allowed values aren't provided.

Note: also not for serverless.

- [ ] when to use IAM policy and when to use compute policies for tag enforcement?

## object tag
Tag policies are account-level controls that define constraints on tags assignable to objects in Databricks, such as tables and catalogs. 

Tag policies ensure that tags are consistently applied and conform to organizational standards. They help prevent inconsistent naming, unauthorized tag assignments, or incorrect tag values. Tag policies allow administrators to:
- Specify which tag keys are governed.
- Define the set of allowed values for each governed tag.
- Control which users and groups can assign governed tags to resources and manage governed tag definitions.

