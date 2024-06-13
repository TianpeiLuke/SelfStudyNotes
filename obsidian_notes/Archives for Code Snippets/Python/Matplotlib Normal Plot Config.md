---
tags:
  - code
  - code_snippet
  - python/plot
keywords: 
topics: 
language: 
date of note: 2024-04-04
---

## Code Snippet Summary

>[!important]
>Include the normal codes to plot figures using `matplotlib`


## Code

### Common Template

```python
import matplotlib.pyplot as plt

plt.figure(figsize=(10, 6))

plt.plot(...)
plt.xlabel('x')
plt.ylabel('y')
plt.title('Title')
#plt.grid(True). # show grid or not


fig_name = ...

plt.savefig(fig_name)

# Display the plot
plt.show()
```

### Legends, Plot size, Property of Lines 

>[!important]
>- Adjust *line width*, *line style*, *markers*
>- Add *legends*



### Manage Figure and Axes

>[!important]
>- Get current **axes** so that we can direct adjust plot, labels, ticks, legend etc.
>	- Adjust xtick value


- The [`Axes`](https://matplotlib.org/stable/api/_as_gen/matplotlib.axes.Axes.html#matplotlib.axes.Axes "matplotlib.axes.Axes") class represents **one (sub-)plot** in a figure. It contains the *plotted data*, *axis ticks*, *labels*, *title*, *legend*, etc. Its methods are the main interface for manipulating the plot. [reference](https://matplotlib.org/stable/api/axes_api.html#matplotlib-axes)
- `matplotlib.pyplot`: is a state-based **interface** to matplotlib. [reference](https://matplotlib.org/stable/api/pyplot_summary.html#module-matplotlib.pyplot)
	- **`gca()`**: Get the current Axes. [reference](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.gca.html#matplotlib.pyplot.gca)
		- If there is currently no Axes on this Figure, a new one is created using [`Figure.add_subplot`](https://matplotlib.org/stable/api/figure_api.html#matplotlib.figure.Figure.add_subplot "matplotlib.figure.Figure.add_subplot").
	- **`gcf()`**: Get the current figure. [reference](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.gcf.html#matplotlib.pyplot.gcf)
		- If there is currently no figure on the pyplot figure stack, a new one is created using [`figure()`](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.figure.html#matplotlib.pyplot.figure "matplotlib.pyplot.figure").


```python
plt.figure(figsize=(10, 6))
plt.plot(...)

# get current axes
ax = plt.gca()
# remove xtick labels
ax.set_xticklabels([])

```




>[!important]
>- Create multiple sub-plots

```python
# using the variable ax for single a Axes
fig, ax = plt.subplots()

# using the variable axs for multiple Axes
fig, axs = plt.subplots(2, 2)

# using tuple unpacking for multiple Axes
fig, (ax1, ax2) = plt.subplots(1, 2)
fig, ((ax1, ax2), (ax3, ax4)) = plt.subplots(2, 2)
```

- `matplotlib.pyplot.subplots()`: [reference](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.subplots.html#matplotlib.pyplot.subplots)
	- 



>[!important]
>- Adjust figure shape


### Axis configuration

>[!important]
>*Get* or *Set* **axis** properties
>- the limit (boundary) of x-axis and y-axis in the plot

```python
plt.plot(...)

# confine the plot to show only x in [x_min, x_max], y in [y_min, y_max]
plt.axis([x_min, x_max, y_min, y_max])
```

- `matplotlib.pyplot.axis()`: Convenience method to get or set some axis properties. [reference](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.axis.html#matplotlib-pyplot-axis)

Note that similar effect can be done via changing the **axes** directly

```python
ax = plt.gca()

ax.set_xlim(x_min, x_max)
ax.set_ylim(y_min, y_max)
# or
ax.set_xlim((x_min, x_max))
ax.set_ylim((y_min, y_max))
```

- `matplotlib.axes.Axes.set_xlim()`: [reference](https://matplotlib.org/stable/api/_as_gen/matplotlib.axes.Axes.set_xlim.html#matplotlib.axes.Axes.set_xlim)
- `matplotlib.axes.Axes.set_ylim()`: [reference](https://matplotlib.org/stable/api/_as_gen/matplotlib.axes.Axes.set_ylim.html#matplotlib.axes.Axes.set_ylim)


>[!important]
>Change the configuration on **ticks** (spacing of labels) showing in x-axis and y-axis
 
```python
plt.plot(...) 

# label values to show x-axis, could skip points 
xtick_bins = [...]
ytick_bins = [...]

# rotation of label on x-axis
x_rotation = 90
y_rotation = 0

plt.xticks(xtick_bins, rotation=x_rotation, fontsize=10)
plt.yticks(ytick_bins, rotation=y_rotation, fontsize=10)
```


>[!important]
>Change the **labels** on x-axis and y-axis 

```python

```

### Layout

>[!important]
>- Change margins of the plot
>- Adjust subplot layouts
>- Adjust padding between and around subplots


### Color Mapping




-----------
##  Recommended Notes

- `matploblib` package [API reference](https://matplotlib.org/stable/api/index)
	- `pyplot`: is a state-based **interface** to matplotlib. [reference](https://matplotlib.org/stable/api/pyplot_summary.html#module-matplotlib.pyplot)
		- It provides an implicit, **MATLAB**-like, way of plotting. 
		- It also opens figures on your screen, and acts as the figure GUI manager. 
	- `axes`: The [`Axes`](https://matplotlib.org/stable/api/_as_gen/matplotlib.axes.Axes.html#matplotlib.axes.Axes "matplotlib.axes.Axes") class represents **one (sub-)plot** in a figure. It contains the *plotted data*, *axis ticks*, *labels*, *title*, *legend*, etc. Its methods are the main interface for manipulating the plot. [reference](https://matplotlib.org/stable/api/axes_api.html#matplotlib-axes)
	- `axis`: Classes for the ticks and x- and y-axis. [reference](https://matplotlib.org/stable/api/axis_api.html#matplotlib-axis)
	- `tight_layout`: Routines to adjust subplot params so that subplots are nicely fit in the figure. [reference](https://matplotlib.org/stable/api/tight_layout_api.html#matplotlib-tight-layout)
