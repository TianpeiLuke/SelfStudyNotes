---
tags:
  - code
  - code_snippet
  - feature_engineering
  - risk_value
  - python/dataframe
keywords: 
topics: 
language: python
date of note: 2024-04-03
---

## Code Snippet Summary

>[!info]
>The **Risk Value** (or **Sugar Index (SI)** for Buyer Risk Evaluation) is computed as follows:
>- Suppose field `x` takes *categorical values* in `{a, b, c, ...}`, the target `y \in {0, 1}` is *binary*
>- The risk value of `y` given `x = c` is computed as
>$$
>P(y = 1 | x = c) = \frac{\#\{i: x_i = c \land y_i = 1\}}{\#\{i: x_i = c\}}
>$$
>- Thus we can define the **risk value mapping** $r: \mathcal{X} \mapsto [0,1]$ as  $r[x] = P(y=1 | x)$ where $x \in \mathcal{X} = \{a, b, c, \ldots \}$
>- Risk value mapping is used for **categorical feature encoding**.


>[!important]
>Task: compute both numerator and denominator of the above formula and to handle the anomalies and exceptions
>- Input `pandas.DataFrame`
>- Output a list of `dict` each representing a risk value mapping for a selected feature field `x`
>- Apply **Bayesian smoothing** with *smoothing factor* $\rho>0$
>$$
>r[c] = \hat{P}(y=1 | x=c) = \frac{\#\{i: x_i = c \land y_i = 1\} + \rho P(y=1) }{\#\{i: x_i = c\} + \rho}
>$$
>- For $x \not\in \mathcal{X}$, $r[x] = P(y=1)$ default value.

- [[Processors Risk Binning]]
- [[Binning as Categorical Feature Transformation]]
- [[Risk Table for Categorical Feature]]
- [[Binning]]
- [[Binning and Pivot Table - Count Frequency of Pairs of Features]]

## Code

```python
import pandas as pd
import numpy as np


def df_category_risk(df, col_names, tags, default_risk=0.001, cnt_threshold=5, smoothing_factor=1, tag_range=1):
    '''
       for each given cols in df, for each category, compute the ratio of positive risk tags  vs. negative risk tags
       tag_range = 1 => default positive tag =1, negative tag=0
                = 2 => default positive tag =1, negative tag=-1
                
        Input:
	        df: pandas.DataFrame including col_names
	        col_names: list of `x`'s upon which the risk value mapping is on. 
	        tags: `y`, should be of the same number of rows as df
	        
	        
    '''
    
	# determine the binary set of label to be {0,1} or {1, -1}
    if tag_range == 1:
        POS_TAG = 1
        NEG_TAG = 0
    else:
        POS_TAG = 1
        NEG_TAG = -1
        
    ratio_dict_list = []
    count_dict_list = []
    
	# embed the label column into the dataframe 
    df['_'] = tags
    
	# compute the overall ratio of y=1, as the prior distribution P(y)
    global_pos_ratio = len(tags[tags == POS_TAG]) / len(tags)
	
	# for each `x` to compute the risk value
    for col in col_names:
        cat_risk_map = dict()
        cat_count_map = dict()
        
        # for each category in col compute the ratio of positive risk tags vs. negative risk tag
        # groupby col and tags
        # | col | tags  | counts |
	    # demoniator
        df_total = df.groupby([col]).agg({col: 'count'})
        # numerator
        df_col = df.groupby([col, '_']).agg({'_': 'count'})
        
        # groupby first level and take the ratio
        # | col | tags  | ratio  |
        # if the available tags for each category == 3 ? == 2? ==1 
        # smooth denomiator with a constant smoothing factor
        df_ratio = df_col.groupby(level=0, group_keys=False).apply(lambda x: (x + smoothing_factor*global_pos_ratio) / (float(x.sum())  + smoothing_factor) if x.shape[0] == 2 \
                                                      else (x + smoothing_factor*global_pos_ratio) / (float(x[1:].sum())  + smoothing_factor) if x.shape[0] > 2 \
                                                      else x/ (float(x.sum()) / smoothing_factor))
                                                      
        # only choose the row segment with condition `tags = POS_TAG`
        pos_count = df_col.xs(POS_TAG, level=1)
        risk_ratio = df_ratio.xs(POS_TAG, level=1)
        
        # output dict
        cat_risk_map = risk_ratio['_'].to_dict()
        cat_count_map = pos_count['_'].to_dict()
        cat_total_map = df_total[col].to_dict()
        
        # filter out small total count categorical values
        for key, val in cat_total_map.items():
            # for category that does not have postive tag 
            if key not in cat_risk_map:
                cat_risk_map[key] = global_pos_ratio #default using global_pos_ratio
                cat_count_map[key] = 0
            if val < cnt_threshold:
                cat_risk_map[key] = default_risk
        ratio_dict_list.append(cat_risk_map)
        count_dict_list.append(cat_count_map)
        
    df.drop(['_'], axis=1, inplace=True)
    return ratio_dict_list, count_dict_list
```

- `pandas.DataFrame`
	- `groupby()`: Group DataFrame using a mapper or by a Series of columns. [reference](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.groupby.html#pandas-dataframe-groupby)
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
			  
		- `apply(function)`: See below.  [Guide](https://pandas.pydata.org/docs/user_guide/groupby.html#flexible-apply)
		  
	- `apply()`: Apply a function along an axis of the DataFrame. [reference](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.apply.html#pandas-dataframe-apply)
		- Objects passed to the function are **Series objects** whose *index* is either the *DataFrame’s index (`axis=0`)* or the *DataFrame’s columns (`axis=1`)*. 
		- By default (`result_type=None`), the final return type is inferred from the *return type of the applied function*. Otherwise, it depends on the *`result_type`* argument.
		  
		- **`func`**: Function to apply to each *column or row*.
		- **`axis`**: Axis along which the function is applied:
			- 0 or ‘index’: apply function to each column.
			- 1 or ‘columns’: apply function to each row.
		- `raw`: Determines if row or column is passed as a Series or ndarray object:
			- `False` : passes each row or column as a *Series* to the function.
			- `True` : the passed function will receive *ndarray* objects instead. If you are just applying a *NumPy reduction function* this will achieve much better performance.
		- `result_type`: These *only act when `axis=1`* (columns):
			- `‘expand’` : *list-like results* will be turned into columns.
			- `‘reduce’` : returns a *Series* if possible rather than expanding list-like results. This is the *opposite* of `‘expand’`.
			- `‘broadcast’` : results will be *broadcast* to the *original shape* of the DataFrame, the original index and columns will be retained.
		- **`args`** : *Positional arguments* to pass to **`func`** in addition to the array/series.
		    
	- `xs()`: Return cross-section from the Series/DataFrame. [reference](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.xs.html#pandas.DataFrame.xs)
		- This method takes a *key argument* to **select** data at **a particular level** of a MultiIndex.



-----------
##  Recommended Notes

- Pandas **DataFrame**: [User Guide](https://pandas.pydata.org/docs/user_guide/dsintro.html#basics-dataframe)
	- **Group by: split-apply-combine**: [User Guide](https://pandas.pydata.org/docs/user_guide/groupby.html)[API reference](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.groupby.html#pandas-dataframe-groupby)
		- with Multi-Index: [Guide](https://pandas.pydata.org/docs/user_guide/groupby.html#groupby-with-multiindex)
		- with index levels: [Guide](https://pandas.pydata.org/docs/user_guide/groupby.html#grouping-dataframe-with-index-levels-and-columns)
		- Flexible `apply()`: [Guide](https://pandas.pydata.org/docs/user_guide/groupby.html#flexible-apply) [API reference](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.apply.html#pandas-dataframe-apply)
	- `xs()`: Return cross-section from the Series/DataFrame. [reference](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.xs.html#pandas.DataFrame.xs)
- source code: [link](https://code.amazon.com/packages/TRMSSTAT_lukexie/blobs/mainline/--/codes/df_category_risk.py)