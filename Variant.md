#snowflake 

❓Operators : and subsequent . and [] always return VARIANT values containing strings.

```sql
select
    PARSE_JSON(' { "key1": "value1", "key2": "value2" } ') as a
    , a:key1 as b
    , typeof(b)
```

```markdown
|   |   |   |
|---|---|---|
|A|B|TYPEOF(B)|
|{ "key1": "value1", "key2": "value2" }|"value1"|VARCHAR|
```
why is type of b `VARCHAR`?