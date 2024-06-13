---
tags:
  - code
  - code_snippet
  - python/plot
keywords: 
topics: 
language: python
date of note: 2024-04-08
---

## Code Snippet Summary

>[!important]
>- A [**violin plot**](https://en.wikipedia.org/wiki/Violin_plot) is a [statistical graphic](https://en.wikipedia.org/wiki/Statistical_graphics "Statistical graphics") for comparing [probability distributions](https://en.wikipedia.org/wiki/Probability_distribution "Probability distribution").
>- We show how to use `matplotlib.pyplot.violinplot` and how to how to fully customize violin plots.

## Code

```python
import matplotlib.pyplot as plt
import numpy as np


def adjacent_values(vals, q1, q3):
    upper_adjacent_value = q3 + (q3 - q1) * 1.5
    upper_adjacent_value = np.clip(upper_adjacent_value, q3, vals[-1])

    lower_adjacent_value = q1 - (q3 - q1) * 1.5
    lower_adjacent_value = np.clip(lower_adjacent_value, vals[0], q1)
    return lower_adjacent_value, upper_adjacent_value


def set_axis_style(ax, labels):
    ax.set_xticks(np.arange(1, len(labels) + 1), labels=labels)
    ax.set_xlim(0.25, len(labels) + 0.75)
    ax.set_xlabel('Sample name')


# create test data
np.random.seed(19680801)
data = [sorted(np.random.normal(0, std, 100)) for std in range(1, 5)]

fig, (ax1, ax2) = plt.subplots(nrows=1, ncols=2, figsize=(9, 4), sharey=True)

ax1.set_title('Default violin plot')
ax1.set_ylabel('Observed values')
ax1.violinplot(data)

ax2.set_title('Customized violin plot')
parts = ax2.violinplot(
        data, showmeans=False, showmedians=False,
        showextrema=False)

for pc in parts['bodies']:
    pc.set_facecolor('#D43F3A')
    pc.set_edgecolor('black')
    pc.set_alpha(1)

# find p25, p50, p75
quartile1, medians, quartile3 = np.percentile(data, [25, 50, 75], axis=1)
# whiskers define the line between two extremes
whiskers = np.array([
    adjacent_values(sorted_array, q1, q3)
    for sorted_array, q1, q3 in zip(data, quartile1, quartile3)])
whiskers_min, whiskers_max = whiskers[:, 0], whiskers[:, 1]

inds = np.arange(1, len(medians) + 1)
# plot median
ax2.scatter(inds, medians, marker='o', color='white', s=30, zorder=3)
# plot vertical line from p25 to p75
ax2.vlines(inds, quartile1, quartile3, color='k', linestyle='-', lw=5)
# plot vertical line between top and bottom extremes
ax2.vlines(inds, whiskers_min, whiskers_max, color='k', linestyle='-', lw=1)

# set style for the axes
labels = ['A', 'B', 'C', 'D']
for ax in [ax1, ax2]:
    set_axis_style(ax, labels)

plt.subplots_adjust(bottom=0.15, wspace=0.05)
plt.show()
```

![[Violin_Plot_Example.png]]

- `matplotlib.axes.Axes.violinplot` Make a violin plot. [reference](https://matplotlib.org/stable/api/_as_gen/matplotlib.axes.Axes.violinplot.html#matplotlib.axes.Axes.violinplot "matplotlib.axes.Axes.violinplot") 
	- Make a violin plot for **each column** of _dataset_ or **each vector** in sequence _dataset_. 
	- Each filled area *extends* to represent the *entire data range*, with *optional lines* at 
		- the mean, 
		- **the median**, 
		- the minimum, 
		- the maximum, and 
		- **user-specified quantiles**.
		  
	- **`dataset`**: *Array* or a *sequence of vectors*. The input data.
	- **`positions`**: The positions of the violins. 
		- The ticks and limits are automatically set to match the positions.
		- default: `[1, 2, ..., n]` 
		  
	- `vert`: If true, creates a *vertical violin plot*. Otherwise, creates a horizontal violin plot.
	- `widths`: Either a scalar or a vector that sets the *maximal width of each violin*. 
		- The default is 0.5, which uses about half of the available horizontal space.
	- `showmeans`:  If `True`, will toggle rendering of the **means**. Default `True`.
	- `showextrema`: If `True`, will toggle rendering of the **extrema**. Default `True`.
	- `showmedians`: If `True`, will toggle rendering of the **medians**. Default `False`.
	  
	- **`quantiles`**: array-like, default: None.
		- If not None, set a list of floats in interval `[0, 1]` for each violin, which stands for the **quantiles** that will be **rendered** for that violin.
		  
	- Return: A *dictionary mapping* each component of the violinplot to a list of the corresponding collection instances created. The dictionary has the following keys:
		- `bodies`: A list of the [`PolyCollection`](https://matplotlib.org/stable/api/collections_api.html#matplotlib.collections.PolyCollection "matplotlib.collections.PolyCollection") instances containing the filled area of each violin.
	    - `cmeans`: A [`LineCollection`](https://matplotlib.org/stable/api/collections_api.html#matplotlib.collections.LineCollection "matplotlib.collections.LineCollection") instance that marks the mean values of each of the violin's distribution.
	    - `cmins`: A [`LineCollection`](https://matplotlib.org/stable/api/collections_api.html#matplotlib.collections.LineCollection "matplotlib.collections.LineCollection") instance that marks the bottom of each violin's distribution.
	    - `cmaxes`: A [`LineCollection`](https://matplotlib.org/stable/api/collections_api.html#matplotlib.collections.LineCollection "matplotlib.collections.LineCollection") instance that marks the top of each violin's distribution.
	    - `cbars`: A [`LineCollection`](https://matplotlib.org/stable/api/collections_api.html#matplotlib.collections.LineCollection "matplotlib.collections.LineCollection") instance that marks the centers of each violin's distribution.
	    - `cmedians`: A [`LineCollection`](https://matplotlib.org/stable/api/collections_api.html#matplotlib.collections.LineCollection "matplotlib.collections.LineCollection") instance that marks the median values of each of the violin's distribution.
	    - `cquantiles`: A [`LineCollection`](https://matplotlib.org/stable/api/collections_api.html#matplotlib.collections.LineCollection "matplotlib.collections.LineCollection") instance created to identify the quantile values of each of the violin's distribution.


-----------
##  Recommended Notes
- `matplotlib.axes.Axes.violinplot` Make a violin plot. [reference](https://matplotlib.org/stable/api/_as_gen/matplotlib.axes.Axes.violinplot.html#matplotlib.axes.Axes.violinplot "matplotlib.axes.Axes.violinplot") 
- `matplotlib.pyplot.violinplot` [reference](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.violinplot.html#matplotlib.pyplot.violinplot "matplotlib.pyplot.violinplot")
- `matplotlib.axes.Axes.vlines` [reference](https://matplotlib.org/stable/api/_as_gen/matplotlib.axes.Axes.vlines.html#matplotlib.axes.Axes.vlines "matplotlib.axes.Axes.vlines") 
- `matplotlib.pyplot.vlines` [reference](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.vlines.html#matplotlib.pyplot.vlines "matplotlib.pyplot.vlines")
  
- [Violin Plot Wikipedia](https://en.wikipedia.org/wiki/Violin_plot)

>[!quote]
>Violin plots are similar to [box plots](https://en.wikipedia.org/wiki/Box_plot "Box plot"), except that they also show the [probability density](https://en.wikipedia.org/wiki/Probability_density_function "Probability density function") of the data at different values, usually smoothed by a [kernel density estimator](https://en.wikipedia.org/wiki/Kernel_density_estimator "Kernel density estimator"). A violin plot will include all the data that is in a box plot: a marker for the *median* of the data; a box or marker indicating the *interquartile range*; and possibly all sample points, if the number of samples is not too high.


- Example: [Violin plot customization](https://matplotlib.org/stable/gallery/statistics/customized_violin.html#violin-plot-customization)