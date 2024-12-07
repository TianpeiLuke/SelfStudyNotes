---
tags:
  - excerpt
  - documentation
  - code_package
  - pytorch/lightning
aliases: 
keywords: 
topics:
  - code/doc
language: python
date of note: 2024-03-25
name: Pytorch Lightning User Guide and Doc
version: 2.2.1
year: 2024
---
# Trainer

>[!quote]
>Once you’ve organized your PyTorch code into a [`LightningModule`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.LightningModule.html#lightning.pytorch.core.LightningModule "lightning.pytorch.core.LightningModule"), the `Trainer` automates everything else.
>
> The `Trainer` achieves the following:
> 
> 1. You maintain control over all aspects via PyTorch code in your [`LightningModule`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.LightningModule.html#lightning.pytorch.core.LightningModule "lightning.pytorch.core.LightningModule").
>     
> 2. The trainer uses best practices embedded by contributors and users from top AI labs such as Facebook AI Research, NYU, MIT, Stanford, etc…
>     
> 3. The trainer allows disabling any key part that you don’t want automated.
>    
> -- [link](https://lightning.ai/docs/pytorch/stable/common/trainer.html)   


## Basic use

```python
model = MyLightningModule()

trainer = Trainer()
trainer.fit(model, train_dataloader, val_dataloader)
```


## Under the hood

> The Lightning `Trainer` does much more than just “training”. Under the hood, it handles all loop details for you, some examples include:
> 
> - Automatically **enabling/disabling grads**
> - Running the training, validation and test **dataloaders**
> - Calling the **Callbacks** at the appropriate times
> - Putting batches and computations on **the correct devices**
>     
> Here’s the pseudocode for what the trainer does under the hood (showing the train loop only)
> 

```python
# enable grads
torch.set_grad_enabled(True)

losses = []
for batch in train_dataloader:
    # calls hooks like this one
    on_train_batch_start()

    # train step
    loss = training_step(batch)

    # clear gradients
    optimizer.zero_grad()

    # backward
    loss.backward()

    # update parameters
    optimizer.step()

    losses.append(loss)
```


## Validation, Test

```python
trainer.validate(model=model, dataloaders=val_dataloaders)

trainer.test(dataloaders=test_dataloaders)
```


## Additional `Trainer` Arguments

### Basic parameters

>[!important] **Basic parameters**
> - **max_epochs**: Stop training once this number of epochs is reached
> - **min_epochs**: Force training for at least these many epochs
> - **max_steps**: Stop training after this number of [global steps](https://lightning.ai/docs/pytorch/stable/common/trainer.html#global-step). Training will stop if max_steps or max_epochs have reached (earliest).
> - **min_steps**: the opposite
> - **max_time**: Training will get interrupted mid-epoch.

### Parallel and Distributed Computing

>[!important] **Parallel and Distributed Computing**
> - **accelerator**: Supports passing different accelerator types (`"cpu", "gpu", "tpu", "ipu", "auto"`) as well as custom accelerator instances.
> 	- If the `devices` flag is not defined, it will assume `devices` to be `"auto"` and fetch the `auto_device_count` from the accelerator.
> - **devices**: Number of devices to train on (`int`), which devices to train on (`list` or `str`), or `"auto"`.
> - **num_nodes**: Number of GPU nodes for distributed training.
> - **sync_batchnorm**: Enable synchronization between batchnorm layers across all GPUs.
> - **strategy**:  Supports passing different training strategies with aliases (**ddp**, **fsdp**, etc) as well as configured strategies.
> 	- Additionally, you can pass a `strategy` object.

```python
# CPU accelerator
trainer = Trainer(accelerator="cpu")

# Training with GPU Accelerator using 2 GPUs
trainer = Trainer(devices=2, accelerator="gpu")

# Training with TPU Accelerator using 8 tpu cores
trainer = Trainer(devices=8, accelerator="tpu")

# Training with GPU Accelerator using the DistributedDataParallel strategy
trainer = Trainer(devices=4, accelerator="gpu", strategy="ddp")
```

```python
# Training with CPU Accelerator using 2 processes
trainer = Trainer(devices=2, accelerator="cpu")

# Training with GPU Accelerator using GPUs 1 and 3
trainer = Trainer(devices=[1, 3], accelerator="gpu")

# Training with TPU Accelerator using 8 tpu cores
trainer = Trainer(devices=8, accelerator="tpu")
```


```python
# Data-parallel training with the DDP strategy on 4 GPUs
trainer = Trainer(strategy="ddp", accelerator="gpu", devices=4)

# Model-parallel training with the FSDP strategy on 4 GPUs
trainer = Trainer(strategy="fsdp", accelerator="gpu", devices=4)

from lightning.pytorch.strategies import DDPStrategy

trainer = Trainer(strategy=DDPStrategy(static_graph=True), accelerator="gpu", devices=2)
```

### Logging and Check-pointing

>[!important] **Checkpointing, Logging**
>- **check_val_every_n_epoch**: Check val every n train epochs.
>- **enable_checkpointing**: By default Lightning saves a checkpoint for you in your current working directory, with the state of your *last training epoch*, Checkpoints capture the exact value of all parameters used by a model. To *disable automatic checkpointing*, set this to *False*.
>- **default_root_dir**: Default path for logs and weights when no logger or [`lightning.pytorch.callbacks.ModelCheckpoint`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.callbacks.ModelCheckpoint.html#lightning.pytorch.callbacks.ModelCheckpoint "lightning.pytorch.callbacks.ModelCheckpoint") callback passed. On certain clusters you might want to separate where logs and checkpoints are stored. If you don’t then use this argument for convenience. Paths can be local paths or remote paths such as `s3://bucket/path` or `hdfs://path/`. Credentials will need to be set up to use remote filepaths.
>- **val_check_interval**: How often within one training epoch to check the validation set. Can specify as float or int.
>	- pass a `float` in the range [0.0, 1.0] to check after a fraction of the training epoch.
>	- pass an `int` to check after a fixed number of training batches. An `int` value can only be higher than the number of training batches when `check_val_every_n_epoch=None`, which validates after every `N` training batches across epochs or iteration-based training.
>- **log_every_n_steps**: How often to add logging rows (does not write to disk) 

### Flow Control

>[!important] **Flow Control**
>- **callbacks**: This argument can be used to add a [`Callback`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.callbacks.Callback.html#lightning.pytorch.callbacks.Callback "lightning.pytorch.callbacks.callback.Callback") or a list of them. *Callbacks run sequentially* in the order defined here with the exception of [`ModelCheckpoint`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.callbacks.ModelCheckpoint.html#lightning.pytorch.callbacks.ModelCheckpoint "lightning.pytorch.callbacks.model_checkpoint.ModelCheckpoint") callbacks which run *after all others* to ensure all states are saved to the checkpoints.
>	- Model-specific callbacks can also be added inside the `LightningModule` through [`configure_callbacks()`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.LightningModule.html#lightning.pytorch.core.LightningModule.configure_callbacks "lightning.pytorch.core.LightningModule.configure_callbacks"). Callbacks returned in this hook will extend the list initially given to the `Trainer` argument, and replace the trainer callbacks should there be two or more of the same type. [`ModelCheckpoint`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.callbacks.ModelCheckpoint.html#lightning.pytorch.callbacks.ModelCheckpoint "lightning.pytorch.callbacks.model_checkpoint.ModelCheckpoint") callbacks always run last.
>- **enable_progress_bar**: Whether to enable or disable the progress bar. Defaults to True.

### Debugging

>[!important] **Debugging Usage**:
> - **fast_dev_run**: Runs n if set to `n` (int) else 1 if set to `True` batch(es) to ensure your code will execute without errors. This flag is **only** recommended for debugging purposes and should not be used to limit the number of batches to run. These are the changes enabled:
> 	- Sets `Trainer(max_epochs=1)`.
> 	- Sets `Trainer(max_steps=...)` to 1 or the number passed.
> 	- Sets `Trainer(num_sanity_val_steps=0)`.
> 	- Sets `Trainer(val_check_interval=1.0)`.
> 	- Sets `Trainer(check_every_n_epoch=1)`.
> - **limit_train/test/val_batches**: How much of training/test/validation dataset to check. Useful when debugging or testing something that happens at the end of an epoch.
> - **num_sanity_val_steps**: Sanity check runs n batches of val *before starting the training routine*. This catches any bugs in your validation without having to wait for the first validation check. The Trainer uses *2* steps by default. Turn it off or modify it here.
> - **val_check_interval**: 
> - **check_every_n_epoch**: 

### Quantization

- **precision**: There are two different techniques to set the mixed precision. “True” precision and “Mixed” precision.
	- Lightning supports doing floating point operations in 64-bit precision (“double”), 32-bit precision (“full”), or 16-bit (“half”) with both regular and [bfloat16](https://pytorch.org/docs/1.10.0/generated/torch.Tensor.bfloat16.html)). This selected precision will have a direct impact in the performance and memory usage based on your hardware. **Automatic mixed precision** settings are denoted by a `"-mixed"` suffix, while “true” precision settings have a `"-true"` suffix:

```python
# Default used by the Trainer
fabric = Fabric(precision="32-true", devices=1)

# the same as:
trainer = Trainer(precision="32", devices=1)

# 16-bit mixed precision (model weights remain in torch.float32)
trainer = Trainer(precision="16-mixed", devices=1)

# 16-bit bfloat mixed precision (model weights remain in torch.float32)
trainer = Trainer(precision="bf16-mixed", devices=1)

# 8-bit mixed precision via TransformerEngine (model weights get cast to torch.bfloat16)
trainer = Trainer(precision="transformer-engine", devices=1)

# 16-bit precision (model weights get cast to torch.float16)
trainer = Trainer(precision="16-true", devices=1)

# 16-bit bfloat precision (model weights get cast to torch.bfloat16)
trainer = Trainer(precision="bf16-true", devices=1)

# 64-bit (double) precision (model weights get cast to torch.float64)
trainer = Trainer(precision="64-true", devices=1)
```

### Gradient Manipulation

>[!important] **Gradient Manipulation**
>- **accumulate_grad_batches**: Accumulates gradients over k batches before stepping the optimizer. [^1]
>- **gradient_clip_val**: Gradient clipping value

```python
# accumulate every 4 batches (effective batch size is batch*4)
trainer = Trainer(accumulate_grad_batches=4)
```

### Inference

- **inference_mode**: Whether to use `torch.inference_mode()` or `torch.no_grad()` mode during evaluation (`validate`/`test`/`predict`)
	- With `torch.inference_mode()` *disabled*, you can *enable the grad of your model layers* if required.


-----------
##  Recommended Notes


[^1]: See also: [Gradient Accumulation](https://lightning.ai/docs/pytorch/stable/common/optimization.html#id3) to enable more fine-grained accumulation schedules.




----------
##  Citations

- Pytorch Lightning Homepage Doc [link](https://lightning.ai/docs/pytorch/stable/)
- `Trainer` API [page](https://lightning.ai/docs/pytorch/stable/common/trainer.html)
- *code source*:
- *code package link*




