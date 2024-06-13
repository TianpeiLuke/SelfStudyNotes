---
tags:
  - code
  - code_snippet
  - python/dataframe
keywords: 
topics: 
language: python
date of note: 2024-04-04
---

## Code Snippet Summary

>[!important]
>**Group** the dataframe by one column `col1` and then **sort** in descending order the data as per the *size* of each group

>[!example]
>Assume the table
>
> | col1 | col2 |
> | ---- | ---- |
> | a    | x    |
> | a    | x    |
> | a    | x    |
> | a    | x    |
> | a    | y    |
> | a    | y    |
> | b    | x    |
> | b    | y    |
> | b    | y    |
> | b    | y    |

## Code

```python
import pandas as pd


df.groupby('col1').size().sort_values(ascending=False)
```

- `DataFrame.groupby()`: Group DataFrame using a mapper or by a Series of columns. [reference](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.groupby.html#pandas-dataframe-groupby)
	- A groupby operation involves some combination of *splitting the object*, *applying a function*, and *combining the results*. This can be used to group large amounts of data and compute operations on these groups.
	- This method returns a `pandas.api.typing.DataFrameGroupBy` instance.
	- with Multi-Index: [Guide](https://pandas.pydata.org/docs/user_guide/groupby.html#groupby-with-multiindex)
		  
	- **`by`**: Used to determine the groups for the groupby. 
		- If `by` is a *function*, it’s called **on each value of the object’s index**. 
		- If a *dict or Series* is passed, the Series or dict *VALUES* will be used to determine the groups (the Series’ values are first aligned; see `.align()` method). 
		- If a *list or ndarray* of **length equal to the selected axis** is passed (see the [groupby user guide](https://pandas.pydata.org/pandas-docs/stable/user_guide/groupby.html#splitting-an-object-into-groups)), the values are used as-is to determine the groups. 
		- A label or list of labels may be passed to group by the columns in `self`. Notice that a tuple is interpreted as a (single) key.
	- **`axis`**: Split along rows (*0*) or columns (*1*). For Series this parameter is unused and defaults to 0.
	- **`level`**: If the axis is a MultiIndex (hierarchical), group by a particular level or levels. 
		- **Do not specify both `by` and `level`**.
	- **`group_keys`**: When calling **`apply`** and the `by` argument produces a like-indexed (i.e. [a transform](https://pandas.pydata.org/docs/user_guide/groupby.html#groupby-transform)) result, *add group keys to index to identify pieces. *
		- By default group keys are not included when the result’s index (and column) labels match the inputs, and are included otherwise. 

### Extension

>[!important]
>- Group by two columns `col1` and `col2` together and sort the group according to their size
>- Do not break the grouping of multi-index `col1` and `col2`

- If we use the above code, we would break `col1` and `col2` grouping. In example below, the `col1=a` row group is broken. 
- In other word, sort applies to `count` in entire resulting dataframe not just within the group

```python
df.groupby(by=['col1', 'col2']).size().sort_values(ascending=False)
```
 
| col1 | col2 | count |
| ---- | ---- | ----- |
| a    | x    | 4     |
| b    | y    | 3     |
| a    | y    | 2     |
| b    | x    | 1     |

- To fix this, we can do this code

```python
df.groupby(by=['col1', 'col2']).size().reset_index(name='count').sort_values(['col1', 'count'], ascending=[True, False])
```

| col1 | col2 | count |
| ---- | ---- | ----- |
| a    | x    | 4     |
| a    | y    | 2     |
| b    | y    | 3     |
| b    | x    | 1     |


-----------
##  Recommended Notes

- Stack Overflow [Sorting the grouped data as per group size in Pandas](https://stackoverflow.com/questions/22291395/sorting-the-grouped-data-as-per-group-size-in-pandas)
- `pandas.DataFrame`: [reference](https://pandas.pydata.org/pandas-docs/stable/reference/frame.html)
	- **Group by: split-apply-combine**: [User Guide](https://pandas.pydata.org/docs/user_guide/groupby.html)
	- `reset_index()`:  [reference](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.reset_index.html#pandas.DataFrame.reset_index)