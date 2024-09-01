---
tags:
  - code
  - code_snippet
  - python/ml
keywords: 
topics: 
language: python
date of note: 2024-08-31
---

## Code Snippet Summary

>[!important]
>Given a dataframe `df` with probability score `prob` and the ground truth label `label`, 
>- **sort** the data according to `prob`
>- **chunk** the data into bins $$x_{i} \in b_{j} \text{ if } prob(x_{i}) \ge prob^{(j)}$$ where $prob^{(j)} = \text{quantile}(prob, q_{j})$
>- compute **precision at k** i.e. $$\text{precision @ k} = \frac{\text{ predicted and true positive}  \land \text{ score percentile } \le k }{\text{predicted positive } \land \text{ score percentile } \le k}$$
>- compute **recall at k** i.e. $$\text{recall @ k} = \frac{\text{ predicted and true positive}  \land \text{ score percentile } \le k }{\text{true positive } \land \text{ score percentile } \le k}$$
>- calculate precision and recall for bins $b_{j}: j \le k$


## Code

```python
import pandas as pd
```

### Fixed Threshold on Predicted Positive
#### Sort the dataframe according to score

```python
# sort the dataframe
df.sort_values(by='prob',ascending=False,inplace=True)
# remove rows with missing values
df.dropna(inplace=True)

```

## Weighted by Amount

>[!important] 
>Consider the case when `amount` is added in `df`.
>
>- compute **precision at k** i.e. $$\text{precision @ k} = \frac{\sum_{i\in \text{ predicted and true positive} \land \text{ score percentile } \le k}\text{amount}(i)   }{\sum_{i \in \text{predicted positive } \land \text{ score percentile } \le k}\text{amount}(i)}$$
>- compute **recall at k** i.e. $$\text{recall @ k} = \frac{\sum_{i \in\text{ predicted and true positive}  \land \text{ score percentile } \le k }\text{amount}(i)}{\sum_{i \in \text{true positive } \land \text{ score percentile } \le k}\text{amount}(i)}$$


## Precision and Recall at k-th Bin

>[!important]
>We define $$\text{pred}(x_{i}) = 1 \text{ if } prob(x_{i}) \ge \text{quantile}(prob, q_{j})$$ where $q_{j}$ is the *minimum rank* of $prob$ for $j$-th bin.

>[!important]
> compute **precision at kth bin** i.e. $$\text{precision @ k} = \frac{\sum_{i\in \text{ pred pos} \land \text{ score percentile } \le q_{k}}\text{amount}(i)   }{\sum_{i \in \text{pred pos } \land \text{ score percentile } \le q_{k}}\text{amount}(i)}$$ where $$q_{k} = \min\left\{i: x^{(i)} \in b_{k} \right\} \implies prob(b_{k}) \in [q_{k-1}, q_{k}] $$

#### Chunk based on score bins

```python
# chunk based on score bins
score_field = 'prob'
score_bin_field = score_field+'_bin'
df[score_bin_field] = pd.cut(df[score_field], score_bins)
```

#### Compute the Cumulative Amount for Bins above Cutoff Threshold

>[!info]
> $$
> \begin{align*}
>\text{cumulative amount} @ k = \sum_{j \le k}\text{total amount}(j) = \sum_{j \le k}\sum_{x_{i}\in b_{j}}\text{amount}(x_{i})
>\end{align*}
> $$

>[!info]
>Since we predict $1$ for all population whose bin $j \le k$, 
>$$
>\text{cumulative amount} @ k = \text{cumulative predicted positive amount} @ k
>$$ 

```python

total_amount_field = amount_field + '_sum'

df_score_amount_groupby = 
df.groupby([score_bin_field])
.agg({amount_field: 'sum'})
.reset_index()
.rename(columns={amount_field: total_amount_field})
.iloc[::-1]


total_cum_amount_field = amount_field + '_cumsum'

df_score_amount_groupby[total_cum_amount_field] = df_score_amount_groupby[total_amount_field].cumsum()
```

#### Compute the Cumulative True Positive Amount for Bins above Cutoff Threshold

>[!info]
> $$
>\begin{align*}
>&\text{cumulative predicted true positive amount} @ k \\
>&= \sum_{j \le k}\text{total positive amount}(j) \\
>&= \sum_{j \le k}\sum_{x_{i}\in b_{j}, \; y(x_{i}) = 1}\text{amount}(x_{i})
>\end{align*}
> $$

```python

df_score_label_amount_groupby = df.groupby([score_bin_field, label_field]).agg({amount_field: 'sum'})

df_score_label_amount_groupby = df_score_label_amount_groupby
.reset_index()
.rename(columns={amount_field: total_amount_field})
.iloc[::-1]


df_score_pos_label_amount_groupby = df_score_label_amount_groupby[data_score_label_amount_groupby[label_field] == 1]

total_pos_amount_field = amount_field + '_pos_sum'

df_score_pos_label_amount_groupby[total_pos_amount_field] = df_score_pos_label_amount_groupby[total_amount_field].cumsum()
```

#### Join Denominator and Numerator in one Table

```python
df_score_amount_pos_amount_groupby = 
df_score_amount_groupby
.loc[:, [score_bin_field, total_cum_amount_field]]
.set_index([score_bin_field])
.join(data_score_pos_label_amount_groupby.loc[:, [score_bin_field, total_pos_amount_field]].set_index([score_bin_field]))
.reset_index()
```

#### Compute Precision

```python

precision_field = 'precision_at_n'

df_score_amount_pos_amount_groupby[precision_field] = df_score_amount_pos_amount_groupby[total_pos_amount_field] / df_score_amount_pos_amount_groupby[total_cum_amount_field]

```

#### Report 

```python
#### Count number of postive items for bin id <= k

df_order_count_groupby = df.groupby([score_bin_field])
.agg({label_field: 'count'})
.reset_index()
.rename(columns={label_field: 'bin_support'})
.iloc[::-1]

#### Count number of total items for bin id <= k

df_score_order_count_groupby['n'] = df_score_order_count_groupby['bin_support'].cumsum()

#### positive ratio of population whose bin id <= k

df_score_order_count_groupby['n_percentage'] = df_score_order_count_groupby['n'] / (df_score_order_count_groupby['bin_support'].sum())


report = df_score_amount_pos_amount_groupby
.set_index(score_bin_field)
.join(df_score_order_count_groupby.loc[:, [score_bin_field, 'n', 'n_percentage']].set_index(score_bin_field))
.reset_index()

report['threshold_at_n'] = report[score_bin_field].apply(lambda s: s.left)

report_snapshot = report.loc[:, ['threshold_at_n', 'n_percentage', 'precision_at_n']]
```






-----------
##  Recommended Notes


- [[Calculate Recall at 1 percent false positive rate]]
- [[Chunk Inputs into equal length batch]]
- [[Sort Dictionary Keys by List]]

- Blog [precisionk_and_recallk](https://insidelearningmachines.com/precisionk_and_recallk/)