---
tags:
  - code
  - code_snippet
  - reversal_reclassification
  - aws/sagemaker
  - python/aws_python_sdk
keywords: 
topics: 
language: python
date of note: 2025-04-13
---

## Code Snippet Summary

>[!important]
>This is the entry point for Pytorch Estimator `fit()`
>
>It involves the following tasks
>- Load hyperparameters
>- Load train, validation, test dataset
>- Preprocessing
>	- normalization
>	- chunking
>	- tokenization
>	- label transformation
>	- dataset construction
>	- dataloader construction
>- Trainer start training
>- Save to Pytorch
>- Save to ONNX
>- Evaluation on test dataset
>- Plot performance metric


- [[Pytorch Estimator Training for RnR BSM]]

## Code

```python
#!/usr/bin/env python3
import os
import json
import sys
import traceback
import ast
import argparse
import logging
import pandas as pd
import numpy as np
from typing import List, Tuple, Pattern, Union, Dict, Set, Optional
from collections.abc import Callable, Mapping
import torch
from torch.utils.data import Dataset, IterableDataset, DataLoader
import torch.optim as optim
from torch import nn
from torch.utils.tensorboard import SummaryWriter
import lightning.pytorch as pl
from lightning.pytorch.strategies import FSDPStrategy


from transformers import AutoTokenizer, AutoModel
import warnings

warnings.filterwarnings("ignore")
from processing.processors import (
    Processor,
    HTMLNormalizerProcessor,
    EmojiRemoverProcessor,
    TextNormalizationProcessor,
    DialogueSplitterProcessor,
    DialogueChunkerProcessor,
)
from processing.bert_tokenize_processor import TokenizationProcessor
from processing.categorical_label_processor import CategoricalLabelProcessor
from processing.multiclass_label_processor import MultiClassLabelProcessor
from processing.bsm_datasets import BSMDataset
from processing.bsm_dataloader import build_collate_batch
from lightning_models.pl_tab_ae import TabAE
from lightning_models.pl_text_cnn import TextCNN
from lightning_models.pl_multimodal_cnn import MultimodalCNN
from lightning_models.pl_multimodal_bert import MultimodalBert
from lightning_models.pl_multimodal_moe import MultimodalBertMoE
from lightning_models.pl_multimodal_gate_fusion import MultimodalBertGateFusion
from lightning_models.pl_multimodal_cross_attn import MultimodalBertCrossAttn
from lightning_models.pl_bert_classification import TextBertClassification
from lightning_models.pl_lstm import TextLSTM
from lightning_models.pl_train import (
    model_train,
    model_inference,
    predict_stack_transform,
    save_model,
    save_prediction,
    save_artifacts,
    load_model,
    load_artifacts,
    load_checkpoint,
)
from lightning_models.pl_model_plots import (
    compute_metrics,
    roc_metric_plot,
    pr_metric_plot,
)
from lightning_models.dist_utils import get_rank, is_main_process
from pydantic import BaseModel, Field, ValidationError, field_validator  # For Config Validation
```

### Local Directory under Pytorch Pre-built Container

```python
# ================== Model, Data and Hyperparameter Folder =================
prefix = "/opt/ml/"
input_path = os.path.join(prefix, "input/data")
output_path = os.path.join(prefix, "output")
model_path = os.path.join(prefix, "model")
hparam_path = os.path.join(prefix, "input/config/hyperparameters.json")
checkpoint_path = os.environ.get("SM_CHECKPOINT_DIR", "/opt/ml/checkpoints")
train_channel = "train"
train_path = os.path.join(input_path, train_channel)
val_channel = "val"
val_path = os.path.join(input_path, val_channel)
test_channel = "test"
test_path = os.path.join(input_path, test_channel)
```

![[pytorch_container_folder_structure.drawio.png]]
### Logger 

```python
# ============ Logging Setup =================================
logger = logging.getLogger(__name__)
logger.setLevel(logging.INFO)  

if is_main_process():
    handler = logging.StreamHandler()
    handler.setLevel(logging.INFO)
    formatter = logging.Formatter("%(levelname)s - %(message)s")
    handler.setFormatter(formatter)
    logger.addHandler(handler)
    logger.propagate = False

def log_once(logger, message, level=logging.INFO):
    if is_main_process():
        logger.log(level, message)
```


