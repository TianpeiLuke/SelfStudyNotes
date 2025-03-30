---
tags:
  - code
  - code_snippet
  - python/dataframe
keywords: 
topics: 
language: python
date of note: 2025-01-29
---

## Code Snippet Summary

>[!important]
>Convert the output of `df.value_counts()` into dataframe


## Code

```python
import pandas as pd
```

```python
df = df.value_counts().rename_axis('unique_values').reset_index(name='counts')
```

- [`rename_axis`](http://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.rename_axis.html)
	- set the axis name as `unique_values`
	- **mapper**: Value to set the axis name attribute.
	- **index, columns**: optional, 
		- A scalar, list-like, dict-like or functions transformations to apply to that axis’ values.
	- **axis**
		- The axis to rename.

- [`reset_index`](http://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.reset_index.html):
	- Reset the index, or a level of it.
		- Reset the index of the DataFrame, and use the default one instead. 
		- If the DataFrame has a MultiIndex, this method can *remove one or more levels*.
	- **names**
		- Using the given string, rename the DataFrame column which contains the index data. If the DataFrame has a MultiIndex, this has to be a list or tuple with length equal to the number of levels.






-----------
##  Recommended Notes


- [`rename_axis`](http://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.rename_axis.html)
	- Set the name of the axis for the index or columns.


- Stack Overflow
	- [Python Pandas: Convert ".value_counts" output to dataframe](https://stackoverflow.com/questions/47136436/python-pandas-convert-value-counts-output-to-dataframe)