---
tags:
  - code
  - code_snippet
  - reversal_reclassification
keywords: 
topics: 
language: python
date of note: 2025-04-11
---

## Code Snippet Summary

>[!important]


## Code

```python
import io
import os
import matplotlib.pyplot as plt
from PIL import Image
from typing import Union, List, Dict, Tuple
import shutil
import tempfile
```

```python
import torch
from torch import Tensor
from torch.utils.tensorboard import SummaryWriter

from torchmetrics.functional import (
    confusion_matrix,
    f1_score,
    precision,
    recall,
    auroc,
    average_precision,
    specificity,
    kl_divergence,
)

from torchmetrics.functional.classification import (
    accuracy,
    binary_recall_at_fixed_precision,
    multiclass_recall_at_fixed_precision,
    roc as binary_roc,
    auroc as binary_auroc,
    average_precision as binary_ap,
    precision_recall_curve as binary_pr_curve,
    multiclass_roc,
    multiclass_auroc,
    multiclass_precision_recall_curve,
    multiclass_average_precision
)

```

### Save to Tensorboard

```python
def plot_to_tensorboard(writer: SummaryWriter, tag: str, figure: plt.Figure, global_step: int = 0):
    """
    Convert a matplotlib figure to a TensorBoard image and log it.
    """
    buf = io.BytesIO()
    figure.savefig(buf, format='png')
    buf.seek(0)
    import PIL.Image
    image = PIL.Image.open(buf)
    image = torch.tensor(np.array(image)).permute(2, 0, 1).unsqueeze(0)  # Convert to CHW
    writer.add_image(tag, image[0], global_step=global_step)
    buf.close()
```

### Fixed Color


```python
from matplotlib import cm

# Color palettes
class_colors = cm.get_cmap('tab10')  # tab10 supports up to 10 distinct colors
curve_colors = {
    "test": "red",
    "val": "green",
    "micro": "blue",
    "macro": "purple",
    "weighted": "orange"
}
```

### ROC (Binary and Multiclass)


```python
def roc_metric_plot(
    y_pred: Tensor,
    y_true: Tensor,
    y_val_pred: Tensor,
    y_val_true: Tensor,
    path: str,
    task: str = 'binary',
    num_classes: int = 2,
    writer: SummaryWriter = None,
    global_step: int = 0
):
    # Ensure tensors are detached from graph and moved to CPU
    y_pred = y_pred.clone().detach()
    y_true = y_true.clone().detach()
    y_val_pred = y_val_pred.clone().detach()
    y_val_true = y_val_true.clone().detach()

    if task == "binary":
        # Compute ROC curve and AUC for binary classification
        fpr, tpr, _ = roc(y_pred, y_true, task='binary')
        fpr_val, tpr_val, _ = roc(y_val_pred, y_val_true, task='binary')
        auc = auroc(y_pred, y_true, task='binary')
        auc_val = auroc(y_val_pred, y_val_true, task='binary')

        # Plot and save ROC curve
        plt.figure(figsize=(10, 8))
        plt.plot(fpr, tpr, color="darkorange", lw=2, label=f"Test AUC = {auc:.3f}")
        plt.plot(fpr_val, tpr_val, color="blue", lw=2, label=f"Val AUC = {auc_val:.3f}")
        plt.plot([0, 1], [0, 1], 'k--', lw=1)  # Diagonal reference line
        plt.xlabel("False Positive Rate")
        plt.ylabel("True Positive Rate")
        plt.title("ROC Curve (Binary)")
        plt.legend()
        plt.tight_layout()
        file_path = os.path.join(path, "ROC-BSM.svg")
        plt.savefig(file_path)
        if writer:
            writer.add_figure("ROC/Binary", plt.gcf(), global_step=global_step)
        plt.close()

    else:
        # --------------------------
        # One-vs-Rest ROC Curves
        # --------------------------        
        fpr, tpr, _ = roc(y_pred, y_true, task="multiclass", num_classes=num_classes,  average=None)
        auc_scores = auroc(y_pred, y_true, task="multiclass", num_classes=num_classes, average=None)
        
        fpr_val, tpr_val, _ = roc(y_val_pred, y_val_true, task='multiclass', num_classes=num_classes,  average=None)
        auc_val = auroc(y_val_pred, y_val_true, task='multiclass', num_classes=num_classes,  average=None)


        # Plot all class-wise ROC curves on Test Data
        plt.figure(figsize=(10, 8))
        for i in range(num_classes):
            plt.plot(fpr[i], tpr[i], label=f"Class {i} (AUC = {auc_scores[i]:.3f})")
        plt.plot([0, 1], [0, 1], 'k--', lw=1)
        plt.xlabel("False Positive Rate")
        plt.ylabel("True Positive Rate")
        plt.title("One-vs-Rest ROC Curve")
        plt.legend()
        plt.tight_layout()
        file_path = os.path.join(path, "ROC-BSM-ovr.svg")
        plt.savefig(file_path)
        if writer:
            writer.add_figure("ROC/Multiclass-OneVsRest-Test", plt.gcf(), global_step=global_step)
        plt.close()
        
        # Plot all class-wise ROC curves on Validation Data
        plt.figure(figsize=(10, 8))
        for i in range(num_classes):
            plt.plot(fpr_val[i], tpr_val[i], label=f"Class {i} (AUC = {auc_val[i]:.3f})")
        plt.plot([0, 1], [0, 1], 'k--', lw=1)
        plt.xlabel("False Positive Rate")
        plt.ylabel("True Positive Rate")
        plt.title("One-vs-Rest ROC Curve")
        plt.legend()
        plt.tight_layout()
        file_path = os.path.join(path, "ROC-BSM-validation-ovr.svg")
        plt.savefig(file_path)
        if writer:
            writer.add_figure("ROC/Multiclass-OneVsRest-Validation", plt.gcf(), global_step=global_step)
        plt.close()

        # --------------------------
        # Macro and Weighted Averaged ROC Curves
        # --------------------------
        for avg in ["macro", "weighted"]:
            # Compute averaged ROC using built-in multiclass_roc
            roc_avg = avg if avg == "macro" else "micro"
            fpr_avg, tpr_avg, _ = roc(
                y_pred, y_true, task="multiclass",  num_classes=num_classes, average=roc_avg
            )
            auc_avg = auroc(
                y_pred, y_true, task="multiclass", num_classes=num_classes, average=avg
            )

            # Plot averaged ROC curve
            plt.figure(figsize=(10, 8))
            plt.plot(fpr_avg, tpr_avg, label=f"{avg.capitalize()} AUC = {auc_avg:.3f}")
            plt.plot([0, 1], [0, 1], 'k--')
            plt.xlabel("False Positive Rate")
            plt.ylabel("True Positive Rate")
            plt.title(f"{avg.capitalize()}-Averaged ROC Curve")
            plt.legend()
            plt.tight_layout()
            file_path = os.path.join(path, f"ROC-BSM-{avg}.svg")
            plt.savefig(file_path)
            if writer:
                writer.add_figure(f"ROC/{avg.capitalize()}", plt.gcf(), global_step=global_step)
            plt.close()
```


