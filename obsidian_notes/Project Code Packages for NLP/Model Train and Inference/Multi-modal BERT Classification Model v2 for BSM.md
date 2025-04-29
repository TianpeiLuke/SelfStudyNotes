---
tags:
  - code
  - code_snippet
  - buyer_seller_messaging
  - natural_language_processing
keywords:
  - pytorch
topics: 
language: python
date of note: 2025-01-02
---

## Code Snippet Summary

>[!important]
>This script contains the BERT class for *text classification*
>- The model class inherits from the `LightningModule` in `lightning` package
>- the main step loads *pretrained BERT* from huggingface
>- It *randomized* the last two layers for fine-tuning
>- The module contains two parts
>	- **forward pass** and *one forward steps* at training, testing and validation
>	- **event hooks**, mainly used for evaluation and synchronization

- [[Fine-Tuning for Sequence or Sequence-Pair Classification via BERT]]
- [[Bidirectional Encoder Representation from Transformer or BERT]]
- [[Pytorch Lightning 1 Module]]
- [[Hugging Face transformers doc excerpt 1 overview]]


## Code

```python
#!/usr/bin/env python3
import os
import json
import pickle
import sys
import time
import logging
import tarfile
from tqdm import tqdm, trange
from datetime import datetime

import boto3
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

from typing import Union, List, Tuple, Optional, Set, Dict
```

```python
import torch 
from torch.utils.data import Dataset, IterableDataset, DataLoader
import torch.optim as optim
from torch import nn

import lightning.pytorch as pl

from transformers import (AdamW,
                          AutoConfig,
                          AutoModel,
                          AutoTokenizer,
                          get_linear_schedule_with_warmup,
                          get_polynomial_decay_schedule_with_warmup,
                          get_constant_schedule_with_warmup,
                          get_cosine_schedule_with_warmup
                         )
```


```python
from .dist_utils import (all_gather, get_rank)
from .pl_bert import TextBertBase
from .pl_tab_ae import TabAE
from .pl_model_plots import compute_metrics
from torchmetrics.utilities.distributed import gather_all_tensors

dtype = torch.float
device = torch.device('cuda' if torch.cuda.is_available() else 'cpu') 


logger = logging.getLogger(__name__)
logging.basicConfig(format = '%(asctime)s - %(levelname)s - %(name)s -   %(message)s',
                    datefmt = '%m/%d/%Y %H:%M:%S',
                    level = logging.INFO)

```


- [[Tabular Autoencoder]]
- [[BERT Base Emedding Model for BSM]]
- [[RnR Model Compute Metrics]]


