---
tags:
  - code
  - code_snippet
  - python/dataframe
keywords: 
topics: 
language: python
date of note: 2025-03-21
---

## Code Snippet Summary

>[!important]
>Given a dataframe `df`, return a list of dictionary for `(column_name, missing_rate)` as 
>
>```
>{'column_1': missing_rate_1, ... 'column_n': missing_rate_n} 
>```

## Code

```python
import pandas as pd

df = pd.read_csv(...)
```

- compute missing rate for each column of dataframe
- convert it to dictionary

```python
missing_rates = (df.isnull().sum() / len(df)).to_dict()
```

- `pandas.isnull()`
- `pandas.isull().sum()`
- `pandas.to_dict()`

- If rounded with decimal

```python
missing_rates = (df.isnull().sum() / len(df)).round(decimals).to_dict()
```

- Find columns with missing rate more than threshold 

```python
[col for col, rate in missing_rates.items() if rate > threshold]
```





-----------
##  Recommended Notes

