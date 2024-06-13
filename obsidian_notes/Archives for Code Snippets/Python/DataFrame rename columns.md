---
tags:
  - code
  - code_snippet
  - python/dataframe
keywords: 
topics: 
language: python
date of note: 2024-04-15
---

## Code Snippet Summary

>[!important]
>rename a pandas data frame `df`


## Code

```python
## suppose df is pandas.DataFrame

df = df.rename(columns={'oldName1': 'newName1', 'oldName2': 'newName2'})

# Or rename the existing DataFrame (rather than creating a copy) 
df.rename(columns={'oldName1': 'newName1', 'oldName2': 'newName2'}, inplace=True)
```



-----------
##  Recommended Notes

