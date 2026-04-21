#databricks

Retention is 7 days
delta table supports change data feed, [table_changes](https://docs.databricks.com/aws/en/sql/language-manual/functions/table_changes) function is used to retrieve all the data modifications of a table. 
## questions:
When inserting multiple rows with one insert command, will this create multiple versions or just one new version for the delta table? 