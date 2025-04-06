---
tags:
  - code
  - code_snippet
  - SQL/concat
  - SQL/groupby
  - SQL/spark_sql
keywords: 
topics: 
language: SQL
date of note: 2025-03-25
---

## Code Snippet Summary

>[!important]
>Assume that a table `tab` has primary key `key1`, and field `key2`, a time field `time_field` and  a text field `text_field`.
>```
>tab
>- key1 <- primary key
>- time_field 
>- key2
>- text_field    
>```
>
>Complete the following tasks
>- Group by `key2`
>- Concatenate all `text_field` field associated with `key1` into a list, separated by `,`
>- During the concatenation, make sure `text_field` are arranged according to `time_field`
  

## Code

```sql
SELECT
	key2,
	-- access second field of struct after sorting 
	CONCAT_WS(' ', 
		SORT_ARRAY(
			COLLECT_LIST(
				STRUCT(time_field, text_field) 
				) 
			).col2 
		) as ordered_messages
FROM tab
GROUP BY key2
```

- It uses `struct` to create a struct object with time as first field
- `collect_list` will collect all `struct` objects during the group by, then return an array of `struct` objects 
- `sort_array` will sort this array based on the *first field* in `struct` object
- `.col2` will return the list of `second field` from the list of `struct` objects
- `concat_ws` concatenate the returned ordered list into one field

>[!example]
> ```sql
> -- Sample data
> CREATE TEMPORARY VIEW messages AS (
>     SELECT '2023-01-01' as ARRIVAL_DATE, 'First message' as MESSAGE_BODY UNION ALL
>     SELECT '2023-01-03' as ARRIVAL_DATE, 'Third message' as MESSAGE_BODY UNION ALL
>     SELECT '2023-01-02' as ARRIVAL_DATE, 'Second message' as MESSAGE_BODY
> );
> 
> -- Using STRUCT and SORT_ARRAY
> SELECT 
>     CONCAT_WS(' ',
>         SORT_ARRAY(
>             COLLECT_LIST(
>                 STRUCT(ARRIVAL_DATE, MESSAGE_BODY)
>             )
>         ).col2  -- access second field of struct after sorting
>     ) as ordered_messages
> FROM messages;
> 
> -- Result:
> -- "First message Second message Third message"
> 
> ```


- `collect_list` aggregate function
	- [reference](https://docs.databricks.com/aws/en/sql/language-manual/functions/collect_list)
	- [reference API](https://spark.apache.org/docs/latest/api/sql/index.html#collect_list)
	- `collect_list(expr)` 
		- Collects and returns a list of non-unique elements.

>[!example]
> **Examples:**
> 
> ```sql
> SELECT collect_list(col) FROM VALUES (1), (2), (1) AS tab(col);
>  [1,2,1]
> ```
> 
> **Note:**
> 
> The function is non-deterministic because the order of collected results depends on the order of the rows which may be non-deterministic after a shuffle.


- `struct`:
	- [reference](https://docs.databricks.com/aws/en/sql/language-manual/data-types/struct-type)
	- [struct](https://spark.apache.org/docs/latest/api/sql/index.html#struct)
	- `struct(col1, col2, col3, ...)` 
		- Creates a struct with the given field values.
	- `STRUCT < [fieldName [:] fieldType [NOT NULL] [COLLATE collationName] [COMMENT str] [, …] ] >`
		- `fieldName`: An identifier naming the field. The names need not be unique.
		- `fieldType`: Any data type.
	- In the example above, `STRUCT(ARRIVAL_DATE, MESSAGE_BODY)` returns
```
[
    {'col1': '2023-01-01', 'col2': 'First message'},
    {'col1': '2023-01-03', 'col2': 'Third message'},
    {'col1': '2023-01-02', 'col2': 'Second message'}
]
```

>[!example]
>**Examples:**
> 
> ```sql
> SELECT struct(1, 2, 3);
>  {"col1":1,"col2":2,"col3":3}
> ```
> 
> **Since:** 1.4.0


- `sort_array`
	- [reference](https://docs.databricks.com/aws/en/sql/language-manual/functions/sort_array)
	- [Spark SQL link](https://spark.apache.org/docs/latest/api/sql/index.html#sort_array)
	- `sort_array(array[, ascendingOrder])` 
		- Sorts the input array in ascending or descending order according to the natural ordering of the array elements. NaN is greater than any non-NaN elements for double/float type. Null elements will be placed at the beginning of the returned array in ascending order or at the end of the returned array in descending order.
	- `sort_array(expr [, ascendingOrder] )`
		- `expr`: An `ARRAY` expression of sortable elements.
		- `ascendingOrder`: An optional `BOOLEAN` expression defaulting to `true`.
		- Sorts the input array in ascending or descending order according to the natural ordering of the array elements. `NULL` elements are placed at the beginning of the returned array in ascending order or at the end of the returned array in descending order.
	- In this example, `sort_array` sort `struct` by the first field 
		- This is the default ordering of Spark SQL
```
[
    {'col1': '2023-01-01', 'col2': 'First message'},
    {'col1': '2023-01-02', 'col2': 'Second message'},
    {'col1': '2023-01-03', 'col2': 'Third message'}
]
```
- `.col2` extracts just the messages in sorted order:
```
['First message', 'Second message', 'Third message']
```


>[!example]
>**Examples:**
> 
> ```sql
> SELECT sort_array(array('b', 'd', null, 'c', 'a'), true);
>  [null,"a","b","c","d"]
> ```
> 
> **Since:** 1.5.0


- Finally `CONCAT_WS` concatenate them
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

- Spark SQL API 
	- [doc link](https://spark.apache.org/docs/latest/api/sql/index.html)

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



- [[Group by and Aggregate Text Fields via Concatenation]]
- [[Concatenate Strings with Separator]]

- Medium
	- [Harnessing the Power of COLLECT_LIST() and COLLECT_SET() in PySpark and PySQL](https://medium.com/@rahulgosavi.94/harnessing-the-power-of-collect-list-and-collect-set-in-pyspark-and-pysql-d6926f5383cf)