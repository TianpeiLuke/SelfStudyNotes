---
tags:
  - code
  - code_snippet
  - SQL/spark_sql
  - SQL/split
keywords: 
topics: 
language: SQL
date of note: 2025-04-08
---

## Code Snippet Summary

>[!important]
>Split text with separator or some regular expression


## Code

```sql
select MESSAGE_ID, 
    THREAD_ID, 
    ORDER,
    cast(amzn_id_decrypt(split(SENDER,':')[0]) as bigint) AS SENDER_CUSTOMER_ID,
    split(SENDER,':')[2] as SENDER_ROLE,
    ARRIVAL_DATE
from BSM_Body_FE
);
```

- `split(str, regex, limit)` 
	- [reference](https://spark.apache.org/docs/latest/api/sql/index.html#split)
	- Splits `str` around occurrences that match `regex` and returns an array with a length of at most `limit`
	- `regex`: a string representing a regular expression. 
		- The regex string should be a *Java regular expression*.





-----------
##  Recommended Notes

