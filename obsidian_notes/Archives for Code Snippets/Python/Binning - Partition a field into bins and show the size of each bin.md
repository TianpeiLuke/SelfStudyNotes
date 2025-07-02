---
tags:
  - code
  - code_snippet
  - python/dataframe
  - feature_engineering
  - machine_learning/feature_engineering
keywords: 
topics: 
language: python
date of note: 2024-04-04
---

## Code Snippet Summary

>[!important]
>Suppose we have a dataframe `df` with a column `col1` with float values. 
>- We want to **partition** the column into a set of **bins**, whose threshold is stored in `bins` variable
>- Then we want to *count* the number of records whose `col1` lies within each bin.
>
>In feature engineering, this step is called **binning**, which convert *continuous variable* to *categorical variables*. 

## Code

```python
import pandas as pd

# Define the bin thresholds
bins = ...

# Create a new column 'bin' with the partitioned bins
df['bin'] = pd.cut(df['col1'], bins)

# Create a new column `qbin` with the quantile partitioned bins
qbins = ...
df['qbin'] = pd.qcut(df['col1'], qbins)

# Group by the 'bin' column and calculate the size of each group
result = df.groupby('bin').size()

# Print the result
print(result)
```

- `pandas.cut()`: Bin values into discrete intervals. [reference](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.cut.html#pandas.cut)
	- Use *cut* when you need to **segment** and **sort** data values into **bins**. 
	- This function is also useful for going from a **continuous variable** to a **categorical variable**. 
	- Supports binning into an *equal number of bins*, or a *pre-specified array of bins*.
	- **`x`**: The input array to be binned. Must be 1-dimensional.
	- **`bins`**: The criteria to bin by.
		- *int* : Defines the *number of equal-width bins* in the range of x. The range of x is *extended* by **.1%** on each side to include the minimum and maximum values of x.
		- *sequence of scalars* : Defines the **bin edges** allowing for non-uniform width. No extension of the range of x is done.
		- *IntervalIndex* : Defines the **exact bins** to be used. Note that IntervalIndex for bins must be **non-overlapping**.
	- **`labels`**: Specifies the labels for the returned bins. 
		- Must be *the same length* as the *resulting bins*. 
		- If False, returns only *integer indicators* of the bins. This affects the type of the output container (see below). 
		- This argument is ignored when bins is an *IntervalIndex*. 
		- If True, raises an error. 
		- When `ordered=False`, labels must be provided.
	- `ordered`:
	- Return 
		- `out`: An *array-like object* representing the **respective bin** *for each value* of `x`. The type depends on the value of labels.
			- *None (default)* : returns a Series for Series x or a Categorical for all other inputs. The values stored within are Interval dtype.
			- *sequence of scalars* : returns a Series for Series `x` or a Categorical for all other inputs. The values stored within are whatever the type in the sequence is.
			- *False* : returns an ndarray of integers.
			  
- `pandas.qcut()`: Quantile-based discretization function. Discretize variable into equal-sized buckets based on rank or based on sample quantiles.  [reference](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.qcut.html#pandas.qcut)

-----------
##  Recommended Notes

- `pandas.DataFrame`: [reference](https://pandas.pydata.org/pandas-docs/stable/reference/frame.html)
- `pandas.cut()`: [reference](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.cut.html#pandas.cut)
- `pandas.qcut()`: Quantile-based discretization function. Discretize variable into equal-sized buckets based on rank or based on sample quantiles.  [reference](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.qcut.html#pandas.qcut)

- Wikipedia
	- [Data binning](https://en.wikipedia.org/wiki/Data_binning)

- [[Processor Risk Table Mapping]]
- [[Binning and Pivot Table - Count Frequency of Pairs of Features]]