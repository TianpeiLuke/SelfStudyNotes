---
tags:
  - code
  - code_snippet
  - buyer_seller_messaging
  - pytorch/torchmetrics
keywords: 
topics: 
language: python
date of note: 2025-04-10
---

## Code Snippet Summary

>[!important]
>Define an interface for various metric computation, used in training logging


## Code

```python
from torch import Tensor
```

```python
from torchmetrics.functional import (
    auroc,
    roc,
    confusion_matrix,
    average_precision,
    f1_score,
    precision,
    recall,
    specificity,
    kl_divergence
)

from torchmetrics.functional.classification import (
    accuracy, binary_recall_at_fixed_precision, multiclass_recall_at_fixed_precision
)
```

### Mapper

```python
LABEL_BASED_METRICS = {
    "accuracy", "f1_score", "precision", "recall"
}

PROB_BASED_METRICS = {
    "auroc", "average_precision", "kl_divergence",
    "binary_recall_at_fixed_precision", "multiclass_recall_at_fixed_precision"
}

SUPPORTED_METRICS = {
    "accuracy": accuracy,
    "f1_score": f1_score,
    "auroc": auroc,
    "average_precision": average_precision,
    "precision": precision,
    "recall": recall,
    "kl_divergence": kl_divergence,
    "specificity": specificity,
    "binary_recall_at_fixed_precision": binary_recall_at_fixed_precision,
    "multiclass_recall_at_fixed_precision": multiclass_recall_at_fixed_precision,
}
```

### Interface of Metric Computation

```python
def compute_metrics(
    preds: Tensor,
    target: Tensor,
    metric_choices: Union[str, List[str]],
    task: str = "binary",
    num_classes: int = 2,
    stage: str = None,
) -> Dict[str, Union[Tensor, Tuple[Tensor, Tensor]]]:
    """
    Compute classification metrics.

    Args:
        preds (Tensor): Model predictions.
        target (Tensor): Ground-truth labels.
        metric_choices (Union[str, List[str]]): Metric or list of metrics.
        task (str): One of 'binary' or 'multiclass'.
        num_classes (int): Number of classes (for multiclass).
        stage (str, optional): Stage name for prefixing metric keys (e.g. 'val').

    Returns:
        Dict[str, Tensor]: Dictionary of metric names and values.
    """
    if isinstance(metric_choices, str):
        metric_choices = [metric_choices]
    elif not isinstance(metric_choices, list):
        raise TypeError("metric_choices must be a str or list of str")

    prefix = f"{stage}/" if stage else ""
    metrics = {}

    for metric in metric_choices:
        if metric not in SUPPORTED_METRICS:
            raise ValueError(
                f"Unsupported metric '{metric}'. Supported metrics are: {', '.join(SUPPORTED_METRICS)}"
            )

        key = f"{prefix}{metric}"
        fn = SUPPORTED_METRICS[metric]

        if metric == "kl_divergence":
            val = fn(preds, target)

        elif metric == "binary_recall_at_fixed_precision":
            val = fn(preds, target, min_precision=0.5)

        elif metric == "multiclass_recall_at_fixed_precision":
            val = fn(preds, target, num_classes=num_classes, min_precision=0.5)

        elif metric in {"accuracy", "f1_score", "auroc", "average_precision", "precision", "recall", "specificity"}:
            val = fn(preds, target, task=task, num_classes=num_classes)

        else:
            val = fn(preds, target)

        metrics[key] = val

    return metrics
```


### Test 

