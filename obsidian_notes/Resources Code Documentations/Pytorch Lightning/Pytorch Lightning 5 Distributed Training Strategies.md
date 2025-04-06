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
date of note: 2024-03-27
name: Pytorch Lightning User Guide and Doc
version: 2.2.1
year: 2024
---

# Distributed Training strategies

>[!quote]
>Lightning supports multiple ways of doing distributed training.
>- DistributedDataParallel (multiple-gpus across many machines)
>     
>     - Regular (`strategy='ddp'`)
>         
>     - Spawn (`strategy='ddp_spawn'`)
>         
>     - Notebook/Fork (`strategy='ddp_notebook'`)

>[!important]
>If you request multiple GPUs or nodes without setting a strategy, DDP will be automatically used.


>[!info] Highlight 
>These Strategies can be divided into several groups:
>- **Data Parallelism**: Split *data* into multiple chunks. Each GPU runs one chunk of data with a copy of full model weights. At training phase, each copy of model updates its own model with given chunk of data while the gradient of multiple GPUs are synced and aggregated. Example  `DDPStrategy`
>- **Model Parallelism**: Shard *model parameters* or *layer activations* or *optimizer states* or *gradients* into different GPUs or nodes. Example `FSDPStrategy` and `DeepSpeedStrategy`

### GPU Training

