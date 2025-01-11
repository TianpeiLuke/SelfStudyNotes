---
tags:
  - code
  - code_snippet
  - pytorch/distributed
  - parallel_computing
keywords: 
topics: 
language: python
date of note: 2024-04-03
---

## Code Snippet Summary

>[!important]
> - If the **world size (total number of processes)** is 1, return the original tensor
> - If the world size is greater than 1 (e.g. parallel setting such as multi-GPU):
> 	- **serializes the data** and **store** it in `torch.Tensor`
> 	- **pads** tensor in all ranks to the *maximum size*
> 	- uses **`dist.all_gather`** to **gather** the tensors **from all ranks**.
> 	- **deserializes** the gathered tensors back into the original data format using **pickle**  
> 	- **returns** a list of data gathered from each rank.

## Code

- Import

```python
import functools
import numpy as np
import torch
import torch.distributed as dist
```

- `get_rank()` function: return the **rank** of current process in the distributed setup.

```python
import torch.distributed as dist 

def get_rank() -> int:
    if not dist.is_available():
        return 0
    if not dist.is_initialized():
        return 0
    return dist.get_rank()
```

- `get_world_size()` function: returns **the number of processes** in the **distributed** setup. 
	- If distributed training is *not initialized or available*, it returns 1.

```python
import torch.distributed as dist 

def get_world_size() -> int:
    if not dist.is_available():
        return 1
    if not dist.is_initialized():
        return 1
    return dist.get_world_size()
```

- `__get_global_gloo_group()` function:  returns a **process group** based on the **`"gloo"` backend**, containing all the ranks. 
	- If the backend is `"nccl"` (**NVIDIA Collective Communications Library**), it creates a *new group* with the `"gloo"` backend. 
	- Otherwise, it returns the default `dist.group.WORLD` group.
	- The result is **cached** using **`@functools.lru_cache()`** to *avoid creating the group multiple times*.
	  

```python
import functools
import torch.distributed as dist 

@functools.lru_cache()
def _get_global_gloo_group():
    """
    Return a process group based on gloo backend, containing all the ranks
    The result is cached.
    """
    if dist.get_backend() == "nccl":
        return dist.new_group(backend="gloo")
    else:
        return dist.group.WORLD
```

