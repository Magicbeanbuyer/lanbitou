#databricks 

## channel
You can use the `channel` field in the Lakeflow Spark Declarative Pipelines settings to control the Lakeflow Spark Declarative Pipelines runtime version that runs your pipeline. The supported values are:
- `current` to use the current runtime version.
- `preview` to test your pipeline with upcoming changes to the runtime version.

> The pipelines module is only available in the context of a pipeline. It is not available in Python running outside of pipelines. ([link](https://docs.databricks.com/aws/en/ldp/developer/python-dev#basics-of-python-for-pipeline-development))

This is why when importing `pyspark.pipeline` in a databricks job, it fails.


> If you use Lakeflow Spark Declarative Pipelines, Databricks manages **schema location** and other **checkpoint** information automatically. ([link](https://docs.databricks.com/aws/en/ingestion/cloud-object-storage/auto-loader/schema#syntax-for-schema-inference-and-evolution))

