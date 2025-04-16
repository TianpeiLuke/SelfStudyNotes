---
tags:
  - project
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
>- Add pydantic to verify config

- [[BERT Base Emedding Model for BSM]]


## Code

```python
import os  # Added os
from datetime import datetime  # Added datetime
import pandas as pd  # Added pandas
```

```python
import torch
import torch.nn as nn
import lightning.pytorch as pl

from transformers import (
    AutoModel,
    AutoConfig,
    AutoTokenizer,  # Added AutoTokenizer
    get_linear_schedule_with_warmup,
    get_constant_schedule_with_warmup,
)
from torch.optim import AdamW  # Added AdamW
from lightning.pytorch.callbacks.early_stopping import EarlyStopping  # Added EarlyStopping
from lightning.pytorch.callbacks import ModelCheckpoint  # Added ModelCheckpoint
```

```python
from .dist_utils import all_gather  # Added all_gather
from .pl_model_plots import compute_metrics  # Added compute_metrics
```

### Config via Pydantic

```python
from typing import Dict, Union, List, Optional
from pydantic import BaseModel, Field, validator
```

```python
class TextBertBaseConfig(BaseModel):
    text_name: str
    label_name: Optional[str] = None
    tokenizer: str = "bert-base-cased"
    is_binary: bool = True
    num_classes: int = 2
    metric_choices: List[str] = Field(default_factory=lambda: ["accuracy", "f1_score"])
    weight_decay: float = 0.0
    warmup_steps: int = 0
    adam_epsilon: float = 1e-8
    lr: float = 2e-5
    run_scheduler: bool = True
    reinit_pooler: bool = False
    reinit_layers: int = 0
    model_path: Optional[str] = None
    hidden_common_dim: int
    text_input_ids_key: str = "input_ids"
    text_attention_mask_key: str = "attention_mask"

    @validator("num_classes", always=True)
    def validate_num_classes(cls, value, values):
        if values.get("is_binary") and value != 2:
            raise ValueError("For binary classification, num_classes must be 2")
        if not values.get("is_binary") and value < 2:
            raise ValueError("For multiclass classification, num_classes must be >= 2")
        return value
```

- [[Data Class with Pydantic]]
- [[Simple Data Class from Pydantic]]

#### Pydantic v2

```python
from pydantic import BaseModel, Field, field_validator, ValidationInfo
from typing import Dict, Union, List, Optional

class TextBertBaseConfig(BaseModel):
    text_name: str
    label_name: Optional[str] = None
    tokenizer: str = "bert-base-cased"
    is_binary: bool = True
    num_classes: int = 2
    metric_choices: List[str] = Field(default_factory=lambda: ["accuracy", "f1_score"])
    weight_decay: float = 0.0
    warmup_steps: int = 0
    adam_epsilon: float = 1e-8
    lr: float = 2e-5
    run_scheduler: bool = True
    reinit_pooler: bool = False
    reinit_layers: int = 0
    model_path: Optional[str] = None
    hidden_common_dim: int
    text_input_ids_key: str = "input_ids"
    text_attention_mask_key: str = "attention_mask"

    @field_validator("num_classes")  # Changed to field_validator
    @classmethod
    def validate_num_classes(cls, value: int, info: ValidationInfo) -> int:  # Added type hints
        if info.data.get("is_binary") and value != 2:
            raise ValueError("For binary classification, num_classes must be 2")
        if not info.data.get("is_binary") and value < 2:
            raise ValueError("For multiclass classification, num_classes must be >= 2")
        return value
```



### Base Embedding

```python
class TextBertBase(pl.LightningModule):  # Or nn.Module if not training independently
    def __init__(self, config: Union[Dict, TextBertBaseConfig]):
        super().__init__()
        if isinstance(config, dict):
            config = TextBertBaseConfig(**config)
        self.config = config
        self.text_input_ids_key = config.text_input_ids_key
        self.text_attention_mask_key = config.text_attention_mask_key
        self.text_name = config.text_name + "_processed_" + self.text_input_ids_key
        self.text_attention_mask = config.text_name + "_processed_" + self.text_attention_mask_key

        self.bert = AutoModel.from_pretrained(
            self.config.tokenizer, output_attentions=False
        )
        self._maybe_reinitialize()

        self.output_bert_dim = self.bert.config.hidden_size
        self.output_text_dim = self.config.hidden_common_dim

        self.head_layer = nn.Sequential(
            nn.Dropout(0.1),
            nn.Linear(self.output_bert_dim, self.output_text_dim),
        )

        if isinstance(config, dict):
            self.save_hyperparameters(config)  # If using pl.LightningModule
        else:
            self.save_hyperparameters(config.dict())

    def forward(self, batch: Dict[str, torch.Tensor]) -> torch.Tensor:
        input_ids = batch[self.text_name]
        attention_mask = batch[self.text_attention_mask]

        B, C, T = input_ids.shape
        input_ids = input_ids.view(B * C, T)
        attention_mask = attention_mask.view(B * C, T)

        valid_mask = attention_mask.sum(dim=1) > 0
        if not valid_mask.any():
            raise ValueError("All input chunks in batch are empty!")

        outputs = self.bert(input_ids=input_ids, attention_mask=attention_mask)
        pooled = outputs.pooler_output
        pooled = pooled.view(B, C, -1).mean(dim=1)

        logits = self.head_layer(pooled)
        return logits

    def _maybe_reinitialize(self):
        if not self.config.reinit_pooler:
            return
        encoder = self.bert
        encoder.pooler.dense.weight.data.normal_(
            mean=0.0, std=encoder.config.initializer_range
        )
        encoder.pooler.dense.bias.data.zero_()
        for p in encoder.pooler.parameters():
            p.requires_grad = True

        if self.config.reinit_layers > 0:
            for layer in encoder.encoder.layer[-self.config.reinit_layers :]:
                for module in layer.modules():
                    if isinstance(module, (nn.Linear, nn.Embedding)):
                        module.weight.data.normal_(
                            mean=0.0, std=encoder.config.initializer_range
                        )
                    elif isinstance(module, nn.LayerNorm):
                        module.bias.data.zero_()
                        module.weight.data.fill_(1.0)
                    if isinstance(module, nn.Linear) and module.bias is not None:
                        module.bias.data.zero_()
```





-----------
##  Recommended Notes


- [[AtoZ BSM Model Training Script]]
- [[AtoZ BSM MODS script]]