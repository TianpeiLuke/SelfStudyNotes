---
tags:
  - code
  - code_snippet
  - aws/sagemaker
  - aws/pytorch_estimator
  - python/aws_cdk
keywords: 
topics: 
language: python
date of note: 2025-04-15
---

## Code Snippet Summary

>[!important]
>Execute the Training script using prebuit container in **Pytorch Estimator**

- [[SageMaker SDK Training with Pytorch Container]]


## Code

```python
from sagemaker.pytorch import PyTorch
```

### Profile Monitor

```python
from sagemaker.debugger import ProfilerConfig

profiler_config = ProfilerConfig(
    system_monitor_interval_millis=1000  # Example: Monitor every 500ms
)
```

### Hyperparameter

#### Field Names

```python
full_field_list = [
'order_id',    
'net_conc_amt', 
'ttm_conc_amt', 
'ttm_conc_count',
'concsi',
'deliverable_flag', 
'undeliverable_flag', 
'dnr_pmml_score_calibrated', 
'notr_pmml_score_calibrated',
'bears_normal_prob', 
'bears_risky_prob', 
'bears_abuse_prob',
'dialogue',
'llm_reverssal_flag'   
]

cat_field_list = [
'dialogue'
]

tab_field_list = [
'net_conc_amt', 
'ttm_conc_amt', 
'ttm_conc_count',
'concsi',
'deliverable_flag', 
'undeliverable_flag', 
'dnr_pmml_score_calibrated', 
'notr_pmml_score_calibrated',
'bears_normal_prob', 
'bears_risky_prob', 
'bears_abuse_prob',
]
```

```python
input_tab_dim = len(tab_field_list)
label_name = 'llm_reverssal_flag'          
text_name = 'dialogue'         
id_name = 'order_id'
```

#### Tokenization and Batch Size

```python
batch_size = 1 #8
tokenizer_choice = 'bert-base-multilingual-uncased' 
```

#### Multi-Class

```python
multiclass_categories = [0, 1, 2]
num_classes = len(multiclass_categories)
is_binary = (num_classes == 2)
class_weights = [2.0, 1.0, 1.0]


if len(class_weights) != num_classes:
    raise ValueError(f"The dimension '{len(class_weights)}' not match with number of classses {num_classes}.")
```

#### Model Class

```python
model_class_list = [
    'multimodal_bert',
    'multimodal_moe',
    'multimodal_gate_fusion',
    'multimodal_cross_attn'
]

model_id_choice = 3

model_class = model_class_list[model_id_choice]
```


#### Config File

```python
config = {'adam_epsilon' : 1e-08,
        'batch_size': batch_size, # this is for each GPU in multi-GPU setting
        'class_weights': [1.0, 1.0, 1.0],  #[1.0, 10.0]
        'cat_field_list':  cat_field_list,
        'full_field_list': full_field_list,
        'device': -1, 
        'dropout_keep': 0.1,
        'early_stop_metric': 'val_loss',
        'early_stop_patience':  6,
        'fixed_tokenizer_length': True,
        'header':  0,
        'hidden_common_dim': 100,
        'input_tab_dim': input_tab_dim,
        'id_name': id_name,
        'is_binary': is_binary,                #True,
        'is_embeddings_trainable': True,
        'kernel_size': [3, 5, 7],
        'label_name': label_name,
        'load_ckpt': False,
        'lr': 3e-05,
        'lr_decay': 0.05,
        'max_epochs': 1, #15,
        'max_sen_len': 512,
        'chunk_trancate': True,
        'max_total_chunks': 3,   
        'metric_choices':  ['f1_score', 'auroc'],
        'model_class': model_class,
        'momentum': 0.9,
        'num_channels': [100, 100],
        'num_classes': num_classes,                         #2,
        'multiclass_categories': multiclass_categories,
        'num_layers': 2,
        'optimizer': 'SGD',
        'pretrained_embedding': True,
        'reinit_layers': 2,
        'reinit_pooler': True,
        'run_scheduler': True,
        'tab_field_dim': len(tab_field_list),
        'tab_field_list': tab_field_list,
        'text_field_overwrite': False,
        'text_name': text_name,
        'text_input_ids_key': 'input_ids',
        'text_attention_mask_key': 'attention_mask',
        'tokenizer': 'bert-base-multilingual-uncased',
        'val_check_interval': 0.25,
        'warmup_steps': 300,
        'weight_decay': 0
         }
```

