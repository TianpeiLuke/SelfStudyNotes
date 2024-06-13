---
tags:
  - code
  - code_snippet
  - SQL/code_example
keywords: 
topics: 
language: SQL
date of note: 2024-04-19
---

## Code Snippet Summary

>[!important]
>Compute Area-Under-Curve (**AUC**) for Receiver Characteristic Curve (**ROC**)  for a score distribution based on corresponding labels
>- ROC is a plot of `(FPR, TPR)` with x-axis = FPR, and y-axis = TPR
> $$FPR = \frac{FP}{N},\; TPR = \frac{TP}{P}$$
>- AUC is computed via the **trapezoid idea**:
>  $$AUC = \sum_{i=1}^{n}\frac{1}{2}(TPR_{i+1} + TPR_{i})(FPR_{i+1} - FPR_{i})$$


## Code

```sql
/*  setting in Spark SQL to enable Cross-Join */
set spark.sql.crossJoin.enabled=true;

WITH data AS (
SELECT id,
	score,    -- model score
	label,    -- ground truth label in {0, 1}
    1 as dummy -- used as a weight
FROM tab
),

/*  partition scores into bins based on quantile */
binned_data AS (
SELECT dummy,
    score,
    label,
    -- increase the number of bins for a more precise calculation
    ntile(100) OVER (PARTITION BY dummy ORDER BY score) AS BIN
FROM data
),

/*  count the total number of ids with label = 1 */
total_summary AS (
SELECT dummy,
    count(*) as TOTAL_CNT,
    sum(label) as TOTAL_POS_COUNT
FROM data
GROUP BY dummy
),

/*  count the total number of ids with label = 1 for each bin */
binned_summary AS (
SELECT dummy,
    BIN,
    count(*) as BIN_TOTAL_CNT,
    sum(label) as BIN_POS_COUNT
FROM binned_data
GROUP BY dummy, BIN
),

/*  main query:  
1. sort by bin, 
2. for each bin, compute FPR = (FP)/ N, and TPR = (TP) / P
3. compute FP or TP via the cumulative sum of pos count or neg count above
4. join with total pos (P) and neg count (N)
*/
ROC AS (
SELECT b1.dummy,
    b1.BIN,
    s.TOTAL_POS_COUNT,
    s.TOTAL_CNT,
    
    -- the false positive rate =  FP / N
    -- FP = sum of true negative count for all above bins
    cast(sum(b2.BIN_TOTAL_CNT) - sum(b2.BIN_POS_COUNT) as float)/cast(s.TOTAL_CNT -s.TOTAL_POS_COUNT as float) as False_Positive_Rate,
    
    -- the true positive rate = TP/ P
    -- TP = the sum of true positive count for all above bins
    cast(sum(b2.BIN_POS_COUNT) as float)/s.TOTAL_POS_COUNT as True_Positive_Rate,  

    -- this is the ranking id
    row_number() over (PARTITION BY b1.dummy ORDER BY b1.BIN DESC) as i

FROM binned_summary b1
-- CROSS JOIN is used to compute the cumulative sum of bins above the each bin
CROSS JOIN binned_summary b2     
	ON b1.dummy = b2.dummy
		  AND b2.BIN >= b1.BIN -- count all bins above a given bin
-- LEFT JOIN with total positive and total negative count
LEFT JOIN total_summary s
    ON s.dummy = b1.dummy

GROUP BY b1.dummy,
        b1.BIN,
        s.TOTAL_ABUSE_COUNT,
        s.TOTAL_CNT
)


/* Compute the AUC using the trapezoid idea: 
AUC_{i, i+1} = 0.5 * (B.TPR + A.TPR) * (B.FPR - A.FPR)
AUC = \sum_{i=1}^{N} AUC_{i, i+1}
*/
SELECT
    A.dummy,
    sum((B.False_Positive_Rate - A.False_Positive_Rate) * (A.True_Positive_Rate + B.True_Positive_Rate) * 0.5) as AUC
FROM ROC A
JOIN ROC B
    ON A.dummy = B.dummy
    AND A.i + 1 = B.i
GROUP BY A.dummy
;
```


- The SQL `NTILE()` is a [window function](https://www.sqltutorial.org/sql-window-functions/) that allows you to break the result set into a specified number of approximately equal groups, or buckets.
	- It *assigns each group a bucket number* starting from one. 
	- For each row in a group, the `NTILE()` function assigns a *bucket number* representing the group to which the row belongs.
	  
- The syntax of the `NTILE()` function is as follows:

```SQL
NTILE(buckets) OVER (PARTITION BY expr1, expr2,... 	ORDER BY expr1 [ASC|DESC], expr2 ... )
```



-----------
##  Recommended Notes

- SQL Tutorial [`NTILE`](https://www.sqltutorial.org/sql-window-functions/sql-ntile/)
- [SQL | Window Functions | NTILE()](https://www.codecademy.com/resources/docs/sql/window-functions/ntile)
- Amazon Redshift [NTILE window function](https://docs.aws.amazon.com/redshift/latest/dg/r_WF_NTILE.html)

- Blog [AUC with SQL](https://roywrightme.wordpress.com/2018/01/11/auc-sql/)
  
- A similar computation in Python Pandas [[Risk Value Mapping of Categorical Field]]