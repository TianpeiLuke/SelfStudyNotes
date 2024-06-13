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
>- We want to create a new plot on top of existing one with **different Y-axis** and share the **same X-axis**. 
>- This type of plot is to show the correlation of two statistics with a common factor. 

## Code


```python
import matplotlib.pyplot as plt


# x_label = ...
# y1_label = ...
# y2_label = ...

fig, ax1 = plt.subplots(figsize=(20, 10))
plt.title('%s vs. %s' %(y1_label, y2_label), fontsize=18)

# plot figure with black line, on left
ax1.plot(...)    
ax1.set_xlabel(x_label, fontsize=18)
ax1.set_ylabel(y1_label, fontsize=18)
ax1.tick_params('y', colors='b'). # use blue color of y-tick on left
ax1.tick_params(labelsize=18)

# plot figure with red line, on the right
ax2 = ax1.twinx()   # duplicate a new axes
ax2.plot(...)
ax2.set_ylabel(y2_label, fontsize=18)
ax2.tick_params('y', colors='r') # use red color of y-tick on right
ax2.tick_params(labelsize=18)


h1, l1 = ax1.get_legend_handles_labels()
h2, l2 = ax2.get_legend_handles_labels()
ax1.legend(h1+h2, l1+l2, loc='best', fontsize = 18)
```

- `Axes.twinx()`: Create a twin Axes sharing the x-axis. [reference](https://matplotlib.org/stable/api/_as_gen/matplotlib.axes.Axes.twinx.html#matplotlib.axes.Axes.twinx)
	- Create a **new Axes** with an *invisible x-axis* and an **independent y-axis** positioned **opposite** to the original one (i.e. **at right**). 
	- The x-axis autoscale setting will be inherited from the original Axes. To ensure that the tick marks of both y-axes align, see [`LinearLocator`](https://matplotlib.org/stable/api/ticker_api.html#matplotlib.ticker.LinearLocator "matplotlib.ticker.LinearLocator").
	- Return the newly created **Axes** instance.

- `matplotlib.pyplot.twinx()` Make and return a **second axes** that shares the _x_-axis.  [referece](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.twinx.html#matplotlib.pyplot.twinx)
	- The new axes will overlay _ax_ (or the current axes if _ax_ is _None_), and its ticks will be **on the right.**

-----------
##  Recommended Notes

- `Axes.twinx()`: Create a twin Axes sharing the x-axis. [reference](https://matplotlib.org/stable/api/_as_gen/matplotlib.axes.Axes.twinx.html#matplotlib.axes.Axes.twinx)
- `matplotlib.pyplot.twinx()` Make and return a **second axes** that shares the _x_-axis.  [referece](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.twinx.html#matplotlib.pyplot.twinx)
- Matplotlib Example:
	- [Plots with different scales](https://matplotlib.org/stable/gallery/subplots_axes_and_figures/two_scales.html#plots-with-different-scales)
	- [Percentiles as horizontal bar chart](https://matplotlib.org/stable/gallery/statistics/barchart_demo.html#percentiles-as-horizontal-bar-chart)