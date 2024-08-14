---
tags:
  - code
  - code_snippet
  - python/plot
  - python/sklearn
keywords:
  - roc_curve
  - python/plot
topics:
  - plot
language: python
date of note: 2024-06-25
---

## Code Snippet Summary

>[!important]
>Given two dataframes `df_new`, `df_old`
>- for each df, there are two columns in `df`, 
>	- one for binary label, named `label`, 
>	- one for probability score, named `prob`,  
>- plot *Precision-Recall curve* and *Average Precision* metric

## Code

```python
from sklearn.metrics import precision_recall_curve, average_precision_score
import pandas as pd
import matplotlib.pyplot as plt
import os
```

```python
precision_old, recall_old, _ = precision_recall_curve(df_old['label'], df_old['prob'])
precision_new, recall_new, _ = precision_recall_curve(df_new['label'], df_new['prob'])


ap_old = average_precision_score(df_old['label'], df_old['prob'])
ap_new = average_precision_score(df_new['label'], df_new['prob'])

plt.figure(figsize=(10,8))

lw = 1.5
plt.plot(recall_new, precision_new, color='red', lw=2*lw, label='new data (area = %0.3f)' % ap_new)
plt.plot(recall_old, precision_old, color='darkgreen', lw=lw, label='old data (area = %0.3f)' % ap_old)


plt.plot([0,1], [0,1], color='navy', lw=lw, linestyle='--')
plt.xlim([0.0, 1.0])
plt.ylim([0.0, 1.05])
plt.xlabel('Recall', fontsize=15)
plt.ylabel('Precision', fontsize=15)
plt.title("Precision-Recall Curve", fontsize=15)
plt.legend(loc='lower right', fontsize=15)

path = ''
filename = "PR-BSM"+".png"

print("save png file to {}".format(os.path.join(path, filename)))
plt.savefig(os.path.join(path, filename))
```






-----------
##  Recommended Notes


- Sklearn `precision_recall_curve`: [reference](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.precision_recall_curve.html)
- Sklearn `average_precision_score`: [reference](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.average_precision_score.html)
- [AUC of Precision-Recall curve vs. Average Precision](https://stats.stackexchange.com/questions/157012/area-under-precision-recall-curve-auc-of-pr-curve-and-average-precision-ap)