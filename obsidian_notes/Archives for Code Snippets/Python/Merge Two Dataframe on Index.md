---
tags:
  - code
  - code_snippet
  - python/dataframe
keywords: 
topics: 
language: python
date of note: 2025-04-05
---

## Code Snippet Summary

>[!important]
>Given two dataframe `df1` and `df2`, combine them along field `index`


## Code

```python
import pandas as pd
```

### Concatenate

- merge along index (columns from both are kept side by side)

```python
merged_df = pd.concat([df1, df2], axis=1)
```

### SQL Join on Index

- Inner join on index (only keep matching index rows)

```python
merged_df = df1.join(df2, how='inner')
```

### Reset index First

```python
merged_df = pd.concat([df1.reset_index(drop=True), df2.reset_index(drop=True)], axis=1)
```

### Merge 

- if both dataframes have a column as `index`

```python
merged_df = df1.merge(df2, on='index', how='inner')
```

- the following works as inner join

```python
merged_df = df1.merge(df2, left_index=True, right_index=True)
```







-----------
##  Recommended Notes

- [[Prompt RnR Reason Code 02 2-Batch Processing with Checkpointing]]
- [[Prompt RnR Reason Code 02 2-Batch Processing with Checkpointing Logs]]
- [[Prompt RnR Reason Code 02 2-Batch Processing with Progress Bar]]
