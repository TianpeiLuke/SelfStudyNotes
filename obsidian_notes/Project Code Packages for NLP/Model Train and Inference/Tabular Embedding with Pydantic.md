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
>- Add pydantic for config
>

- [[Tabular Autoencoder]]

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

- [[Processor Tokenizer]]

### Pydantic Config

```python
from typing import Dict, Union, List
from pydantic import BaseModel, Field
```

```python
class TabularEmbeddingConfig(BaseModel):
    tab_field_list: List[str]
    hidden_common_dim: int
    input_tab_dim: int = Field(init=False)  # Calculated dynamically
    is_binary: bool = True  # Added for clarity (though not used)
    num_classes: int = 2  # Added for clarity (though not used)


    @property
    def output_tab_dim(self) -> int:
        return self.hidden_common_dim


    @validator("tab_field_list")
    def validate_tab_field_list(cls, v):
        if not v:
            raise ValueError("tab_field_list must not be empty")
        return v


    @validator("input_tab_dim", always=True)
    def set_input_tab_dim(cls, v, values):
        tab_field_list = values.get("tab_field_list")
        if tab_field_list:
            return len(tab_field_list)
        return v
```

#### Pydantic V2

```python
from pydantic import BaseModel, Field, field_validator, ValidationInfo
from typing import List
```

```python
class TabularEmbeddingConfig(BaseModel):
    tab_field_list: List[str]
    hidden_common_dim: int
    input_tab_dim: int = Field(init=False)  # Calculated dynamically
    is_binary: bool = True  # Added for clarity (though not used)
    num_classes: int = 2  # Added for clarity (though not used)

    @property
    def output_tab_dim(self) -> int:
        return self.hidden_common_dim

    @field_validator("tab_field_list")
    @classmethod
    def validate_tab_field_list(cls, v: List[str], info: ValidationInfo) -> List[str]:
        if not v:
            raise ValueError("tab_field_list must not be empty")
        return v

    @field_validator("input_tab_dim", always=True)
    @classmethod
    def set_input_tab_dim(cls, v: int, info: ValidationInfo) -> int:
        tab_field_list = info.data.get("tab_field_list")
        if tab_field_list:
            return len(tab_field_list)
        return v
```


### Tabular Model

```python
import torch
import torch.nn as nn
import torch.optim as optim

import lightning.pytorch as pl  # Or torch.nn.Module if not training independently
from typing import Dict, Union, List
import lightning.pytorch as pl
```


```python
class TabularEmbeddingModule(pl.LightningModule): 
    def __init__(self, config: Union[Dict, TabularEmbeddingConfig]):
        super().__init__()
        if isinstance(config, dict):
            config = TabularEmbeddingConfig(**config)
        self.config = config

        self.embedding_layer = nn.Sequential(
            nn.BatchNorm1d(self.config.input_tab_dim),
            nn.Linear(self.config.input_tab_dim, self.config.hidden_common_dim),
            nn.ReLU()
        )
        self.output_tab_dim = self.config.hidden_common_dim

        if isinstance(config, dict):
            self.save_hyperparameters(config)
        else:
            self.save_hyperparameters(config.dict())

    def combine_tab_data(self, batch: Dict[str, Union[torch.Tensor, List]]) -> torch.Tensor:
        """
        Combines tabular fields into a single tensor of shape [B, input_tab_dim]
        """
        features = []
        for field in self.config.tab_field_list:
            val = batch[field]
            if isinstance(val, list):
                val = torch.tensor(val, dtype=torch.float32, device=next(self.parameters()).device)
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
```


```python
class TabAE(TabularEmbeddingModule, pl.LightningModule):  # Inherit for combine_tab_data and config
    def __init__(self, config: Union[Dict, TabularEmbeddingConfig]):
        super().__init__(config)
        self.save_hyperparameters(config)  # Still useful in Lightning
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

