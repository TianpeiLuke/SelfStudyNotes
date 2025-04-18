---
tags:
  - concept
  - parallel_computing/principles
  - deep_learning/large_language_models
  - tensor_parallelism
  - model_parallelism
keywords:
  - tensor_parallelism
  - model_parallelism
topics:
  - deep_learning/large_language_models
  - parallel_computation
name: Tensor Parallelism
date of note: 2025-03-16
---

## Concept Definition

>[!important]
>**Name**: Tensor Parallelism for Training Large-Scale Parameteric Models

>[!important] Definition
>**Tensor Parallelism** is a type of **model parallelism** where *individual tensor operations* (like matrix multiplication) are *split across multiple devices* (e.g., GPUs). 
>- Instead of assigning different layers to different GPUs (as in pipeline parallelism), tensor parallelism splits the computation *within a single layer*.

- [[Pipeline Parallelism]]

## Explanation

>[!info]
>- **How it works**: Breaks down **mathematical operations** inside a layer. For instance, a linear layer with shape `[B, D] × [D, H]` could be split across GPUs along the `H` dimension.
>     
> - **Used in**: Megatron-LM, DeepSpeed, GPT-NeoX
>     
> - **Pros**:
>     
>     - Fine-grained control for extremely large layers
>         
>     - High throughput when optimized
>         
> - **Cons**:
>     
>     - Requires **tight synchronization**
>         
>     - Complex communication (e.g., AllReduce, AllGather)


- [[Data Parallelism]]
- [[Model Parallelism]]

### Compare with Pipeline Parallelism

- [[Pipeline Parallelism]]

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

- [[Parallel Pretraining of Large Language Models]]
- [[Large Language Model and Pretrained Language Models]]
- [[The Art of Multiprocessor Programming by Herlihy]]
- Blog
	- [paradigms_of_parallelism](https://colossalai.org/docs/concepts/paradigms_of_parallelism/)
	- [A Brief Overview of Parallelism Strategies in Deep Learning](https://afmck.in/posts/2023-02-26-parallelism/)
	- [Top Parallelism Techniques to Enhance LLM Training & Deployment](https://www.genesiscloud.com/blog/top-parallelism-techniques-llm-training)
	- [Parallel Training Techniques](https://github.com/saforem2/parallel-training-slides#parallel-training-techniques) [Slides](https://saforem2.github.io/parallel-training-slides/#/title-slide)