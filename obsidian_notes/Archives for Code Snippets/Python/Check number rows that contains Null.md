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
>Suppose the `pandas.DataFrame` name is `df`
>- **Count** the number of rows that contains at least one *NULL (NaN)* value
>- For given field `col1`, count the number of rows that contains NULL value
>- **Drop** NULL values or **Fill** NULL values


## Code

```python
import pandas as pd

# count number of NA values in `col`
null_count_col1 = df['col1'].isnull().sum()
```

- `pandas.isnull()`: Detect missing values for an array-like object. [reference](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.isnull.html#pandas-isnull)
	- This function takes a *scalar* or *array-like* object and indicates **whether values are missing** (`NaN` in numeric arrays, `None` or `NaN` in object arrays, `NaT` in datetimelike).
	- return *bool* or *array-like of bool*
		- For scalar input, returns a scalar **boolean*8. 
		- For array input, returns an **array of boolean** indicating whether *each* corresponding element is missing.
	- `sum()`: sum of elements. For `.isnull().sum()`, it return the number of NULL values in the array
- `Series.isnull()` is an alias of `Series.isna()` [reference](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.isnull.html#pandas.Series.isnull)

Thus, a similar solution using `isna()`

```python
null_count_col1 = df['col1'].isna().sum()
```

- `Series.isna()`: Detect missing values. . [reference](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.isna.html#pandas.Series.isna)
	- Return a **boolean** same-sized object indicating if the values are `NA`. 
		- `NA` values, such as `None` or `numpy.NaN`, gets mapped to *True* values. 
		- Everything else gets mapped to *False* values. 
		- Characters such as empty strings `''` or `numpy.inf` are **not considered `NA`** values (*unless* you set `pandas.options.mode.use_inf_as_na = True`)

For DataFrame
```python

# return a Series, with each column and the corresponding null value count

null_count_per_column = df.isna().sum()

# col1    0
# col2    10
# ...

```

- `DataFrame.isna()`: Detect missing values. [reference](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.isna.html#pandas.DataFrame.isna)
	- Return a boolean *same-sized object* indicating if the values are` NA`. 
		- NA values, such as None or `numpy.NaN`, gets mapped to *True* values.
		- Everything else gets mapped to False values. 
		- Characters such as empty strings `''` or `numpy.inf` are not considered `NA` values (unless you set `pandas.options.mode.use_inf_as_na = True`).

So to compute the number of rows that contain at least one `NA`

```python
df.isna().any(axis=0).sum()
```

- `df.isna()` returns the dataframe with each entity either False or True
	- `df.isna().any(axis=0)` return rows with at least one True
		- `df.isna().any(axis=0).sum()` add all True's to compute the number of rows with at least one NULL

- `Series.any()`:
- `DataFrame.any()`: Return whether **any element is True**, potentially over an axis. [reference](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.any.html#pandas.DataFrame.any)
	- Returns *False* unless there is **at least one element** within a *series* or along a *Dataframe axis* that is *True* or *equivalent* (e.g. non-zero or non-empty).
	- **`axis`**: Determine if rows or columns which contain missing values are removed.
		- `0`, or `‘index’` : Drop rows which contain missing values.
		- `1`, or `‘columns’` : Drop columns which contain missing value.
### Drop null values

```python
df.dropna(axis=0)
```

- `DataFrame.dropna()`: Remove missing values.  [reference](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.dropna.html#pandas.DataFrame.dropna)
	- **`axis`**: Determine if rows or columns which contain missing values are removed.
		- `0`, or `‘index’` : Drop rows which contain missing values.
		- `1`, or `‘columns’` : Drop columns which contain missing value.
	- **`how` = {`‘any’`, `‘all’`}**, default ‘any’.
		- Determine if row or column is removed from DataFrame, when we have *at least one* `NA` or *all* `NA`.
			- `‘any’` : If *any* `NA` values are present, drop that row or column.
			- `‘all’` : If *all* values are `NA`, drop that row or column.
    - `inplace`: Whether to modify the DataFrame rather than creating a new one.
    - `ignore_index`: If `True`, the resulting axis will be labeled 0, 1, …, n - 1.

### Fill null values

```python
df.fillna(0, axis=1)

df['col1'].fillna(0, axis=1)
```

- `DataFrame.fillna()`: Fill NA/NaN values using the specified method. [reference](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.fillna.html#pandas.DataFrame.fillna)
	- **`value`**:  Value to use to fill holes (e.g. 0), 
		- alternately a *dict/Series/DataFrame* of values specifying *which value to use* for *each index* (for a Series) or *column* (for a DataFrame). 
		- Values not in the dict/Series/DataFrame **will not be filled**. 
		- This value **cannot be a list**.
	- `axis`
	- `inplace`



-----------
##  Recommended Notes

- `pandas.isnull()`: Detect missing values for an array-like object. [reference](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.isnull.html#pandas-isnull)
- `Series.isnull()` is an alias of `Series.isna()` [reference](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.isnull.html#pandas.Series.isnull)
- `Series.isna()`: [reference](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.isna.html#pandas.Series.isna)
- `DataFrame.isna()`: Detect missing values. [reference](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.isna.html#pandas.DataFrame.isna)
- `DataFrame.any()`: Return whether **any element is True**, potentially over an axis. [reference](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.any.html#pandas.DataFrame.any)
- `DataFrame.dropna()`: [reference](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.dropna.html#pandas.DataFrame.dropna)
- `DataFrame.fillna()`: Fill NA/NaN values using the specified method. [reference](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.fillna.html#pandas.DataFrame.fillna)
- Stack Overflow: [Best way to count the number of rows with missing values in a pandas DataFrame](https://stackoverflow.com/questions/28199524/best-way-to-count-the-number-of-rows-with-missing-values-in-a-pandas-dataframe)