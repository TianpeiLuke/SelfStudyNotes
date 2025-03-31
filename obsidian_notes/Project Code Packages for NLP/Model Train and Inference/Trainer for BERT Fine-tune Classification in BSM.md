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
>This script contains the fine-tuning process from BERT
>- the main step calls `Trainer` from `lightning` package
>	- add **checkpointing**


- [[Fine-Tuning for Sequence or Sequence-Pair Classification via BERT]]
- [[Bidirectional Encoder Representation from Transformer or BERT]]
- [[Pytorch Lightning 3 Trainer]]


## Code

```python
import os
import json
import pickle
import sys
import time
import logging
import tarfile
from tqdm import tqdm, trange
from typing import Union, List, Tuple, Optional, Set, Dict


import boto3
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

import torch 
from torch.utils.data import Dataset, IterableDataset, DataLoader
import torch.optim as optim
from torch import nn
```

- [[Pytorch Lightning 7 Data Module]]

```python
import lightning.pytorch as pl
from lightning.pytorch.callbacks.early_stopping import EarlyStopping
from lightning.pytorch.callbacks import ModelCheckpoint, TQDMProgressBar, LearningRateMonitor
from lightning.pytorch.loggers import TensorBoardLogger
# from lightning.pytorch.accelerators import find_usable_cuda_devices
from lightning.pytorch.strategies import DDPStrategy


from transformers import AutoTokenizer, AutoModel
import json

```

- [[Pytorch Lightning 3 Trainer]]
- [[Pytorch Lightning 5 Distributed Training Strategies]]


```python
from .pl_text_cnn import TextCNN
from .pl_tab_ae import TabAE
from .pl_multimodal_cnn import MultimodalCNN
from .pl_multimodal_bert import MultimodalBert
from .pl_bert import (TextBertBase,
                      TextBertClassification
                      )
from .pl_lstm import TextLSTM
from .pl_model_plots import compute_metrics
from .dist_utils import all_gather
```

```python
dtype = torch.float
device = torch.device('cuda' if torch.cuda.is_available() else 'cpu')  

logger = logging.getLogger(__name__)
handler = logging.StreamHandler()
handler.setLevel(logging.INFO)
formatter = logging.Formatter('%(levelname)s - %(message)s')
handler.setFormatter(formatter)
logger.addHandler(handler)

```

### Model Train Interface

```python
def model_train(model, 
                config, 
                train_dataloader: torch.utils.data.DataLoader, 
                val_dataloader: torch.utils.data.DataLoader, 
                device: Optional[str] = "auto", 
                model_log_path: Optional[str] = './model_logs', 
                early_stop_metric: Optional[str] = 'f1_score/val'
                ):
    
    if 'max_epochs' in config:
        max_epochs = config['max_epochs']
    else:
        max_epochs = 10

    if 'early_stop_patience' in config:
        early_stop_patience = config['early_stop_patience']
    else:
        early_stop_patience = 10

    if 'model_class' in config:
        model_class = config['model_class']
    else:
        model_class = 'multimodal_cnn'

    if 'val_check_interval' in config:
        val_check_interval = config['val_check_interval']
    else:
        val_check_interval = 1.0

    logger = TensorBoardLogger(os.path.join(model_log_path, 'tensorboard_logs'))

	# Checkpointing
    ckpt_filename= '%s_{epoch:02d}-{%s:.2f}' % (model_class, early_stop_metric)

	# Early stop
    if early_stop_metric == 'val_loss' or early_stop_metric == 'test_loss':
        checkpoint_callback = ModelCheckpoint(dirpath= os.path.join(model_log_path, 'ckpts'),
                                       filename = ckpt_filename, 
                                      save_top_k = 3, 
                                      monitor=f"{early_stop_metric}",
                                      mode="min"
                                     )
        earlystopping_callback = EarlyStopping(monitor = f"{early_stop_metric}",
                                           patience= early_stop_patience, 
                                           verbose = False,
                                           mode = "min")
    else:
        checkpoint_callback = ModelCheckpoint(dirpath= os.path.join(model_log_path, 'ckpts'),
                                       filename = ckpt_filename, 
                                      save_top_k = 3, 
                                      monitor=f"{early_stop_metric}",
                                      mode="max"
                                     )
        earlystopping_callback = EarlyStopping(monitor = f"{early_stop_metric}", 
                                           patience= early_stop_patience, 
                                           verbose = False, 
                                           mode = "max")   
    # Show progresser bar                                        
    progressbar_callback = TQDMProgressBar(process_position = -1)
    
    # Monitor the learning rate
    lr_monitor = LearningRateMonitor(logging_interval='step')

    # train model
    trainer = pl.Trainer(max_epochs = max_epochs,
                         logger = logger,
                         default_root_dir = model_log_path,
                         callbacks = [earlystopping_callback,
                                      checkpoint_callback,
                                      progressbar_callback,
                                      lr_monitor
                                     ],
                         val_check_interval = val_check_interval,
                         sync_batchnorm=True,
                         accelerator = "gpu", 
                         devices = device,
                         precision=16 if config["fp16"] else 32,
                         gradient_clip_val = config["gradient_clip_val"],
                         strategy = "ddp"
                        )

    trainer.fit(model, train_dataloaders = train_dataloader, val_dataloaders = val_dataloader) 
    return trainer

```

- [[Pytorch Lightning 3 Trainer]]

### Model Inference Interface

#### Offline Inference by Calling `Trainer` module