```python
class MultimodalBert(pl.LightningModule):
    def __init__(self, config: Dict[str, Union[int, float, str, bool, List[str], torch.FloatTensor]]):
        super().__init__()
        self.config = config
        self.model_class = "multimodal_bert"

        # === Core configuration ===
        self.id_name = config.get("id_name", None)
        self.label_name = config["label_name"]
        self.text_name = config["text_name"] + "_processed_input_ids"
        self.text_attention_mask = config["text_name"] + "_processed_attention_mask"
        self.tab_field_list = config.get("tab_field_list", None)

        self.is_binary = config.get("is_binary", True)
        self.task = "binary" if self.is_binary else "multiclass"
        self.num_classes = 2 if self.is_binary else config.get("num_classes", 2)
        self.metric_choices = config.get("metric_choices", ["accuracy", "f1_score"])

        self.model_path = config.get("model_path", "")
        self.lr = config.get("lr", 2e-5)
        self.weight_decay = config.get("weight_decay", 0.0)
        self.adam_epsilon = config.get("adam_epsilon", 1e-8)
        self.warmup_steps = config.get("warmup_steps", 0)
        self.run_scheduler = config.get("run_scheduler", True)

        self.id_lst, self.pred_lst, self.label_lst = [], [], []
        self.test_output_folder = None
        self.test_has_label = False

        # === Sub-networks ===
        self.tab_subnetwork = TabAE(config) if self.tab_field_list else None
        tab_dim = self.tab_subnetwork.output_tab_dim if self.tab_subnetwork else 0

        self.text_subnetwork = TextBertBase(config)
        text_dim = self.text_subnetwork.output_text_dim

        self.final_merge_network = nn.Sequential(
            nn.ReLU(),
            nn.Linear(tab_dim + text_dim, self.num_classes),
        )

        # === Loss function ===
        weights = config.get("class_weights")
        if weights and len(weights) == self.num_classes:
            self.loss_op = nn.CrossEntropyLoss(weight=torch.tensor(weights))
        else:
            self.loss_op = nn.CrossEntropyLoss()

        self.save_hyperparameters()

    def forward(self, batch: Dict[str, torch.Tensor]) -> torch.Tensor:
        tab_data = self.tab_subnetwork.combine_tab_data(batch) if self.tab_subnetwork else None
        return self._forward_impl(batch, tab_data)

    def _forward_impl(self, batch, tab_data) -> torch.Tensor:
        tab_data = tab_data.float()
        text_out = self.text_subnetwork(batch)  # keep this as is
        tab_out = self.tab_subnetwork(tab_data)
        combined = torch.cat([text_out, tab_out], dim=1)
        return self.final_merge_network(combined)

    def configure_optimizers(self):
        no_decay = ["bias", "LayerNorm.weight"]
        params = [
            {
                "params": [p for n, p in self.named_parameters() if not any(nd in n for nd in no_decay)],
                "weight_decay": self.weight_decay,
            },
            {
                "params": [p for n, p in self.named_parameters() if any(nd in n for nd in no_decay)],
                "weight_decay": 0.0,
            },
        ]
        optimizer = torch.optim.AdamW(params, lr=self.lr, eps=self.adam_epsilon)

        scheduler = (
            get_linear_schedule_with_warmup(optimizer, self.warmup_steps, self.trainer.estimated_stepping_batches)
            if self.run_scheduler
            else get_constant_schedule_with_warmup(optimizer, num_warmup_steps=self.warmup_steps)
        )
        return {"optimizer": optimizer, "lr_scheduler": {"scheduler": scheduler, "interval": "step"}}

    def run_epoch(self, batch, stage):
        labels = batch.get(self.label_name) if stage != "pred" else None

        if labels is not None and not isinstance(labels, torch.Tensor):
            labels = torch.tensor(labels, device=self.device)
            
        tab_data = self.tab_subnetwork.combine_tab_data(batch) if self.tab_subnetwork else None

        logits = self._forward_impl(batch, tab_data)
        loss = self.loss_op(logits, labels) if stage != "pred" else None

        preds = torch.softmax(logits, dim=1)
        preds = preds[:, 1] if self.is_binary else preds
        return loss, preds, labels

    def training_step(self, batch, batch_idx):
        loss, _, _ = self.run_epoch(batch, "train")
        self.log("train_loss", loss, sync_dist=True, prog_bar=True)
        return {"loss": loss}

    def on_validation_epoch_start(self):
        self.pred_lst.clear()
        self.label_lst.clear()

    def validation_step(self, batch, batch_idx):
        loss, preds, labels = self.run_epoch(batch, "val")
        self.log("val_loss", loss, sync_dist=True, prog_bar=True)
        self.pred_lst.extend(preds.detach().cpu().tolist())
        self.label_lst.extend(labels.detach().cpu().tolist())

    def on_validation_epoch_end(self):
        preds = torch.tensor(sum(all_gather(self.pred_lst), []))
        labels = torch.tensor(sum(all_gather(self.label_lst), []))
        metrics = compute_metrics(preds, labels, self.metric_choices, self.task, self.num_classes, "val")
        self.log_dict(metrics, prog_bar=True)

    def test_step(self, batch, batch_idx):
        mode = "test" if self.label_name in batch else "pred"
        self.test_has_label = mode == "test"

        loss, preds, labels = self.run_epoch(batch, mode)
        self.pred_lst.extend(preds.detach().cpu().tolist())
        if labels is not None:
            self.label_lst.extend(labels.detach().cpu().tolist())

        self.log("test_loss", loss, sync_dist=True, prog_bar=True)
        if self.id_name:
            self.id_lst.extend(batch[self.id_name])

    def on_test_epoch_start(self):
        self.id_lst.clear()
        self.pred_lst.clear()
        self.label_lst.clear()
        timestamp = datetime.now().strftime("%Y-%m-%d-%H-%M-%S")
        self.test_output_folder = Path(self.model_path) / f"{self.model_class}-{timestamp}"
        if self.trainer.is_global_zero:
            self.test_output_folder.mkdir(parents=True, exist_ok=True)

    def on_test_epoch_end(self):
        import pandas as pd

        results = {"prob": sum(all_gather(self.pred_lst), [])}
        if self.test_has_label:
            results["label"] = sum(all_gather(self.label_lst), [])
        if self.id_name:
            results[self.id_name] = sum(all_gather(self.id_lst), [])

        if self.global_rank == 0:
            df = pd.DataFrame(results)
            test_file = self.test_output_folder / f"test_result_{get_rank()}.tsv"
            df.to_csv(test_file, sep="\t", index=False)
            print(f"[Rank {get_rank()}] Saved test results to {test_file}")

    def predict_step(self, batch, batch_idx, dataloader_idx=0):
        mode = "test" if self.label_name in batch else "pred"
        _, preds, labels = self.run_epoch(batch, mode)
        return (preds, labels) if mode == "test" else preds
```