[link](https://lightning.ai/docs/pytorch/stable/accelerators/gpu_basic.html)

>[!quote]
>The Trainer will run on **all available GPUs by default**. Make sure you’re running on a machine with at least one GPU. There’s no need to specify any NVIDIA flags as Lightning will do it for you.

```python
# run on as many GPUs as available by default
trainer = Trainer(accelerator="auto", devices="auto", strategy="auto")
# equivalent to
trainer = Trainer()

# run on one GPU
trainer = Trainer(accelerator="gpu", devices=1)
# run on multiple GPUs
trainer = Trainer(accelerator="gpu", devices=8)
# choose the number of devices automatically
trainer = Trainer(accelerator="gpu", devices="auto")
```

- Check `device` parameter in  [[Pytorch Lightning 3 Trainer]]

- You can select the GPU devices using *ranges*, *a list of indices* or *a string* containing a *comma separated list* of GPU *ids*:
	- `device=k`: first k GPUs
	- `device=-1`: all available GPUs
	- `device=[1,3]`: GPU index 1 and 3 (0-based)
	- `device="1,3"`: GPU index 1 and 3 (0-based)
	- `device="-1"`: all available GPUs

```python
# DEFAULT (int) specifies how many GPUs to use per node
Trainer(accelerator="gpu", devices=k)

# Above is equivalent to
Trainer(accelerator="gpu", devices=list(range(k)))

# Specify which GPUs to use (don't use when running on cluster)
Trainer(accelerator="gpu", devices=[0, 1])

# Equivalent using a string
Trainer(accelerator="gpu", devices="0, 1")

# To use all available GPUs put -1 or '-1'
# equivalent to `list(range(torch.cuda.device_count())) and `"auto"`
Trainer(accelerator="gpu", devices=-1)
```

- If you want to run several experiments at the same time on your machine, for example for a hyperparameter sweep, then you can use the following utility function to pick GPU indices that are “accessible”, without having to change your code every time.

```python
from lightning.pytorch.accelerators import find_usable_cuda_devices

# Find two GPUs on the system that are not already occupied
trainer = Trainer(accelerator="cuda", devices=find_usable_cuda_devices(2))

from lightning.fabric.accelerators import find_usable_cuda_devices

# Works with Fabric too
fabric = Fabric(accelerator="cuda", devices=find_usable_cuda_devices(2))
```


### Distributed Data Parallel

[link](https://lightning.ai/docs/pytorch/stable/accelerators/gpu_intermediate.html)

> [!quote]
> **[`DistributedDataParallel`](https://pytorch.org/docs/stable/generated/torch.nn.parallel.DistributedDataParallel.html#torch.nn.parallel.DistributedDataParallel "(in PyTorch v2.2)") (DDP)** works as follows:
> 
> 1. **Each GPU** across **each node** gets its **own process**.
>     
> 2. Each GPU gets visibility into a **subset of the overall dataset**. It will only ever see that subset.
>     
> 3. Each **process inits the model**.
>     
> 4. Each process performs a **full** *forward and backward pass* **in parallel**.
>     
> 5. **The gradients are synced and averaged across all processes.**
>     
> 6. Each process *updates its optimizer*.

```python
# train on 8 GPUs (same machine (ie: node))
trainer = Trainer(accelerator="gpu", devices=8, strategy="ddp")

# train on 32 GPUs (4 nodes)
trainer = Trainer(accelerator="gpu", devices=8, strategy="ddp", num_nodes=4)
```


>[!important] Note
>There are cases in which it is **NOT possible to use DDP**. Examples are:
> 
> - Jupyter Notebook, Google COLAB, Kaggle, etc.
>     
> - You have a nested script without a root package
>     
> 
> In these situations you should use `ddp_notebook` or `dp` instead.

### Distributed and 16-bit precision

[link](https://lightning.ai/docs/pytorch/stable/accelerators/gpu_intermediate.html#distributed-and-16-bit-precision)

Below are the possible configurations we support.

| 1 GPU | 1+ GPUs | DDP | 16-bit | command                                                               |
| ----- | ------- | --- | ------ | --------------------------------------------------------------------- |
| Y     |         |     |        | `Trainer(accelerator=”gpu”, devices=1)`                               |
| Y     |         |     | Y      | `Trainer(accelerator=”gpu”, devices=1, precision=16)`                 |
|       | Y       | Y   |        | `Trainer(accelerator=”gpu”, devices=k, strategy=’ddp’)`               |
|       | Y       | Y   | Y      | `Trainer(accelerator=”gpu”, devices=k, strategy=’ddp’, precision=16)` |

DDP can also be used with 1 GPU, but there’s no reason to do so other than debugging distributed-related issues.

### Training Billion Parameter Model using FSDP

[link](https://lightning.ai/docs/pytorch/stable/advanced/model_parallel/fsdp.html#fully-sharded-training)

Use **Fully Sharded Data Parallel (FSDP)** to train large models with billions of parameters efficiently on multiple GPUs and across multiple machines.

>[!info]
>The memory consumption for training is generally made up of
> 
> 1. the **model parameters**,
>     
> 2. the **layer activations (forward)**,
>     
> 3. the **gradients (backward)** and
>     
> 4. the **optimizer states** (e.g., Adam has two additional exponential averages per parameter).


>[!important] **When to use FSDP**
>- I have *multiple GPUs*
>- I have tried regular DDP training with batch size 1 but I *run out of memory*
>- I have *PyTorch 2.0* or newer installed

- To enable model-parallel training with FSDP in a single-line change, set `strategy="fsdp"`:

```python
trainer = L.Trainer(accelerator="cuda", devices=2, strategy="fsdp")
```

- As we will see in the next sections, there are many settings we can tune to optimize memory usage and throughput, scaling to massively large models. This is equivalent to the above, but will let us configure additional settings later:

```python
from lightning.pytorch.strategies import FSDPStrategy

trainer = L.Trainer(accelerator="cuda", devices=2, strategy=FSDPStrategy())
```

>[!important] Identify large layers
>Models that have many large layers like linear layers in LLMs, ViTs, etc. with >100M parameters will benefit the most from FSDP because the memory they consume through parameters, activations and corresponding optimizer states can be evenly split across all GPUs. 
>
>However, one should avoid splitting small layers that have a few thousand parameters because **communication overhead** would dominate and slow the training down. We can specify a list of layer classes in the **wrapping policy** to inform FSDP which parameters it should wrap:

```python
# 1. Define a set of layers that FSDP should manage
#    Here we are choosing the large encoder and decoder layers
policy = {nn.TransformerEncoderLayer, nn.TransformerDecoderLayer}

# 2. Pass the policy to the FSDPStrategy object
strategy = FSDPStrategy(auto_wrap_policy=policy)

trainer = L.Trainer(..., strategy=strategy)
```


# Strategies

[link](https://lightning.ai/docs/pytorch/stable/api_references.html#strategies)

|                                                                                                                                                                                                                                                 |                                                                                                                                        |
| ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| [`DDPStrategy`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.strategies.DDPStrategy.html#lightning.pytorch.strategies.DDPStrategy "lightning.pytorch.strategies.DDPStrategy")                                                 | Strategy for **multi-process single-device** training on one or multiple nodes.                                                        |
| [`DeepSpeedStrategy`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.strategies.DeepSpeedStrategy.html#lightning.pytorch.strategies.DeepSpeedStrategy "lightning.pytorch.strategies.DeepSpeedStrategy")                         | Provides capabilities to run training using the **DeepSpeed library**, with training optimizations for large billion parameter models. |
| [`FSDPStrategy`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.strategies.FSDPStrategy.html#lightning.pytorch.strategies.FSDPStrategy "lightning.pytorch.strategies.FSDPStrategy")                                             | Strategy for **Fully Sharded Data Parallel** provided by torch.distributed.                                                            |
| [`ParallelStrategy`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.strategies.ParallelStrategy.html#lightning.pytorch.strategies.ParallelStrategy "lightning.pytorch.strategies.ParallelStrategy")                             | Strategy for training with multiple processes in parallel.                                                                             |
| [`SingleDeviceStrategy`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.strategies.SingleDeviceStrategy.html#lightning.pytorch.strategies.SingleDeviceStrategy "lightning.pytorch.strategies.SingleDeviceStrategy")             | Strategy that handles communication on a single device.                                                                                |
| [`SingleDeviceXLAStrategy`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.strategies.SingleDeviceXLAStrategy.html#lightning.pytorch.strategies.SingleDeviceXLAStrategy "lightning.pytorch.strategies.SingleDeviceXLAStrategy") | Strategy for training on a single XLA device.                                                                                          |
| [`Strategy`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.strategies.Strategy.html#lightning.pytorch.strategies.Strategy "lightning.pytorch.strategies.Strategy")                                                             | **Base class** for all strategies that change the behaviour of the training, validation and test- loop.                                |
| [`XLAStrategy`](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.strategies.XLAStrategy.html#lightning.pytorch.strategies.XLAStrategy "lightning.pytorch.strategies.XLAStrategy")                                                 | Strategy for training multiple TPU devices using the `torch_xla.distributed.xla_multiprocessing.spawn()` method.                       |

## DDPStrategy

[link](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.strategies.DDPStrategy.html#lightning.pytorch.strategies.DDPStrategy)

- Base `ParallelStrategy`
- Strategy for **multi-process single-device** training on *one or multiple nodes*.

## FSDPStrategy

[link](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.strategies.FSDPStrategy.html#lightning.pytorch.strategies.FSDPStrategy)

- Base `ParallelStrategy`
- Strategy for *Fully Sharded Data Parallel* provided by torch.distributed.
- **Fully Sharded Training** shards **the entire model** across all available GPUs, allowing you to scale model size, whilst using efficient communication to reduce overhead. In practice, this means we can *remain at parity with PyTorch DDP*, whilst scaling our model sizes dramatically. The technique is similar to **ZeRO-Stage 3**.

## DeepSpeedStrategy

[link](https://lightning.ai/docs/pytorch/stable/api/lightning.pytorch.strategies.DeepSpeedStrategy.html#lightning.pytorch.strategies.DeepSpeedStrategy)

- Base `DDPStrategy`
- Provides capabilities to run training using the **DeepSpeed library**, with training optimizations for large billion parameter models. For more information: [link](https://pytorch-lightning.readthedocs.io/en/stable/advanced/model_parallel.html#deepspeed).

## Choosing the right strategy for your use case

[link](https://lightning.ai/docs/pytorch/stable/advanced/model_parallel.html)

>[!important]  **When NOT to use model-parallel strategies**
> 
> Model parallel techniques help when model sizes are fairly large; roughly 500M+ parameters is where we’ve seen benefits. For *small models* (for example ResNet50 of around 80M Parameters) where the weights, activations, optimizer states and gradients *all fit in GPU memory*, you do not need to use a model-parallel strategy. Instead, use regular [distributed data-parallel (DDP)](https://lightning.ai/docs/pytorch/stable/accelerators/gpu_intermediate.html#gpu-intermediate) training to scale your batch size and speed up training across multiple GPUs and machines. There are several [DDP optimizations](https://lightning.ai/docs/pytorch/stable/advanced/ddp_optimizations.html#ddp-optimizations) you can explore if memory and speed are a concern.


> [!quote]
> If you’ve determined that your model is large enough that you need to leverage model parallelism, you have two training strategies to choose from: **FSDP**, the native solution that comes *built-in with PyTorch*, or the popular third-party [**DeepSpeed**](https://github.com/microsoft/DeepSpeed) library. Both have a very similar feature set and have been used to train the largest SOTA models in the world. Our recommendation is
> 
> - **Use FSDP** if you are new to *model-parallel training*, if you are migrating from PyTorch FSDP to Lightning, or if you are already familiar with DDP.
>     
> - **Use DeepSpeed** if you know you will need cutting edge features not present in FSDP, or you are already familiar with DeepSpeed and are migrating to Lightning.
    

The table below points out a few important differences between the two.

Differences between **FSDP** and **DeepSpeed**:

|                          | [FSDP](https://lightning.ai/docs/pytorch/stable/advanced/model_parallel/fsdp.html#fully-sharded-training) | [DeepSpeed](https://lightning.ai/docs/pytorch/stable/advanced/model_parallel/deepspeed.html#deepspeed-advanced) |
| ------------------------ | --------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| Dependencies             | None                                                                                                      | Requires the `deepspeed` package                                                                                |
| Configuration options    | *Simpler and easier* to get started                                                                       | More *comprehensive, allows finer control*                                                                      |
| Configuration            | Via Trainer                                                                                               | Via Trainer or configuration file                                                                               |
| Activation checkpointing | Yes                                                                                                       | Yes, but requires *changing the model code*                                                                     |
| Offload parameters       | CPU                                                                                                       | CPU or disk                                                                                                     |
| Distributed checkpoints  | Coming soon                                                                                               | Yes                                                                                                             |


----------
##  Citations

- Pytorch Lightning Homepage Doc [link](https://lightning.ai/docs/pytorch/stable/)
- `Strategies` API [page](https://lightning.ai/docs/pytorch/stable/api_references.html#strategies)
- GPU Training Intermediate [page](https://lightning.ai/docs/pytorch/stable/accelerators/gpu_intermediate.html)
- Training Models with Billions of Parameters [page](https://lightning.ai/docs/pytorch/stable/advanced/model_parallel.html)
- 9 Tips For Training Lightning-Fast Neural Networks in Pytorch [blog](https://towardsdatascience.com/9-tips-for-training-lightning-fast-neural-networks-in-pytorch-8e63a502f565)
- Getting Started with Fully Sharded Data Parallel [Tutorial](https://pytorch.org/tutorials/intermediate/FSDP_tutorial.html)
- *code source*:
- *code package link*




