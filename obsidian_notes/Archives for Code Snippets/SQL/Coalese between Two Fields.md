---
tags:
  - code
  - code_snippet
  - SQL/coalese
keywords: 
topics: 
language: SQL
date of note: 2025-03-22
---

## Code Snippet Summary

>[!important]
>Combine two fields so that if one field is missing it is filled by the other field


## Code

```sql
COALESCE(_val1_, _val2_, _...._, _val_n_)
```

- `coalesce(expr1, expr2, ...)`
	- [reference](https://spark.apache.org/docs/latest/api/sql/index.html#coalesce)
	- Returns the first non-null argument if exists. Otherwise, null.




-----------
##  Recommended Notes

