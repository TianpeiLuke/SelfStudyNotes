---
tags:
  - code
  - code_snippet
  - python/sklearn
  - python/plot
keywords: 
topics: 
language: python
date of note: 2024-04-07
---

## Code Snippet Summary

>[!important]
>Given two binary vectors `vec_true` and `vec_predict` of the same dimension, 
>- plot **confusion matrix**, assuming `vec_true` is true label, `vec_predict` is predicted label
>- compute **recall** and **precision**
>- compute **false positive rate (FPR)**, **false negative rate (FNR)**, **true positive rate (TPR)** and **true negative rate(TNR)**.



## Code

```python
import matplotlib.pyplot as plt
import numpy as np
from sklearn.metrics import confusion_matrix, ConfusionMatrixDisplay

plt.figure(figsize=(10, 6))

# row normalized, conditioned on true label
cm = confusion_matrix(vec_true, vec_predict, normalize='true')

# column normalized, conditioned on predicted label
cm = confusion_matrix(y_true, y_pred,normalize='pred')

cm_display = ConfusionMatrixDisplay(cm).plot()

plt.xlabel('predicted label')
plt.ylabel('true label')
plt.title('Confusion Table (conditioned on true label)')

# Save the plot to a .png file
root_folder = ...
date_folder = ...
fig_filename = ...

if not os.path.exists(os.path.join(root_folder, date_folder)):
    os.makedirs(os.path.join(root_folder, date_folder))

plt.savefig(os.path.join(root_folder, date_folder, fig_filename))

# Display the plot
plt.show()
```


- `sklearn.metrics.confusion_matrix`: Compute confusion matrix to evaluate the accuracy of a classification. [reference](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.confusion_matrix.html#sklearn-metrics-confusion-matrix)
	- By definition a **confusion matrix $C$** is such that $C_{i,j}$  is equal to the *number* of observations *known to be in group $i$* and *predicted* to be in group $j$.
	- Thus in *binary classification*, the count of 
		- **true negatives** is $C_{0,0}$, 
		- **false negatives** is $C_{1,0}$, 
		- **true positives** is $C_{1,1}$ and 
		- **false positives** is $C_{0,1}$.
	- **`y_true`**: true label. shape $(n_{sample} \;,\; )$
	- **`y_pred`**: predicted label. Same shape as above
	- `labels`: List of labels to index the matrix. 
		- This may be used to *reorder* or *select a subset of labels.* 
		- If `None` is given, those that appear at least once in `y_true` or `y_pred` are used in *sorted order*.
	- **`normalize`**: Normalizes confusion matrix over the *true (rows)*, *predicted (columns)* conditions or all the population. 
		- If `None`, confusion matrix will be *not be normalized*.
		  
	- Return $C \in \mathbf{R}_{n_{class} \times n_{class}}$
	    
- `sklearn.metrics.ConfusionMatrixDisplay`: [reference](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.ConfusionMatrixDisplay.html#sklearn-metrics-confusionmatrixdisplay)
	- **`confusion_matrix`**: ndarray $n_{class} \times n_{class}$: Confusion matrix.
	- **`display_labels`**: ndarray of shape (n_classes,), default=None. Display labels for plot. If None, display labels are set from 0 to `n_classes - 1`.
	  
	- `from_predictions()`: Plot Confusion Matrix given true and predicted labels. [reference](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.ConfusionMatrixDisplay.html#sklearn.metrics.ConfusionMatrixDisplay.from_predictions)
		- `y_true`: true label. shape $(n_{sample} \;,\; )$
		- `y_pred`: predicted label. Same shape as above
		- `labels`: List of labels to index the matrix. 
		- `normalize`: Normalizes confusion matrix over the *true (rows)*, *predicted (columns)* conditions or all the population. 
		- `display_labels`: Target names used for plotting. 
			- By default, `labels` will be used if it is defined, otherwise the unique labels of `y_true` and `y_pred` will be used.
			  
		- **`cmap`**: colormap. `matplotlib` parameters
		- **`ax`**: Axes object to plot on
		- **`colorbar`**: Whether or not to add a colorbar to the plot. `matplotlib` parameters


-----------
##  Recommended Notes

- `sklearn.metrics.confusion_matrix`: [reference](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.confusion_matrix.html#sklearn-metrics-confusion-matrix)
- `sklearn.metrics.ConfusionMatrixDisplay`: [reference](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.ConfusionMatrixDisplay.html#sklearn-metrics-confusionmatrixdisplay)
	- `from_predictions()`: Plot Confusion Matrix given true and predicted labels. [reference](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.ConfusionMatrixDisplay.html#sklearn.metrics.ConfusionMatrixDisplay.from_predictions)