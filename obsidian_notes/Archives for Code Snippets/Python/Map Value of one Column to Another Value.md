---
tags:
  - code
  - code_snippet
  - python/dataframe
keywords: 
topics: 
language: python
date of note: 2024-04-06
---

## Code Snippet Summary

>[!important]
>Assume a DataFrame `df` has a column `col1`.
>- Map value of `col1` according to a dictionary `dict_map = {key1: value1, ...}`, where the `key` is the current value and the `value` the mapped value


## Code

```python
import pandas as pd

df['col1'] = df['col1'].map(dict_map)
```

- `Series.map()`: Map values of Series according to an input mapping or function. [reference](https://pandas.pydata.org/docs/reference/api/pandas.Series.map.html#pandas.Series.map)
	- Used for **substituting** each value in a Series with another value, that may be derived from a *function*, a *`dict`* or a [`Series`](https://pandas.pydata.org/docs/reference/api/pandas.Series.html#pandas.Series "pandas.Series").
	- **`arg`**: *function, collections.abc.Mapping subclass or Series*. Mapping correspondence.


-----------
##  Recommended Notes

- `Series.map()`: Map values of Series according to an input mapping or function. [reference](https://pandas.pydata.org/docs/reference/api/pandas.Series.map.html#pandas.Series.map)