### Precision Recall (Binary and Multiclass)

```python
def pr_metric_plot(
    y_pred,
    y_true,
    y_val_pred,
    y_val_true,
    path,
    task='binary',
    num_classes=2,
    writer: SummaryWriter = None,
    global_step: int = 0
):
    y_pred = y_pred.clone().detach()
    y_true = y_true.clone().detach()
    y_val_pred = y_val_pred.clone().detach()
    y_val_true = y_val_true.clone().detach()

    if task == "binary":
        precision_test, recall_test, _ = precision_recall_curve(y_pred, y_true, task='binary')
        ap_test = average_precision(y_pred, y_true, task='binary')
        precision_val, recall_val, _ = precision_recall_curve(y_val_pred, y_val_true, task='binary')
        ap_val = average_precision(y_val_pred, y_val_true, task='binary')

        plt.figure(figsize=(10, 8))
        plt.plot(recall_test, precision_test, label=f"Test AP = {ap_test:.3f}", color="darkorange")
        plt.plot(recall_val, precision_val, label=f"Val AP = {ap_val:.3f}", color="blue")
        plt.xlabel("Recall")
        plt.ylabel("Precision")
        plt.title("Precision-Recall Curve (Binary)")
        plt.legend()
        file_path = os.path.join(path, "PR-BSM.svg")
        plt.savefig(file_path)
        plt.close()
        if writer:
            writer.add_figure("PR/Binary", plt.gcf(), global_step=global_step)

    else:
        # One-vs-rest
        precision, recall, _ = precision_recall_curve(y_pred, y_true, task='multiclass', num_classes=num_classes, average=None)
        ap_scores = average_precision(y_pred, y_true, task='multiclass', num_classes=num_classes, average=None)

        precision_val, recall_val, _ = precision_recall_curve(y_pred, y_true, task='multiclass', num_classes=num_classes, average=None)
        ap_val = average_precision(y_pred, y_true, task='multiclass', num_classes=num_classes, average=None)
        
        plt.figure(figsize=(10, 8))
        for i in range(num_classes):
            plt.plot(recall[i], precision[i], label=f"Class {i} (AP = {ap_scores[i]:.3f})")
        plt.xlabel("Recall")
        plt.ylabel("Precision")
        plt.title("One-vs-Rest PR Curve")
        plt.legend()
        file_path = os.path.join(path, "PR-BSM-ovr.svg")
        plt.savefig(file_path)
        plt.close()
        if writer:
            writer.add_figure("PR/Multiclass-OneVsRest-Test", plt.gcf(), global_step=global_step)

        plt.figure(figsize=(10, 8))
        for i in range(num_classes):
            plt.plot(recall_val[i], precision_val[i], label=f"Class {i} (AP = {ap_val[i]:.3f})")
        plt.xlabel("Recall")
        plt.ylabel("Precision")
        plt.title("One-vs-Rest PR Curve")
        plt.legend()
        file_path = os.path.join(path, "PR-BSM-validation-ovr.svg")
        plt.savefig(file_path)
        plt.close()
        if writer:
            writer.add_figure("PR/Multiclass-OneVsRest-Validation", plt.gcf(), global_step=global_step)
            
            
        for avg in ["macro", "weighted"]:
            # precision recall curve only accept "micro" and "macro"
            pr_avg = avg if avg == "macro" else "micro"
            precision_avg, recall_avg, _ = precision_recall_curve(
                y_pred, y_true, task='multiclass', num_classes=num_classes, average=pr_avg
            )
            ap_avg = average_precision(y_pred, y_true,  task='multiclass', num_classes=num_classes, average=avg)

            plt.figure(figsize=(10, 8))
            plt.plot(recall_avg, precision_avg, label=f"{avg.capitalize()} AP = {ap_avg:.3f}", color="darkgreen")
            plt.xlabel("Recall")
            plt.ylabel("Precision")
            plt.title(f"{avg.capitalize()}-Averaged PR Curve")
            plt.legend()
            file_path = os.path.join(path, f"PR-BSM-{avg}.svg")
            plt.savefig(file_path)
            plt.close()
            if writer:
                writer.add_figure(f"PR/{avg.capitalize()}", plt.gcf(), global_step=global_step)

```


