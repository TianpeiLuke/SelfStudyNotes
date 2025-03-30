---
tags:
  - code
  - code_snippet
  - SQL/concat
  - SQL/groupby
keywords: 
topics: 
language: SQL
date of note: 2025-03-25
---

## Code Snippet Summary

>[!important]
>Assume that a table `tab` has primary key `key1`, and field `key2`, as well as a text field `text_field`.
>```
>tab
>- key1 <- primary key
>- key2
>- text_field    
>```
>
>Complete the following tasks
>- Group by `key2`
>- Concatenate all `text_field` field associated with `key1` into a list, separated by `,`
>
  

## Code

```sql
SELECT
	key2,
	CONCAT_WS(',', COLLECT_LIST(text_field)) as text_field_list
FROM tab
GROUP BY key2
```

- `collect_list` aggregate function
	- [reference](https://docs.databricks.com/aws/en/sql/language-manual/functions/collect_list)
	- syntax 
	  `collect_list ( [ALL | DISTINCT] expr ) [FILTER ( WHERE cond ) ]`
	- `expr`: an expression of any type
	- `cond`: optional, filtering rows used in aggregation
	- returns
		- An ARRAY of the argument type.
		- The order of elements in the array is non-deterministic. `NULL` values are excluded.


- `CONCAT_WS` function
	- [reference](https://www.w3schools.com/sql/func_sqlserver_concat_ws.asp)
	- syntax `CONCAT_WS(_separator, string1_, _string2_, _...._, _string_n_)`
	- The CONCAT_WS() function adds two or more strings together with a *separator*.
	- `seperator`: required. 
	- `_string1, string2, string_n_`: the strings to add together




-----------
##  Recommended Notes


- [[Concatenate Strings with Separator]]
- [[Group by and Aggregate Ordered Text Fields via Concatenation]]

- Medium
	- [Harnessing the Power of COLLECT_LIST() and COLLECT_SET() in PySpark and PySQL](https://medium.com/@rahulgosavi.94/harnessing-the-power-of-collect-list-and-collect-set-in-pyspark-and-pysql-d6926f5383cf)