- When running inference with `@torch.inference_mode()`, need to adjust above code to create process group in **GPU** (i.e. using `"nccl"` backend)  not **CPU** (using `"gloo"` backend)
	- [Distributed collective ops fail in `inference_mode` for CPU-on](https://github.com/pytorch/pytorch/issues/86830)

```python
@functools.lru_cache()
def _get_global_gloo_group():
    """
    Return a process group based on gloo backend, containing all the ranks
    The result is cached.
    """
    if dist.get_backend() == "nccl":
        return dist.new_group(backend="nccl")
    else:
        return dist.group.WORLD
```


- `all_gather()` function: the *main entry point*. It takes the *input data* and an optional *process group*.
	- This function is used to **gather data from all processes**.
	- If the **world size** is 1 (**single process**), it simply returns a list containing input data.
	- If the *group* is not provided, it uses the *global `"gloo"` group (CPU process)* obtained from `_get_global_gloo_group()`.
	- It creates an output list with `None` values, where the length of the list is equal to the world size.
	- It uses **`dist.all_gather_object()`** to gather the `data` from all processes and store it in the `output` list.
	- Finally, it returns the `output` list containing the gathered data from all processes.

```python
def all_gather(data, group=None):
    """
    Run all_gather on arbitrary picklable data (not necessarily tensors).

    Args:
        data: any picklable object
        group: a torch process group. By default, will use a group which
            contains all ranks on gloo backend.

    Returns:
        list[data]: list of data gathered from each rank
    """
    if get_world_size() == 1:
        return [data]
    if group is None:
        group = _get_global_gloo_group()  # use CPU group by default, to reduce GPU RAM usage.
    world_size = dist.get_world_size(group)
    if world_size == 1:
        return [data]

    output = [None for _ in range(world_size)]
    dist.all_gather_object(output, data, group=group)
    return output
```


## Comments

- `torch.distributed.is_available()`: `True` if the distributed package is available. [reference](https://pytorch.org/docs/stable/distributed.html#torch.distributed.is_available)
- `torch.distributed.is_initialized()`: Check if the default process group has been initialized. [reference](https://pytorch.org/docs/stable/distributed.html#torch.distributed.is_initialized)
- `torch.distributed.init_process_group()`: Initialize *the default distributed process group*.
	- There are 2 main ways to initialize a process group:
		- Specify `store`, `rank`, and `world_size` explicitly.
		- Specify `init_method` (a URL string) which indicates where/how to discover peers. Optionally specify `rank` and `world_size`, or encode all required parameters in the URL and omit them.
- `torch.distributed.new_group()`: Create a new distributed group. [reference](https://pytorch.org/docs/stable/distributed.html#torch.distributed.new_group)
- `torch.distributed.get_backend()`: Return the backend of the given process group. [reference](https://pytorch.org/docs/stable/distributed.html#torch.distributed.get_backend)
- `torch.distributed.get_rank()`: Return the rank of the current process in the provided `group`, default otherwise.  [reference](https://pytorch.org/docs/stable/distributed.html#torch.distributed.get_rank)
- `torch.distributed.get_world_size()`: Return the number of processes in the current process group.  [reference](https://pytorch.org/docs/stable/distributed.html#torch.distributed.get_world_size)
- `torch.distributed.all_gather()`: Gathers **tensors** from the whole group in a list.  [reference](https://pytorch.org/docs/stable/distributed.html#torch.distributed.all_gather)
	- The `all_gather()` function allows you to gather data from all processes, regardless of whether you are in *training or inference mode*.
	- Note that the `all_gather()` function **uses the `"gloo"` backend by default**, which is a **CPU-based backend**.
	- keep in mind that the `all_gather()` function assumes that the `data` being gathered is the **same size across all processes**. If the data sizes differ, you may need to handle that separately.
- `torch.distributed.all_gather_into_tensor()`: Gather tensors from all ranks and put them in a single output tensor.
	- The `"gloo"` backend **does not support** this API.
- `torch.distributed.all_gather_object()`: Gathers **picklable objects** from the whole group into a list. [reference](https://pytorch.org/docs/stable/distributed.html#torch.distributed.all_gather_object)
	- Similar to [`all_gather()`](https://pytorch.org/docs/stable/distributed.html#torch.distributed.all_gather "torch.distributed.all_gather"), but Python objects can be passed in. Note that the object must be **picklable** in order to be gathered.
	- Note that this API differs slightly from the [`all_gather()`](https://pytorch.org/docs/stable/distributed.html#torch.distributed.all_gather "torch.distributed.all_gather") collective since it does not provide an `async_op` handle and thus will be a **blocking call**.
	- [`all_gather_object()`](https://pytorch.org/docs/stable/distributed.html#torch.distributed.all_gather_object "torch.distributed.all_gather_object") uses **`pickle` module** *implicitly*, which is known to be insecure. It is possible to construct **malicious pickle data** which will execute arbitrary code during unpickling. Only call this function with data you trust.
	- Calling [`all_gather_object()`](https://pytorch.org/docs/stable/distributed.html#torch.distributed.all_gather_object "torch.distributed.all_gather_object") with *GPU tensors* is not well supported and **inefficient** as it incurs **GPU -> CPU transfer** since tensors would be *pickled*. Please consider using [`all_gather()`](https://pytorch.org/docs/stable/distributed.html#torch.distributed.all_gather "torch.distributed.all_gather") instead.



-----------
##  Recommended Notes

- `torch.distributed`: distributed communication package [reference](https://pytorch.org/docs/stable/distributed.html)
	- `is_available()`: `True` if the distributed package is available. [reference](https://pytorch.org/docs/stable/distributed.html#torch.distributed.is_available)
	- `is_initialized()`: Check if the default process group has been initialized. [reference](https://pytorch.org/docs/stable/distributed.html#torch.distributed.is_initialized)
	- `new_group()`: Create a new distributed group. [reference](https://pytorch.org/docs/stable/distributed.html#torch.distributed.new_group)
	- `get_backend()`: Return the backend of the given process group. [reference](https://pytorch.org/docs/stable/distributed.html#torch.distributed.get_backend)
	- `get_rank()`: Return the rank of the current process in the provided `group`, default otherwise.  [reference](https://pytorch.org/docs/stable/distributed.html#torch.distributed.get_rank)
	- `get_world_size()`: Return the number of processes in the current process group.  [reference](https://pytorch.org/docs/stable/distributed.html#torch.distributed.get_world_size)
	- `all_gather()`: Gathers *tensors* from the *whole group* in *a list*.  [reference](https://pytorch.org/docs/stable/distributed.html#torch.distributed.all_gather)
	- `all_gather_into_tensor()`: Gather *tensors* from *all ranks* and *put them in a single output tensor*. [reference](https://pytorch.org/docs/stable/distributed.html#torch.distributed.all_gather_into_tensor)
	- `all_gather_object()`: Gathers *picklable objects* from the *whole group* into a *list*. [reference](https://pytorch.org/docs/stable/distributed.html#torch.distributed.all_gather_object)
	- `gather()`: Gathers a list of *tensors* in a *single process*. [reference](https://pytorch.org/docs/stable/distributed.html#torch.distributed.gather)
	- `gather_object()`: Gathers *picklable objects* from the whole group in a *single process*. [reference](https://pytorch.org/docs/stable/distributed.html#torch.distributed.gather_object)
	- `barrier()`: Synchronize all processes. [reference](https://pytorch.org/docs/stable/distributed.html#torch.distributed.barrier)

- [Message Passing Interface (MPI)](https://en.wikipedia.org/wiki/Message_Passing_Interface#Concepts)
- Stack Overflow: [In distributed computing, what are world size and rank?](https://stackoverflow.com/questions/58271635/in-distributed-computing-what-are-world-size-and-rank)

>[!quote]
>You can think of **`world`** as a *group* containing *all the processes for your distributed training*. Usually, each GPU corresponds to one process. Processes in the `world` can communicate with each other, which is why you can train your model distributedly and still get the correct gradient update. So **world size is the number of processes for your training**, which is usually the number of GPUs you are using for distributed training.
>
>**`Rank`** is the **unique ID given to a process**, so that other processes know how to identify a particular process. **Local rank** is the a *unique local ID* for processes running in a **single node**,

- *source code* : [Facebook research - detectron2](https://github.com/facebookresearch/detectron2/blob/main/detectron2/utils/comm.py)