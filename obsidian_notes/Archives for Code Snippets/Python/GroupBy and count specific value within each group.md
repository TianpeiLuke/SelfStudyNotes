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
>Given dataframe `df` with column `id`, and column  `col1` which takes values `value1` and `value2`, ...
>- Count how many rows with the same `id` whose `col1` take value `value1`


## Code

The following solution returns a Series

```python
import pandas as pd

col1_value1_count = df.groupby('id')['col1'].apply(lambda x: (x == value1).sum())

### return is a Series
# id1 0
# id2 1
# id3 0
```

- Note that in lambda function `x` is a Series, so `x == value1` returns a Series, which cannot be applied to each element of a Series. 
- It should aggregate first then return.


Another solution which returns a DataFrame

```python
count_df = df[df['col1'] == 'value1'].groupby('id').size().reset_index(name='count')
```




-----------
##  Recommended Notes

