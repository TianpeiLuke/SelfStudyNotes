---
tags:
  - code
  - code_snippet
  - python/numpy
  - python/ml
keywords: 
topics: 
language: python
date of note: 2024-04-05
---

## Code Snippet Summary

>[!important]
>Calculate the **Recall**  at 1% **False Positive Rate (FPR)**
>- *Recall*: Detected Positive / **All Positive** $=\frac{TP}{P}$
>- *Precision*: True Positive / **Detected Positive** $=\frac{TP}{PP}$ 
>- *True Positive Rate*: True Positive / (True Positive + False Negative) = True Positive / **All Positive** $=\frac{TP}{P} = \frac{TP}{TP + FN}$
>- *False Positive Rate*: False Positive / (False Positive + True Negative) = False Positive / **All Negative**  $=\frac{FP}{N} = \frac{FP}{FP + TN}$
>- *Recall = True Positive Rate*. 
>- Retrieved/Detected Positive and it is truely Positive =  'True Positive'

- [[Confusion Table]]
- [[True or False Positive Rate and True or False Negative Rate]]
- [[Recall and Precision and F-Measure]]


>[!info] 
>In order to compute *recall* at the threshold of *1% FPR*, complete the following steps:
>1. obtain **score threshold** at **top 1 percentile** among records whose **true labels** are **negative**. Records whose score *above this threshold* are supposed to be flagged as *positive*. This means that these records form the population of **false positive**.
>   
>2. for the population whose **true labels** are **positive**:
>	- compute the **total amount/count** of this population (*All positive*)
>	- compute the **total amount/count** for the subpopulation whose scores are *above* the cutoff threshold above (*True Positive*)
>	- compute the **ratio** of True Positive vs. All Positive to obtain *Recall*.

## Code

```python
from sklearn.metrics import roc_curve, auc
import pandas as pd
import numpy as np

def calculate_dollar_amount_recall(score, label, order_total):
	'''
	amount recall
	'''
    assert len(score) == len(label) == len(order_total), "Input lengths don't match!"
    
    # threshold = model score at 1% FPR
    threshold = np.quantile(score[label == 0], 0.99)
    # all positive
    abuse_amount_total = order_total[label == 1].sum()
    # true positive
    abuse_amount_above_threshold = order_total[(label == 1) & (score > threshold)].sum()
    # recall = true positive / all positive
    amount_recall = abuse_amount_above_threshold / abuse_amount_total
    return amount_recall
    
def calculate_order_count_recall(score, label):
	'''
	count recall
	'''
    assert len(score) == len(label), "Input lengths don't match!"
    # threshold = model score at 1% FPR
    threshold = np.quantile(score[label == 0], 0.99)
    abuse_order_total = len(label[label == 1])
    abuse_order_above_threshold = len(label[(label == 1) & (score > threshold)])
    order_count_recall = abuse_order_above_threshold / abuse_order_total
    return order_count_recall
```

- `numpy.quantile()`: Compute the **q-th quantile** of the data along the specified axis. [reference](https://numpy.org/doc/stable/reference/generated/numpy.quantile.html)
	- **`a`**:  Input array or object that can be converted to an array.
	- **`q`**: *Probability* or *sequence of probabilities* for the **quantiles** to compute.
		- Values must be between *0 and 1* inclusive.
	- **`axis`**: Axis or axes along which the quantiles are computed. 
		- The default is to compute the quantile(s) along a flattened version of the array.
	- `out`: optional. Alternative output array in which to place the result. 
		- It must have the same shape and buffer length as the expected output, but the type (of the output) will be cast if necessary.
	- `keepdims`: optional.  If this is set to *True*, the axes which are **reduced** are left in the result as *dimensions with size **one***. 
		- With this option, the result will broadcast correctly against the original array _a_.
	- `method`: optional. This parameter specifies the method to use for *estimating the quantile*.
		1. `‘inverted_cdf’`
	    2. `‘averaged_inverted_cdf’`
	    3. `‘closest_observation’`
	    4. `‘interpolated_inverted_cdf’`
	    5. `‘hazen’`
	    6. `‘weibull’`
	    7. **`‘linear’ (default)`**
	    8. `‘median_unbiased’`
	    9. `‘normal_unbiased’`
		- The first three methods are discontinuous. NumPy further defines the following *discontinuous variations* of the default ‘linear’ (7.) option:
			- `‘lower’`
			- `‘higher’`
			- `‘midpoint’`
			- `‘nearest’`

### Unified Interface

```python
def calculate_recalls(test_score, test_data, target_col, order_amount_col, verbose=False):
    score = test_score
    label = test_data[target_col]
    order_total = test_data[order_amount_col]
    
    # compute both amount recall and count recall
    dollar_amount_recall = calculate_dollar_amount_recall(score, label, order_total)
    order_count_recall = calculate_order_count_recall(score, label)
    
    if verbose:
        print(f"dollar_amount_recall = {dollar_amount_recall:.4f}")
        print(f"order_count_recall = {order_count_recall:.4f}")
    return dollar_amount_recall, order_count_recall
```

-----------
##  Recommended Notes

- Recall definition: [wikipedia](https://en.wikipedia.org/wiki/Precision_and_recall)
- `numpy.quantile()`: [reference](https://numpy.org/doc/stable/reference/generated/numpy.quantile.html)