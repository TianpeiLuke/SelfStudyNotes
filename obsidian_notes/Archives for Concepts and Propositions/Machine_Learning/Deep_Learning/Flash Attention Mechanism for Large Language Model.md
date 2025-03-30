---
tags:
  - concept
  - deep_learning/architecture
  - deep_learning/large_language_models
  - deep_learning/models
  - deep_learning/algorithms
  - deep_learning/hardware_acceleration
keywords:
  - flash_attention
  - large_language_models
topics:
  - deep_learning/algorithm
  - deep_learning/acceleration
  - deep_learning/large_language_models
name: Flash Attention Mechanism for Large Language Model
date of note: 2024-10-21
---

## Concept Definition

>[!important]
>**Name**: Flash Attention Mechanism for Large Language Model




![[flash_attention.png]]

![[flash_attention_gpu_model.png]]

![[flash_attention_bottleneck.png]]

### Reduce HBM Reads and Writes as Computing by Blocks

- Challenge
	- compute *softmax reduction* without access to full input
	- *backward* without the large attention matrix from forward

- [[Attention Mechanism in Neural Network]]
- [[Back-Propagation Algorithm]]

#### Tiling

>[!important] Definition
>**Tiling** is a restructure algorithm to *load block* by block from *HBM* to *SRAM* to compute attention.

![[flash_atten_tiling.png]]

#### Recomputation

>[!important] Definition
>In **recomputation**, we do not store *attention matrix* from *forward*, *recompute* it in the *backward*

![[flash_atten_recompute.png]]




## Explanation





-----------
##  Recommended Notes and References


- [[Attention Mechanism in Neural Network]]
- [[Transformer Network]]

- [[daoFlashAttentionFastMemoryEfficient2022]]
- [[touvronLlamaOpenFoundation2023]]

- Youtube
	- [FlashAttention: Fast and Memory-Efficient Exact Attention with IO-Awareness | Tri Dao](https://www.youtube.com/watch?v=FThvfkXWqtE)
	- [FlashAttention - Tri Dao | Stanford MLSys #67](https://www.youtube.com/watch?v=gMOAud7hZg4)
- Medium
	- [From Costly Attention to FlashAttention: A Deep Dive into Transformer Efficiency](https://generativeai.pub/from-costly-attention-to-flashattention-a-deep-dive-into-transformer-efficiency-62a7bcbf43d6)