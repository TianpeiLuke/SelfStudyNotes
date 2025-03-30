---
tags:
  - code
  - code_snippet
  - deep_dive
  - SQL/groupby
  - SQL
keywords: 
topics:
  - data_analysis
language: SQL
date of note: 2024-03-21
---

## Code Snippet Summary

>[!important]
> - Create a temporary table that indexed by a field
> - *Group by* the index field
> - Generate two columns: 
> 	- *Total count* of items under given index
> 	- The *percentage* (\%) of that count over the whole population in the table; i.e.  $$P(f \,| i)$$
> 	- Round the percentage value to be 2 digits after decimal point
> - *Sort* according to the total count


## Code

```sql
create temp table tab1 as (  
select  
       index,  
       count(distinct feature) as total_feature_count,  
       round(
       cast(count(distinct feature) as float) /  
       cast(
	       (select count(distinct feature) from tab0) 
	       as float) * 100
	       , 2) as total_feature_percentage  
from tab0 
group by index   
);  
  
select *  
from tab1  
order by total_feature_count desc;
```

### Option 3 Create Temp Table and Cross Join

```sql
create temp table tab_total as (
select  
       count(*) as total_count,  
from tab0 
);

create temp table tab1 as (  
select  
       index,  
       count(distinct feature) as total_feature_count,  
from tab0 
group by index   
);  
  
select 
	tab1.index,  
	tab1.total_feature_count,
	ROUND((tab1.total_feature_count::NUMERIC * 100.0 / tab_total.total_count ), 2) as total_feature_percentage
from tab1  
cross join tab_total
order by total_feature_count desc;
```

- Cross Join for SQL 
	- Stack Overflow [What are the uses for Cross Join?](https://stackoverflow.com/questions/219716/what-are-the-uses-for-cross-join)

>[!quote]
>The **CROSS JOIN** is used to generate a *paired combination* of *each row* of the first table with *each row* of the second table. This join type is also known as **cartesian join**.
>
>-- SQLShark [SQL CROSS JOIN with examples](https://www.sqlshack.com/sql-cross-join-with-examples/)

>[!info]
>CROSS JOIN do not need "on" since this is **catesian product**
>
>If table 1 has size $x_{1} \times y_{1}$, and table 2 has size $x_{2}\times y_{2}$, the output of cross join size is $$(x_{1}\,x_{2}) \times (y_{1} + y_{2})$$ 
>- for example, the above operation is the cross join of table of size $r\times 2$ with table of size $1\times 1$, resulting in table of size $$r\times 3$$


## Additional Points

- Add `sortkey` to optimize performance; 
- Use case: sort by index itself
- Add cast conversion to `decimal(10,4)` to avoid floating point representation

```sql
create temp table tab1 sortkey(index) as (  
select  
       index,  
       count(distinct feature) as total_feature_count,  
       round(
       cast(count(distinct feature) as float) /  
       cast(
	       (select count(distinct feature) from tab0) 
	       as float) * 100
	       , 2)::decimal(10, 2) as total_feature_percentage  
from tab0 
group by index   
);  
  
select *  
from tab1  
order by total_feature_count desc;
```







-----------
##  Recommended Notes

- documentation on `ROUND` function in RedShift. [link](https://docs.aws.amazon.com/redshift/latest/dg/r_ROUND.html)
- Stack overflow [redshift-round-function-doesnt-round-in-some-cases](https://stackoverflow.com/questions/65943500/redshift-round-function-doesnt-round-in-some-cases)
- [[Table mfn_abuse_reversals]]
