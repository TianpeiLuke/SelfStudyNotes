---
tags:
  - concept
  - parallel_computing/principles
  - deep_learning/large_language_models
  - natural_language_processing/large_language_models
  - fully_sharded_data_parallelism
keywords:
  - fully_sharded_data_parallel
topics:
  - parallel_computation
  - deep_learning/large_language_models
name: Fully Sharded Data Parallel or FSDP for LLM Training
date of note: 2024-12-14
---

## Concept Definition

>[!important]
>**Name**: Fully Sharded Data Parallel or FSDP for LLM Training



- [[Data Parallelism]]
- [[MapReduce Architecture for Data Parallelism]]

## Explanation

### Compare with Model Parallelism

>[!question]
>Is Fully Sharded Data Parallel (FSDP) model parallelism?

- **No**, **FSDP is not model parallelism** — it is **data parallelism with full parameter sharding**.
- [[Model Parallelism]]

>[!question]
>What FSDP _is_:

>[!important]
> **FSDP** is a **data parallel** training strategy that:
> 
> - **Shards model parameters, gradients, and optimizer states** across devices (typically GPUs).
> - Each GPU only holds _a portion_ of the model's weights at any time.
> - Parameters are gathered just-in-time for forward and backward passes.
> - *Reduces memory footprint*, enabling training of larger models.


#### How it's different from Model Parallelism

| Feature                       | FSDP (Data Parallel + Sharding)           | Model Parallelism                            |
| ----------------------------- | ----------------------------------------- | -------------------------------------------- |
| **Model copy on each device** | Yes, but **sharded**                      | No — model is **split** across devices       |
| **Memory savings**            | Yes, via **sharding**                     | Yes, via **slicing model computation**       |
| **Communication pattern**     | All-reduce on **gradients**, gather/shard | *Inter-device* activation passing            |
| Use case                      | Training large models efficiently         | *Fitting* extremely large models across GPUs |
| Example framework             | **PyTorch FSDP**                          | Megatron-LM, **DeepSpeed ZeRO-3 (with MP)**  |

### Compare with DeepSpeed

| Feature / Aspect                            | **FSDP** (PyTorch Native)              | **DeepSpeed** (ZeRO Optimizer)                   |
| ------------------------------------------- | -------------------------------------- | ------------------------------------------------ |
| **Developed By**                            | PyTorch (Meta / Facebook AI)           | Microsoft AI                                     |
| **Parallelism Type**                        | Fully Sharded Data Parallel (FSDP)     | ZeRO: Sharded Optimizer/Gradients/Model States   |
| **ZeRO Stages Equivalent**                  | ~Stage 3                               | Stage 1–3 (configurable granularity)             |
| **Model Weights Sharded?**                  | ✅ Yes                                  | ❌ Stage 1/2  <br>✅ Stage 3                       |
| **Gradients Sharded?**                      | ✅ Yes                                  | ✅ Stage 2/3                                      |
| **Optimizer States Sharded?**               | ✅ Yes                                  | ✅ Stage 1/2/3                                    |
| **Communication Overhead**                  | Higher (more all-gathers)              | Lower for Stage 1/2  <br>Higher for Stage 3      |
| **Checkpointing**                           | Sharded checkpoints                    | Sharded + optional CPU offloaded checkpoints     |
| **Memory Efficiency**                       | Excellent                              | Stage 2/3 = Very Good  <br>Stage 1 = Moderate    |
| **Offload Support (CPU/NVMe)**              | ❌ Not native                           | ✅ Stage 2+ (gradient/optimizer/model offloading) |
| **Integration in HuggingFace / HF Trainer** | ✅ Built-in via `fsdp` arg              | ✅ Full support via `deepspeed_config.json`       |
| **Custom Schedule/Optimizer Support**       | ✅ PyTorch native                       | ✅ via DeepSpeed engine                           |
| **Inference Support**                       | ✅ (as of PyTorch 2.x)                  | ✅ (with `deepspeed-inference`)                   |
| **Ease of Use**                             | Native PyTorch, better with Lightning  | Extra config file (`ds_config.json`) needed      |
| **Activation Checkpointing**                | ✅ Supported                            | ✅ Supported                                      |
| **Auto Mixed Precision (AMP)**              | ✅ Native AMP / bf16 / fp16             | ✅ AMP + optimizer offloading                     |
| **Offloading to CPU/NVMe**                  | ❌ No                                   | ✅ Yes (Stage 2+)                                 |
| **Zero Redundancy in Weights**              | ✅ Yes (shards weights too)             | ❌ Stage 1/2  <br>✅ Stage 3 only                  |
| **Deployment Complexity**                   | Moderate (PyTorch config + wrapping)   | Higher (requires engine, launcher, config file)  |
| **Multi-node Training**                     | ✅ Yes (via `torchrun` / DDP launchers) | ✅ Yes (via DeepSpeed launcher)                   |
| **Performance on Large Models**             | Excellent                              | Excellent, especially with offloading            |




-----------
##  Recommended Notes and References


- [[Parallel Pretraining of Large Language Models]]
- [[Large Language Model and Pretrained Language Models]]
- [[The Art of Multiprocessor Programming by Herlihy]]


- Example
	- [[Trainer for FSDP Model Parallelism]]
	- [[Inference for FSDP Model Parallelism]]
	- [[Multi-modal BERT for FSDP Model Parallelism]]
	- [[Export to ONNX and Inference]]

- [[Pipeline Parallelism]]
- [[Tensor Parallelism]]

- Blog
	- [paradigms_of_parallelism](https://colossalai.org/docs/concepts/paradigms_of_parallelism/)
	- [A Brief Overview of Parallelism Strategies in Deep Learning](https://afmck.in/posts/2023-02-26-parallelism/)
	- [Distributed Parallel Training: Data Parallelism and Model Parallelism](https://towardsdatascience.com/distributed-parallel-training-data-parallelism-and-model-parallelism-ec2d234e3214)
	- [Introducing PyTorch Fully Sharded Data Parallel (FSDP) API](https://pytorch.org/blog/introducing-pytorch-fully-sharded-data-parallel-api/)
	- [PyTorch Lightning vs DeepSpeed vs FSDP vs FFCV vs …](https://medium.com/data-science/pytorch-lightning-vs-deepspeed-vs-fsdp-vs-ffcv-vs-e0d6b2a95719)