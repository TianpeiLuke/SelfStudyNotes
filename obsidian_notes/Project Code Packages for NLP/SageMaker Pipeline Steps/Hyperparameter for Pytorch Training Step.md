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

- [[Builder Pytorch Training Step]]

## Code

```python
from pydantic import BaseModel, Field, model_validator, field_validator
from typing import List, Optional, Dict, Any
```

### Import Base

```python
from .hyperparameters_base import ModelHyperparameters
```

- [[Base Hyperparameters]]
### Hyperparameter for RnR

- [[Pytorch Train Script under FSDP]]
- [[Pytorch Inference Script for RnR BSM]]


```python
class BSMModelHyperparameters(ModelHyperparameters):
    """
    Hyperparameters for the BSM (Buyer Seller Messaging) model training,
    extending the base ModelHyperparameters.
    """
    # Override model_class from base
    model_class: str = Field(default="multimodal_bert", description="Model class identifier, set to XGBoost.")

    # Trainer and Optimization parameters
    # For optimizer
    lr_decay: float = Field(default=0.05, description="Learning rate decay")
    adam_epsilon: float = Field(default=1e-08, description="Epsilon for Adam optimizer")
    momentum: float = Field(default=0.9, description="Momentum for SGD optimizer (if SGD is chosen)")
    # For scheduler
    run_scheduler: bool = Field(default=True, description="Run learning rate scheduler flag")
    val_check_interval: float = Field(default=0.25, description="Validation check interval during training (float for fraction of epoch, int for steps)")
    # For trainer
    warmup_steps: int = Field(default=300, gt=0, le=1000, description="Warmup steps for learning rate scheduler")
    weight_decay: float = Field(default=0.0, description="Weight decay for optimizer (L2 penalty)")
    gradient_clip_val: float = Field(default=1.0, description="Value for gradient clipping to prevent exploding gradients")
    fp16: bool = Field(default=False, description="Enable 16-bit mixed precision training (requires compatible hardware)")
    # Early stopping and Checkpointing parameters
    early_stop_metric: str = Field(default='val_loss', description="Metric for early stopping")
    early_stop_patience: int = Field(default=3, gt=0, le=10, description="Patience for early stopping")
    load_ckpt: bool = Field(default=False, description="Load checkpoint flag")

    # Text Preprocessing and Tokenization parameters
    text_field_overwrite: bool = Field(default=False, description="Overwrite text field if it exists (e.g. during feature engineering)")
    text_name: str = Field(default='dialogue', description="Name of the primary text field to be processed")
    # For chunking long texts
    chunk_trancate: bool = Field(default=True, description="Chunk truncation flag for long texts") # Typo 'trancate' kept as per original
    max_total_chunks: int = Field(default=3, description="Maximum total chunks for processing long texts")
    # For tokenizer settings
    tokenizer: str = Field(default='bert-base-multilingual-uncased', description="Tokenizer name or path (e.g., from Hugging Face)")
    max_sen_len: int = Field(default=512, description="Maximum sentence length for tokenizer")
    fixed_tokenizer_length: bool = Field(default=True, description="Use fixed tokenizer length")
    text_input_ids_key: str = Field(default='input_ids', description="Key name for input_ids from tokenizer output")
    text_attention_mask_key: str = Field(default='attention_mask', description="Key name for attention_mask from tokenizer output")
    
    # Model structure parameters
    # For Convolutional layers
    num_channels: List[int] = Field(default=[100, 100], description="Number of channels for convolutional layers")
    num_layers: int = Field(default=2, description="Number of layers in the model (e.g., BiLSTM, Transformer encoders)")
    dropout_keep: float = Field(default=0.1, description="Dropout keep probability")
    kernel_size: List[int] = Field(default=[3, 5, 7], description="Kernel sizes for convolutional layers")
    is_embeddings_trainable: bool = Field(default=True, description="Trainable embeddings flag")
    # For BERT fine-tuning
    pretrained_embedding: bool = Field(default=True, description="Use pretrained embeddings")
    reinit_layers: int = Field(default=2, description="Number of layers to reinitialize from pretrained model")
    reinit_pooler: bool = Field(default=True, description="Reinitialize pooler layer flag")
    # For Multimodal BERT
    hidden_common_dim: int = Field(default=100, description="Common hidden dimension for multimodal model")
```

- [[Pytorch Estimator Training for RnR BSM]]
- [[Data Class with Pydantic]]
- [[Simple Data Class from Pydantic]]


-----------
##  Recommended Notes


- [[Pytorch Estimator Inference for RnR BSM]]
