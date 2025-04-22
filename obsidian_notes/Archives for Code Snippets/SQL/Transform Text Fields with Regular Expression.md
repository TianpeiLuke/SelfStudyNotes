---
tags:
  - code
  - code_snippet
  - SQL/regexp
  - SQL/spark_sql
keywords: 
topics: 
language: SQL
date of note: 2025-04-08
---

## Code Snippet Summary

>[!important]
>Transform text in regular expression

## Code

```sql
select MESSAGE_ID, 
    THREAD_ID, 
    ORDER,
    regexp_replace(regexp_replace(SUBJECT, '([^a-zA-Z0-9])', ' '), '(Re|RE)\s+', '') as SUBJECT,
    regexp_replace(regexp_replace(regexp_replace(MESSAGE_BODY, '(")', ''), '\n', ''), '\t', '') as MESSAGE_BODY,  -- remove quotes since hard to load to Pandas
    ARRIVAL_DATE
from BSM_Body_FE
```

- `regexp_replace(str, regexp, rep[, position])`
	- [reference](https://spark.apache.org/docs/latest/api/sql/index.html#regexp_replace)
	- Replaces all substrings of `str` that match `regexp` with `rep`.
	- `regexp` 
		- a string representing a regular expression. The regex string should be a *Java regular expression*.
	- `rep` 
		- a string expression to replace matched substrings.
	- `position` 
		- a positive integer literal that indicates the position within `str` to *begin searching*. The default is 1. If position is greater than the number of characters in `str`, the result is `str`.


- `regexp(str, regexp)`
	- [reference](https://spark.apache.org/docs/latest/api/sql/index.html#regexp)
	- Returns true if `str` matches `regexp`, or false otherwise.
	- `str` 
		- a string expression
	- `regexp` 
		- a string expression. The regex string should be a Java regular expression.



-----------
##  Recommended Notes

