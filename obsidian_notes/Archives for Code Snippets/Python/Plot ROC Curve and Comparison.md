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
>- plot *ROC curve* and *AUC-ROC* metric

- [[Receiver Characteristic Curve for Binary Classification]]

## Code

```python
from sklearn.metrics import roc_curve, roc_auc_score
import pandas as pd
import matplotlib.pyplot as plt
import os
```

```python
fpr_old, tpr_old, _ = roc_curve(df_old['label'], df_old['prob'])
fpr_new, tpr_new, _ = roc_curve(df_new['label'], df_new['prob'])


roc_auc_old = roc_auc_score(df_old['label'], df_old['prob'])
roc_auc_new = roc_auc_score(df_new['label'], df_new['prob'])

plt.figure(figsize=(10,8))

lw = 1.5
plt.plot(fpr_new, tpr_new, color='red', lw=2*lw, label='new data (area = %0.3f)' % roc_auc_new)
plt.plot(fpr_old, tpr_old, color='darkgreen', lw=lw, label='old data (area = %0.3f)' % roc_auc_old)


plt.plot([0,1], [0,1], color='navy', lw=lw, linestyle='--')
plt.xlim([0.0, 1.0])
plt.ylim([0.0, 1.05])
plt.xlabel('False Positive Rate', fontsize=15)
plt.ylabel('True Positive Rate', fontsize=15)
plt.title("Receiver operating characteristic", fontsize=15)
plt.legend(loc='lower right', fontsize=15)


path = ''
filename = "ROC-BSM"+".png"

print("save png file to {}".format(os.path.join(path, filename)))
plt.savefig(os.path.join(path, filename))
```






-----------
##  Recommended Notes


- Sklearn `roc_curve`: [reference](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_curve.html)
- Sklearn `roc_auc_score`: [reference](https://scikit-learn.org/stable/modules/generated/sklearn.metrics.roc_auc_score.html)