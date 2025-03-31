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


```python
class MultimodalBert(pl.LightningModule):
    def __init__(self, 
                 config: Dict[str, Union[int, float, str, bool, List[str], torch.FloatTensor]]
                ) -> None:
        super(MultimodalBert, self).__init__()
        
        self.config = config
        self.model_class = 'multimodal_bert'
        
        # Define Field names and Id names
        ...

		# text attention mask field
        ...
        
        # label field
        ...
        
        # tabular fields
        ...

		# if binary classification or not
        ... 
                
	    # evaluation metric choice
        ...
        
        # warm up
        ...
    
	    # weight decay
        ...
        
        # optimization parameters
        ...
            
        
        # tabular-field linear subnetwork to expand dimension in order to match the text field
        ...

        # text-field linear subnetwork to reduce dimension in order to match the meta field
        ...
        
        # Final subnetwork with Fully-Connected layer
        ...
    
	
	### Merge subnetwork
    def build_merge_subnetwork(self, 
                               input_merge_dim: int,
                               output_merge_dim: int
                              ):
        ...
        return final_common_network
         
    
	### Forward pass        
    def forward(self, input_ids, attention_mask, tab_data):
        ...
        return final_out
    
    
    def configure_optimizers(self):
        """Prepare optimizer and schedule (linear warmup and decay)
        See https://lightning.ai/docs/pytorch/stable/notebooks/lightning_examples/text-transformers.html
        """
        ...
        return [optimizer], [scheduler]
         
        
    def add_loss_op(self, loss_op=None):
        if loss_op:
            self.loss_op = loss_op
        
    
    def run_epoch(self, batch, stage):  
        ...
        
        return loss, preds, labels
    
    
    def training_step(self, batch, batch_idx):
        # training_step defines the train loop.
        ...
        output_dict = {'loss': loss}
        return output_dict

    
    def on_validation_epoch_start(self) -> None:
        ...

        
    def validation_step(self, batch, batch_idx):
        # training_step defines the train loop.
        ...
            
        self.pred_lst.extend(preds.tolist())
        self.label_lst.extend(labels.tolist())
        
        
    def on_validation_epoch_end(self):
        # collect all information from multiple processes when used DDP
        ...

        
    def on_test_epoch_start(self) -> None:
        # create directory and initialize the gather list
        
    
    def test_step(self, batch, batch_idx):
        # test step defines the test loop.
        # test step defines the test loop.
        try:
            labels = batch[self.label_name]
            mode = 'test'
            ...
            self.pred_lst.extend(preds.tolist())
            self.label_lst.extend(labels.tolist())
            self.test_has_label = True
        except KeyError:
            mode = 'pred'
            ...
            self.pred_lst.extend(preds.tolist())
            self.test_has_label = False
        
        self.log("test_loss", loss, sync_dist=True, prog_bar=True) 
        
        if self.id_name:
            ids = batch[self.id_name]
            self.id_lst.extend(ids)
    

    def on_test_epoch_end(self):
        # collect all information from multiple processes when used DDP
        # save the metric after gather all information from DDP
        final_pred_lst_gather = all_gather(self.pred_lst)
        ...
        
        final_preds_tensor = ...

        final_label_lst = []
        if self.test_has_label:
            
            final_labels_tensor = ...

        final_id_lst = []
        if self.id_name:
            # self.all_gather function cannot handle non-tensor object; implement our own all_gather function
            ...
                final_id_lst.extend(id_lists)

        if self.global_rank == 0:
            ...
            if self.id_name:
                ...
                
            if self.test_has_label:
                ...
            
            ### Save test result into disk
    
    
    def predict_step(self, batch, batch_idx, dataloader_idx=0):
        # training_step defines the train loop.
        ...
```

### Initialization

