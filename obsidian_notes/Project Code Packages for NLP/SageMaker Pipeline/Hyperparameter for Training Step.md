---
tags:
  - code
  - code_snippet
  - python/pydantic
keywords: 
topics: 
language: python
date of note: 2025-05-20
---

## Code Snippet Summary

>[!important]
>Create Hyperparameter from Pydantic class
>- Used to construct `Pytorch` Estimator
>- Used in `PyTorchTrainingStepBuilder`

- [[Builder Training Step]]

## Code

```python
from pydantic import BaseModel, Field, model_validator, field_validator
from typing import List, Optional, Dict, Any
from pathlib import Path
import json
from datetime import datetime
```


```python
class ModelHyperparameters(BaseModel):
    # Field lists
    full_field_list: List[str] = Field(default=[
        'order_id', 'net_conc_amt', 'ttm_conc_amt', 'ttm_conc_count',
        'concsi', 'deliverable_flag', 'undeliverable_flag',
        'dialogue', 'llm_reversal_flag'
    ],  description="Full field list")
    
    cat_field_list: List[str] = Field(default=['dialogue'], description="Categorical fields")
    
    tab_field_list: List[str] = Field(default=[
        'net_conc_amt', 'ttm_conc_amt', 'ttm_conc_count',
        'concsi', 'deliverable_flag', 'undeliverable_flag'
    ], description="Tabular fields")

    # Training parameters
    batch_size: int = Field(default=2, gt=0, le=256, description="Batch size for training")
    adam_epsilon: float = Field(default=1e-08, description="Epsilon for Adam optimizer")
    class_weights: List[float] = Field(default=[1.0, 1.0], description="Class weights for loss function")
    device: int = Field(default=-1, description="Device ID for training")
    dropout_keep: float = Field(default=0.1, description="Dropout keep probability")
    
    # Early stopping configuration
    early_stop_metric: str = Field(default='val_loss', description="Metric for early stopping")
    early_stop_patience: int = Field(default=3, gt=0, le=10, description="Patience for early stopping")
    
    # Model configuration
    fixed_tokenizer_length: bool = Field(default=True, description="Use fixed tokenizer length")
    header: int = Field(default=0,  description="Header row for CSV files")
    hidden_common_dim: int = Field(default=100, description="Common hidden dimension")
    input_tab_dim: int  = Field(default=6, description="Input tabular dimension")
    id_name: str = Field(default='order_id', description="ID field name")    
    is_binary: bool = Field(default=True, description="Binary classification flag")
    is_embeddings_trainable: bool = Field(default=True, description="Trainable embeddings flag")
    kernel_size: List[int] = Field(default=[3, 5, 7], description="Kernel sizes for convolutional layers")
    label_name: str = Field(default='llm_reversal_flag', description="Label field name")
    
    # Checkpoint and learning rate
    load_ckpt: bool = Field(default=False, description="Load checkpoint flag")
    lr: float = Field(default=3e-05, description="Learning rate")
    lr_decay: float = Field(default=0.05, description="Learning rate decay")
    
    # Training configuration
    max_epochs: int = Field(default=3, gt=0, le=10, description="Maximum epochs for training")
    max_sen_len: int = Field(default=512, description="Maximum sentence length")
    chunk_trancate: bool = Field(default=True, description="Chunk truncation flag")
    max_total_chunks: int = Field(default=3, description="Maximum total chunks")
    metric_choices: List[str] = Field(default=['f1_score', 'auroc'], description="Metric choices for evaluation")
    model_class: str = Field(default='multimodal_bert', description="Model class name")
    momentum: float = Field(default=0.9, description="Momentum for SGD optimizer")
    
    # Network architecture
    num_channels: List[int] = Field(default=[100, 100], description="Number of channels for convolutional layers")
    num_classes: int = Field(default=2, description="Number of classes for classification")
    multiclass_categories: List[int] = Field(default=[0, 1], description="Multiclass categories")
    num_layers: int = Field(default=2, description="Number of layers in the model")
    
    # Optimizer and model settings
    optimizer: str = Field(default='SGD', description="Optimizer type")
    pretrained_embedding: bool = Field(default=True, description="Use pretrained embeddings")
    reinit_layers: int = Field(default=2, description="Number of layers to reinitialize")
    reinit_pooler: bool = Field(default=True, description="Reinitialize pooler flag")
    run_scheduler: bool = Field(default=True, description="Run scheduler flag")
    
    # Field configurations
    tab_field_dim: int = Field(default=6, description="Tabular field dimension")
    text_field_overwrite: bool = Field(default=False, description="Overwrite text field flag")
    text_name: str = Field(default='dialogue', description="Text field name")
    text_input_ids_key: str = Field(default='input_ids', description="Input IDs key for text field")
    text_attention_mask_key: str = Field(default='attention_mask', description="Attention mask key for text field")
    tokenizer: str = Field(default='bert-base-multilingual-uncased', description="Tokenizer name")
    
    # Training schedule
    val_check_interval: float = Field(default=0.25, description="Validation check interval")
    warmup_steps: int = Field(default=300, gt=0, le=1000, description="Warmup steps for learning rate scheduler")
    weight_decay: float = Field(default=0, description="Weight decay for optimizer")
    
    class Config:
        arbitrary_types_allowed = True
        validate_assignment = True
        extra = 'forbid'
        protected_namespaces = ()

    @model_validator(mode='after')
    def validate_dimensions(self) -> 'ModelHyperparameters':
        """Validate model dimensions and configurations"""
        # Validate class weights match number of classes
        if len(self.class_weights) != len(self.multiclass_categories):
            raise ValueError(
                f"The dimension of class_weights ({len(self.class_weights)}) "
                f"does not match with number of classes ({len(self.multiclass_categories)})"
            )
        
        # Validate tab field dimensions
        if self.tab_field_dim != len(self.tab_field_list):
            raise ValueError(
                f"tab_field_dim ({self.tab_field_dim}) does not match "
                f"length of tab_field_list ({len(self.tab_field_list)})"
            )
        
        # Validate input tab dimensions
        if self.input_tab_dim != len(self.tab_field_list):
            raise ValueError(
                f"input_tab_dim ({self.input_tab_dim}) does not match "
                f"length of tab_field_list ({len(self.tab_field_list)})"
            )
        
        # Validate binary classification setting
        if self.is_binary and len(self.multiclass_categories) != 2:
            raise ValueError(
                f"is_binary is True but number of classes is {len(self.multiclass_categories)}"
            )
        
        return self

    def get_config(self) -> Dict[str, Any]:
        """Get the complete configuration dictionary"""
        return self.model_dump()

    def serialize_config(self) -> Dict[str, str]:
        """Serialize configuration for SageMaker"""
        config = self.get_config()
        return {
            k: json.dumps(v) if isinstance(v, (list, dict, bool)) else str(v)
            for k, v in config.items()
        }

```

- [[Pytorch Estimator Training for RnR BSM]]
- [[Data Class with Pydantic]]
- [[Simple Data Class from Pydantic]]


-----------
##  Recommended Notes


- [[Pytorch Estimator Inference for RnR BSM]]
