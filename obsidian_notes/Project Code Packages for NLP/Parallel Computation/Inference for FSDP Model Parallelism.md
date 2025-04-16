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
>This script contains the inference step 
>- the main step calls `Trainer` from `lightning` package
>	- assign multi-GPU devices
>- Use **FSDP (Fully Sharded Data Parallel) strategy**


- [[Trainer for BERT Fine-tune v2]]
- [[Model Parallelism]]
- [[Fully Sharded Data Parallel or FSDP for LLM Training]]



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
from lightning.pytorch.accelerators import find_usable_cuda_devices

from transformers import AutoTokenizer, AutoModel
```

- [[Pytorch Lightning 3 Trainer]]
- [[Pytorch Lightning 5 Distributed Training Strategies]]

- FDSP strategy

```python
from lightning.pytorch.strategies import FSDPStrategy, DDPStrategy


from torch.utils.data import DataLoader
import torch.distributed as dist
from torch.distributed.fsdp import FullyShardedDataParallel as FSDP
```


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

### Logger

```python
def setup_logger():
    import logging
    logger = logging.getLogger(__name__)
    if not logger.hasHandlers():
        handler = logging.StreamHandler()
        formatter = logging.Formatter('%(asctime)s - %(levelname)s - %(message)s')
        handler.setFormatter(formatter)
        logger.addHandler(handler)
        logger.setLevel(logging.INFO)
    return logger


logger = setup_logger()
```


### Model Inference 

```python
def model_inference(
    model: pl.LightningModule,
    dataloader: DataLoader,
    accelerator: Union[str, int, List[int]] = "auto",
    device: Union[str, int, List[int]] = "auto",
    model_log_path: str = './model_logs',
    return_dataframe: bool = False,
) -> Union[Tuple[torch.Tensor, torch.Tensor], Tuple[torch.Tensor, torch.Tensor, pd.DataFrame]]:
    """
    Runs inference and returns predicted probabilities and true labels as tensors.
    Supports both binary and multiclass classification.
    
    Args:
        model (pl.LightningModule): Trained Lightning model.
        dataloader (DataLoader): DataLoader for inference.
        accelerator (str/int/List[int]): Accelerator setting.
        device (str/int/List[int]): Device setting.
        model_log_path (str): Path to save logs.
        return_dataframe (bool): Whether to return the original dataframe.
    
    Returns:
        Tuple of (y_pred, y_true) or (y_pred, y_true, df) depending on `return_dataframe`.
    """
    
    # Safe handling: force CPU if no GPU available
    resolved_accelerator = "gpu" if torch.cuda.is_available() else "cpu"
    resolved_devices = 1 if resolved_accelerator == "cpu" else device

    
    tester = pl.Trainer(
        max_epochs=1,
        default_root_dir=model_log_path,
        enable_checkpointing=False,
        logger=False,
        callbacks=[TQDMProgressBar()],
        accelerator=resolved_accelerator,
        devices=resolved_devices,
        strategy="auto",
        inference_mode=True
    )

    tester.test(model, dataloaders=dataloader)
    result_folder = model.test_output_folder
    if not result_folder or not os.path.exists(result_folder):
        raise RuntimeError(f"Expected test output folder '{result_folder}' does not exist.")

    # Match files like test_result_*.tsv from all ranks
    result_files = sorted(Path(result_folder).glob("test_result_*.tsv"))
    if not result_files:
        raise RuntimeError(f"No test result files found in {result_folder}.")

    #dfs = [
    #    pd.read_csv(Path(result_folder) / f, sep='\t')
    #    for f in os.listdir(result_folder)
    #    if f.endswith('.tsv')
    #]
    
    dfs = []
    for f in result_files:
        try:
            dfs.append(pd.read_csv(f, sep="\t"))
        except Exception as e:
            print(f"[Warning] Skipping file {f} due to read error: {e}")
    
    if not dfs:
        raise RuntimeError("No valid result files could be loaded.")
    df = pd.concat(dfs, ignore_index=True)

    is_binary = model.task == "binary"
    if is_binary:
        y_pred = torch.tensor(df["prob"].values.astype(float))
    else:
        y_pred = torch.tensor([ast.literal_eval(p) if isinstance(p, str) else p for p in df["prob"]])

    y_true = torch.tensor(df["label"].values)

    if return_dataframe:
        return y_pred, y_true, df
    else:
        return y_pred, y_true
```

- [[Trainer for BERT Fine-tune v2]]
- [[Pytorch Lightning 3 Trainer]]

### Update: Save Model under FSDP

```python
def save_model(filename: str, model: nn.Module):
    logger.info("Saving model weights.")

    # Unwrap if wrapped in FSDP
    if isinstance(model, FSDP):
        model_to_save = model.module
    else:
        model_to_save = model

    torch.save(model_to_save.state_dict(), filename)
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

- [[Tabular Embedding with Pydantic]]
- [[Tabular Autoencoder]]

- [[BERT Base Embedding Model with Pydantic]]
- [[BERT Base Emedding Model for BSM]]

- [[AtoZ BSM Model Training Script]]
- [[AtoZ BSM MODS script]]