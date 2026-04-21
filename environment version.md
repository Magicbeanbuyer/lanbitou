#databricks 

Serverless compute for notebooks and jobs uses environment versions.
Environment versions provide a stable client API based on [[Spark Connect]].

In Databricks, a base environment is a shareable YAML specification that defines a [serverless environment version](https://docs.databricks.com/aws/en/release-notes/serverless/environment-version/) and a set of additional Python dependencies for serverless **notebooks**. Workspace admins create and manage base environments so users can quickly start from a consistent, cached environment and optionally add their own libraries.

For jobs, only notebook tasks can use base environments.

- [Serverless environment versions](https://docs.databricks.com/aws/en/release-notes/serverless/environment-version/)
- [Serverless environment version 4](https://docs.databricks.com/aws/en/release-notes/serverless/environment-version/four)
- [Serverless compute release notes](https://docs.databricks.com/aws/en/release-notes/serverless/#environment-version)
- [Configure the serverless environment | Databricks on AWS](https://docs.databricks.com/aws/en/compute/serverless/dependencies)
- [Databricks on AWS](https://docs.databricks.com/aws/en/admin/workspace-settings/base-environment)