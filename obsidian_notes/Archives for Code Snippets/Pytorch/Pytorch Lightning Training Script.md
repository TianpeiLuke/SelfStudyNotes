---
tags:
  - code
  - code_snippet
  - pytorch/lightning
  - multi-gpu
  - deep_learning
  - parallel_computing
keywords: 
topics: 
language: python
date of note: 2024-03-27
---

## Code Snippet Summary

>[!important]
> - Write a training script using **Pytorch Lightning** package
> - Input the following parameters
> 	- `model_class`:  choose a model from a list of available models
> 	- `early_stop_metric`: choose a metric to monitor for early stopping
> 	- `max_epochs` defined the maximum epochs to run
> 	- `default_root_dir` define the root directory for saving. In container it is a predefined folder for output.

- [[SageMaker SDK Training with BYO Container]]
- [[Pytorch Train Script under FSDP]]
## Code

### Define logger

- only report event equal to or more severe than `INFO` level.

```python
import logging

logger = logging.getLogger(__name__)
logger.setLevel(logging.INFO)
formatter = logging.Formatter('%(levelname)s - %(message)s')
handler.setFormatter(formatter)
logger.addHandler(handler)
```

### Define basic **callbacks**

```python
from lightning.pytorch.callbacks.early_stopping import EarlyStopping
from lightning.pytorch.callbacks import ModelCheckpoint, TQDMProgressBar, LearningRateMonitor

ckpt_filename= '%s_{epoch:02d}-{%s:.2f}' % (model_class, early_stop_metric)

# checkpoint saving callbacks
checkpoint_callback = ModelCheckpoint(dirpath= os.path.join(model_log_path, 'ckpts'),
                                      filename = ckpt_filename, 
                                      save_top_k = 3, 
                                      monitor=f"{early_stop_metric}",
                                      mode="min"
                                     )
# early stopping callbacks           
# select how many steps to wait in `early_stop_patience`
earlystopping_callback = EarlyStopping(monitor = f"{early_stop_metric}", 
                                           patience= early_stop_patience, 
                                           verbose = False, 
                                           mode = "min")  

# this is the default progress bar. Choose `position = -1` to make sure the progress bar updates without restarting a new line
progressbar_callback = TQDMProgressBar(process_position = -1)

# monitor the learning rate
lr_monitor = LearningRateMonitor(logging_interval='step')
```

### Define `Trainer` object

- `Trainer` takes the following argument to specify:
	- `callbacks` parameters to include all callbacks defined above
	  
	- Debug settings:
		- `val_check_interval`: How often to check the validation set. Pass an `int` to check *after a fixed number of training batches*. An `int` value can only be higher than the number of training batches when `check_val_every_n_epoch=None`, which validates after every `N` training batches across epochs or during iteration-based training.
		  
	- Multi-GPU settings:
		- `accelerator = "auto"` or `accelerator = "gpu"`
		- `devices = k` or `devices = "auto"`
		- `strategy = "ddp"`: use *Data Parallelism [[Pytorch Lightning 5 Distributed Training Strategies]]*
		- `sync_batchnorm = True`:  When training a large language model using multiple GPUs, it is generally recommended to synchronize the batch normalization layers between processes to ensure consistent statistics across all GPUs. [^1]

	- Precision: 
		- Choose *16 bit mixed precision* if user choose `fp16`. Otherwise choose full precision (`fp32`)

```python
import lightning.pytorch as pl

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
                    strategy = "ddp"
                    )
```

### Fit using Trainer 

- Input needed to run training process
	- `model`
	- `train_dataloaders`
	- `val_dataloaders`

```python
trainer.fit(model, 
			train_dataloaders = train_dataloader, 
			val_dataloaders = val_dataloader
			) 
```

- `Trainer.fit()` can takes `LightningDataModule` as input, which encapsulates the dataset download, data loader construction, preprocessing steps.
- Can start training from saved checkpoint in `ckpt_path`


### Test the trained model

```python
trainer.test(model, test_dataloader)
```


-----------
##  Recommended Notes

- [[Pytorch Lightning 1 Module]]
- [[Pytorch Lightning 3 Trainer]]
- [[Pytorch Lightning 4 Callbacks]]
- [[Pytorch Lightning 5 Distributed Training Strategies]]

[^1]: Check discussion on whether or not to sync batch normalization in [blog](https://hangzhang.org/PyTorch-Encoding/tutorials/syncbn.html)