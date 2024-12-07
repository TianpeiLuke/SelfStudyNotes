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
# LightningModule

> [!quote]
> A [`LightningModule`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.LightningModule.html#lightning.pytorch.core.LightningModule "lightning.pytorch.core.LightningModule") organizes your PyTorch code into 6 sections:
> 
> - Initialization (`__init__` and `setup()`).
>     
> - Train Loop ([`training_step()`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.LightningModule.html#lightning.pytorch.core.LightningModule.training_step "lightning.pytorch.core.LightningModule.training_step"))
>     
> - Validation Loop ([`validation_step()`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.LightningModule.html#lightning.pytorch.core.LightningModule.validation_step "lightning.pytorch.core.LightningModule.validation_step"))
>     
> - Test Loop ([`test_step()`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.LightningModule.html#lightning.pytorch.core.LightningModule.test_step "lightning.pytorch.core.LightningModule.test_step"))
>     
> - Prediction Loop ([`predict_step()`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.LightningModule.html#lightning.pytorch.core.LightningModule.predict_step "lightning.pytorch.core.LightningModule.predict_step"))
>     
> - Optimizers and LR Schedulers ([`configure_optimizers()`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.LightningModule.html#lightning.pytorch.core.LightningModule.configure_optimizers "lightning.pytorch.core.LightningModule.configure_optimizers"))


>[!important] Note
>- When you convert to use Lightning, the code IS NOT abstracted - just organized. All the other code that’s not in the [`LightningModule`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.LightningModule.html#lightning.pytorch.core.LightningModule "lightning.pytorch.core.LightningModule") has been **automated** for you by the [`Trainer`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.trainer.trainer.Trainer.html#lightning.pytorch.trainer.trainer.Trainer "lightning.pytorch.trainer.trainer.Trainer").
>- There are **no `.cuda()` or `.to(device)` calls required**. Lightning does these for you.
>- A [`LightningModule`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.LightningModule.html#lightning.pytorch.core.LightningModule "lightning.pytorch.core.LightningModule") is a [`torch.nn.Module`](https://pytorch.org/docs/stable/generated/torch.nn.Module.html#torch.nn.Module "(in PyTorch v2.2)") but with added functionality.

## Basic Setting

[[Pytorch Lightning Model Template]]

The core methods in `LightningModule`:

- **__init__** and **setup**: Define initialization here.
  
- **forward**:  To run data through your model only (separate from **training_step**). 
	- **NOTE**: When using forward, you are responsible to call `eval()` and use the `no_grad()` context manager.
	- In the case where you want to scale your inference, you should be using [`predict_step()`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.LightningModule.html#lightning.pytorch.core.LightningModule.predict_step "lightning.pytorch.core.LightningModule.predict_step").
	  
- **training_step**: The complete training step. Under the hood, Lightning does the following (*pseudocode*):

```python
# enable gradient calculation
torch.set_grad_enabled(True)

for batch_idx, batch in enumerate(train_dataloader):
    loss = training_step(batch, batch_idx)

    # clear gradients
    optimizer.zero_grad()

    # backward
    loss.backward()

    # update parameters
    optimizer.step()
```


- **validation_step**: The complete validation step. Under the hood, Lightning does the following (*pseudocode*):

```python
# ...
for batch_idx, batch in enumerate(train_dataloader):
    loss = model.training_step(batch, batch_idx)
    loss.backward()
    # ...

    if validate_at_some_point:
        # disable grads + batchnorm + dropout
        torch.set_grad_enabled(False)
        model.eval()

        # ----------------- VAL LOOP ---------------
        for val_batch_idx, val_batch in enumerate(val_dataloader):
            val_out = model.validation_step(val_batch, val_batch_idx)
        # ----------------- VAL LOOP ---------------

        # enable grads + batchnorm + dropout
        torch.set_grad_enabled(True)
        model.train()
```

- **test_step**: The complete test step. Similar to **validation_step**. The only difference is that the test loop is only called when [`test()`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.trainer.trainer.Trainer.html#lightning.pytorch.trainer.trainer.Trainer.test "lightning.pytorch.trainer.trainer.Trainer.test") is used.
  
- **predict_step**: The complete prediction step.  By default, the [`predict_step()`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.LightningModule.html#lightning.pytorch.core.LightningModule.predict_step "lightning.pytorch.core.LightningModule.predict_step") method runs the [`forward()`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.LightningModule.html#lightning.pytorch.core.LightningModule.forward "lightning.pytorch.core.LightningModule.forward") method. Under the hood, Lightning does the following (*pseudocode*):

```python
# disable grads + batchnorm + dropout
torch.set_grad_enabled(False)
model.eval()
all_preds = []

for batch_idx, batch in enumerate(predict_dataloader):
    pred = model.predict_step(batch, batch_idx)
    all_preds.append(pred)
```
  
- **configure_optimizers**: Define optimizers and LR schedulers. [link](https://lightning.ai/docs/pytorch/stable/common/lightning_module.html#configure-optimizers)

## Methods

>[!important] Highlights
>- **epoch-level metrics and log**: `log()`, `log_dict()`
>- **epoch-level operations**:  `on_{train/validation/test}_epoch_end()`
>- **save hyperparameters**: `save_hyperparameters()`
>- **configure optimizers and LR scheduler**: `configure_optimizers()` and `lr_scheduler_config`
>- **freeze and unfreeze parameters**: `freeze()` and `unfreeze()`
>- **save model**: `to_onnx()`, `to_torchscript()`


### Tracking Epoch-level Metrics

- If you want to calculate **epoch-level metrics and log** them, use [`log()`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.LightningModule.html#lightning.pytorch.core.LightningModule.log "lightning.pytorch.core.LightningModule.log").
	- The [`log()`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.LightningModule.html#lightning.pytorch.core.LightningModule.log "lightning.pytorch.core.LightningModule.log") method automatically reduces the requested metrics across a complete epoch and devices. 
	- Useful parameters:
		- **name**: key to log.
		- **value**: value to log. Can be a `float`, `Tensor`, or a `Metric`.
		- **prog_bar**: if `True` logs to the progress bar.
		- **logger**: if `True` logs to the logger.
		- **on_step**: if `True` logs *at this step*.
		- **on_epoch**: if `True` logs *epoch accumulated metrics*.
		- **reduce_fx**: *reduction function* over step values for end of epoch.
	- In multiple device setting, be aware of parameters such as 
		- **sync_dist**: if `True`, reduces the metric **across GPUs/TPUs**. Use with care as this may lead to a new *significant communication overhead*.
	- Here’s the pseudocode of what it does under the hood:

```python
outs = [] #<- track metric container
for batch_idx, batch in enumerate(train_dataloader):
    # forward
    loss = training_step(batch, batch_idx)
    outs.append(loss.detach()) #<- track metric

    # clear gradients
    optimizer.zero_grad()
    # backward
    loss.backward()
    # update parameters
    optimizer.step()

# note: in reality, we do this incrementally, instead of keeping all outputs in memory
epoch_metric = torch.mean(torch.stack(outs)) #<- aggregate metric
```


- If you want to log a dictionary of values at once, call [`log_dict()`](https://lightning.ai/docs/pytorch/stable/common/lightning_module.html#log-dict)

###  Epoch-level Operations

- In the case that you need to make use of all the outputs from each `training_step()`, override the `on_train_epoch_end()` method. 
- In the case that you need to make use of all the outputs from each `validation_step()`, override the `on_validation_epoch_end()` method. **Note** that this method is called **before** `on_train_epoch_end()`.

### Validation

- You can also run just the validation loop on your validation dataloaders by overriding [`validation_step()`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.LightningModule.html#lightning.pytorch.core.LightningModule.validation_step "lightning.pytorch.core.LightningModule.validation_step") and calling [`validate()`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.trainer.trainer.Trainer.html#lightning.pytorch.trainer.trainer.Trainer.validate "lightning.pytorch.trainer.trainer.Trainer.validate") in `Trainer`

- It is recommended to *validate* on **single device** to ensure each sample/batch gets evaluated exactly once. This is helpful to make sure benchmarking for research papers is done the right way. Otherwise, in a *multi-device setting*, samples could occur **duplicated** when [`DistributedSampler`](https://pytorch.org/docs/stable/data.html#torch.utils.data.distributed.DistributedSampler "(in PyTorch v2.2)") is used, for eg. with `strategy="ddp"`. It replicates some samples on some devices to make sure all devices have same batch size in case of uneven inputs.

### Save Hyperparameters

- Often times we train many versions of a model. You might share that model or come back to it a few months later at which point it is very useful to know how that model was trained (i.e.: what learning rate, neural network, etc…).
  
- Use `save_hyperparameters()` within your [`LightningModule`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.LightningModule.html#lightning.pytorch.core.LightningModule "lightning.pytorch.core.LightningModule")’s `__init__` method. It will enable Lightning to **store all the provided arguments under the `self.hparams` attribute.** These hyperparameters will also be stored within the model checkpoint, which simplifies model re-instantiation after training.

```python
class LitMNIST(L.LightningModule):
    def __init__(self, layer_1_dim=128, learning_rate=1e-2):
        super().__init__()
        # call this to save (layer_1_dim=128, learning_rate=1e-4) to the checkpoint
        self.save_hyperparameters()

        # equivalent
        self.save_hyperparameters("layer_1_dim", "learning_rate")

        # Now possible to access layer_1_dim from hparams
        self.hparams.layer_1_dim
```

- By default, *every parameter* of the `__init__` method will be considered a hyperparameter to the LightningModule. However, sometimes some parameters need to be **excluded from saving**, for example when they are not serializable. Those parameters should be provided back when reloading the LightningModule. In this case, *exclude them explicitly*:

```python
self.save_hyperparameters(ignore=["param2"])
```

- LightningModules that have hyperparameters automatically saved with `save_hyperparameters()` can conveniently be loaded and instantiated directly from a checkpoint with [`load_from_checkpoint()`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.LightningModule.html#lightning.pytorch.core.LightningModule.load_from_checkpoint "lightning.pytorch.core.LightningModule.load_from_checkpoint"):

```python
# hyperparameters are saved together with model weights. When load from checkpoint, no need to provide param1, param2
model = LitMNIST.load_from_checkpoint(PATH)

# to load specify the other args
model = LitMNIST.load_from_checkpoint(PATH, param1, param2)
```

### Configure Optimizers and Learning Rate Scheduler

- `LightningModule.configure_optimizers()` returns **Any** of these 6 options:
	- **Single optimizer**.
	- **List or Tuple** of optimizers.
	- **Two lists** - The first list has multiple optimizers, and the second has multiple **LR schedulers** (or multiple `lr_scheduler_config`).
	- **Dictionary**, with an `"optimizer"` key, and (optionally) a `"lr_scheduler"` key whose value is a single LR scheduler or `lr_scheduler_config`.
	- **None** - Fit will run without any optimizer.

- The `lr_scheduler_config` is a dictionary which contains the scheduler and its associated configuration. The default configuration is shown below.

```python
lr_scheduler_config = {
    # REQUIRED: The scheduler instance
    "scheduler": lr_scheduler,
    # The unit of the scheduler's step size, could also be 'step'.
    # 'epoch' updates the scheduler on epoch end whereas 'step'
    # updates it after a optimizer update.
    "interval": "epoch",
    # How many epochs/steps should pass between calls to
    # `scheduler.step()`. 1 corresponds to updating the learning
    # rate after every epoch/step.
    "frequency": 1,
    # Metric to to monitor for schedulers like `ReduceLROnPlateau`
    "monitor": "val_loss",
    # If set to `True`, will enforce that the value specified 'monitor'
    # is available when the scheduler is updated, thus stopping
    # training if not found. If set to `False`, it will only produce a warning
    "strict": True,
    # If using the `LearningRateMonitor` callback to monitor the
    # learning rate progress, this keyword can be used to specify
    # a custom logged name
    "name": None,
}
```

### Save Model

- Saves the model in **ONNX format** `to_onnx()`. Arguments will be passed to `torch.onnx.export` function.
- Saves to `ScriptModule`. 

## Internal Attributes

>[!important] Highlights
>- **hparams**: hyper-parameters saved via `save_hyperparameters()`
>- **current_epoch**: 
>- **logger**:
>- **precision**: The type of precision used:
>- **trainer**: Pointer to the trainer
>- **global_step**: The number of optimizer steps taken (does not reset each epoch). This includes multiple optimizers (if enabled).


>[!important] Properties used in multiple device
>- **device**: The device the module is on. Use it to keep your code device agnostic.
>- **local_rank**: The `local_rank` is the index of *the current process* across all the devices **for the current node**. You usually do not need to use this property, but it is useful to know how to access it if needed. For example, if using 10 machines (or nodes), the GPU at index 0 on each machine has local_rank = 0.
>- **global_rank**: The `global_rank` is the index of *the current process* across all **nodes and devices**. Lightning will perform some operations such as logging, weight checkpointing only when `global_rank=0`. You usually do not need to use this property, but it is useful to know how to access it if needed.


[link](https://lightning.ai/docs/pytorch/stable/common/lightning_module.html#properties)




----------
##  Citations

- Pytorch Lightning Homepage Doc [link](https://lightning.ai/docs/pytorch/stable/)
- `LightningModule` API [page](https://lightning.ai/docs/pytorch/stable/common/lightning_module.html)
- [[Pytorch Lightning Model Template]]
- *code source*:
- *code package link*




