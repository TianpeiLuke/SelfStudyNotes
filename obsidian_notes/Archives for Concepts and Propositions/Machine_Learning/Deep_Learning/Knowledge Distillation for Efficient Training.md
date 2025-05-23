---
tags:
  - concept
  - deep_learning/large_language_models
  - natural_language_processing/large_language_models
  - knowledge_distillation
  - fine_tuning
  - Pre-training
keywords:
  - knowledge_distillation
topics:
  - deep_learning/large_language_models
name: Knowledge Distillation for Efficient Training
date of note: 2024-11-26
---

## Concept Definition

>[!important]
>**Name**: Knowledge Distillation for Efficient Training

>[!important] Definition
>**Knowledge Distillation** in the context of LLMs (Large Language Models) and MLMs (Masked Language Models) refers to the process of *transferring the knowledge* learned by a large, complex **teacher model** into a smaller, more efficient **student model**. 


>[!important]
>During **distillation**, the student is trained not just on the 
>- *original ground-truth labels*, 
>- but also to *match the soft predictions* (e.g., output logits, probability distributions) generated by the teacher, 
>
>thereby capturing richer information about inter-class relationships and model confidence. 

- [[Large Language Model and Pretrained Language Models]]

## Explanation


>[!info]
>This technique enables the student to *approximate the teacher’s behavior* while significantly *reducing* 
>- *computational cost*, 
>- *memory footprint*, 
>- and *inference latency,* 
>
>making it suitable for deployment in resource-constrained environments. 
>
>In LLMs and MLMs, distillation can also involve transferring
>- *representations*, 
>- *attention patterns*, 
>- or *masked token predictions*, 
>
>and it plays a critical role in scaling down large pre-trained models for practical use cases without heavily sacrificing performance.




-----------
##  Recommended Notes and References

- [[Supervised Fine-Tuning or Instruction Fine-Tuning of LLM]]
