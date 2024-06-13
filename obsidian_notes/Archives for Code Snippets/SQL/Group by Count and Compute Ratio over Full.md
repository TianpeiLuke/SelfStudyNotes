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
date of note: 2024-03-21
---

## Code Snippet Summary

- Create a temporary table that indexed by a field
- Group by the index field
- Generate two columns: 
	- Total count of items under given index
	- The percentage (\%) of that count over the whole population in the table; i.e.  P(f | i)
	- Round the percentage value to be 2 digits after decimal point
- Sort according to the total count

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