```python
    def __init__(self, 
                 config: Dict[str, Union[int, float, str, bool, List[str], torch.FloatTensor]]
                ) -> None:
        super(MultimodalBert, self).__init__()
        
        self.config = config
        self.model_class = 'multimodal_bert'
        
        if 'id_name' in self.config:
            self.id_name = self.config['id_name']
        else:
            self.id_name = None
            
        if 'text_name' in self.config:
            self.text_name = self.config['text_name'] + '_input_ids'
        else:
            raise ValueError('''Config file must contain 'text_name' field ''')

		# text attention mask field
        if 'text_name' in self.config:
            self.text_attention_mask = self.config['text_name'] + '_attention_mask'
        else:
            raise ValueError('''Config file must contain 'text_name' field ''')
        # label field
        if 'label_name' in self.config:
            self.label_name = self.config['label_name']
        else:
            raise ValueError('''Config file must contain 'label_name' field ''')
        # tabular fields
        if 'tab_field_list' in self.config:
            self.tab_field_list = self.config['tab_field_list']
        else:
            self.tab_field_list = None

		# if binary classification or not
        if 'is_binary' in self.config:
            self.is_binary = self.config['is_binary']
        else:
            self.is_binary = True #default binary      
            
        if self.is_binary:
            self.task = 'binary'     
            self.num_classes = 2
        else:
            self.task = 'multiclass'
            if 'num_classes' in self.config:
                self.num_classes = self.config['num_classes']
            else:
                self.num_classes = 2 
                
	    # metric choice
        if 'metric_choices' in self.config:
            self.metric_choices = self.config['metric_choices']
        else:
            self.metric_choices = ['accuracy', 'f1_score']
        
        # warm up
        if 'warmup_steps' in self.config:
            self.warmup_steps = self.config['warmup_steps']
        else:
            self.warmup_steps = 0
    
        if 'weight_decay' in self.config:
            self.weight_decay = self.config['weight_decay']
        else:
            self.weight_decay = 0
        
        # optimization parameters
        if 'adam_epsilon' in self.config:
            self.adam_epsilon = self.config['adam_epsilon']
        else:
            self.adam_epsilon = 1e-8
            
        if 'lr' in self.config:
            self.lr = self.config['lr']
        else:
            self.lr = 2e-5   
            
        if 'run_scheduler' in self.config:
            self.run_scheduler = self.config['run_scheduler']
        else:
            self.run_scheduler = True
            
        self.model_path = self.config['model_path']
        self.id_lst = []
        self.pred_lst = []
        self.label_lst = []
        self.test_output_folder = None
        self.test_has_label = False
        
        # tabular-field linear subnetwork to expand dimension in order to match the text field
        if self.tab_field_list:
            self.tab_subnetwork = TabAE(config)
            output_tab_dim = self.tab_subnetwork.output_tab_dim
        else:
            output_tab_dim = 0

        # text-field linear subnetwork to reduce dimension in order to match the meta field
        self.text_subnetwork = TextBertBase(config)
        output_text_dim = self.text_subnetwork.output_text_dim
        
        # Final subnetwork with Fully-Connected layer
        self.final_merge_network = self.build_merge_subnetwork(input_merge_dim = output_tab_dim + output_text_dim, 
                                                                output_merge_dim = self.config['num_classes'])
        
        if 'class_weights' in self.config:
            if len(self.config['class_weights']) == self.num_classes:
                class_weights = torch.tensor(self.config['class_weights'])
            else:
                class_weights = torch.ones(self.num_classes)
            self.loss_op = nn.CrossEntropyLoss(weight=class_weights)
        else:
            self.loss_op = nn.CrossEntropyLoss()
            
        self.save_hyperparameters()
```


### Concatenate Subnetwork

```python
    def build_merge_subnetwork(self, 
                               input_merge_dim: int,
                               output_merge_dim: int
                              ):
        final_common_network = nn.Sequential() 
        #final_common_network.add_module("dropout_final", 
        #                                     nn.Dropout(self.config['dropout_keep']))
        final_common_network.add_module("relu_layer_final",
                                        nn.ReLU()
                                        )
        final_common_network.add_module("linear_layer_final",
                                        nn.Linear(input_merge_dim, output_merge_dim))
        return final_common_network
```

### Define the Forward Pass and Computational Graph

```python
    def forward(self, input_ids, attention_mask, tab_data):
        tab_data = tab_data.float() 
        
        text_out = self.text_subnetwork(input_ids, attention_mask)
        tab_out = self.tab_subnetwork(tab_data)
        combine_out = torch.cat([text_out, tab_out], 1)
        final_out = self.final_merge_network(combine_out)
        return final_out
```

- [[Pytorch Lightning 1 Module]]

### Configure Optimizer

```python
    def configure_optimizers(self):
        """Prepare optimizer and schedule (linear warmup and decay)
        See https://lightning.ai/docs/pytorch/stable/notebooks/lightning_examples/text-transformers.html
        """
        no_decay = ["bias", "LayerNorm.weight"]
        optimizer_grouped_parameters = [
            {
                "params": [p for n, p in self.named_parameters() if not any(nd in n for nd in no_decay)],
                "weight_decay": self.weight_decay,
            },
            {
                "params": [p for n, p in self.named_parameters() if any(nd in n for nd in no_decay)],
                "weight_decay": 0.0,
            },
        ]
        
        optimizer = AdamW(optimizer_grouped_parameters,
                  lr = self.lr,  #2e-5, # args.learning_rate - default is 5e-5, our notebook had 2e-5
                  eps = self.adam_epsilon #1e-8 # args.adam_epsilon  - default is 1e-8.
                )    
        
        if self.run_scheduler:
            scheduler = get_linear_schedule_with_warmup(
                optimizer,
                num_warmup_steps = self.warmup_steps,
                num_training_steps = self.trainer.estimated_stepping_batches,
            )
        else:
            scheduler = get_constant_schedule_with_warmup(
                optimizer, num_warmup_steps = self.warmup_steps
            )        

        scheduler = {"scheduler": scheduler, "interval": "step", "frequency": 1}
        return [optimizer], [scheduler]
```