```python
class TestComputeMetrics(unittest.TestCase):

    def setUp(self):
        self.binary_preds = torch.tensor([0.8, 0.1, 0.9, 0.4])
        self.binary_target = torch.tensor([1, 0, 1, 0])

        self.multi_preds = torch.tensor([
            [0.7, 0.2, 0.1],
            [0.1, 0.8, 0.1],
            [0.2, 0.3, 0.5],
            [0.9, 0.05, 0.05]
        ])
        self.multi_target = torch.tensor([0, 1, 2, 0])

        self.kl_preds = torch.tensor([[0.9, 0.1], [0.6, 0.4]])
        self.kl_target = torch.tensor([[0.8, 0.2], [0.5, 0.5]])

    def test_binary_all_metrics(self):
        for metric in SUPPORTED_METRICS:
            if metric in {"kl_divergence", "multiclass_recall_at_fixed_precision"}:
                continue

            with self.subTest(metric=metric):
                result = compute_metrics(
                    preds=self.binary_preds,
                    target=self.binary_target,
                    metric_choices=[metric],
                    task="binary",
                    num_classes=2
                )
                self.assertIn(metric, result)
                val = result[metric]
                if metric == "binary_recall_at_fixed_precision":
                    self.assertIsInstance(val, tuple)
                    self.assertTrue(all(isinstance(v, torch.Tensor) for v in val))
                else:
                    self.assertIsInstance(val, torch.Tensor)

    def test_multiclass_all_metrics(self):
        for metric in SUPPORTED_METRICS:
            if metric in {"kl_divergence", "binary_recall_at_fixed_precision"}:
                continue

            with self.subTest(metric=metric):
                result = compute_metrics(
                    preds=self.multi_preds,
                    target=self.multi_target,
                    metric_choices=[metric],
                    task="multiclass",
                    num_classes=3
                )
                self.assertIn(metric, result)
                val = result[metric]
                if metric == "multiclass_recall_at_fixed_precision":
                    self.assertIsInstance(val, tuple)
                    self.assertTrue(all(isinstance(v, torch.Tensor) for v in val))
                else:
                    self.assertIsInstance(val, torch.Tensor)

    def test_kl_divergence_metric(self):
        result = compute_metrics(
            preds=self.kl_preds,
            target=self.kl_target,
            metric_choices="kl_divergence"
        )
        self.assertIn("kl_divergence", result)
        self.assertIsInstance(result["kl_divergence"], torch.Tensor)

    def test_stage_prefix(self):
        result = compute_metrics(
            preds=self.binary_preds,
            target=self.binary_target,
            metric_choices="accuracy",
            stage="val"
        )
        self.assertIn("val/accuracy", result)

    def test_invalid_metric_raises(self):
        with self.assertRaises(ValueError):
            compute_metrics(
                preds=self.binary_preds,
                target=self.binary_target,
                metric_choices="not_a_metric"
            )

    def test_invalid_metric_type(self):
        with self.assertRaises(TypeError):
            compute_metrics(
                preds=self.binary_preds,
                target=self.binary_target,
                metric_choices=123
            )

    def test_binary_metrics(self):
        y_pred = torch.tensor([0.1, 0.4, 0.6, 0.8])
        y_true = torch.tensor([0, 0, 1, 1])
        metric_choices = [
            "accuracy", "f1_score", "auroc", "average_precision",
            "precision", "recall", "binary_recall_at_fixed_precision"
        ]

        results = compute_metrics(y_pred, y_true, metric_choices, task='binary', num_classes=2)

        self.assertAlmostEqual(results["accuracy"].item(), accuracy(y_pred, y_true, task='binary').item(), places=4)
        self.assertAlmostEqual(results["f1_score"].item(), f1_score(y_pred, y_true, task='binary').item(), places=4)
        self.assertAlmostEqual(results["auroc"].item(), auroc(y_pred, y_true, task='binary').item(), places=4)
        self.assertAlmostEqual(results["average_precision"].item(), average_precision(y_pred, y_true, task='binary').item(), places=4)
        self.assertAlmostEqual(results["precision"].item(), precision(y_pred, y_true, task='binary').item(), places=4)
        self.assertAlmostEqual(results["recall"].item(), recall(y_pred, y_true, task='binary').item(), places=4)

        precision_out, recall_out = results["binary_recall_at_fixed_precision"]
        ref_precision, ref_recall = binary_recall_at_fixed_precision(y_pred, y_true, min_precision=0.5)
        self.assertTrue(torch.allclose(precision_out, ref_precision, atol=1e-4))
        self.assertTrue(torch.allclose(recall_out, ref_recall, atol=1e-4))

    def test_multiclass_metrics(self):
        y_pred = torch.softmax(torch.tensor([[0.1, 0.2, 0.7],
                                             [0.2, 0.7, 0.1],
                                             [0.6, 0.2, 0.2]]), dim=1)
        y_true = torch.tensor([2, 1, 0])
        num_classes = 3
        metric_choices = [
            "accuracy", "f1_score", "auroc", "average_precision",
            "precision", "recall", "multiclass_recall_at_fixed_precision"
        ]

        results = compute_metrics(y_pred, y_true, metric_choices, task='multiclass', num_classes=num_classes)

        self.assertAlmostEqual(results["accuracy"].item(), accuracy(y_pred, y_true, task='multiclass', num_classes=num_classes).item(), places=4)
        self.assertAlmostEqual(results["f1_score"].item(), f1_score(y_pred, y_true, task='multiclass', num_classes=num_classes).item(), places=4)
        self.assertAlmostEqual(results["auroc"].item(), auroc(y_pred, y_true, task='multiclass', num_classes=num_classes).item(), places=4)
        self.assertAlmostEqual(results["average_precision"].item(), average_precision(y_pred, y_true, task='multiclass', num_classes=num_classes).item(), places=4)
        self.assertAlmostEqual(results["precision"].item(), precision(y_pred, y_true, task='multiclass', num_classes=num_classes).item(), places=4)
        self.assertAlmostEqual(results["recall"].item(), recall(y_pred, y_true, task='multiclass', num_classes=num_classes).item(), places=4)

        precision_out, recall_out = results["multiclass_recall_at_fixed_precision"]
        ref_precision, ref_recall = multiclass_recall_at_fixed_precision(y_pred, y_true, num_classes=num_classes, min_precision=0.5)
        self.assertTrue(torch.allclose(precision_out, ref_precision, atol=1e-4))
        self.assertTrue(torch.allclose(recall_out, ref_recall, atol=1e-4))
```






-----------
##  Recommended Notes

- [[RnR Model Performance Plots]]