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


- [[Trainer for FSDP Model Parallelism]]
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

- [[Multi-modal BERT for FSDP Model Parallelism]]
- [[Multi-modal BERT via Cross-Attention]]
- [[Multi-modal BERT via Fusion Gate]]
- [[Multi-modal BERT via Mixture of Experts]]


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

### Update: Online Inference ONNX and Pytorch

- key is to design the batch sample and format
- all keys (input_ids, attention_mask) are int
- all tabular fields are float
- skip all string fields
- [[Export to ONNX and Inference]]

```python
def model_online_inference(model: Union[pl.LightningModule, ort.InferenceSession], dataloader: DataLoader) -> np.ndarray:
    """
    Run online inference for either a PyTorch Lightning model or an ONNX Runtime session.
    """
    if isinstance(model, ort.InferenceSession):
        print("Running inference with ONNX Runtime.")
        predictions = []
        expected_input_names = [inp.name for inp in model.get_inputs()]

        for batch in dataloader:
            input_feed = {}
            for k in expected_input_names:
                if k not in batch:
                    raise KeyError(f"ONNX input '{k}' not found in batch")

                val = batch[k]

                # Convert to numpy with correct type
                if isinstance(val, torch.Tensor):
                    val_np = val.cpu().numpy()

                    # Ensure correct dtype
                    if "input_ids" in k or "attention_mask" in k:
                        val_np = val_np.astype("int64")  # Required for ONNX
                    else:
                        val_np = val_np.astype("float32")

                    input_feed[k] = val_np
                    
                elif isinstance(val, list) and all(isinstance(x, (int, float)) for x in val):
                    # Fallback for list-based numeric features
                    val_np = np.array(val, dtype="float32").reshape(-1, 1)
                    input_feed[k] = val_np

                else:
                    # Skip fields like order_id (string/list[str]) or raise error
                    print(f"[Warning] Skipping unsupported ONNX input field: '{k}' ({type(val)})")

            output = model.run(None, input_feed)[0]  # Run inference
            predictions.append(output)

        return np.concatenate(predictions, axis=0)
    
    else:
        print("Running inference with PyTorch model.")
        model.eval()
        predictions = []
        for batch in dataloader:
            _, preds, _ = model.run_epoch(batch, 'pred')
            predictions.append(preds.detach().cpu().numpy())
        return np.concatenate(predictions, axis=0)
```


### Load Model

```python
def load_model(filename: str, config: Dict, embedding_mat: torch.Tensor, model_class: str = 'multimodal_bert', device_l: str = 'cpu') -> nn.Module:
    """
    Load model weights into a fresh model instance.

    Returns:
        torch.nn.Module: Model with loaded weights.
    """
    logger.info("Instantiating model.")
    model = {
        'multimodal_cnn': lambda: MultimodalCNN(config, embedding_mat.shape[0], embedding_mat),
        'bert': lambda: TextBertClassification(config),
        'lstm': lambda: TextLSTM(config, embedding_mat.shape[0], embedding_mat),
        'multimodal_bert': lambda: MultimodalBert(config),
        'multimodal_gate_fusion': lambda: MultimodalBertGateFusion(config),
        'multimodal_moe': lambda: MultimodalBertMoE(config),
        'multimodal_cross_attn': lambda: MultimodalBertCrossAttn(config)
    }.get(model_class, lambda: MultimodalBert(config))()

    try:
        model.load_state_dict(torch.load(filename, map_location=device_l))
    except RuntimeError as e:
        logger.error(f"Failed to load model weights: {e}")
    raise

    return model
```

### Load ONNX Model

```python
def load_onnx_model(onnx_path: Union[str, Path]) -> ort.InferenceSession:
    """
    Load an ONNX model exported by MultimodalBert.export_to_onnx and return an ONNX Runtime InferenceSession.

    Args:
        onnx_path (str or Path): Path to the ONNX model file.

    Returns:
        ort.InferenceSession: A session object that can be used to run inference.
    
    Example:
        >>> session = load_onnx_model("model.onnx")
        >>> inputs = {
        >>>     "input_ids": np.array([[101, 1024, 102]]),
        >>>     "attention_mask": np.array([[1, 1, 1]]),
        >>>     "tab_field1": np.array([[0.3, 1.5]]),
        >>>     ...
        >>> }
        >>> outputs = session.run(None, inputs)
        >>> prob = outputs[0]
    """
    if not os.path.isfile(onnx_path):
        raise FileNotFoundError(f"ONNX model not found at: {onnx_path}")

    providers = ['CUDAExecutionProvider', 'CPUExecutionProvider'] if ort.get_device() == 'GPU' else ['CPUExecutionProvider']
    
    try:
        session = ort.InferenceSession(str(onnx_path), providers=providers)
        logger.info(f"Successfully loaded ONNX model from {onnx_path}")
        return session
    except Exception as e:
        raise RuntimeError(f"Failed to load ONNX model: {e}")
```

- [[Export to ONNX and Inference]]

### Load Artifacts

```python
def load_artifacts(filename: str, device_l: str = 'cpu') -> Tuple[Dict, torch.Tensor, Dict, str]:
    logger.info("Loading artifacts.")
    artifacts = torch.load(filename, map_location=device_l)
    config = artifacts['config']
    embedding_mat = artifacts['embedding_mat']
    vocab = artifacts['vocab']
    model_class = artifacts['model_class']
    for k in ['torch_version', 'transformers_version', 'pytorch_lightning_version']:
        logger.info(f"{k}: {artifacts.get(k, 'N/A')}")
    return config, embedding_mat, vocab, model_class 
```


### Load Checkpoints

```python
def load_checkpoint(filename: str, model_class: str = 'multimodal_bert', device_l: str = 'cpu') -> nn.Module:
    logger.info("Loading checkpoint.")
    model_fn = {
        'multimodal_cnn': MultimodalCNN,
        'bert': TextBertClassification,
        'lstm': TextLSTM,
        'multimodal_bert': MultimodalBert,
        'multimodal_gate_fusion': MultimodalBertGateFusion,
        'multimodal_moe': MultimodalBertMoE,
        'multimodal_cross_attn': MultimodalBertCrossAttn
    }.get(model_class, MultimodalBert)
    return model_fn.load_from_checkpoint(filename, map_location=device_l)
```





-----------
##  Recommended Notes

- [[Tabular Embedding with Pydantic]]
- [[Tabular Autoencoder]]

- [[BERT Base Embedding Model with Pydantic]]
- [[BERT Base Emedding Model for BSM]]

- [[AtoZ BSM Model Training Script]]
- [[AtoZ BSM MODS script]]