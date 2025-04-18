---
tags:
  - concept
  - parallel_computing/principles
  - deep_learning/large_language_models
  - pipeline_parallelism
keywords:
  - tensor_parallelism
  - pipeline_parallelism
  - model_parallelism
topics:
  - deep_learning/large_language_models
  - parallel_computation
name: Pipeline Parallelism for Efficient Large-Parameter Model Training
date of note: 2024-12-14
---

## Concept Definition

>[!important]
>**Name**: Pipeline Parallelism for Efficient Large-Parameter Model Training

>[!important] Definition
>**Pipeline Parallelism** is a type of **model parallelism** where a *model is split by layers* across multiple devices (e.g., GPUs), and *different microbatches* are processed in parallel across those devices like an assembly line (i.e., a pipeline).

- [[Model Parallelism]]


## Explanation

>[!info]
>- **How it works**: Partitions the **model’s layers** into sequential stages. Each stage runs on a separate GPU, and inputs are divided into **microbatches** to keep the pipeline full.
>     
> - **Used in**: GPipe, DeepSpeed pipeline engine, FairScale
>     
> - **Pros**:
>     
>     - Simple to implement
>         
>     - Great for deep models
>         
> - **Cons**:
>     
>     - Idle time at the beginning (pipeline "bubble")
>         
>     - Less flexible for shallow or very wide models


### Compare with Tensor Parallelism

- [[Tensor Parallelism]]

| Feature                 | **Tensor Parallelism**                              | **Pipeline Parallelism**                             |
| ----------------------- | --------------------------------------------------- | ---------------------------------------------------- |
| **What it splits**      | **Single layer** operations (e.g., matrix multiply) | **Entire layers** across devices                     |
| **Granularity**         | Fine-grained (**within-layer**)                     | Coarse-grained (**layer-wise**)                      |
| Typical use case        | Huge layers (e.g., GPT attention, MLPs)             | Deep networks with many layers                       |
| **Communication**       | *Very frequent* (during every operation)            | Only at boundaries *between pipeline stages*         |
| **Scheduling** required | **No** (layers are distributed *statically*)        | **Yes** (*micro-batching* and *pipelining* required) |
| **GPU utilization**     | High, when combined with other parallelism          | High, after warmup (some bubbles in early batches)   |
| Works best with         | Data + pipeline parallelism                         | **Tensor** + **data parallelism**                    |
| **Memory efficiency**   | Reduces *layer memory* footprint                    | Reduces memory per-device by *offloading* layer sets |
| **Failure scope**       | A tensor op failure can block *entire step*         | Stage failure affects *only local stage*             |
| Example                 | GPT-3's *attention head split across GPUs*          | BERT layers 0–3 on GPU0, 4–7 on GPU1, etc.           |




-----------
##  Recommended Notes and References


- [[Fully Sharded Data Parallel or FSDP for LLM Training]]
- [[Data Parallelism]]


- [[Parallel Pretraining of Large Language Models]]
- [[Large Language Model and Pretrained Language Models]]
- [[The Art of Multiprocessor Programming by Herlihy]]
- Blog
	- [paradigms_of_parallelism](https://colossalai.org/docs/concepts/paradigms_of_parallelism/)
	- [A Brief Overview of Parallelism Strategies in Deep Learning](https://afmck.in/posts/2023-02-26-parallelism/)
	- [Top Parallelism Techniques to Enhance LLM Training & Deployment](https://www.genesiscloud.com/blog/top-parallelism-techniques-llm-training)
	- [Parallel Training Techniques](https://github.com/saforem2/parallel-training-slides#parallel-training-techniques) [Slides](https://saforem2.github.io/parallel-training-slides/#/title-slide)