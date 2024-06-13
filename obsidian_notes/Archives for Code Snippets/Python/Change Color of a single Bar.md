---
tags:
  - code
  - code_snippet
  - python/plot
keywords: 
topics: 
language: python
date of note: 2024-04-27
---

## Code Snippet Summary

>[!important]
>In bar plot, highlight a single bar by changing its color


## Code

```python
barlist=plt.bar([1,2,3,4], [1,2,3,4])
barlist[0].set_color('r')
plt.show()
```

- `pyplot.bar()`: Make a bar plot.  [reference](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.bar.html#matplotlib-pyplot-bar)
	- The bars are positioned at _x_ with the given _alignment_. Their dimensions are given by _height_ and _width_. The vertical baseline is _bottom_ (default 0).
	- Many parameters can take either a single value applying to all bars or a sequence of values, one for each bar.
	  
	- **`x`**: The x coordinates of the bars. See also _align_ for the alignment of the bars to the coordinates.
	- **`height`**: The height(s) of the bars.
		- Note that if _bottom_ has units (e.g. datetime), _height_ should be in units that are a difference from the value of _bottom_ (e.g. timedelta).
	- **`width`**:  The width(s) of the bars.
		- Note that if _x_ has units (e.g. datetime), then _width_ should be in units that are a difference (e.g. timedelta) around the _x_ values.
	- **`bottom`**:  The y coordinate(s) of the bottom side(s) of the bars.
		- Note that if _bottom_ has units, then the y-axis will get a Locator and Formatter appropriate for the units (e.g. dates, or categorical).
	- `align`: {'center', 'edge'}, default: 'center', Alignment of the bars to the _x_ coordinates:
		- `'center'`: Center the base on the _x_ positions.
		- `'edge'`: Align the left edges of the bars with the _x_ positions.
		- To align the bars on the right edge pass a negative _width_ and `align='edge'`.
	- Returns: 
		- [`BarContainer`](https://matplotlib.org/stable/api/container_api.html#matplotlib.container.BarContainer "matplotlib.container.BarContainer") Container with all the bars and optionally errorbars.
	
	- `bar(),set_color()`: set `color` attribute of the bar




-----------
##  Recommended Notes

- `matploblib` package [API reference](https://matplotlib.org/stable/api/index)
	- `pyplot`: is a state-based **interface** to matplotlib. [reference](https://matplotlib.org/stable/api/pyplot_summary.html#module-matplotlib.pyplot)
		- It provides an implicit, **MATLAB**-like, way of plotting. 
		- It also opens figures on your screen, and acts as the figure GUI manager. 
	- `axes`: The [`Axes`](https://matplotlib.org/stable/api/_as_gen/matplotlib.axes.Axes.html#matplotlib.axes.Axes "matplotlib.axes.Axes") class represents **one (sub-)plot** in a figure. It contains the *plotted data*, *axis ticks*, *labels*, *title*, *legend*, etc. Its methods are the main interface for manipulating the plot. [reference](https://matplotlib.org/stable/api/axes_api.html#matplotlib-axes)

- [[Matplotlib Normal Plot Config]]

- Stack Overflow:
	- [How to change the color of a single bar in a bar plot](https://stackoverflow.com/questions/18973404/how-to-change-the-color-of-a-single-bar-in-a-bar-plot)