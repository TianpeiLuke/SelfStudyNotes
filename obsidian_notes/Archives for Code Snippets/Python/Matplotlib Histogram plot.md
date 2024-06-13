---
tags:
  - code
  - code_snippet
  - python/plot
keywords: 
topics: 
language: python
date of note: 2024-04-25
---

## Code Snippet Summary

>[!important]
>Plot histogram with **multiple sample sets** and demonstrate:
> - Use of legend with multiple sample sets
>     
> - **Stacked bars**
>     
> - **Step curve** with no fill
>     
> - Data sets of different sample sizes
> 


## Code

```python
import matplotlib.pyplot as plt
import numpy as np

np.random.seed(19680801)

n_bins = 10
x = np.random.randn(1000, 3)

fig, ((ax0, ax1), (ax2, ax3)) = plt.subplots(nrows=2, ncols=2)

colors = ['red', 'tan', 'lime']
ax0.hist(x, n_bins, density=True, histtype='bar', color=colors, label=colors)
ax0.legend(prop={'size': 10})
ax0.set_title('bars with legend')

ax1.hist(x, n_bins, density=True, histtype='bar', stacked=True)
ax1.set_title('stacked bar')

ax2.hist(x, n_bins, histtype='step', stacked=True, fill=False)
ax2.set_title('stack step (unfilled)')

# Make a multiple-histogram of data-sets with different length.
x_multi = [np.random.randn(n) for n in [10000, 5000, 2000]]
ax3.hist(x_multi, n_bins, histtype='bar')
ax3.set_title('different sample sizes')

fig.tight_layout()
plt.show()
```

- subplot of 2 by 2, return all axes `ax0`, `ax1`, `ax2`, `ax3`
```python
fig, ((ax0, ax1), (ax2, ax3)) = plt.subplots(nrows=2, ncols=2)
```

- *plot 0*: histograms of three different datasets,  with bar graph type `histtype = 'bar'`. The bar graphs are grouped into 3 for each bar
```python
ax0.hist(x, n_bins, density=True, histtype='bar', color=colors, label=colors)
ax0.legend(prop={'size': 10})
ax0.set_title('bars with legend')
```

- *plot 1*: stacked bar of three histograms, with `stacked=True`

```python
ax1.hist(x, n_bins, density=True, histtype='bar', stacked=True)
ax1.set_title('stacked bar')
```

- *plot 2*: histogram with step graph, `histtype='step'`, stacked `stacked=True`  without fill `fill=False`
```python
ax2.hist(x, n_bins, histtype='step', stacked=True, fill=False)
ax2.set_title('stack step (unfilled)')
```





-----------
##  Recommended Notes

- Matplotlib Documentation
	- [The histogram (hist) function with multiple data sets](https://matplotlib.org/stable/gallery/statistics/histogram_multihist.html)

- [[Matplotlib Normal Plot Config]]

- Stack Overflow:
	- [creating stacked histogram with pandas dataframes data python](https://stackoverflow.com/questions/24594511/creating-stacked-histogram-with-pandas-dataframes-data-python)