---
tags:
  - code
  - code_snippet
  - pytorch/lightning
keywords:
  - pytorch
topics: 
language: python
date of note: 2025-04-10
---

## Code Snippet Summary

>[!important]
>Develop a Tabular Autoencoder that takes multiple tabular fields in a batch as input
>


## Code

### Example of a Batch

```json
{
'reversal_flag':                //list of size = B, each an integer
 'dialogue':                    //list of size = B, each a string dialogue
 'deliverable_flag':            //list of size = B, each an integer
 'net_conc_amt':                //list of size = B, each float
 'bears_risky_prob':            //list of size = B, each float
 'ttm_conc_amt':                //list of size = B, each float
 'dnr_pmml_score_calibrated':   //list of size = B, each float
 'notr_pmml_score_calibrated':  //list of size = B, each float
 'concsi':                      //list of size = B, each float
 'bears_normal_prob':           //list of size = B, each float
 'undeliverable_flag':          //list of size = B, each float
 'bears_abuse_prob':            //list of size = B, each float
 'ttm_conc_count':              //list of size = B, each float
 'dialogue_processed_input_ids': //torch tensor [B x C x L]
 'dialogue_processed_attention_mask': //torch tensor [B x C x L]
```

- [[Processors Tokenizer]]
### Configuration Dictionary

```json
{'text_name': 'dialogue',
 'label_name': 'reversal_flag',
 'full_field_list': ['reversal_flag',
  'dialogue',
  'deliverable_flag',
  'net_conc_amt',
  'bears_risky_prob',
  'ttm_conc_amt',
  'dnr_pmml_score_calibrated',
  'notr_pmml_score_calibrated',
  'concsi',
  'bears_normal_prob',
  'undeliverable_flag',
  'bears_abuse_prob',
  'ttm_conc_count'],
 'cat_field_list': ['dialogue'],
 'tab_field_list': ['reversal_flag', 'deliverable_flag', 'net_conc_amt',
  'bears_risky_prob',
  'ttm_conc_amt',
  'dnr_pmml_score_calibrated',
  'notr_pmml_score_calibrated',
  'concsi',
  'bears_normal_prob',
  'undeliverable_flag',
  'bears_abuse_prob',
  'ttm_conc_count'],
 'need_language_detect': False,
 'hidden_common_dim': 100,
 'model_path': '',
 'tokenizer': 'bert-base-multilingual-cased'
 }
```


### Tabular Model

```python
import torch
import torch.nn as nn
import torch.optim as optim
import lightning.pytorch as pl
from typing import Dict, Union, List
```

