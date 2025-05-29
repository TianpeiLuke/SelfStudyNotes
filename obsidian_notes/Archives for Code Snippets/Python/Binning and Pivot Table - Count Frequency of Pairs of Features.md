---
tags:
  - code
  - code_snippet
  - python/dataframe
keywords: 
topics: 
language: python
date of note: 2025-01-21
---

## Code Snippet Summary

>[!important]
>Given two features `f1` and `f2`, compute the *count of occurrences* for each pair of values $$p(f_{1}, f_{2})$$ 
>- Output a dataframe, where 
>	- each row corresponds to values of `f1`
>	- each column corresponds to values of `f2`
>	- count of occurrence for each cell
>- If `f2` is binary vector, then the resulting binning of feature `f1` is given by  $$b(f_{1}) :=  \frac{p(f_{1}, 1)}{p(f_{1}, 0) + p(f_{1}, 1)}$$ 

^f5d031

## Code

```python
import pandas as pd
import numpy as np
```

- array of feature 1  `f1`
- array of feature 2 `f2`

```python
f1 = np.array(['a', 'a', 'b', 'c', 'b'], dtype=object)
f2 = np.array([1, 0, 0, 0, 1], dtype=object)
```

- Note if we set the binary variable as type `float`, the binning would fail
	- we should set the binary variable as object

- compute the *instance matrix* using  `pandas.crosstab`

```python
table = pd.crosstab(f1, 
					f2, 
					rownames=['f1'],
					colnames=['f2'],
					margins=True, 
					margins_name = ['total'],
					dropna =True
					)
```

- `pandas.crosstab`
	- [reference](https://pandas.pydata.org/docs/reference/api/pandas.crosstab.html)
	- Compute a simple cross tabulation of two (or more) factors.
		- By default, computes a frequency table of the factors unless an array of values and an aggregation function are passed.
	- Input:
		- **`index`**: value to group by in *rows*
		- **`columns`**: value to group by in *columns*
		- `values`: optional, Array of values to aggregate according to the factors. Requires aggfunc be specified.
		- **`margins`**: Add row/column margins (subtotals).
		- **`margins_name`**: Name of the row/column that will contain the totals when margins is True.
	- Return
		- `DataFrame`

- compute the binning matrix

```python
table_reset = table.reset_index()
table_reset.apply(lambda x: x[1] / (x[1] + x[0]), axis=1)
```




-----------
##  Recommended Notes


- [[Binning]]
- [[Processors Risk Binning]]
- [[Pivot Table using Value of one column as Column Name]]

- Wikipedia
	- [Data binning](https://en.wikipedia.org/wiki/Data_binning)
- Documentation
	- `pandas.crosstab`  [reference](https://pandas.pydata.org/docs/reference/api/pandas.crosstab.html)
	- `pandas.pivot_table` [reference](https://pandas.pydata.org/docs/reference/api/pandas.pivot_table.html)
- Blog
	- [https://docs.kanaries.net/topics/Pandas/pandas-crosstab](https://docs.kanaries.net/topics/Pandas/pandas-crosstab)