---
tags:
  - code
  - code_snippet
  - python/plot
keywords: 
topics: 
language: python
date of note: 2025-05-12
---

## Code Snippet Summary

>[!important]
>- Compare ROC and PR between single classes
>- Micro-average

- [[Download and Compute Metrics of SageMaker Models]]
- [[Macro-Average and Micro-Average for Multi-Class Metric]]


## Code

```python
import matplotlib.pyplot as plt
```

### Plot Micro-Average ROC curves for multiple models

```python
def plot_roc_comparison(all_results, model_classes, metrics_results, n_classes):
    plt.figure(figsize=(10, 8))
    colors = ['#2ecc71', '#3498db', '#e74c3c', '#f1c40f']

    for i, model_class in enumerate(model_classes):
        if model_class in all_results:
            y_true = all_results[model_class]['y_true']
            y_pred = all_results[model_class]['y_pred']
            
            if len(y_true.shape) == 1:
                y_true_bin = label_binarize(y_true, classes=np.arange(n_classes))
            else:
                y_true_bin = y_true

            fpr = dict()
            tpr = dict()
            for cls in range(n_classes):
                fpr[cls], tpr[cls], _ = roc_curve(y_true_bin[:, cls], y_pred[:, cls])
            
            fpr_micro = np.unique(np.concatenate([fpr[i] for i in range(n_classes)]))
            tpr_micro = np.mean([np.interp(fpr_micro, fpr[i], tpr[i]) for i in range(n_classes)], axis=0)
            
            plt.plot(fpr_micro, tpr_micro, color=colors[i], 
                    label=f'{model_class} (AUC = {metrics_results[model_class]["AUC-ROC"]:.3f})',
                    linewidth=2)

    plt.plot([0, 1], [0, 1], 'k--', label='Random')
    plt.xlabel('False Positive Rate')
    plt.ylabel('True Positive Rate')
    plt.title('Micro-average ROC Curves Comparison')
    plt.legend(loc='lower right')
    plt.grid(True)
    plt.savefig('roc_comparison.png', dpi=300, bbox_inches='tight')
    plt.close()
```

#### Micro-Averaging ROC Curve

```python
fpr = dict()
tpr = dict()
# compute FPR, TPR for each class
for cls in range(n_classes):
    fpr[cls], tpr[cls], _ = roc_curve(y_true_bin[:, cls], y_pred[:, cls])

# find a common set of unique FPR values
fpr_micro = np.unique(np.concatenate([fpr[i] for i in range(n_classes)]))

# Micro-averaging of TPR
tpr_micro = np.mean([np.interp(fpr_micro, fpr[i], tpr[i]) for i in range(n_classes)], axis=0)
```

- During the mirco-averaging
	- for each unique FPR value, **interpolates** the corresponding *TPR* from each class's ROC curve.
	- calculate the **mean** of *interpolated TPR values* across all classes

>[!info]
> - Note: **this code does not directly compute the micro-average of the AUC-ROC.** 
> 	- Instead, it computes and plots the **micro-averaged ROC curve**.


>[!important]
>Here's why this distinction is important:
> 
> - **Micro-averaged ROC Curve:** 
> 	- This is obtained by pooling the true positives and false positives across all classes and then calculating a single ROC curve. 
> 	- The code achieves this by effectively *averaging the interpolated TPR* values at *common FPR points*.
> - **Micro-averaged AUC-ROC:** 
> 	- This would involve calculating the AUC under the micro-averaged ROC curve. 
> 	- The provided code **does not explicitly calculate this AUC**. It relies on a pre-calculated `"AUC-ROC"` value stored in the `metrics_results` dictionary.


### Plot Micro-Average PR curve for multiple models

