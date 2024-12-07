---
tags:
  - excerpt
  - documentation
  - code_package
  - aws/sagemaker
aliases: 
keywords: 
topics:
  - code/doc
language: python
date of note: 2024-03-31
name: Amazon Developer Guide
version: 
year: 2024
---

##  Overview

>[!info]
>**The SageMaker distributed data parallelism (SMDDP) library** is a collective communication library that improves compute performance of distributed data parallel training. The SMDDP library addresses *communications overhead* of the key collective communication operations by offering the following.
> 
> 1. The library offers **`AllReduce`** *optimized for AWS*. `AllReduce` is a *key operation* used for **synchronizing gradients across GPUs** at the *end of each training iteration* during distributed data training.
>     
> 2. The library offers **`AllGather`** optimized for AWS. `AllGather` is another *key operation* used in **sharded data parallel training**, which is a *memory-efficient data parallelism technique* offered by popular libraries such as the **SageMaker model parallelism (SMP) library**, **DeepSpeed Zero Redundancy Optimizer (ZeRO)**, and **PyTorch Fully Sharded Data Parallelism (FSDP)**.
>     
> 3. The library performs optimized *node-to-node communication* by fully utilizing AWS network infrastructure and the Amazon EC2 instance topology.
>     
> The SMDDP library can **increase training speed** by offering performance improvement as you scale your training cluster, with near-linear scaling efficiency.
> -- [link](https://docs.aws.amazon.com/sagemaker/latest/dg/data-parallel-intro.html)

- *The SageMaker distributed training libraries* are available through the *AWS deep learning containers* for **PyTorch** and **Hugging Face** within the SageMaker Training platform.


## SMDDP collective communication operations

- The SMDDP library provides implementations of the `AllReduce` and `AllGather` collective operations that are optimized for AWS compute resources and network infrastructure.
- SMDDP `AllReduce` and SMDDP `AllGather` are **not mutually compatible** at present.

>[!important]
>- **Data Parallelism**: `AllReduce` collective operation.
>- **Model/Layer Parallelism**: `AllGather` collective operation.

### SMDDP `AllReduce` collective operation

- The SMDDP library achieves *optimal overlapping* of the `AllReduce` operation with the **backward pass**, significantly improving *GPU utilization*. It achieves near-linear scaling efficiency and faster training speed by *optimizing kernel operations between CPUs and GPUs*.

>[!important]
>The library performs `AllReduce` **in parallel** while **GPU is computing gradients** without taking away additional GPU cycles, which makes the library to achieve faster training.
> - *Leverages CPUs*: The library uses **CPUs** to **`AllReduce` gradients**, *offloading* this task from the GPUs.
>     
> - *Improved GPU usage*: The cluster’s **GPUs** focus on **computing gradients**, *improving their utilization* throughout training.


>[!info]
>The following is the high-level workflow of the SMDDP `AllReduce` operation.
> 
> 1. The library assigns **ranks** to *GPUs* (**workers**).
>     
> 2. At *each iteration*, the library **divides** each *global batch* by the *total number of workers* (**world size**) and assigns *small batches* (**batch shards**) to the *workers*.
>     
>     - The **size** of *the global batch* is `(number of nodes in a cluster) * (number of GPUs per node) * (per batch shard)`.
>         
>     - A **batch shard** (*small batch*) is a *subset of dataset* assigned to *each GPU (worker) per iteration*.
>         
>     
> 3. The library launches a *training script* on **each worker**.
>     
> 4. The library manages **copies** of **model weights** and **gradients** from the *workers* at *the end of every iteration*.
>     
> 5. The library **synchronizes** *model weights and gradients* across the workers to **aggregate** a single trained model.

The following architecture diagram shows an example of how the library sets up data parallelism for a cluster of 3 nodes.
![[amazon_sagemaker_sdp-architecture.png]]

### SMDDP `AllGather` collective operation

- `AllGather` is a collective operation where each worker starts with *an input buffer*, and then **concatenates** or **gathers** *the input buffers* from all other workers into *an output buffer*.

>[!important]
>- `AllGather` is heavily used in distributed training techniques such as **sharded data parallelism** where each individual worker holds **a fraction of a model**, or a **sharded layer**. 
>- The workers call `AllGather` *before* **forward** and **backward passes** to *reconstruct the sharded layers*. 
>- The *forward* and *backward passes* continue onward *after the parameters are* **all gathered**. 
>	- During the *backward pass*, each worker also calls `ReduceScatter` to **collect (reduce) gradients** and **break (scatter) them into gradient shards** to update the corresponding sharded layer. 
>	- For more details on the role of these collective operations in sharded data parallelism, see the [SMP library's implementati on of sharded data parallelism](https://docs.aws.amazon.com/sagemaker/latest/dg/model-parallel-extended-features-pytorch-sharded-data-parallelism.html), [ZeRO](https://deepspeed.readthedocs.io/en/latest/zero3.html#) in the DeepSpeed documentation, and the blog about [PyTorch Fully Sharded Data Parallelism](https://engineering.fb.com/2021/07/15/open-source/fsdp/).

- Because *collective operations* like `AllGather` are called in *every iteration*, they are the *main contributors* to *GPU communication overhead*. Faster computation of these collective operations directly translates to a shorter training time with no side effects on convergence. 
- To achieve this, the SMDDP library offers `AllGather` optimized for [P4d instances](https://aws.amazon.com/ec2/instance-types/p4/).


-----------
##  Recommended Notes

- [[Amazon SageMaker Python SDK 3.1.1 Pytorch Train]]
- [[Amazon SageMaker Python SDK 3.1.4 Pytorch Lightning]]




----------
##  Citations

- [SageMaker distributed data parallelism library](https://docs.aws.amazon.com/sagemaker/latest/dg/data-parallel-intro.html)
- *code source*:
- *code package link*




