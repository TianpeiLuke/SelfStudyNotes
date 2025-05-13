---
tags:
  - code
  - code_snippet
  - python/plot
  - python/metric
  - python/ml
keywords: 
topics: 
language: python
date of note: 2025-05-12
---

## Code Snippet Summary

>[!important]
>- Compute the AUC-ROC for each class of multi-class prediction
>- Compute both micro-average and macro-average

- [[Receiver Characteristic Curve for Binary Classification]]
- [[Macro-Average and Micro-Average for Multi-Class Metric]]
- [[Plot Micro-average of ROC and PR Curve for Multiclass]]

## Code

```python
from sklearn.metrics import roc_auc_score, average_precision_score
from sklearn.metrics import roc_curve, precision_recall_curve
from sklearn.preprocessing import label_binarize
```

```python
def calculate_metrics(y_true, y_pred):
    # Get number of classes
    n_classes = y_pred.shape[1] if len(y_pred.shape) > 1 else 2
    
    # If predictions are probabilities, convert to class labels
    if len(y_pred.shape) > 1:
        y_pred_labels = np.argmax(y_pred, axis=1)
    else:
        y_pred_labels = y_pred
        
    # Convert y_true to one-hot encoding if needed
    if len(y_true.shape) == 1:
        y_true_bin = label_binarize(y_true, classes=np.arange(n_classes))
    else:
        y_true_bin = y_true
        
    # Calculate per-class metrics
    auc_scores = []
    ap_scores = []
    
    for i in range(n_classes):
        try:
            auc = roc_auc_score(y_true_bin[:, i], y_pred[:, i])
            ap = average_precision_score(y_true_bin[:, i], y_pred[:, i])
            auc_scores.append(auc)
            ap_scores.append(ap)
        except Exception as e:
            print(f"Error calculating metrics for class {i}: {str(e)}")
    
    # Calculate micro and macro averaged metrics
    try:
        # Micro average
        micro_auc = roc_auc_score(y_true_bin, y_pred, average='micro')
        micro_ap = average_precision_score(y_true_bin, y_pred, average='micro')
        
        # Macro average
        macro_auc = roc_auc_score(y_true_bin, y_pred, average='macro')
        macro_ap = average_precision_score(y_true_bin, y_pred, average='macro')
        
    except Exception as e:
        print(f"Error calculating averaged metrics: {str(e)}")
        micro_auc = macro_auc = micro_ap = macro_ap = np.nan
            
    return {
        'AUC-ROC (micro-avg)': micro_auc,
        'AUC-ROC (macro-avg)': macro_auc,
        'AUC-ROC per class': auc_scores,
        'Average Precision (micro-avg)': micro_ap,
        'Average Precision (macro-avg)': macro_ap,
        'Average Precision per class': ap_scores
    }

```




-----------
##  Recommended Notes

- [[Calculate Precision at N percent based on Score]]
- [[Calculate Recall at 1 percent false positive rate]]