### Step 1: Hyperparameter Parsing

#### Config (Hyperparameter) based on Pydantic

```python
# =============================================================
class Config(BaseModel):
    id_name: str = "order_id"
    text_name: str = "text"
    label_name: str = "label"
    batch_size: int = 32
    full_field_list: List[str] = Field(default_factory=list)
    cat_field_list: List[str] = Field(default_factory=list)
    tab_field_list: List[str] = Field(default_factory=list)
    categorical_features_to_encode: List[str] = Field(default_factory=list)
    header: int = 0
    max_sen_len: int = 512
    chunk_trancate: bool = False
    max_total_chunks: int = 5
    kernel_size: List[int] = Field(default_factory=lambda: [3, 5, 7])
    num_layers: int = 2
    num_channels: List[int] = Field(default_factory=lambda: [100, 100])
    hidden_common_dim: int = 100
    input_tab_dim: int = 11
    num_classes: int = 2
    is_binary: bool = True
    multiclass_categories: List[Union[int, str]] = Field(default_factory=lambda: [0, 1])
    max_epochs: int = 10
    lr: float = 0.02
    lr_decay: float = 0.05
    momentum: float = 0.9
    weight_decay: float = 0
    class_weights: List[float] = Field(default_factory=lambda: [1.0, 10.0])
    dropout_keep: float = 0.5
    optimizer: str = "SGD"
    fixed_tokenizer_length: bool = True
    is_embeddings_trainable: bool = True
    tokenizer: str = "bert-base-multilingual-cased"
    metric_choices: List[str] = Field(default_factory=lambda: ["auroc", "f1_score"])
    early_stop_metric: str = "val/f1_score"
    early_stop_patience: int = 3
    gradient_clip_val: float = 1.0
    model_class: str = "multimodal_bert"
    load_ckpt: bool = False
    val_check_interval: float = 0.25
    adam_epsilon: float = 1e-08
    fp16: bool = False
    run_scheduler: bool = True
    reinit_pooler: bool = True
    reinit_layers: int = 2
    warmup_steps: int = 300
    text_input_ids_key: str = "input_ids"  # Configurable text input key
    text_attention_mask_key: str = "attention_mask"  # Configurable attention mask key
    train_filename: Optional[str] = None
    val_filename: Optional[str] = None
    test_filename: Optional[str] = None
    embed_size: Optional[int] = None  # Added for type consistency
    model_path: str = "/opt/ml/model"  # Add model_path with a default value
    categorical_processor_mappings: Optional[Dict[str, Dict[str, int]]] = None  # Add this line
    label_to_id: Optional[Dict[str, int]] = None  # Added: label to ID mapping
    id_to_label: Optional[List[str]] = None  # Added: ID to label mapping
    
    
    def model_post_init(self, __context):
        # Validate consistency between multiclass_categories and num_classes
        if self.is_binary and self.num_classes != 2:
            raise ValueError("For binary classification, num_classes must be 2.")
        if not self.is_binary:
            if self.num_classes < 2:
                raise ValueError("For multiclass classification, num_classes must be >= 2.")
            if not self.multiclass_categories:
                raise ValueError("multiclass_categories must be provided for multiclass classification.")
            if len(self.multiclass_categories) != self.num_classes:
                raise ValueError(
                    f"num_classes={self.num_classes} does not match "
                    f"len(multiclass_categories)={len(self.multiclass_categories)}"
                )
            if len(set(self.multiclass_categories)) != len(self.multiclass_categories):
                raise ValueError("multiclass_categories must contain unique values.")
        else:
            # Optional: Warn if multiclass_categories is defined when binary
            if self.multiclass_categories and len(self.multiclass_categories) != 2:
                raise ValueError("For binary classification, multiclass_categories must contain exactly 2 items.")
                
        # New: validate class_weights length
        if self.class_weights and len(self.class_weights) != self.num_classes:
            raise ValueError(
                f"class_weights must have the same number of elements as num_classes "
                f"(expected {self.num_classes}, got {len(self.class_weights)})."
            )
```


#### Helper Function

