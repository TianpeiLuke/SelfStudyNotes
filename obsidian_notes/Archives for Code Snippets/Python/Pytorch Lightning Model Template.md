---
tags:
  - code
  - code_snippet
  - python
  - pytorch
  - deep_learning
  - pytorch/lightning
  - multi-gpu
  - parallel_computing
keywords: 
topics:
  - deep_learning_programming
language: python
date of note: 2024-03-22
---

## Code Snippet Summary

- Basic *Model* class definition from **Pytorch Lightning** library
- Import the base class repository via `import lightning.pytorch as pl` 
- Define *constructor* as `__init__(self, ...)`
- Define *forward-pass* function as `forward(self, xxx)`
- *Configure optimizer* via `configure_optimizers(self)` based on imported optimizer class `import torch.optim as optim`
- Define function `loss_fn` to *compute loss* given output of model `logits`and ground truth `label`
- Define `training_step(self, batch, batch_idx)` which covers one *forward pass* and *loss computation* for a *single batch*
- Similarly, define *one step implementation* in validation set, test set or prediction step
	- `validation_step(self, batch, batch_idx)`
	- `test_step(self, batch, batch_idx)`
	- `predict_step(self, batch, batch_idx)`
- No need to explicitly call *backward pass*; also `pl.LightingModule` implements common steps such as
	- *training mode initiation*, 
	- *batch iteration*, 
	- *gradient clearing*, 
	- *loss averaging*, 
	- *gradient forward step* 
	- etc. 
	in the back-end.  
- Allow for **multi-GPU** and **multi-thread parallel** implementation without additional code change.


## Code

>[!important]
> The core methods in `LightningModule`:
> 
> - **__init__** and **setup**: Define initialization here.
> - **forward**:  To run data through your model only (separate from **training_step**).
> - **training_step**: The complete training step. 
> - **validation_step**: The complete validation step. 
> - **test_step**: The complete test step. 
> - **predict_step**: The complete prediction step.  
> - **configure_optimizers**: Define optimizers and LR schedulers. 


```python
from torch import nn
import torch.optim as optim
import lightning.pytorch as pl

class NeuralNetwork(pl.LightningModule):
	def __init__(self, parameter):
		super(NeuralNetwork, self).init()
		# initalize parameters
		# self.parameter_init(parameter)
		# define model architecture
		...
		# initialize loss function
		self.loss_fn = nn.CrossEntropyLoss()
		# save hyperparameters
		self.save_hyperparameters()


	def forward(self, features):
	'''Define forward pass return logits 
	'''
		...
		return logits


	def configure_optimizers(self):
		...
		optimizer = optim.SGD(...) #or optim.AdamW(...)
		return optimizer


	def training_step(self, batch, batch_idx):
	'''Pytorch Lighting wraps the training iteration process as recursive execution of the training_step function for each given batch; only foward pass need to considered.
	'''
		features = batch['x']
		label = batch['label']
		
		# forward pass
		logits = self.__call__(features)
		
		# compute loss and aggregate loss
		loss = self.loss_fn(logits, label)
		
		# log the training loss in built-in log container
		self.log("train_loss", loss, sync_dist=True, prog_bar=True) 
		return {'loss': loss}

	def test_step(self, batch, batch_idx):
		...

	def validation_step(self, batch, batch_idx):
		...

	def predict_step(self, batch, batch_idx):
		...
```

### Tracking Epoch-level Metrics

- If you want to calculate epoch-level metrics and log them, use [`log()`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.LightningModule.html#lightning.pytorch.core.LightningModule.log "lightning.pytorch.core.LightningModule.log").

>[!example]
> ```python
> def training_step(self, batch, batch_idx):
>     inputs, target = batch
>     output = self.model(inputs, target)
>     loss = torch.nn.functional.nll_loss(output, target.view(-1))
> 
>     # logs metrics for each training_step,
>     # and the average across the epoch, to the progress bar and logger
>     self.log("train_loss", loss, on_step=True, on_epoch=True, prog_bar=True, logger=True)
>     return loss
> ```

### Epoch-level Operations

- In the case that you need to make use of all the outputs from each `training_step()`, override the `on_train_epoch_end()` method.

>[!example]
>```python
>class LightningTransformer(L.LightningModule):
>     def __init__(self, vocab_size):
>         super().__init__()
> 	    # define model
>         self.model = .... 
>         
>         self.training_step_outputs = []
> 
>     def training_step(self, batch, batch_idx):
>         inputs, target = batch
>         output = self.model(inputs, target)
>         loss = ...
>         preds = ...
>         
>         # append predictions into containers
>         self.training_step_outputs.append(preds)
>         return loss
> 
>     def on_train_epoch_end(self):
>         all_preds = torch.stack(self.training_step_outputs)
>         # do something with all preds
>         ...
>         self.training_step_outputs.clear()  # free memory
>```

### Save Hyperparameters

- Use `save_hyperparameters()` within your [`LightningModule`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.LightningModule.html#lightning.pytorch.core.LightningModule "lightning.pytorch.core.LightningModule")’s `__init__` method. It will enable Lightning to **store all the provided arguments under the `self.hparams` attribute.** These hyperparameters will also be stored within the model checkpoint, which simplifies model re-instantiation after training.

```python
def __init__(self, param1, param2):
	super().__init__()
	
	# call this to save (param1, param2) to the checkpoint
    self.save_hyperparameters()
    
    # equivalent   
    self.save_hyperparameters(param1, param2) 
    # Now possible to access param1 from hparams 
    self.hparams.param1  
```

- LightningModules that have hyperparameters automatically saved with `save_hyperparameters()` can conveniently be loaded and instantiated directly from a checkpoint with [`load_from_checkpoint()`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.core.LightningModule.html#lightning.pytorch.core.LightningModule.load_from_checkpoint "lightning.pytorch.core.LightningModule.load_from_checkpoint"):

```python
# hyperparameters are saved together with model weights. When load from checkpoint, no need to provide param1, param2
model = LitMNIST.load_from_checkpoint(PATH)

# to load specify the other args
model = LitMNIST.load_from_checkpoint(PATH, param1, param2)
```



-----------
##  Recommended Notes

- Lightning Documentation [link](https://lightning.ai/docs/pytorch/stable/common/lightning_module.html)
- [[Pytorch Lightning 1 Module]]