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
>Define a BERT base model `TextBertBase` 
>- take input from a batch
>- support multi-GPU training
>- support output to *ONNX* and *Torchscript*

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
from datetime import datetime
import logging
from tqdm import tqdm, trange
from typing import Union, List, Tuple, Optional, Set, Dict

import numpy as np
import pandas as pd
import matplotlib.pyplot as plt
```

```python
import torch 
import torch.optim as optim
from torch import nn
from torch.utils.data import Dataset, IterableDataset, DataLoader

from torch.optim import AdamW
```

```python
from transformers import (
                          AutoConfig,
                          AutoModel,
                          AutoModelForSequenceClassification,
                          AutoTokenizer,
                          get_linear_schedule_with_warmup,
                          get_polynomial_decay_schedule_with_warmup,
                          get_constant_schedule_with_warmup,
                          get_cosine_schedule_with_warmup
                         )
```


```python
import lightning.pytorch as pl
from lightning.pytorch.callbacks.early_stopping import EarlyStopping
from lightning.pytorch.callbacks import ModelCheckpoint, TQDMProgressBar
from lightning.pytorch.loggers import TensorBoardLogger
from lightning.pytorch.accelerators import find_usable_cuda_devices
from lightning.pytorch.utilities import rank_zero_only
```



```python
from .dist_utils import all_gather,gather
from .pl_model_plots import compute_metrics
```


```python
class TextBertBase(pl.LightningModule):
    def __init__(self, 
                 config: Dict[str, Union[int, float, str, bool, List[str], torch.FloatTensor]]
                ):
        
        super(TextBertBase, self).__init__()
        
        self.config = config
        self.model_class = 'bert_base'
        
        # Optional field to store ID field name
        self.id_name = self.config.get('id_name', None)

        # Required field: tokenized input IDs and attention mask keys
        # Due to Processor, the field name has `_processed` suffix
        if 'text_name' in self.config:
            text_field = self.config['text_name']
            self.text_name = text_field + '_processed_input_ids'
            self.text_attention_mask = text_field + '_processed_attention_mask'
        else:
            raise ValueError("Config file must contain 'text_name' field")

        # Required field: label name
        self.label_name = self.config.get('label_name')
        if not self.label_name:
            raise ValueError("Config file must contain 'label_name' field")

        # Load the model/tokenizer choice
        bert_choice = self.config.get('tokenizer', 'bert-base-cased')
        
        # Default task setup (binary classification if unspecified)
        self.is_binary = self.config.get('is_binary', True)
        if self.is_binary:
            self.task = 'binary'
            self.num_classes = 2
        else:
            self.task = 'multiclass'
            self.num_classes = self.config.get('num_classes', 2)
        
        # Metric and optimization config
        self.metric_choices = self.config.get('metric_choices', ['accuracy', 'f1_score'])
        self.weight_decay = self.config.get('weight_decay', 0)
        self.warmup_steps = self.config.get('warmup_steps', 0)
        self.adam_epsilon = self.config.get('adam_epsilon', 1e-8)
        self.lr = self.config.get('lr', 2e-5)
        self.run_scheduler = self.config.get('run_scheduler', True)
        self.reinit_pooler = self.config.get('reinit_pooler', False)
        self.reinit_layers = self.config.get('reinit_layers', 0)

        # Tracking variables for inference
        self.model_path = self.config['model_path']  # For checkpointing or saving
        self.id_lst = [] # For test-time tracking
        self.pred_lst = []
        self.label_lst = []
        self.test_output_folder = None
        self.test_has_label = False

        
        # Load pretrained BERT model
        self.bert = AutoModel.from_pretrained(bert_choice, output_attentions=False)
        
        
        # Optionally reinitialize the pooler and some encoder layers
        if self.reinit_pooler:
            encoder_temp = self.bert
            encoder_temp.pooler.dense.weight.data.normal_(
                mean=0.0, std=encoder_temp.config.initializer_range
            )
            encoder_temp.pooler.dense.bias.data.zero_()
            for p in encoder_temp.pooler.parameters():
                p.requires_grad = True
            if self.reinit_layers > 0:
                assert self.reinit_pooler
                bertlayernorm = torch.nn.LayerNorm
                for layer in encoder_temp.encoder.layer[-self.reinit_layers:]:
                    for module in layer.modules():
                        if isinstance(module, (nn.Linear, nn.Embedding)):
                            module.weight.data.normal_(
                                mean=0.0, std=encoder_temp.config.initializer_range
                            )
                        elif isinstance(module, bertlayernorm):
                            module.bias.data.zero_()
                            module.weight.data.fill_(1.0)
                        if isinstance(module, nn.Linear) and module.bias is not None:
                            module.bias.data.zero_()

        
        # --- HEAD LAYER ---    
        # Dimension of BERT output (usually 768 for base models)
        self.output_bert_dim = self.bert.config.hidden_size
        
        # Output dimension after head layer (can be shared with other modalities in multimodal models)
        self.output_text_dim = self.config['hidden_common_dim']
        
        # Final head: Dropout + Linear
        self.head_layer = nn.Sequential(
            nn.Dropout(0.1),
            nn.Linear(self.output_bert_dim, self.output_text_dim)
        )

    def forward(self, batch):
        """
        Forward pass for classification.
        batch: Dict with input_ids and attention_mask of shape [B, C, T]
        - B: Batch size
        - C: Maximum Chunk size
        - T: Maximum Token Length
        """
        input_ids = batch[self.text_name]  # shape: [B, C, T] 
        attention_mask = batch[self.text_attention_mask]  # shape: [B, C, T]

        # Reshape to feed BERT as a single batch: [B*C, T]
        B, C, T = input_ids.shape
        input_ids = input_ids.view(B * C, T)
        attention_mask = attention_mask.view(B * C, T)

        # Skip sequences that are completely padded (i.e., empty chunks)
        valid_mask = attention_mask.sum(dim=1) > 0
        if not valid_mask.any():
            raise ValueError("All input chunks in batch are empty!")

        outputs = self.bert(input_ids=input_ids, attention_mask=attention_mask)
        hidden_repr_cls = outputs.pooler_output  # shape: [B * C, H]

        # Reshape back to original batch: [B, C, H]
        hidden_repr_cls = hidden_repr_cls.view(B, C, -1)
        
        # Mean pooling over C chunks → [B, H]
        pooled = hidden_repr_cls.mean(dim=1)

        # Apply final head layer to get logits or embeddings
        logits = self.head_layer(pooled)
        return logits

    def configure_optimizers(self):
        optimizer = AdamW(self.parameters(),
                                      lr=self.lr,
                                      eps=self.adam_epsilon)
        return optimizer