- [[Pytorch Lightning 1 Module#Configure Optimizers and Learning Rate Scheduler]]


### Training Testing and Validation Runs
#### One Epoch Run

- Run one epoch by calling the forward pass and then pass through softmax

```python
    def run_epoch(self, batch, stage):  
        text_ids = batch[self.text_name]   #torch.Size([batch_size, max_seq_len])
        text_attention_mask = batch[self.text_attention_mask] 
        
        if stage != 'pred':
            labels = batch[self.label_name]  #torch.Size([batch_size])
        else:
            labels = None
             
        tab_data = self.tab_subnetwork.combine_tab_data(batch)

        logits = self(text_ids, text_attention_mask, tab_data)
                
        if stage != 'pred':
            loss = self.loss_op(logits, labels)
        else:
            loss = None
            
        if self.is_binary:
            preds = torch.softmax(logits, dim=1)[:,1]
        else:
            preds = torch.softmax(logits, dim=1)
        
        return loss, preds, labels
```

#### Training Step

- Run one epoch of batch and save the result loss in `train_loss`

```python
    def training_step(self, batch, batch_idx):
        # training_step defines the train loop.
        loss, preds, labels = self.run_epoch(batch, 'train')  
        self.log("train_loss", loss, sync_dist=True, prog_bar=True) 
        output_dict = {'loss': loss}
        return output_dict
```

- [[Pytorch Lightning 1 Module#Basic Setting]]

#### Validation Step

- Run one epoch of batch and save result loss in `val_loss`
- Offload from GPU to CPU for evaluation

```python
    def validation_step(self, batch, batch_idx):
        # training_step defines the train loop.
        loss, preds, labels = self.run_epoch(batch, 'val')
        self.log("val_loss", loss, sync_dist=True, prog_bar=True) 
        
        preds = preds.detach().cpu().numpy()
        labels = labels.detach().cpu().numpy()
            
        self.pred_lst.extend(preds.tolist())
        self.label_lst.extend(labels.tolist())
```

- [[Pytorch Lightning 1 Module#Basic Setting]]
- [[Pytorch Lightning 1 Module#Validation]]

#### Test Step

- Remove label field in the module as the testing do not have label
- Run one epoch of batch and save result loss in `test_loss`
- Offload from GPU to CPU for evaluation

```python
    def test_step(self, batch, batch_idx):
        # test step defines the test loop.
        try:
            labels = batch[self.label_name]
            mode = 'test'
            loss, preds, labels = self.run_epoch(batch, mode)  
            preds = preds.detach().cpu().numpy()
            labels = labels.detach().cpu().numpy()
            self.pred_lst.extend(preds.tolist())
            self.label_lst.extend(labels.tolist())
            self.test_has_label = True
        except KeyError:
            mode = 'pred'
            loss, preds, labels = self.run_epoch(batch, mode)  
            preds = preds.detach().cpu().numpy()
            self.pred_lst.extend(preds.tolist())
            self.test_has_label = False
        
        self.log("test_loss", loss, sync_dist=True, prog_bar=True) 
        
        if self.id_name:
            ids = batch[self.id_name]
            self.id_lst.extend(ids)
```

- [[Pytorch Lightning 1 Module#Basic Setting]]

#### Prediction

```python
    def predict_step(self, batch, batch_idx, dataloader_idx=0):
        # training_step defines the train loop.
        try:
            labels = batch[self.label_name]
            mode = 'test'
        except KeyError:
            mode = 'pred'
            
        loss, preds, labels = self.run_epoch(batch, mode)  
        if mode == 'pred':
            return preds
        else:
            return preds, labels
```

- [[Pytorch Lightning 1 Module#Basic Setting]]

### Hooks

#### Hook at start of evaluation of Validation

```python
    def on_validation_epoch_start(self) -> None:
        self.id_lst = []
        self.pred_lst = []
        self.label_lst = []
```

- [[Pytorch Lightning 2 Module Hooks]]

#### Hook at end of evaluation on Validation

- gather all prediction from all ranks
- compute the metrics
- save metrics in `log_metric_dict`

```python
    def on_validation_epoch_end(self):
        # collect all information from multiple processes when used DDP
        final_pred_lst_gather = self.all_gather(self.pred_lst)
        final_pred_lst = []
        for preds_tensor in final_pred_lst_gather:
            if isinstance(preds_tensor, list):
                final_pred_lst.extend(preds_tensor[1].detach().cpu().numpy())

            else:
                final_pred_lst.extend(preds_tensor.detach().cpu().numpy())
        final_preds_tensor = torch.tensor(final_pred_lst)
        
        final_label_lst = []
        final_label_lst_gather = self.all_gather(self.label_lst)
        for preds_tensor in final_label_lst_gather:
            final_label_lst.extend(preds_tensor.detach().cpu().numpy())
        final_labels_tensor = torch.tensor(final_label_lst)
        
        log_metric_dict = compute_metrics(final_preds_tensor, 
                                          final_labels_tensor, 
                                          self.metric_choices, 
                                          self.task, 
                                          self.num_classes, 
                                          'val')
        self.log_dict(log_metric_dict, #sync_dist=True, 
                      prog_bar=True)
```

- [[Pytorch Lightning 2 Module Hooks]]

#### Hook at the start of evaluation on Test

- create directory that will save the output of prediction results

```python
    def on_test_epoch_start(self) -> None:
        self.id_lst = []
        self.pred_lst = []
        self.label_lst = []
        
        self.test_has_label = False
        timenow = datetime.now().strftime('%Y-%m-%d-%H-%M-%S')
        self.test_output_folder = os.path.join(self.model_path, self.model_class+'-'+timenow)
        
        if self.trainer.is_global_zero:
            if not os.path.exists(self.test_output_folder):
                os.makedirs(self.test_output_folder, exist_ok=True)
```

- [[Pytorch Lightning 2 Module Hooks]]

#### Hook at the end of evaluation on Test

- Gather prediction result as well as ids from all processes 
- Compute the metrics with gathered predictions and labels
- Save prediction result into disk


```python
    def on_test_epoch_end(self):
        # collect all information from multiple processes when used DDP
        
        final_pred_lst_gather = all_gather(self.pred_lst)
        final_pred_lst = []
        for preds_tensor in final_pred_lst_gather:
            final_pred_lst.extend(preds_tensor)
        
        #final_pred_lst_gather = self.all_gather_object(self.pred_lst)
        #final_pred_lst = [pred for preds in final_pred_lst_gather for pred in preds]
        
        #final_pred_lst = self.pred_lst
        #final_pred_lst = all_gather(self.pred_lst)
        final_preds_tensor = torch.tensor(final_pred_lst)

        final_label_lst = []
        if self.test_has_label:
            final_label_lst_gather = all_gather(self.label_lst)
            for preds_tensor in final_label_lst_gather:
                final_label_lst.extend(preds_tensor)
            
            #final_label_lst_gather = self.all_gather_object(self.label_lst)
            #final_label_lst = [label for labels in final_label_lst_gather for label in labels]
        
            #final_label_lst = self.label_lst
            
            #final_label_lst = all_gather(self.label_lst)
            final_labels_tensor = torch.tensor(final_label_lst)
            
            #log_metric_dict = compute_metrics(final_preds_tensor, 
            #                                  final_labels_tensor, 
            #                                  self.metric_choices, 
            #                                  self.task, 
            #                                  self.num_classes, 
            #                                  'test')
            
            #self.log_dict(log_metric_dict, sync_dist=True, 
            #              prog_bar=True)

        final_id_lst = []
        if self.id_name:
            # self.all_gather function cannot handle non-tensor object; implement our own all_gather function
            id_list_gather = all_gather(self.id_lst)
            for id_lists in id_list_gather:
                final_id_lst.extend(id_lists)

        if self.global_rank == 0:
            print("Rank {}: Save prediction to {}".format(get_rank(), self.test_output_folder))
            if self.id_name:
                test_result_df = pd.DataFrame(data={self.id_name: final_id_lst, "prob": final_pred_lst})
            else:
                test_result_df = pd.DataFrame(data={"prob": final_pred_lst})
                
            if self.test_has_label:
                test_result_df['label'] = final_label_lst
            
            print(test_result_df.head())
            test_filename = f"test_result_{get_rank()}.tsv"
            test_result_df.to_csv(os.path.join(self.test_output_folder, test_filename), sep='\t', index=False)
            print("Complete saving prediction to {}".format(os.path.join(self.test_output_folder, test_filename)))
```

- [[Pytorch Lightning 2 Module Hooks]]







-----------
##  Recommended Notes


- [[AtoZ BSM Model Training Script]]
- [[AtoZ BSM MODS script]]