- Note that the hyperparamter.json are all strings
- Need to transform strings into `int`, `float`, `bool`, `list`, 

```python
# --------------- Improved Hyperparameter Parser ---------------
def safe_cast(val):
    if isinstance(val, str):
        val = val.strip()
        if val.lower() == "true":
            return True
        elif val.lower() == "false":
            return False
        if (val.startswith("[") and val.endswith("]")) or (
            val.startswith("{") and val.endswith("}")
        ):
            try:
                return json.loads(val)
            except Exception:
                pass
        try:
            return ast.literal_eval(val)
        except Exception:
            pass
    return val


def sanitize_config(config):
    for key, val in config.items():
        if isinstance(val, str) and val.startswith('"') and val.endswith('"'):
            val = val[1:-1]
        config[key] = safe_cast(val)
    return config

```

#### Load and Parse Hyperparameters

```python
def load_parse_hyperparameters(hparam_path: str) -> Dict:
    converters = {
        "id_name": safe_cast,
        "text_name": safe_cast,
        "label_name": safe_cast,
        "tab_field_list": safe_cast,
        "full_field_list": safe_cast,
        "cat_field_list": safe_cast,
        "categorical_features_to_encode": safe_cast,
        "batch_size": safe_cast,
        "max_sen_len": safe_cast,
        "chunk_trancate": safe_cast,
        "max_total_chunks": safe_cast,
        "tokenizer": safe_cast,
        "hidden_common_dim": safe_cast,
        "input_tab_dim": safe_cast,
        "max_epochs": safe_cast,
        "num_classes": safe_cast,
        "is_binary": safe_cast,
        "multiclass_categories": safe_cast,
        "categorical_label_features": safe_cast,
        "kernel_size": safe_cast,
        "lr": safe_cast,
        "lr_decay": safe_cast,
        "momentum": safe_cast,
        "class_weights": safe_cast,
        "fixed_tokenizer_length": safe_cast,
        "is_embeddings_trainable": safe_cast,
        "optimizer": safe_cast,
        "num_layers": safe_cast,
        "num_channels": safe_cast,
        "weight_decay": safe_cast,
        "num_workers": safe_cast,
        "metric_choices": safe_cast,
        "early_stop_metric": safe_cast,
        "early_stop_patience": safe_cast,
        "model_class": safe_cast,
        "load_ckpt": safe_cast,
        "val_check_interval": safe_cast,
        "fp16": safe_cast,
        "gradient_clip_val": safe_cast,
        "run_scheduler": safe_cast,
        "reinit_pooler": safe_cast,
        "reinit_layers": safe_cast,
        "warmup_steps": safe_cast,
        "adam_epsilon": safe_cast,
        "train_filename": safe_cast,
        "val_filename": safe_cast,
        "test_filename": safe_cast,
        "text_input_ids_key": safe_cast,  # Added
        "text_attention_mask_key": safe_cast,  # Added
    }
    hyperparameters = {}
    with open(hparam_path, "r") as f:
        args = json.load(f)
        log_once(logger, "Hyperparameters for training job:")
        for key, value in args.items():
            if key in converters:
                try:
                    converted = converters[key](value)
                except Exception as e:
                    logger.warning(f"Conversion error for key {key} with value {value}: {e}")
                    converted = value
                hyperparameters[key] = converted
                print(f"{key}: {converted} ({type(converted)})")
            else:
                hyperparameters[key] = value
                print(f"{key}: {value} ({type(value)})")
    return hyperparameters
```

### Step 2: Data Loading

#### Identify Filename of Training,  Validation and Testing 

```python
# --- Detect training, testing and validation file names -------
def find_first_data_file(
    data_dir: str, extensions: List[str] = [".tsv", ".csv", ".parquet"]
) -> Optional[str]:
    for fname in sorted(os.listdir(data_dir)):
        cleaned_fname = fname.strip().lower()
        if any(cleaned_fname.endswith(ext) for ext in extensions):
            return fname
    raise FileNotFoundError(f"No supported data file (.tsv, .csv, .parquet) found in {data_dir}")
```

#### Load Data into BSMDataset