```python
def plot_pr_comparison(all_results, model_classes, metrics_results, n_classes):
    plt.figure(figsize=(10, 8))
    colors = ['#2ecc71', '#3498db', '#e74c3c', '#f1c40f']

    for i, model_class in enumerate(model_classes):
        if model_class in all_results:
            y_true = all_results[model_class]['y_true']
            y_pred = all_results[model_class]['y_pred']
            
            if len(y_true.shape) == 1:
                y_true_bin = label_binarize(y_true, classes=np.arange(n_classes))
            else:
                y_true_bin = y_true

            precision_curves = []
            recall_curves = []
            for cls in range(n_classes):
                p, r, _ = precision_recall_curve(y_true_bin[:, cls], y_pred[:, cls])
                recall_points = np.linspace(0, 1, 100)
                precision_points = np.interp(recall_points, r[::-1], p[::-1])
                precision_curves.append(precision_points)
                recall_curves.append(recall_points)
            
            precision_micro = np.mean(precision_curves, axis=0)
            recall_micro = recall_points
            
            plt.plot(recall_micro, precision_micro, color=colors[i], 
                    label=f'{model_class} (AP = {metrics_results[model_class]["Average Precision"]:.3f})',
                    linewidth=2)

    plt.xlabel('Recall')
    plt.ylabel('Precision')
    plt.title('Micro-average Precision-Recall Curves Comparison')
    plt.legend(loc='lower left')
    plt.grid(True)
    plt.savefig('pr_comparison.png', dpi=300, bbox_inches='tight')
    plt.close()
```


### Plot Metrics by Class

```python
def plot_metrics_by_class(metrics_results, model_classes):
    fig, (ax1, ax2) = plt.subplots(2, 1, figsize=(12, 10))
    colors = ['#2ecc71', '#3498db', '#e74c3c', '#f1c40f']
    
    n_models = len(model_classes)
    n_classes = len(metrics_results[model_classes[0]]['AUC-ROC per class'])
    width = 0.8 / n_models
    x = np.arange(n_classes)
    
    for i, model_class in enumerate(model_classes):
        if model_class in metrics_results:
            metrics = metrics_results[model_class]
            ax1.bar(x + i*width, metrics['AUC-ROC per class'], width, 
                   label=model_class, color=colors[i], alpha=0.8)
    
    ax1.set_ylabel('AUC-ROC Score')
    ax1.set_title('AUC-ROC Scores by Class')
    ax1.set_xticks(x + width * (n_models-1)/2)
    ax1.set_xticklabels([f'Class {i}' for i in range(n_classes)])
    ax1.legend(loc='center right')
    ax1.grid(True, alpha=0.3)
    
    for i, model_class in enumerate(model_classes):
        if model_class in metrics_results:
            metrics = metrics_results[model_class]
            ax2.bar(x + i*width, metrics['Average Precision per class'], width, 
                   label=model_class, color=colors[i], alpha=0.8)
    
    ax2.set_ylabel('Average Precision Score')
    ax2.set_title('Average Precision Scores by Class')
    ax2.set_xticks(x + width * (n_models-1)/2)
    ax2.set_xticklabels([f'Class {i}' for i in range(n_classes)])
    ax2.legend()
    ax2.grid(True, alpha=0.3)
    
    plt.tight_layout()
    plt.savefig('metrics_by_class.png', dpi=300, bbox_inches='tight')
    plt.close()
```

### Main Function

```python
# Main execution
def create_visualizations(all_results, model_classes, metrics_results):
    plt.style.use('default')
    n_classes = all_results[model_classes[0]]['y_pred'].shape[1]
    
    try:
        plot_roc_comparison(all_results, model_classes, metrics_results, n_classes)
        plot_pr_comparison(all_results, model_classes, metrics_results, n_classes)
        plot_metrics_by_class(metrics_results, model_classes)
        
        print("\nVisualization plots saved as:")
        print("- roc_comparison.png")
        print("- pr_comparison.png")
        print("- metrics_by_class.png")
    except Exception as e:
        print(f"\nError creating visualizations: {str(e)}")
```

```python
n_classes = y_pred.shape[1] if len(y_pred.shape) > 1 else 2
```

```python
create_visualizations(all_results, model_classes, metrics_results)
```




-----------
##  Recommended Notes

- [[Plot Precision-Recall Curve and Comparison]]
- [[Plot ROC Curve and Comparison]]