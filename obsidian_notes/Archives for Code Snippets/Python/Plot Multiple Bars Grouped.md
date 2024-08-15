---
tags:
  - code
  - code_snippet
  - python/plot
keywords: 
topics: 
language: python
date of note: 2024-08-14
---

## Code Snippet Summary

>[!important]
>Given a dataframe `df` with two columns `col1` and `col2` with common index column `index`
>- plot a bar graph where the value of two columns as Y-axis and `index` as X-axis
>- two bar graphs are grouped together for each common index


## Code

```python
import matplotlib.pyplot as plt
import pandas as pd

index = df['index']
col_1 = df['col1']
col_2 = df['col2']


plt.figure(figsize=(10,8))

width = 0.3

plt.bar([i for i in range(len(index))], col_1, width,  color='r', label='new model')
plt.bar([i + width for i in range(len(index))], col_2, width, color='b', label='old model')

xtick = [i + width/2 for i in range(len(index))]


# show ticks every xx index
plt.xticks(xtick[::1], index[::1], rotation=90)

plt.xlabel('x-axis', fontsize=15)
plt.ylabel('y-axis', fontsize=15)
plt.title("plot", fontsize=15)
plt.legend(loc='upper right', fontsize=15)

```





-----------
##  Recommended Notes

