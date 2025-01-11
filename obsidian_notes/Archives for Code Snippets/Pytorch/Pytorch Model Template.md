---
tags:
  - code
  - code_snippet
  - python
  - pytorch
  - deep_learning
keywords: 
topics:
  - deep_learning_programming
language: python
date of note: 2024-03-22
---

## Code Snippet Summary

- Basic *Model* class definition from **Pytorch** library
- Import the base class repository via `from torch import nn` 
- Define *constructor* as `__init__(self, ...)`
- Define *forward-pass* function as `forward(self, xxx)`
- Define *optimizer* based on imported optimizer class `import torch.optim as optim`
- Define function `loss_compute(logits, label)` to *compute loss* given output of model `logits`and ground truth `label`
- Define batch data *iterator* as `data_iterator`. Loop over this iterator will generate random `batch` with given size during the training/inference phase. 
- Define model *run* function at given *epoch* during *training time* as `run(self, epoch, data_iterator)`
	- *start training mode* `self.train()`
	- loop over data iterator, each iteration providing a `batch`:
		- *clear out gradient value* 
		  `self.optimizer.zero_grad()`
		- *forward pass* by direct function call on given batch and return logits from model output: 
		  `logits = self.__call__(features)`
		- compute loss function for given batch with ground truth `label` and forward pass output `logits` and average with historical loss aggregate: 
		  `loss = self.loss_compute(logits, label)`
		- *backward pass* by 
		  `loss.backward()`; 
		  finish the **back-propagation** and compute the *gradient of neural network model*  with respect to its learnable parameters.
		- using *stochastic gradient descent* take one step forward on parameter space `self.optimizer.step()`

## Code

```python
import torch.optim as optim
from torch import nn

class NeuralNetwork(nn.Module):
	def __init__(self, parameter):
		super(NeuralNetwork, self).init()
		# initalize parameters
		# self.parameter_init(parameter)
		# define model architecture
		...
		# initialize optimizer object
		self.optimizer = optim.SGD(...)
		# initialize loss function
		self.loss_fn = nn.CrossEntropyLoss()


	def forward(self, features):
	'''Define forward pass return logits 
	'''
		...
		return logits


	def run(self, epoch, data_iterator):
	'''Define the training process for one epoch (iterate through entire dataset once)
	'''
		self.train() # train mode
		train_acc_loss = 0.0
		train_avg_loss = 0.0
		
		# loop over dataset, random sampling batch
		for i, batch in enumerate(data_iterator):
		    # gradient initalize for each batch
			self.optimizer.zero_grad()
			
			features = batch['x']
			label = batch['label']
			# forward pass
			logits = self.__call__(features)
			# compute loss and aggregate loss
			loss = self.loss_fn(logits, label)
			train_acc_loss += loss.data
			train_avg_loss = train_acc_loss / (i+1)
			# backward pass
			loss.backward()
			# stochastic gradient descent one step
			self.optimizer.step()
	

```




-----------
##  Recommended Notes

- [[Pytorch Lightning 1 Module]]