- [[RnR Model Compute Metrics]]


### Initialization

```python
    def __init__(self, config: Dict[str, Union[int, float, str, bool, List[str], torch.FloatTensor]]):
        super().__init__()
        self.config = config
        self.model_class = "multimodal_bert"

        # === Core configuration ===
        self.id_name = config.get("id_name", None)
        self.label_name = config["label_name"]
        self.text_name = config["text_name"] + "_processed_input_ids"
        self.text_attention_mask = config["text_name"] + "_processed_attention_mask"
        self.tab_field_list = config.get("tab_field_list", None)

        self.is_binary = config.get("is_binary", True)
        self.task = "binary" if self.is_binary else "multiclass"
        self.num_classes = 2 if self.is_binary else config.get("num_classes", 2)
        self.metric_choices = config.get("metric_choices", ["accuracy", "f1_score"])

        self.model_path = config.get("model_path", "")
        self.lr = config.get("lr", 2e-5)
        self.weight_decay = config.get("weight_decay", 0.0)
        self.adam_epsilon = config.get("adam_epsilon", 1e-8)
        self.warmup_steps = config.get("warmup_steps", 0)
        self.run_scheduler = config.get("run_scheduler", True)

        self.id_lst, self.pred_lst, self.label_lst = [], [], []
        self.test_output_folder = None
        self.test_has_label = False

        # === Sub-networks ===
        self.tab_subnetwork = TabAE(config) if self.tab_field_list else None
        tab_dim = self.tab_subnetwork.output_tab_dim if self.tab_subnetwork else 0

        self.text_subnetwork = TextBertBase(config)
        text_dim = self.text_subnetwork.output_text_dim

        self.final_merge_network = nn.Sequential(
            nn.ReLU(),
            nn.Linear(tab_dim + text_dim, self.num_classes),
        )

        # === Loss function ===
        weights = config.get("class_weights")
        if weights and len(weights) == self.num_classes:
            self.loss_op = nn.CrossEntropyLoss(weight=torch.tensor(weights))
        else:
            self.loss_op = nn.CrossEntropyLoss()

        self.save_hyperparameters()
```


### Define the Forward Pass and Computational Graph

```python
    def _forward_impl(self, batch, tab_data) -> torch.Tensor:
        tab_data = tab_data.float()
        text_out = self.text_subnetwork(batch)  # keep this as is
        tab_out = self.tab_subnetwork(tab_data)
        combined = torch.cat([text_out, tab_out], dim=1)
        return self.final_merge_network(combined)
```