#### Stringtify the Config

- `Pytorch Estimator` only takes hyperparameter in **string** format
- need to convert *bool*, *int*, *float*, *list*, *dict* fields into *str*

```python
import json

def serialize_config(config):
    safe_config = {}
    for k, v in config.items():
        if isinstance(v, (list, dict, bool)):
            safe_config[k] = json.dumps(v)
        else:
            safe_config[k] = str(v)
    return safe_config
```

```python
hyperparameters = serialize_config(config)
```

- [[Hyperparameter for Training Step]]

### Source Directory and Entry Point

- `source_dir` is the path of the package/codes that would like to copy into the container
- `entry_point` is the training script


```python
entry_point = "train.py"
source_dir = "/home/ec2-user/SageMaker/AmazonSageMaker-lukexie-sagemaker-bsm-repo/dockers/docker_fsdp/bsm"
```

- [[Train Script under FSDP]]
- The file structure of codes in `/opt/ml` folder in container

![[pytorch_container_folder_structure.drawio.png]]

### Input / Output S3 Location

```python
s3_folder_root = f"s3://{bucket}/train_test_val/{cur_date}/"
output_path = f"s3://{bucket}/models/{cur_date}/"
checkpoint_path = f"s3://{bucket}/checkpointing/{cur_date}/"
```

```python
inputs = {
    "train": os.path.join(s3_folder_root, "train", "train.parquet"),
    "val": os.path.join(s3_folder_root, "val", "val.parquet"),
    "test": os.path.join(s3_folder_root, "test", "test.parquet")
}
```


### Configure Pytorch Estimator

```python
from sagemaker.pytorch import PyTorch
```

#### Instance Type

```python
instance_type_list=[
    "ml.g4dn.16xlarge", 
    "ml.g5.12xlarge", 
    "ml.g5.16xlarge",
    "ml.p3.16xlarge", 
    "ml.m5.12xlarge"
]
instance_select = 3
instance_type = instance_type_list[instance_select]
```

#### Pytorch Framework Version and Python Version

```python
# This uses the latest PyTorch version from SageMaker prebuilt images (e.g., PyTorch 2.1)
framework_version = "2.1.0"
py_version = "py310"
```


#### Build Estimator

```python
estimator = PyTorch(
    entry_point=entry_point,  # train.py
    source_dir=source_dir,    # folder containing train, package, requirements.txt etc.
    role=role,
    instance_count=1,
    instance_type=instance_type,
    framework_version=framework_version,
    py_version=py_version,
    volume_size=500,
    max_run=4 * 24 * 60 * 60,
    output_path=output_path,
    checkpoint_s3_uri=checkpoint_path,
    sagemaker_session=session,
    hyperparameters=hyperparameters,
    profiler_config=profiler_config,  # Enable Profiler
    metric_definitions=[
        {'Name': 'Train Loss', 'Regex': 'train_loss=([0-9\\.]+)'},
        {'Name': 'Validation Loss', 'Regex': 'val_loss=([0-9\\.]+)'},
        {'Name': 'Validation F1 Score', 'Regex': 'val/f1_score=([0-9\\.]+)'},
        {'Name': 'Validation AUC ROC', 'Regex': 'val/auroc=([0-9\\.]+)'},
    ]
)
```

- [[Config for Training Step]]
- [[Amazon SageMaker Python SDK 1 Training Model with SDK]]
- [[Amazon SageMaker Python SDK 2 Deploy a Pre-Trained Model]]
- [[Amazon SageMaker Python SDK 3.1.1 Pytorch Train]]

### Fit Estimator

- Trigger SageMaker Training Job

```python
estimator.fit(inputs)
```



## End-to-End Pipeline

- [[An End-to-End Training Deployment Pipeline on AWS]]


-----------
##  Recommended Notes

- [[SageMaker BYO Container - Pytorch Lightning Training]]
- [[Docker Container Images]]