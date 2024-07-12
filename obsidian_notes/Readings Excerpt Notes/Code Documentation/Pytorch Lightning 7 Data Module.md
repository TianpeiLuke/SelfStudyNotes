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
date of note: 2024-03-29
name: Pytorch Lightning User Guide and Doc
version: 2.2.1
year: 2024
---

##  Lightning DataModule

- `lightning.pytorch.core.LightningDataModule`: A **DataModule** standardizes *the training, val, test splits*, *data preparation* and *transforms*. [reference](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.LightningDataModule.html#lightning.pytorch.core.LightningDataModule)
	- The main advantage is **consistent data splits**, **data preparation** and **transforms** *across models*. 
	- `prepare_data_per_node`: If *True*, each `LOCAL_RANK=0` will call prepare data. Otherwise only `NODE_RANK=0`, `LOCAL_RANK=0` will prepare data.
	  
	- **`from_datasets()`**:
		- Create an instance from `torch.utils.data.Dataset`.
		- **`train_dataset`**: *Optional* dataset or iterable of datasets to be used for `train_dataloader()`
		- **`val_dataset`**: *Optional* dataset or iterable of datasets to be used for `val_dataloader()`
		- **`test_dataset`**: *Optional* dataset or iterable of datasets to be used for `test_dataloader()`
		- `predict_dataset`: Optional dataset or iterable of datasets to be used for `predict_dataloader()`
		- **`batch_size`**: *Batch size* to use for each dataloader. 
			- Default is 1. 
			- This parameter gets forwarded to the `__init__` if the datamodule has such a name defined in its signature.
		- **`num_workers`**: Number of *subprocesses* to use for data loading. 
			- 0 means that the data will be loaded in the main process. 
			- *Number of CPUs available*. 
			- This parameter gets forwarded to the `__init__` if the datamodule has such a name defined in its signature.
			  
	- `load_state_dict( state_dict )`: Called when **loading a checkpoint**, implement to **reload datamodule state** given datamodule `state_dict`.
	  
	- `state_dict()`: Called when **saving a checkpoint**, implement to generate and **save datamodule state**.


>[!example]
> ```python
> import lightning as L
> import torch.utils.data as data
> from lightning.pytorch.demos.boring_classes import RandomDataset
> 
> class MyDataModule(L.LightningDataModule):
>     def prepare_data(self):
>         # download, IO, etc. Useful with shared filesystems
>         # only called on 1 GPU/TPU in distributed
>         ...
> 
>     def setup(self, stage):
>         # make assignments here (val/train/test split)
>         # called on every process in DDP
>         dataset = RandomDataset(1, 100)
>         self.train, self.val, self.test = data.random_split(
>             dataset, [80, 10, 10], generator=torch.Generator().manual_seed(42)
>         )
> 
>     def train_dataloader(self):
>         return data.DataLoader(self.train)
> 
>     def val_dataloader(self):
>         return data.DataLoader(self.val)
> 
>     def test_dataloader(self):
>         return data.DataLoader(self.test)
> 
>     def teardown(self):
>         # clean up state after the trainer stops, delete files...
>         # called on every process in DDP
>         ...
> ```

### Base Class

- Bases: 
	- [`DataHooks`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.hooks.DataHooks.html#lightning.pytorch.core.hooks.DataHooks "lightning.pytorch.core.hooks.DataHooks"), 
	- [`HyperparametersMixin`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.mixins.HyperparametersMixin.html#lightning.pytorch.core.mixins.HyperparametersMixin "lightning.pytorch.core.mixins.hparams_mixin.HyperparametersMixin")

  
- `lightning.pytorch.core.hooks.DataHooks`: **Hooks** to be used for data related stuff. [reference](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.hooks.DataHooks.html#lightning.pytorch.core.hooks.DataHooks "lightning.pytorch.core.hooks.DataHooks")
	- `prepare_data_per_node`: 
	  
	- **`prepare_data()`**: Use this to **download and prepare data**. 
		- Downloading and saving data with **multiple processes (distributed settings)** will result in corrupted data. 
		- Lightning ensures this method is called **only within a single process**, so you can safely add your downloading logic within.
		- In a *distributed environment*, `prepare_data` can be called in two ways (using [prepare_data_per_node](https://lightning.ai/docs/pytorch/stable/common/lightning_module.html#prepare-data-per-node))
			1. Once per node. This is the *default* and is only called on `LOCAL_RANK=0`.
			2. Once in total. Only called on `GLOBAL_RANK=0`.
		 - This is called **before requesting the dataloaders** 
		 - *DO NOT set state* to the model (use `setup` instead) since this is NOT called on every device.
		   
	- **`setup()`**: Called at the **beginning** of *fit (train + validate)*, *validate*, *test*, or *predict*. 
		- This is a good hook when you need to *build models* **dynamically** or adjust something about them. 
		- This hook is called on **every process** when using **DDP**.
		- **`stage`**: either `'fit'`, `'validate'`, `'test'`, or `'predict'`
		  
	- `teardown()`: Called at the **end** of *fit (train + validate), validate, test, or predict*.
	  
	- `predict_dataloader()`: An iterable or collection of iterables specifying *prediction samples*.
		- It’s recommended that all data downloads and preparation happen in `prepare_data()`
		  
	- **`test_dataloader()`**: An iterable or collection of iterables specifying *test samples*.
		- If you don’t need a test dataset and a `test_step()`, you don’t need to implement this method.
	  
	- **`train_dataloader()`**: An iterable or collection of iterables specifying *training samples*. 
		- The dataloader you return will **not be reloaded** *unless* you set [`reload_dataloaders_every_n_epochs`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.trainer.trainer.Trainer.html#lightning.pytorch.trainer.trainer.Trainer.params.reload_dataloaders_every_n_epochs "lightning.pytorch.trainer.trainer.Trainer") to a *positive integer*.
		- For data processing use the following pattern:
			- download in [`prepare_data()`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.hooks.DataHooks.html#lightning.pytorch.core.hooks.DataHooks.prepare_data "lightning.pytorch.core.hooks.DataHooks.prepare_data")
			- process and split in [`setup()`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.hooks.DataHooks.html#lightning.pytorch.core.hooks.DataHooks.setup "lightning.pytorch.core.hooks.DataHooks.setup")
			  
	- **`val_dataloader()`**: An iterable or collection of iterables specifying *validation samples*.
		- The dataloader you return will not be reloaded unless you set [`reload_dataloaders_every_n_epochs`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.trainer.trainer.Trainer.html#lightning.pytorch.trainer.trainer.Trainer.params.reload_dataloaders_every_n_epochs "lightning.pytorch.trainer.trainer.Trainer") to a positive integer.
		- If you don’t need a validation dataset and a `validation_step()`, you don’t need to implement this method.



>[!example]
> ```python
> # DEFAULT
> # called once per node on LOCAL_RANK=0 of that node
> class LitDataModule(LightningDataModule):
>     def __init__(self):
>         super().__init__()
>         self.prepare_data_per_node = True
> 
> 
> # call on GLOBAL_RANK=0 (great for shared file systems)
> class LitDataModule(LightningDataModule):
>     def __init__(self):
>         super().__init__()
>         self.prepare_data_per_node = False
> ```

>[!example]
> ```python
> class LitModel(...):
>     def __init__(self):
>         self.l1 = None
> 
>     def prepare_data(self):
>         download_data()
>         tokenize()
> 
>         # don't do this
>         self.something = else
> 
>     def setup(self, stage):
>         data = load_data(...)
>         self.l1 = nn.Linear(28, data.num_classes)
> ```
> 



-----------
##  Recommended Notes

- Pytorch `LightningDataModule` [reference](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.LightningDataModule.html)
- Pytorch `LightningModule` [reference](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.LightningModule.html#lightning.pytorch.core.LightningModule)
- Pytorch `DataHooks` [reference](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.hooks.DataHooks.html#lightning.pytorch.core.hooks.DataHooks "lightning.pytorch.core.hooks.DataHooks")






----------
##  Citations

- *code source*:
- *code package link*