```python
    def forward(self, batch: Dict[str, torch.Tensor]) -> torch.Tensor:
        tab_data = self.tab_subnetwork.combine_tab_data(batch) if self.tab_subnetwork else None
        return self._forward_impl(batch, tab_data)
```

- [[Pytorch Lightning 1 Module]]

### Configure Optimizer

```python
    def configure_optimizers(self):
        no_decay = ["bias", "LayerNorm.weight"]
        params = [
            {
                "params": [p for n, p in self.named_parameters() if not any(nd in n for nd in no_decay)],
                "weight_decay": self.weight_decay,
            },
            {
                "params": [p for n, p in self.named_parameters() if any(nd in n for nd in no_decay)],
                "weight_decay": 0.0,
            },
        ]
        optimizer = torch.optim.AdamW(params, lr=self.lr, eps=self.adam_epsilon)

        scheduler = (
            get_linear_schedule_with_warmup(optimizer, self.warmup_steps, self.trainer.estimated_stepping_batches)
            if self.run_scheduler
            else get_constant_schedule_with_warmup(optimizer, num_warmup_steps=self.warmup_steps)
        )
        return {"optimizer": optimizer, "lr_scheduler": {"scheduler": scheduler, "interval": "step"}}
```

- [[Pytorch Lightning 1 Module#Configure Optimizers and Learning Rate Scheduler]]


### Training Testing and Validation Runs
#### One Epoch Run

- Run one epoch by calling the forward pass and then pass through softmax

```python
    def run_epoch(self, batch, stage):
        labels = batch.get(self.label_name) if stage != "pred" else None

        if labels is not None and not isinstance(labels, torch.Tensor):
            labels = torch.tensor(labels, device=self.device)
            
        tab_data = self.tab_subnetwork.combine_tab_data(batch) if self.tab_subnetwork else None

        logits = self._forward_impl(batch, tab_data)
        loss = self.loss_op(logits, labels) if stage != "pred" else None

        preds = torch.softmax(logits, dim=1)
        preds = preds[:, 1] if self.is_binary else preds
        return loss, preds, labels
```

#### Training Step

- Run one epoch of batch and save the result loss in `train_loss`

```python
    def training_step(self, batch, batch_idx):
        loss, _, _ = self.run_epoch(batch, "train")
        self.log("train_loss", loss, sync_dist=True, prog_bar=True)
        return {"loss": loss}
```

- [[Pytorch Lightning 1 Module#Basic Setting]]

#### Validation Step

- Run one epoch of batch and save result loss in `val_loss`
- Offload from GPU to CPU for evaluation

```python
    def on_validation_epoch_start(self):
        self.pred_lst.clear()
        self.label_lst.clear()

    def validation_step(self, batch, batch_idx):
        loss, preds, labels = self.run_epoch(batch, "val")
        self.log("val_loss", loss, sync_dist=True, prog_bar=True)
        self.pred_lst.extend(preds.detach().cpu().tolist())
        self.label_lst.extend(labels.detach().cpu().tolist())

    def on_validation_epoch_end(self):
        preds = torch.tensor(sum(all_gather(self.pred_lst), []))
        labels = torch.tensor(sum(all_gather(self.label_lst), []))
        metrics = compute_metrics(preds, labels, self.metric_choices, self.task, self.num_classes, "val")
        self.log_dict(metrics, prog_bar=True)
```

- [[Pytorch Lightning 1 Module#Basic Setting]]
- [[Pytorch Lightning 1 Module#Validation]]

#### Test Step

- Remove label field in the module as the testing do not have label
- Run one epoch of batch and save result loss in `test_loss`
- Offload from GPU to CPU for evaluation

```python
    def test_step(self, batch, batch_idx):
        mode = "test" if self.label_name in batch else "pred"
        self.test_has_label = mode == "test"

        loss, preds, labels = self.run_epoch(batch, mode)
        self.pred_lst.extend(preds.detach().cpu().tolist())
        if labels is not None:
            self.label_lst.extend(labels.detach().cpu().tolist())

        self.log("test_loss", loss, sync_dist=True, prog_bar=True)
        if self.id_name:
            self.id_lst.extend(batch[self.id_name])

    def on_test_epoch_start(self):
        self.id_lst.clear()
        self.pred_lst.clear()
        self.label_lst.clear()
        timestamp = datetime.now().strftime("%Y-%m-%d-%H-%M-%S")
        self.test_output_folder = Path(self.model_path) / f"{self.model_class}-{timestamp}"
        if self.trainer.is_global_zero:
            self.test_output_folder.mkdir(parents=True, exist_ok=True)

    def on_test_epoch_end(self):
        import pandas as pd

        results = {"prob": sum(all_gather(self.pred_lst), [])}
        if self.test_has_label:
            results["label"] = sum(all_gather(self.label_lst), [])
        if self.id_name:
            results[self.id_name] = sum(all_gather(self.id_lst), [])

        if self.global_rank == 0:
            df = pd.DataFrame(results)
            test_file = self.test_output_folder / f"test_result_{get_rank()}.tsv"
            df.to_csv(test_file, sep="\t", index=False)
            print(f"[Rank {get_rank()}] Saved test results to {test_file}")
```

- [[Pytorch Lightning 1 Module#Basic Setting]]

#### Prediction

```python
    def predict_step(self, batch, batch_idx, dataloader_idx=0):
        mode = "test" if self.label_name in batch else "pred"
        _, preds, labels = self.run_epoch(batch, mode)
        return (preds, labels) if mode == "test" else preds
```

- [[Pytorch Lightning 1 Module#Basic Setting]]

### Hooks

#### Hook at start of evaluation of Validation

```python
    def on_validation_epoch_start(self):
        self.pred_lst.clear()
        self.label_lst.clear()
```

- [[Pytorch Lightning 2 Module Hooks]]

#### Hook at end of evaluation on Validation

- gather all prediction from all ranks
- compute the metrics
- save metrics in `log_metric_dict`

```python
    def on_validation_epoch_end(self):
        preds = torch.tensor(sum(all_gather(self.pred_lst), []))
        labels = torch.tensor(sum(all_gather(self.label_lst), []))
        metrics = compute_metrics(preds, labels, self.metric_choices, self.task, self.num_classes, "val")
        self.log_dict(metrics, prog_bar=True)
```

- [[Pytorch Lightning 2 Module Hooks]]

#### Hook at the start of evaluation on Test

- create directory that will save the output of prediction results

```python
    def on_test_epoch_start(self):
        self.id_lst.clear()
        self.pred_lst.clear()
        self.label_lst.clear()
        timestamp = datetime.now().strftime("%Y-%m-%d-%H-%M-%S")
        self.test_output_folder = Path(self.model_path) / f"{self.model_class}-{timestamp}"
        if self.trainer.is_global_zero:
            self.test_output_folder.mkdir(parents=True, exist_ok=True)
```

- [[Pytorch Lightning 2 Module Hooks]]

#### Hook at the end of evaluation on Test

- Gather prediction result as well as ids from all processes 
- Compute the metrics with gathered predictions and labels
- Save prediction result into disk


```python
    def on_test_epoch_end(self):
        import pandas as pd

        results = {"prob": sum(all_gather(self.pred_lst), [])}
        if self.test_has_label:
            results["label"] = sum(all_gather(self.label_lst), [])
        if self.id_name:
            results[self.id_name] = sum(all_gather(self.id_lst), [])

        if self.global_rank == 0:
            df = pd.DataFrame(results)
            test_file = self.test_output_folder / f"test_result_{get_rank()}.tsv"
            df.to_csv(test_file, sep="\t", index=False)
            print(f"[Rank {get_rank()}] Saved test results to {test_file}")
```

- [[Pytorch Lightning 2 Module Hooks]]







-----------
##  Recommended Notes


- [[AtoZ BSM Model Training Script]]
- [[AtoZ BSM MODS script]]