```python
# ----------------- Dataset Loading -------------------------
def load_data_module(file_dir, filename, config: Config) -> BSMDataset:
    log_once(logger, f"Loading BSM dataset from {filename} in folder {file_dir}")
    bsm_dataset = BSMDataset(config=config.model_dump(), file_dir=file_dir, filename=filename)  # Pass as dict
    log_once(logger, f"Filling missing values in dataset {filename}")
    bsm_dataset.fill_missing_value(
        label_name=config.label_name, column_cat_name=config.cat_field_list
    )
    return bsm_dataset
```

- [[BSMDataset]]

### Step 3: Data Preprocessing

#### Text Preprocessing Pipeline and Tokenization

- process text fields

```python
# ----------- Updated Data Preprocessing Pipeline -------------
def data_preprocess_pipeline(config: Config) -> Tuple[AutoTokenizer, Dict[str, Processor]]:
    if not config.tokenizer:
        config.tokenizer = "bert-base-multilingual-cased"
    log_once(logger, f"Constructing tokenizer: {config.tokenizer}")
    tokenizer = AutoTokenizer.from_pretrained(config.tokenizer)
    dialogue_pipeline = (
        HTMLNormalizerProcessor()
        >> EmojiRemoverProcessor()
        >> TextNormalizationProcessor()
        >> DialogueSplitterProcessor()
        >> DialogueChunkerProcessor(tokenizer=tokenizer, 
                                    max_tokens=config.max_sen_len,
                                    truncate=config.chunk_trancate,
                                    max_total_chunks=config.max_total_chunks
                                   )
        >> TokenizationProcessor(
            tokenizer,
            add_special_tokens=True,
            max_length = config.max_sen_len,
            input_ids_key=config.text_input_ids_key,  # Pass key names
            attention_mask_key=config.text_attention_mask_key,
        )
    )
    pipelines = {config.text_name: dialogue_pipeline}
    return tokenizer, pipelines
```

- [[Processors ver 2.0]]
- [[Processor Tokenizer]]

#### Categorical Preprocessing Pipeline

```python
# ------------- Updated Categorical Label Pipeline -----------
def build_categorical_label_pipelines(
    config: Config, datasets: List[BSMDataset]
) -> Dict[str, CategoricalLabelProcessor]:
    cat_fields = config.categorical_features_to_encode
    if not cat_fields:
        return {}
    field_to_processor = {}
    for field in cat_fields:
        all_values = []
        for dataset in datasets:
            if field in dataset.DataReader.columns:
                values = dataset.DataReader[field].dropna().astype(str).tolist()
                all_values.extend(values)
        unique_values = sorted(set(all_values))
        processor = CategoricalLabelProcessor(initial_categories=unique_values)
        field_to_processor[field] = processor
    return field_to_processor
```

- [[Processor Categorical Labeler]]
#### Choose Model Type

```python
# ----------------- Model Selection -----------------------
def model_select(
    model_class: str, config: Config, vocab_size: int, embedding_mat: torch.Tensor
) -> nn.Module:
    if model_class == "multimodal_cnn":
        return MultimodalCNN(config.model_dump(), vocab_size, embedding_mat)
    elif model_class == "bert":
        return TextBertClassification(config.model_dump())
    elif model_class == "lstm":
        return TextLSTM(config.model_dump(), vocab_size, embedding_mat)
    elif model_class == "multimodal_bert":
        return MultimodalBert(config.model_dump())
    elif model_class == "multimodal_moe":
        return MultimodalBertMoE(config.model_dump())
    elif model_class == "multimodal_gate_fusion":
        return MultimodalBertGateFusion(config.model_dump())
    elif model_class == "multimodal_cross_attn":
        return MultimodalBertCrossAttn(config.model_dump())
    else:
        return TextBertClassification(config.model_dump())
```

- [[Multi-modal BERT for FSDP Model Parallelism]]
- [[Multi-modal BERT Classification Model v2 for BSM]]

#### Setup Device

```python
# ----------------- Training Setup -----------------------
def setup_training_environment(config: Config) -> torch.device:
    device = torch.device("cuda" if torch.cuda.is_available() else "cpu")
    print("Using device:", device)
    if device.type == "cuda":
        print(torch.cuda.get_device_name(0))
        if torch.cuda.device_count() > 1:
            print("Let's use", torch.cuda.device_count(), "GPUs!")
    return device
```

