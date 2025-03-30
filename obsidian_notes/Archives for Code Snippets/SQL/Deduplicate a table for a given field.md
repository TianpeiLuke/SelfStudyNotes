---
tags:
  - code
  - code_snippet
  - SQL
  - SQL/partition_by
  - SQL/having
  - SQL/groupby
keywords: 
topics: 
language: SQL
date of note: 2024-04-04
---

## Code Snippet Summary

>[!important]
>Given a table `tab` with potential duplicates in field `field1`, write SQL program to **remove duplicates** in `field1`

## Code

### Using `ROW_NUMBER()` and `PARTITION BY`

>[!info] 
>**Option 1**
>- Use **`ROW_NUMBER() OVER ()`** **window function** combining with **`PARTITION BY`** and **`ORDER BY`** commands

- **`ROW_NUMBER() OVER ()`**

```SQL
SELECT *
FROM (
    SELECT *,
    ROW_NUMBER() OVER (PARTITION BY field1 ORDER BY field1) as RN
    FROM (
	        SELECT *       
	        FROM tab
        )
    )
    WHERE RN = 1
);
```

Similarly, we can delete the duplicated rows using **`DELETE` command** and   [**`Common Table Expression` (CTE)**](https://technet.microsoft.com/en-us/library/ms190766(v=sql.105).aspx)  

```SQL
WITH tab2 AS (
SELECT *,
    ROW_NUMBER() OVER (PARTITION BY field1 ORDER BY field1) as RN
FROM (
		SELECT *       
		FROM tab
    )
)

DELETE FROM tab2 WHERE RN > 1;
```

### Using `GROUP BY` and `HAVING`

>[!info]
>**Option 2**
>- Use **`GROUP BY`  and `HAVING` clause**

```SQL
SELECT field1,
	count(*) as field1_duplicate_cnt
FROM tab
GROUP BY field1
;
```

Then to remove the duplicated rows using **`DELETE` command** and **`HAVING` clause**

```SQL
DELETE FROM (
	SELECT field1,
		count(*) as field1_duplicate_cnt
	FROM tab
	GROUP BY field1
	HAVING count(*) > 1
)
```


### Using `RANK()` and `PARTITION BY`

>[!info]
>**Option 3**
>- Use **`RANK() OVER ()`  window function** combining with **`PARTITION BY`** and **`ORDER BY`** commands

```SQL
SELECT *
FROM (
    SELECT *,
    RANK() OVER (PARTITION BY field1 ORDER BY field1) as RN
    FROM (
	        SELECT *       
	        FROM tab
        )
    )
    WHERE RN = 1
);
```


### Using `DISTINCT`

>[!info]
>**Option 4**
>- Use **`DISTINCT`** to return unique values of a field

```SQL
SELECT distinct field1
FROM tab
```



-----------
##  Recommended Notes

- [Different ways to SQL delete duplicate rows from a SQL Table](https://www.sqlshack.com/different-ways-to-sql-delete-duplicate-rows-from-a-sql-table/)