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
- [[Fully Sharded Data Parallel or FSDP for LLM Training]]

```python
from lightning.pytorch.strategies import FSDPStrategy, DDPStrategy
from torch.distributed.fsdp import FullyShardedDataParallel as FSDP
```


```python
from torch.utils.data import DataLoader
import torch.distributed as dist
```


```python
from .pl_text_cnn import TextCNN
from .pl_tab_ae import TabAE
from .pl_multimodal_cnn import MultimodalCNN
from .pl_multimodal_bert import MultimodalBert
from .pl_multimodal_gate_fusion import MultimodalBertGateFusion
from .pl_multimodal_moe import MultimodalBertMoE
from .pl_multimodal_cross_attn import MultimodalBertCrossAttn
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

### FSDP Strategy

```python
#----------------- FDSP ---------------------
def my_auto_wrap_policy(module: nn.Module, 
                        recurse: bool, 
                        unwrapped_params: int, 
                        min_num_params: int = 1e5) -> bool:
    """
    Custom FSDP auto wrap policy for multimodal models.

    This policy wraps:
    - TextBertBase (Transformer-based encoder)
    - TabAE (tabular encoder)
    - Any Linear / Conv2d / Embedding with large parameter counts

    Args:
        module (nn.Module): Module to inspect
        recurse (bool): Whether FSDP is recursing
        unwrapped_params (int): Number of unwrapped parameters
        min_num_params (int): Minimum number of params to wrap

    Returns:
        bool: Whether to wrap this module
    """
    return (
        isinstance(module, (TextBertBase, TabAE, nn.Linear, nn.Embedding, nn.Conv2d, nn.MultiheadAttention))
        and unwrapped_params >= min_num_params
    )
```


```python
def is_fsdp_available():
    return torch.cuda.is_available() and torch.cuda.device_count() > 1 and dist.is_available() and dist.is_initialized()

```


```python
strategy = FSDPStrategy(auto_wrap_policy=my_auto_wrap_policy, verbose=True) if is_fsdp_available() else "auto"
#-----------------------------
```


### Model Train 

```python
def model_train(
    model: pl.LightningModule,
    config: Dict,
    train_dataloader: DataLoader,
    val_dataloader: DataLoader,
    device: Union[int, str, List[int]] = "auto",
    model_log_path: str = './model_logs',
    early_stop_metric: str = 'val/f1_score'
) -> pl.Trainer:

    max_epochs = config.get("max_epochs", 10)
    early_stop_patience = config.get("early_stop_patience", 10)
    model_class = config.get("model_class", "multimodal_cnn")
    val_check_interval = config.get("val_check_interval", 1.0)
    use_fp16 = config.get("fp16", False)
    clip_val = config.get("gradient_clip_val", 0.0)

    logger_tb = TensorBoardLogger(save_dir=model_log_path, name="tensorboard_logs")
    monitor_mode = "min" if "loss" in early_stop_metric else "max"

    checkpoint_dir = os.environ.get("SM_CHECKPOINT_DIR", "/opt/ml/checkpoints")
    logger.info(f"Checkpoints will be saved to: {checkpoint_dir}")
    
    checkpoint_callback = ModelCheckpoint(
        dirpath=Path(checkpoint_dir),
        filename=f'{model_class}' + '-{epoch:02d}-{' + f'{early_stop_metric}' + ':.2f}',
        monitor=early_stop_metric,
        save_top_k=1,
        mode=monitor_mode,
        save_weights_only=False
    )

    earlystopping_callback = EarlyStopping(
        monitor=early_stop_metric,
        patience=early_stop_patience,
        mode=monitor_mode
    )
    
    device_stats_callback = DeviceStatsMonitor(cpu_stats=False)

    trainer = pl.Trainer(
        max_epochs=max_epochs,
        logger=logger_tb,
        default_root_dir=model_log_path,
        callbacks=[
            earlystopping_callback,
            checkpoint_callback,
            device_stats_callback,
            TQDMProgressBar(refresh_rate=10),
            LearningRateMonitor(logging_interval='step')
        ],
        val_check_interval=config.get("val_check_interval", 1.0),
        sync_batchnorm=True if torch.cuda.is_available() else False,
        accelerator="gpu" if torch.cuda.is_available() else "cpu",
        devices=device,
        strategy=strategy, # You might need this
        #accumulate_grad_batches=1,
        precision=16 if use_fp16 else 32
    )

    trainer.fit(model, train_dataloaders=train_dataloader, val_dataloaders=val_dataloader)
    return trainer
```

- [[Trainer for BERT Fine-tune v2]]
- [[Pytorch Lightning 3 Trainer]]

### Update: Save Model under FSDP

```python
def save_model(filename: str, 
				model: nn.Module
				):
    logger.info("Saving model weights.")

    # Unwrap if wrapped in FSDP
    if isinstance(model, FSDP):
        model_to_save = model.module
    else:
        model_to_save = model

    torch.save(model_to_save.state_dict(), filename)
```

### Save Predictions


```python
def save_prediction(filename: str, 
					y_true: List, 
					y_pred: List
					):
    logger.info("Saving prediction.")
    torch.save({'y_true': y_true, 'y_pred': y_pred}, filename)
```


### Save Artifacts

```python
def save_artifacts(filename: str, 
					config: Dict, 
					embedding_mat: torch.Tensor, 
					vocab: Dict[str, int], 
					model_class: str
					):
    logger.info("Saving artifacts.")
    artifacts = {
        'config': config,
        'embedding_mat': embedding_mat,
        'vocab': vocab,
        'model_class': model_class,
        'torch_version': torch.__version__,
        'transformers_version': __import__('transformers').__version__,
        'pytorch_lightning_version': __import__('lightning.pytorch').__version__,
    }
    torch.save(artifacts, filename)
```




-----------
##  Recommended Notes

- [[Inference for FSDP Model Parallelism]]

- [[Tabular Embedding with Pydantic]]
- [[Tabular Autoencoder]]

- [[BERT Base Embedding Model with Pydantic]]
- [[BERT Base Emedding Model for BSM]]

- [[AtoZ BSM Model Training Script]]
- [[AtoZ BSM MODS script]]