### Test

```python
class TestPlModelPlots(unittest.TestCase):

    def setUp(self):
        # Binary predictions: shape must be [B]
        self.binary_logits = torch.tensor([0.1, 0.4, 0.9, 0.7])  # Removed unsqueeze
        self.binary_labels = torch.tensor([0, 0, 1, 1])

        self.multiclass_logits = torch.tensor([
            [0.1, 0.7, 0.2],
            [0.3, 0.3, 0.4],
            [0.9, 0.05, 0.05],
            [0.1, 0.8, 0.1]
        ])
        self.multiclass_labels = torch.tensor([1, 2, 0, 1])

        self.tmpdir = tempfile.TemporaryDirectory()
        self.outdir = self.tmpdir.name

    def tearDown(self):
        self.tmpdir.cleanup()

    def test_roc_metric_plot_binary(self):
        roc_metric_plot(
            y_pred=self.binary_logits,
            y_true=self.binary_labels,
            y_val_pred=self.binary_logits,
            y_val_true=self.binary_labels,
            path=self.outdir,
            task="binary"
        )
        self.assertTrue(os.path.exists(os.path.join(self.outdir, "ROC-BSM.svg")))

    def test_pr_metric_plot_binary(self):
        pr_metric_plot(
            y_pred=self.binary_logits,
            y_true=self.binary_labels,
            y_val_pred=self.binary_logits,
            y_val_true=self.binary_labels,
            path=self.outdir,
            task="binary"
        )
        self.assertTrue(os.path.exists(os.path.join(self.outdir, "PR-BSM.svg")))

    def test_roc_metric_plot_multiclass(self):
        roc_metric_plot(
            y_pred=self.multiclass_logits,
            y_true=self.multiclass_labels,
            y_val_pred=self.multiclass_logits,
            y_val_true=self.multiclass_labels,
            path=self.outdir,
            task="multiclass",
            num_classes=3
        )
        for fname in [
            "ROC-BSM-ovr.svg",
            "ROC-BSM-validation-ovr.svg",
            "ROC-BSM-macro.svg",
            "ROC-BSM-weighted.svg"
        ]:
            self.assertTrue(os.path.exists(os.path.join(self.outdir, fname)))

    def test_pr_metric_plot_multiclass(self):
        pr_metric_plot(
            y_pred=self.multiclass_logits,
            y_true=self.multiclass_labels,
            y_val_pred=self.multiclass_logits,
            y_val_true=self.multiclass_labels,
            path=self.outdir,
            task="multiclass",
            num_classes=3
        )
        for fname in [
            "PR-BSM-ovr.svg",
            "PR-BSM-validation-ovr.svg",
            "PR-BSM-macro.svg",
            "PR-BSM-weighted.svg"
        ]:
            self.assertTrue(os.path.exists(os.path.join(self.outdir, fname)))
```

```python
unittest.main(argv=[''], exit=False,  defaultTest='TestPlModelPlots')
```


-----------
##  Recommended Notes

- [[RnR Model Compute Metrics]]
- [[Trainer for BERT Fine-tune v2]]
- [[Multi-modal BERT Classification Model v2 for BSM]]
- [[RnR Model Compute Metrics]]