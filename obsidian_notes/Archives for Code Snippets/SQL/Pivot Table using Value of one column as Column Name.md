---
tags:
  - code
  - code_snippet
  - sql
  - deep_dive
keywords: 
topics:
  - data_analysis
language: SQL
date of note: 2024-03-22
---

## Code Snippet Summary

- Create a temporary table with three columns: `col_1` as categorical, `col_2` as categorical, `col_3` as numeric
- Create a **Pivot table** 
	- Using all available categories in `col_2` as the *name of column*
	- Using categories in `col_1` as *name of row*
	- Compute sum value of numeric `col_3` for each (`col_1`, `col_2`) pair


## Code

```sql
create temp table tab1 as (  
select  
       col_1,
       col_2,
       col_3 
from tab0 
);  
  
select *  
from tab1 pivot (sum(col_3) for col_2 in ('class_1', 'class_2')
				)
order by total_feature_count desc;
```

| `col_2`   | `col_1:class_1`             | `col_1::class_2`            |
| :-------- | :-------------------------- | :-------------------------- |
| `col_2:a` | `sum(col_3 \| (a, class1))` | `sum(col_3 \| (a, class2))` |
| `col_2:b` | `sum(col_3 \| (b, class1))` | `sum(col_3 \| (b, class2))` |


## Additional Points

- The `PIVOT` operator accepts optional aliases on the aggregate expression and on each value for the `IN` operator. Use aliases to customize the column names. If there is no aggregate alias, only the `IN` list aliases are used. Otherwise, the aggregate alias is appended to the column name with an underscore to separate the names.
- `PIVOT` table is the transposed version of the `GROUP BY`



-----------
##  Recommended Notes

- documentation on `PIVOT` table example in RedShift. [link](https://docs.aws.amazon.com/redshift/latest/dg/r_FROM_clause-pivot-unpivot-examples.html)
- doc of `FROM` clause in Redshift [link](https://docs.aws.amazon.com/redshift/latest/dg/r_FROM_clause30.html)
- [[Table mfn_abuse_reversals]]

