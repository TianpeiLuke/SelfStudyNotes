---
tags:
  - code
  - code_snippet
  - python/dataframe
keywords:
  - python/dataframe
topics: 
language: python
date of note: 2024-08-14
---

## Code Snippet Summary

>[!important]
>Suppose a dataframe `df` has a field `weak` with entity like `2023 Week 01`
>- Convert the field into datatime
>- Sort the dataframe according to the `weak`

## Code

```python
import pandas as pd
import datetime
```

```python
df['weak_number']  = pd.to_datetime(df['week']+ '-1', format='%Y Week %W-%w')
```


### Extract Year and Week Number

```python
df['weak_number'] = df['week'].str.extract(r'Week (\d{2})', expand=False).astype(int)
```

```python
df['year'] = df['week'].str.extract(r'(\d{4})', expand=False)
```

### Sort 




-----------
##  Recommended Notes

- Manual
	- [`strftime()` and `strptime()` behaviour](http://docs.python.org/3/library/datetime.html#strftime-and-strptime-behavior)
	- `%W` - Week number of the year (Monday as the first day of the week) as a zero-padded decimal number. All days in a new year preceding the first Monday are considered to be in week 0.
	- `%U` - Week number of the year (Sunday as the first day of the week) as a zero-padded decimal number. All days in a new year preceding the first Sunday are considered to be in week 0.
	- When used with the `strptime()` method, `%U` and `%W` are only used in calculations when the day of the week and the year are specified.


- [[Compute time difference between two time fields in DataFrame]]
- [[Sort all filenames under a directory by creation time]]

- Stack Overflow 
	- [Get date from week number](https://stackoverflow.com/questions/17087314/get-date-from-week-number)