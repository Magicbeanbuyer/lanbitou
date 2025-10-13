---
tags:
  - snowflake
---
A session is maintained indefinitely with continued user activity. After a period of inactivity in the session, known as the idle session timeout, the user must authenticate to Snowflake again. 

If the Snowflake session expires but the IdP session remains active, a user can log in to Snowflake without entering their login credentials again (i.e. silent authentication).

Snowflake creates a new session for each worksheet in Snowsight. A worksheet session enforces the session policy that applies to the user that creates the worksheet.

The following two statement contradicts each other?
- Active queries are not canceled when the session ends and the user is logged out, even if the [ABORT_DETACHED_QUERY](https://docs.snowflake.com/en/sql-reference/parameters.html#label-abort-detached-query) parameter is set to true.
- All in-progress synchronous queries are aborted immediately regardless of the parameter value.