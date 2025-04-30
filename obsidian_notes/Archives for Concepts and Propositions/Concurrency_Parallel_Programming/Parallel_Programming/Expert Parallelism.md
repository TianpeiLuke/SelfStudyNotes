---
tags:
  - concept
  - parallel_computing/principles
  - expert_parallelism
keywords:
  - expert_parallelism
topics:
  - parallel_computation
name: Expert Parallelism
date of note: 2025-03-16
---

## Concept Definition

>[!important]
>**Name**: Expert Parallelism

>[!important] Definition
>**Expert Parallelism** is the distributed-training strategy used for large **Mixture-of-Experts (MoE)** networks.
>- Instead of splitting every layer’s weight matrix across GPUs (*tensor/parameter parallelism*) or splitting a batch of tokens across GPUs (*data parallelism*), expert parallelism assigns _entire experts_—independent feed-forward sub-networks inside an MoE layer—to *different devices*.
>- At run time a lightweight **gate** (kept replicated on every GPU) scores each token and routes it to the *top-k experts*;
>- the token’s hidden vector is sent over the network only to the *GPUs that host those experts*, processed *locally*, and the results are sent back and merged.

- [[Mixture of Experts or MoE as Deep Ensemble Learning]]


## Explanation

>[!info]
>Because *each token* touches only a *small subset of experts*, every GPU stores and executes a fraction of the model’s total parameters while the _logical_ model capacity grows *linearly* with the *number of experts/devices*. 
>- This yields dramatic *parameter-scale-to-compute ratios* (e.g., hundreds of billions of parameters trained with the FLOPs budget of a few billion-parameter dense model) and nearly linear memory scaling.


- [[Data Parallelism]]
- [[Model Parallelism]]

>[!info]
>Expert parallelism is thus the key technique behind models such as Google’s **Switch Transformer**, **GLaM**, and Microsoft’s **DeepSpeed-MoE**, enabling efficient training and inference of ultra-large Transformer architectures on commodity GPU clusters while maintaining high throughput and modest memory footprints.

- [[Switch Transformer via Mixture of Expert Layer]]




-----------
##  Recommended Notes and References



- [[Parallel Pretraining of Large Language Models]]
- [[Large Language Model and Pretrained Language Models]]
- [[The Art of Multiprocessor Programming by Herlihy]]
- Blog
	- [paradigms_of_parallelism](https://colossalai.org/docs/concepts/paradigms_of_parallelism/)
	- [A Brief Overview of Parallelism Strategies in Deep Learning](https://afmck.in/posts/2023-02-26-parallelism/)
	- [Top Parallelism Techniques to Enhance LLM Training & Deployment](https://www.genesiscloud.com/blog/top-parallelism-techniques-llm-training)
	- [Parallel Training LLM Slides](https://saforem2.github.io/parallel-training-slides/#/title-slide)