```

### Initialization

#### Optional Reinitialize

```python
        # Optionally reinitialize the pooler and some encoder layers
        if self.reinit_pooler:
            encoder_temp = self.bert
            encoder_temp.pooler.dense.weight.data.normal_(
                mean=0.0, std=encoder_temp.config.initializer_range
            )
            encoder_temp.pooler.dense.bias.data.zero_()
            for p in encoder_temp.pooler.parameters():
                p.requires_grad = True
            if self.reinit_layers > 0:
                assert self.reinit_pooler
                bertlayernorm = torch.nn.LayerNorm
                for layer in encoder_temp.encoder.layer[-self.reinit_layers:]:
                    for module in layer.modules():
                        if isinstance(module, (nn.Linear, nn.Embedding)):
                            module.weight.data.normal_(
                                mean=0.0, std=encoder_temp.config.initializer_range
                            )
                        elif isinstance(module, bertlayernorm):
                            module.bias.data.zero_()
                            module.weight.data.fill_(1.0)
                        if isinstance(module, nn.Linear) and module.bias is not None:
                            module.bias.data.zero_()
```


### Batch Example

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

### Define the Forward Pass and Computational Graph

```python
    def forward(self, batch):
        """
        Forward pass for classification.
        batch: Dict with input_ids and attention_mask of shape [B, C, T]
        - B: Batch size
        - C: Maximum Chunk size
        - T: Maximum Token Length
        """
        input_ids = batch[self.text_name]  # shape: [B, C, T] 
        attention_mask = batch[self.text_attention_mask]  # shape: [B, C, T]

        # Reshape to feed BERT as a single batch: [B*C, T]
        B, C, T = input_ids.shape
        input_ids = input_ids.view(B * C, T)
        attention_mask = attention_mask.view(B * C, T)

        # Skip sequences that are completely padded (i.e., empty chunks)
        valid_mask = attention_mask.sum(dim=1) > 0
        if not valid_mask.any():
            raise ValueError("All input chunks in batch are empty!")

        outputs = self.bert(input_ids=input_ids, attention_mask=attention_mask)
        hidden_repr_cls = outputs.pooler_output  # shape: [B * C, H]

        # Reshape back to original batch: [B, C, H]
        hidden_repr_cls = hidden_repr_cls.view(B, C, -1)
        
        # Mean pooling over C chunks → [B, H]
        pooled = hidden_repr_cls.mean(dim=1)

        # Apply final head layer to get logits or embeddings
        logits = self.head_layer(pooled)
        return logits
```

- The input contains one batch of records, 
	- each containing **multiple chunks**
		- Each chunk has its own tokenized input ids, and attention mask 

- Compute BERT embedding for each record and each chunk
- **Mean Pooling** the BERT embedding within each chunk
- **Skip** sequences that are *completely padded* (i.e., empty chunks) 
- Apply MLP with dropout at the output to transform output as new embedding for each record


- [[Pytorch Lightning 1 Module]]
- [[Pytorch Lightning 1 Module#Configure Optimizers and Learning Rate Scheduler]]

### Test

```python
import unittest
```


```python
class TestTextBertBase(unittest.TestCase):
    def setUp(self):
        self.config = {
            'text_name': 'dialogue',
            'label_name': 'reversal_flag',
            'hidden_common_dim': 128,
            'model_path': './checkpoints',
            'tokenizer': 'bert-base-uncased',
            'is_binary': True,
            'num_classes': 2
        }

        # Create dummy input data: B=4, C=2, T=16
        self.batch = {
            'dialogue_processed_input_ids': torch.randint(0, 1000, (4, 2, 16)),
            'dialogue_processed_attention_mask': torch.ones(4, 2, 16, dtype=torch.long),
            'reversal_flag': torch.tensor([0, 1, 0, 1])  # Needed for full run with labels
        }

        self.model = TextBertBase(self.config)

    def test_forward_shape(self):
        """Test output shape of forward pass"""
        output = self.model(self.batch)  # Shape: [B, D]
        self.assertEqual(output.shape, (4, self.config['hidden_common_dim']))

    def test_no_empty_chunks(self):
        """Ensure ValueError is raised if all attention is zero (invalid input)"""
        self.batch['dialogue_processed_attention_mask'].zero_()
        with self.assertRaises(ValueError):
            self.model(self.batch)

```




-----------
##  Recommended Notes


- [[AtoZ BSM Model Training Script]]
- [[AtoZ BSM MODS script]]