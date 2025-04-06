---
tags:
  - code
  - code_snippet
  - SQL/concat
  - SQL/spark_sql
keywords: 
topics: 
language: SQL
date of note: 2025-03-25
---

## Code Snippet Summary

>[!important]
>Assume the table `tab` has two text fields `text_1` and `text_2`
>
>Concatenate two text fields with seperator to create a new field

## Code

```sql
SELECT
	CONCAT_WS(',', text_1, text_2) as concat_text_12
FROM tab	
```

- `CONCAT_WS` function
	- [reference](https://www.w3schools.com/sql/func_sqlserver_concat_ws.asp)
	- syntax `CONCAT_WS(_separator, string1_, _string2_, _...._, _string_n_)`
	- The CONCAT_WS() function adds two or more strings together with a *separator*.
	- `seperator`: required. 
	- `_string1, string2, string_n_`: the strings to add together

- [concat_ws](https://spark.apache.org/docs/latest/api/sql/index.html#concat_ws)
	- `concat_ws(sep[, str | array(str)]+)`
		- Returns the concatenation of the strings separated by `sep`, skipping null values.


>[!example]
>**Examples:**
> 
> ```sql
> SELECT concat_ws(' ', 'Spark', 'SQL');
>   Spark SQL
> SELECT concat_ws('s');
> 
> SELECT concat_ws('/', 'foo', null, 'bar');
>   foo/bar
> SELECT concat_ws(null, 'Spark', 'SQL');
>   NULL
> ```
> 
> **Since:** 1.5.0




-----------
##  Recommended Notes

- [[Group by and Aggregate Text Fields via Concatenation]]