#### Inject Preprocessing Pipeline  and Construct Data Loader

```python
# ----------------- Data Loading and Preprocessing -------------
def load_and_preprocess_data(config: Config) -> Tuple[List[BSMDataset], AutoTokenizer, Dict]:
    """
    Loads and preprocesses the train/val/test datasets according to the provided config.

    Returns:
        Tuple of ([train_dataset, val_dataset, test_dataset], tokenizer, config)
    """
    train_filename = config.train_filename or find_first_data_file(train_path)
    val_filename = config.val_filename or find_first_data_file(val_path)
    test_filename = config.test_filename or find_first_data_file(test_path)
    log_once(
        logger,
        "================================================"
    )
    log_once(logger, f"Train folder: {train_path} | File: {train_filename}")
    log_once(logger, f"Validation folder: {val_path} | File: {val_filename}")
    log_once(logger, f"Test folder: {test_path} | File: {test_filename}")
    log_once(
        logger,
        "================================================"
    )
    if not os.path.exists(checkpoint_path):
        print(f"Creating checkpoint folder {checkpoint_path}")
        os.makedirs(checkpoint_path)
        
    # === Load raw datasets ===
    train_bsm_dataset = load_data_module(train_path, train_filename, config)
    val_bsm_dataset = load_data_module(val_path, val_filename, config)
    test_bsm_dataset = load_data_module(test_path, test_filename, config)
    
    # === Build tokenizer and preprocessing pipelines ===
    tokenizer, pipelines = data_preprocess_pipeline(config)
    train_bsm_dataset.add_pipeline(config.text_name, pipelines[config.text_name])
    val_bsm_dataset.add_pipeline(config.text_name, pipelines[config.text_name])
    test_bsm_dataset.add_pipeline(config.text_name, pipelines[config.text_name])
    
    # === Build categorical feature encoders (tabular side) ===
    categorical_processors = build_categorical_label_pipelines(
        config, [train_bsm_dataset, val_bsm_dataset, test_bsm_dataset]
    )
    
    # === Add multiclass label processor if needed ===
    if not config.is_binary and config.num_classes > 2:
        if config.multiclass_categories:
            label_processor = MultiClassLabelProcessor(label_list=config.multiclass_categories, strict=True)
        else:
            label_processor = MultiClassLabelProcessor()
        train_bsm_dataset.add_pipeline(config.label_name, label_processor)
        val_bsm_dataset.add_pipeline(config.label_name, label_processor)
        test_bsm_dataset.add_pipeline(config.label_name, label_processor)
        
        # Save mappings into config for use in inference/export
        config.label_to_id = label_processor.label_to_id
        config.id_to_label = label_processor.id_to_label
        print(config.label_to_id)
        print(config.id_to_label)
    else:
        config.label_to_id = None
        config.id_to_label = None        
    
    for field, processor in categorical_processors.items():
        train_bsm_dataset.add_pipeline(field, processor)
        val_bsm_dataset.add_pipeline(field, processor)
        test_bsm_dataset.add_pipeline(field, processor)
    config.categorical_processor_mappings = {
        field: proc.category_to_label for field, proc in categorical_processors.items()
    }
    return [train_bsm_dataset, val_bsm_dataset, test_bsm_dataset], tokenizer, config
```


### Step 4: Model Training
#### Construct Model Object