```python
def model_inference(model, 
                    dataloader: torch.utils.data.DataLoader, 
                    accelerator: Optional[str] = "auto",
                    device: Optional[str] = "auto",
                    model_log_path: Optional[str] = './model_logs'
                   ):
    
    progressbar_callback = TQDMProgressBar(process_position = -1)

    # inference on one record
    tester = pl.Trainer(max_epochs = 1,
                        default_root_dir = model_log_path,
                        enable_checkpointing = False,
                        logger = False,
                        callbacks = [progressbar_callback,
                                     ],
                        accelerator = accelerator,
                        devices = device,
                        strategy = "auto",
                        inference_mode = True
                        )
    
    tester.test(model, dataloader)
    result_folder = model.test_output_folder
    
    # get all files saved under test folder, each file corresponding to one GPU process
    onlyfiles = [f for f in os.listdir(result_folder) if os.path.isfile(os.path.join(result_folder, f)) and f.endswith('.tsv')]
    restul_df_lst = []
    for filename in onlyfiles:
        restul_df_lst.append(pd.read_csv(os.path.join(result_folder, filename), sep='\t', index_col = None))
    
    result_df = pd.concat(restul_df_lst, ignore_index = True)
    
    return result_df
```

#### Online Inference Module

```python
@torch.inference_mode()
def model_online_inference(model, 
                            dataloader: torch.utils.data.DataLoader
                           ):
    model.eval()

    predictions = []
    for i, batch in enumerate(dataloader):
        _, preds, _ = model.run_epoch(batch, 'pred')
        predictions.append(preds.detach().cpu().numpy())
    return np.concatenate(predictions, axis=0)
 
```

#### Gather the inference result from all machines / GPUs 

```python
def predict_stack_transform(outputs):
    if not isinstance(outputs, List):
        raise TypeError('input list of tensors or list of tuple of tensors')
    if isinstance(outputs[0], Tuple):
        pred_list, label_list = zip(*outputs)
        preds = torch.cat([pred_batch for pred_batch in pred_list])
        labels = torch.cat([label_batch for label_batch in label_list])
        return preds, labels
    else:
        preds = torch.cat([pred_batch for pred_batch in outputs])
        return preds
    
```

### Save Model and Output

```python
def save_prediction(filename: str,
                    y_true: List[Union[float, int]], 
                    y_pred: List[Union[float, int]]
                   ):
    logger.info("Saving prediction.")
    torch.save({
            'y_true': y_true,
            'y_pred': y_pred
            }, filename)

    
def save_model(filename: str, 
               model: torch.nn.Module):
    logger.info("Saving the model.")    
    #path = os.path.join(model_dir, model_filename)
    # recommended way from http://pytorch.org/docs/master/notes/serialization.html
    #torch.save(model.cpu().state_dict(), path)
    torch.save(model.state_dict(), filename)

    
def save_artifacts(filename: str,
                   config: Dict[str, Union[str, float, List[str]]], 
                   embedding_mat: torch.tensor,
                   vocab: Dict[str, int],
                   model_class: str
                  ):
    logger.info("Saving the artifacts.")
    '''
    if device.type == 'cuda':
        model_artifact_filename = 'model_artifacts.pth'  
    else:
        model_artifact_filename = 'model_artifacts_gpu.pth'      
    path = os.path.join(model_dir, model_artifact_filename)
    model_cpu = model.cpu()
    '''
    torch.save({
            'config':  config,
            'embedding_mat': embedding_mat,
            'vocab': vocab,
            'model_class': model_class
            }, filename)
```

### Load Artifacts

```python
    
def load_artifacts(filename: str, 
                   device_l: Optional[str] = 'cpu') \
-> Tuple[Dict[str, Union[str, float, List[str]]], torch.tensor, Dict[str, int]]:
    logger.info("Loading model artifacts ...")
    artifacts = torch.load(filename, map_location=torch.device(device_l))
    model_class = artifacts['model_class']
    config, embedding_mat, vocab = artifacts['config'], artifacts['embedding_mat'], artifacts['vocab']
    return config, embedding_mat, vocab, model_class

```

### Load Model

```python
def load_model(filename: str, 
               config: Dict[str, Union[str, float, List[str]]], 
               embedding_mat: torch.tensor, 
               model_class: Optional[str] = 'multimodal_cnn',
               device_l: Optional[str] = 'cpu') -> torch.nn.Module:
    
    logger.info("Model initialization ...")    
    if model_class == 'multimodal_cnn':
        model = MultimodalCNN(config, embedding_mat.shape[0], embedding_mat)
    elif model_class == 'bert':
        model = TextBertClassification(config)
    elif model_class == 'lstm':
        model = TextLSTM(config, embedding_mat.shape[0], embedding_mat)
    elif model_class == 'multimodal_bert':
        model = MultimodalBert(config)
    else:
        model = MultimodalCNN(config, embedding_mat.shape[0], embedding_mat)

    logger.info("Loading model parameters...")
    model.load_state_dict(torch.load(filename,  map_location=device_l))
    logger.info("Loading process finished.")

    return model 

```

### Load Checkpoints

```python
def load_checkpoint(filename: str,
                    model_class: Optional[str] = 'multimodal_cnn',
                    device_l: Optional[str] = 'cpu') -> torch.nn.Module:
    
    logger.info(f"Load model state parameters")
    if model_class == 'multimodal_cnn':
        model = MultimodalCNN.load_from_checkpoint(filename, map_location=device_l)
    elif model_class == 'bert':
        model = TextBertClassification.load_from_checkpoint(filename, map_location=device_l)
    elif model_class == 'lstm':
        model = TextLSTM.load_from_checkpoint(filename, map_location=device_l)
    elif model_class == 'multimodal_bert':
        model = MultimodalBert.load_from_checkpoint(filename, map_location=device_l)
    else:
        model = MultimodalCNN.load_from_checkpoint(filename, map_location=device_l)
            
    return model
```




-----------
##  Recommended Notes


- [[AtoZ BSM Model Training Script]]
- [[AtoZ BSM MODS script]]