```python
class TabAE(pl.LightningModule):
    def __init__(self, config):
        super().__init__()
        self.config = config

        self.tab_field_list = config.get('tab_field_list')
        self.label_name = config.get('label_name')
        self.output_tab_dim = config.get('hidden_common_dim')

        if not self.tab_field_list:
            raise ValueError("Config must contain 'tab_field_list'")
        if not self.label_name:
            raise ValueError("Config must contain 'label_name'")

        self.is_binary = config.get('is_binary', True)
        self.num_classes = 2 if self.is_binary else config.get('num_classes', 3)
        self.input_tab_dim = len(self.tab_field_list)

        # Encoder
        self.embedding_layer = nn.Sequential(
            nn.BatchNorm1d(self.input_tab_dim),
            nn.Linear(self.input_tab_dim, self.output_tab_dim),
            nn.ReLU()
        )

        # Classifier head
        self.classifier = nn.Linear(self.output_tab_dim, 1 if self.is_binary else self.num_classes)

        self.loss_op = None  # Set via add_loss_op
        self.save_hyperparameters("config")

    def combine_tab_data(self, batch: Dict[str, Union[torch.Tensor, List]]) -> torch.Tensor:
        """
        Combines tabular fields into a single tensor of shape [B, input_tab_dim]
        """
        features = []
        for field in self.tab_field_list:
            val = batch[field]
            if isinstance(val, list):
                val = torch.tensor(val, dtype=torch.float32, device=self.device)
            elif isinstance(val, torch.Tensor):
                val = val.float()
            else:
                raise TypeError(f"Unsupported type for field {field}: {type(val)}")
            if val.dim() == 1:
                val = val.unsqueeze(1)
            features.append(val)
        return torch.cat(features, dim=1)

    def forward(self, inputs: Union[torch.Tensor, Dict[str, torch.Tensor]]) -> torch.Tensor:
        """
        Returns embedding vector from tabular input.
        """
        if isinstance(inputs, dict):
            inputs = self.combine_tab_data(inputs)
        return self.embedding_layer(inputs)

    def forward_classify(self, inputs: Union[torch.Tensor, Dict[str, torch.Tensor]]) -> torch.Tensor:
        """
        Returns classification logits.
        """
        emb = self.forward(inputs)
        return self.classifier(emb)

    def add_loss_op(self, loss_op=None):
        """
        Configures loss function.
        """
        if loss_op:
            self.loss_op = loss_op
        elif self.is_binary:
            pos_weight = torch.tensor(self.config.get('pos_weight', 1.0), device=self.device)
            self.loss_op = nn.BCEWithLogitsLoss(pos_weight=pos_weight)
        else:
            self.loss_op = nn.CrossEntropyLoss()

    def run_epoch(self, batch, stage: str):
        x = self.combine_tab_data(batch)
        logits = self.classifier(self.embedding_layer(x))

        labels = batch[self.label_name]
        if not isinstance(labels, torch.Tensor):
            labels = torch.tensor(labels)
        labels = labels.float() if self.is_binary else labels.long()

        if self.is_binary:
            logits = logits.squeeze(-1)

        loss = self.loss_op(logits, labels) if stage != 'pred' else None
        preds = torch.sigmoid(logits) if self.is_binary else torch.softmax(logits, dim=1)
        return loss, preds, labels

    def training_step(self, batch, batch_idx):
        loss, _, _ = self.run_epoch(batch, 'train')
        self.log("train_loss", loss, prog_bar=True, sync_dist=True)
        return loss

    def validation_step(self, batch, batch_idx):
        loss, _, _ = self.run_epoch(batch, 'val')
        self.log("val_loss", loss, prog_bar=True, sync_dist=True)
        return loss
```

### Test

```python
import unittest
from lightning.pytorch import seed_everything
```

```python
class TestTabAE(unittest.TestCase):

    def setUp(self):
        seed_everything(42)
        self.config = {
            'tab_field_list': ['feat1', 'feat2', 'feat3'],
            'label_name': 'target',
            'hidden_common_dim': 8,
            'is_binary': True,
            'optimizer_type': 'SGD',
            'lr': 0.01,
            'momentum': 0.9,
            'pos_weight': 1.0
        }

        self.model = TabAE(self.config)
        self.model.add_loss_op()
        self.model.eval()

        # Dummy batch of size 4
        self.batch = {
            'feat1': torch.tensor([0.1, 0.2, 0.3, 0.4]),
            'feat2': torch.tensor([1.0, 1.5, 1.7, 1.9]),
            'feat3': torch.tensor([0.5, 0.7, 0.2, 0.9]),
            'target': torch.tensor([0.0, 1.0, 0.0, 1.0])
        }

    def test_model_init(self):
        self.assertIsInstance(self.model.embedding_layer, nn.Sequential)
        self.assertIsInstance(self.model.classifier, nn.Linear)
        self.assertEqual(self.model.output_tab_dim, 8)
        self.assertEqual(self.model.num_classes, 2)

    def test_embedding_forward_pass(self):
        with torch.no_grad():
            embedding = self.model(self.batch)
        self.assertEqual(embedding.shape, (4, 8))  # [B, D]

    def test_classifier_forward_pass(self):
        with torch.no_grad():
            logits = self.model.forward_classify(self.batch)
        self.assertEqual(logits.shape, (4, 1))  # [B] for binary (squeezed)

    def test_run_epoch_loss(self):
        loss, preds, labels = self.model.run_epoch(self.batch, stage='train')
        self.assertIsNotNone(loss)
        self.assertEqual(preds.shape, labels.shape)
        self.assertTrue(torch.all((preds >= 0) & (preds <= 1)))  # sigmoid output range

    def test_training_step(self):
        loss = self.model.training_step(self.batch, batch_idx=0)
        self.assertIsInstance(loss, torch.Tensor)
        self.assertGreaterEqual(loss.item(), 0)
```

#### Run Test

```python
unittest.main(argv=[''], exit=False, defaultTest='TestTabAE')
```

or

```python
if __name__ == '__main__':
    unittest.main()
```


-----------
##  Recommended Notes