```python
# ----------------- Model Building -----------------------
def build_model_and_optimizer(
    config: Config, 
    tokenizer: AutoTokenizer,
    datasets: List[BSMDataset]
) -> Tuple[nn.Module, DataLoader, DataLoader, DataLoader, torch.Tensor]:
    bsm_collate_batch = build_collate_batch(
        input_ids_key=config.text_input_ids_key, 
        attention_mask_key=config.text_attention_mask_key
    )  # Pass key names
    
    train_bsm_dataset, val_bsm_dataset, test_bsm_dataset = datasets
    
    train_dataloader = DataLoader(
        train_bsm_dataset,
        collate_fn=bsm_collate_batch,
        batch_size=config.batch_size,
        shuffle=True,
    )
    val_dataloader = DataLoader(
        val_bsm_dataset, collate_fn=bsm_collate_batch, batch_size=config.batch_size
    )
    test_dataloader = DataLoader(
        test_bsm_dataset, collate_fn=bsm_collate_batch, batch_size=config.batch_size
    )

    log_once(logger, f"Extract pretrained embedding from model: {config.tokenizer}")
    embedding_model = AutoModel.from_pretrained(config.tokenizer)
    embedding_mat = embedding_model.embeddings.word_embeddings.weight
    log_once(logger, f"Embedding shape: [{embedding_mat.shape[0]}, {embedding_mat.shape[1]}]")
    config.embed_size = embedding_mat.shape[1]
    vocab_size = tokenizer.vocab_size
    log_once(logger, f"Vocabulary Size: {vocab_size}")
    log_once(logger, f"Model choice: {config.model_class}")
    model = model_select(config.model_class, config, vocab_size, embedding_mat)
    return model, train_dataloader, val_dataloader, test_dataloader, embedding_mat

```

#### Exporting to ONNX

```python
# ----------------- Save to ONNX -----------------------------
def export_model_to_onnx(
    model: torch.nn.Module,
    trainer,
    val_dataloader: DataLoader,
    onnx_path: Union[str, Path],
):
    """
    Export a (possibly FSDP-wrapped) MultimodalBert model to ONNX using a sample batch from the validation dataloader.

    Args:
        model (torch.nn.Module): The trained model or FSDP-wrapped model.
        trainer: The Lightning trainer used during training (for strategy check).
        val_dataloader (DataLoader): DataLoader to fetch a sample batch for tracing.
        onnx_path (Union[str, Path]): File path to save the ONNX model.

    Raises:
        RuntimeError: If export fails.
    """
    logger.info(f"Exporting model to ONNX: {onnx_path}")

    # 1. Sample and move batch to CPU
    try:
        sample_batch = next(iter(val_dataloader))
    except StopIteration:
        raise RuntimeError("Validation dataloader is empty. Cannot export ONNX.")

    sample_batch_cpu = {
        k: v.to("cpu") if isinstance(v, torch.Tensor) else v
        for k, v in sample_batch.items()
    }

    # 2. Handle FSDP unwrapping if needed
    model_to_export = model
    if isinstance(trainer.strategy, FSDPStrategy):
        if isinstance(model, FSDP):
            logger.info("Unwrapping FSDP model for ONNX export.")
            model_to_export = model.module
        else:
            logger.warning("Trainer uses FSDPStrategy, but model is not FSDP-wrapped.")

    # 3. Move model to CPU and export
    model_to_export = model_to_export.to("cpu").eval()

    try:
        model_to_export.export_to_onnx(onnx_path, sample_batch_cpu)
        logger.info(f"ONNX export completed: {onnx_path}")
    except Exception as e:
        logger.error(f"ONNX export failed: {e}")
        raise RuntimeError("Failed to export model to ONNX.") from e
```

#### Evaluate Model and Creating Plots

```python
# ----------------- Evaluation and Logging ---------------------
def evaluate_and_log_results(
    model: nn.Module,
    val_dataloader: DataLoader,
    test_dataloader: DataLoader,
    config: Config,
    trainer: pl.Trainer,
) -> None:
    log_once(logger, "Inference Starts ...")
    val_predict_labels, val_true_labels = model_inference(
        model, val_dataloader, accelerator="gpu", device="auto", model_log_path=checkpoint_path
    )
    test_predict_labels, test_true_labels = model_inference(
        model, test_dataloader, accelerator="gpu", device="auto", model_log_path=checkpoint_path
    )
    log_once(logger, "Inference Complete.")
    if is_main_process():
        task = "binary" if config.is_binary else "multiclass"
        num_classes = config.num_classes
        output_metrics = ["auroc", "average_precision", "f1_score"]
        metric_test = compute_metrics(
            test_predict_labels,
            test_true_labels,
            output_metrics,
            task=task,
            num_classes=num_classes,
            stage="test",
        )
        metric_val = compute_metrics(
            val_predict_labels,
            val_true_labels,
            output_metrics,
            task=task,
            num_classes=num_classes,
            stage="val",
        )
        log_once(logger, "Metric output for Hyperparameter optimization:")
        for key, value in metric_val.items():
            log_once(logger, f"{key} = {value:.4f}")
        for key, value in metric_test.items():
            log_once(logger, f"{key} = {value:.4f}")
        log_once(logger, "Saving metric plots...")
        writer = SummaryWriter(log_dir=os.path.join(model_path, "tensorboard_eval"))
        roc_metric_plot(
            y_pred=test_predict_labels,  
            y_true=test_true_labels,
            y_val_pred=val_predict_labels,  
            y_val_true=val_true_labels,
            path=model_path,
            task=task,
            num_classes=num_classes,
            writer=writer,
            global_step=trainer.global_step,
        )
        pr_metric_plot(
            y_pred=test_predict_labels,  
            y_true=test_true_labels,
            y_val_pred=val_predict_labels, 
            y_val_true=val_true_labels,
            path=model_path,
            task=task,
            num_classes=num_classes,
            writer=writer,
            global_step=trainer.global_step,
        )
        writer.close()
        prediction_filename = os.path.join(model_path, "predict_results.pth")
        log_once(logger, f"Saving prediction result to {prediction_filename}")
        save_prediction(prediction_filename, test_true_labels, test_predict_labels)
```

