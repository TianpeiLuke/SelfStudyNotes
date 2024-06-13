---
tags:
  - code
  - code_snippet
keywords: 
topics: 
language: 
date of note: 2024-04-04
---

## Code Snippet Summary

>[!important]
>Given a dataframe `df` with `col1` and `datetime2` columns
>- **Group** by `col1`
>- For *each group*, find the *min* and *max* value of the `datetime2`
>- Compute the *time difference* between min and max value
>- Report the *maximum time gap* of `datetime2` within group of `col1`


## Code

```python
import pandas as pd


result = df.groupby('col1')['datetime2'].agg(['min', 'max'])

# compute time difference in days
result['max_gap'] = (pd.to_datetime(result['max']) -  pd.to_datetime(result['min'])).dt.days

# sort gap value in descending order
result = result.reset_index().sort_values(by=['max_gap'], ascending=False)

```

- `pandas.DataFrameGroupby`
	- `agg()`: [reference](https://pandas.pydata.org/docs/reference/api/pandas.core.groupby.DataFrameGroupBy.agg.html#pandas.core.groupby.DataFrameGroupBy.agg)
		- **`func`**: Function to use for *aggregating the data*. If a function, must either work when passed a DataFrame or when passed to DataFrame.apply.
			- Accepted combinations are:
				- **function**
				- **string function name**
				- **list** of *functions* and/or *function names*, e.g. `[np.sum, 'mean']`
				- **dict** of *axis labels -> functions*, *function names* or *list* of such.
				- *None*, in which case `**kwargs` are used with Named Aggregation. Here the output has one column for each element in `**kwargs`. The name of the column is keyword, whereas the value determines the aggregation used to compute the values in the column.
			- Can also accept a **Numba JIT function** with `engine='numba'` specified. Only passing a single function is supported with this engine.
				- If the `'numba'` engine is chosen, the function must be a user defined function with `values` and `index` as the first and second arguments respectively in the function signature. Each group’s index will be passed to the user defined function and optionally available for use.
		- **`args`**: Positional arguments to pass to func.
		- **`engine`**: default None
			- `'cython'` : Runs the function through **C-extensions** from **cython**.
			- `'numba'` : Runs the function through **JIT compiled code** from **numba**.
			- `None` : Defaults to `'cython'` or globally setting `compute.use_numba`
- `pandas.NamedAgg`: [reference](https://pandas.pydata.org/docs/reference/api/pandas.NamedAgg.html#pandas.NamedAgg)
	- **`column`**: *Column label* in the DataFrame to apply aggfunc.
	- **`aggfunc`**: *Function* to apply to the provided column. If string, the name of a built-in pandas function.

```python
# new columns 'b_min' and 'c_sum' are introduced

df.groupby("A").agg(
...     b_min=pd.NamedAgg(column="B", aggfunc="min"),
...     c_sum=pd.NamedAgg(column="C", aggfunc="sum")
... )
```



-----------
##  Recommended Notes

- [[Compute time difference between two time fields in DataFrame]]
- [[GroupBy and Sort within Group]]
- `pandas.DataFrame`: [reference](https://pandas.pydata.org/pandas-docs/stable/reference/frame.html)
	- **Group by: split-apply-combine**: [User Guide](https://pandas.pydata.org/docs/user_guide/groupby.html)
	- `reset_index()`:  [reference](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.reset_index.html#pandas.DataFrame.reset_index)