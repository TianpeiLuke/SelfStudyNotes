---
tags:
  - code
  - code_snippet
  - SQL/cradle
keywords: 
topics: 
language: SQL
date of note: 2025-01-03
---

## Code Snippet Summary

>[!important] 
>Using **job run date** to define the time interval for SQL query


## Code

>[!quote]
>ETLM used the Amazon Redshift so it follows the redshift syntax

- `to_date('{RUN_DATE_YYYY/MM/DD}', 'YYYY/MM/DD')`: transform the job run date in string format `{RUN_DATE_YYYY/MM/DD}` into date format
- using `>=` and `<=` or using `BETWEEN ... AND` for time window



### Use Wildcards for Time

#### Run-Time Wildcards

>[!quote]
>All Date ildcards show up as *strings* in [SQL](https://w.amazon.com/bin/view/SQL "SQL"). To compare them to a Date column, you need to *wrap* them in a `TO_DATE`: 
>- e.g. `TO_DATE('{RUN_DATE_YYYY/MM/DD}', 'YYYY/MM/DD')`


![[Amazon ETLManager Wildcards#^09b72f]]

- [[Amazon ETLManager Wildcards]]

#### Job Wild Cards

![[Amazon ETLManager Wildcards#^65efab]]

```sql
SELECT * FROM tab1 
WHERE TO_DATE({DIST_YYYYMMDDHH24MISS_UTC}, 'YYYYMMDDHH24MISS') AND TO_DATE({DIET_YYYYMMDDHH24MISS_UTC}, 'YYYYMMDDHH24MISS');
```

- `DIST_YYYYMMDDHH24MISS_UTC` is the MACRO for the *starting date* in the job profile
- `DIET_YYYYMMDDHH24MISS_UTC` is the MACRO for the *end date* in the job profile



-----------
##  Recommended Notes


- Cradle Docs: 
	- [Handling Dates in Cradle](https://w.amazon.com/bin/view/BDT/Products/Cradle/Docs/HandlingDates)

- [[Date Filter in Amazon Redshift SQL]]