### Main Function

```python
# ----------------- Main Function ---------------------------
def main(config: Config):
    device = setup_training_environment(config)
    datasets, tokenizer, config = load_and_preprocess_data(config)
    model, train_dataloader, val_dataloader, test_dataloader, embedding_mat = build_model_and_optimizer(
        config, tokenizer, datasets
    )
    # update tab dimension
    config.input_tab_dim = len(config.tab_field_list)
    log_once(logger, "Training starts using pytorch.lightning ...")
    trainer = model_train(
        model,
        config.model_dump(),
        train_dataloader,
        val_dataloader,
        device="auto",
        model_log_path=checkpoint_path,
        early_stop_metric=config.early_stop_metric,
    )
    log_once(logger, "Training Complete.")
    log_once(logger, "Evaluating final model.")
    
    if config.load_ckpt:
        best_model_path = trainer.checkpoint_callback.best_model_path
        log_once(logger, f"Load best model from checkpoint {best_model_path}")
        model = load_checkpoint(best_model_path, model_class=config.model_class, device_l="cpu")
        
    if is_main_process():
        model_filename = os.path.join(model_path, "model.pth")
        logger.info(f"Saving model to {model_filename}")
        save_model(model_filename, model)
        artifact_filename = os.path.join(model_path, "model_artifacts.pth")
        logger.info(f"Saving model artifacts to {artifact_filename}")
        save_artifacts(
            artifact_filename,
            config.model_dump(),
            embedding_mat,
            tokenizer.vocab,
            model_class=config.model_class,
        )
        
        # ------------------ ONNX Export ------------------
        onnx_path = os.path.join(model_path, "model.onnx")
        logger.info(f"Saving model as ONNX to {onnx_path}")
        export_model_to_onnx(model, trainer, val_dataloader, onnx_path)   
                      

    evaluate_and_log_results(model, val_dataloader, test_dataloader, config, trainer)
    sys.exit(0)

```

### Entry Point

```python
# ----------------- Entrypoint ---------------------------
if __name__ == "__main__":
    hyperparameters = load_parse_hyperparameters(hparam_path)
    hyperparameters = sanitize_config(hyperparameters)
    try:
        config = Config(**hyperparameters)  # Validate config
    except ValidationError as e:
        logger.error(f"Configuration Error: {e}")
        sys.exit(1)  # Exit with error code
    print("Sanitized config:")
    for k, v in config.model_dump().items():
        print(f"{k}: {v} ({type(v)})")
    log_once(logger, "Final Hyperparameters:")
    log_once(logger, json.dumps(config.model_dump(), indent=4))
    log_once(logger, "================================================")
    log_once(logger, "Starting the training process.")
    try:
        main(config)
    except Exception as e:
        trc = traceback.format_exc()
        failure_file = os.path.join(output_path, "failure")
        with open(failure_file, "w") as f:
            f.write("Exception during training: " + str(e) + "\n" + trc)
        logger.error("Exception during training: " + str(e) + "\n" + trc)
        sys.exit(255)
```




-----------
##  Recommended Notes

