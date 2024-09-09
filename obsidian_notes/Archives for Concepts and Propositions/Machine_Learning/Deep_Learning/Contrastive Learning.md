---
tags:
  - concept
  - machine_learning/strategy
  - deep_learning/representation_learning
keywords:
  - contrastive_learning
  - representation_learning
topics:
  - machine_learning_strategy
  - representation_learning
name: Contrastive Learning
date of note: 2024-07-07
---

## Concept Definition

>[!important]
>**Name**: Contrastive Learning



## Explanation

>[!quote]
>One of the most common and powerful representation learning methods is **contrastive learning** (Gutmann and Hyva ̈rinen, 2010; Oord, Li, and Vinyals, 2018; Chen, Kornblith, et al., 2020). The idea is to learn a *representation* such that certain *pairs of inputs*, referred to as **positive pairs**, are *close* in the embedding space, and *other pairs of inputs*, called **negative pairs**, are *far apart*. The intuition is that if we choose our positive pairs in such a way that they are *semantically similar* and choose negative pairs that are *semantically dissimilar*, then we will learn a representation space in which similar inputs are close, making downstream tasks, such as classification, much easier.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 191

>[!quote]
>Contrastive learning is unlike most other machine learning tasks, in that the **error function** for a given input is defined only **with respect to other inputs**, instead of having a per-input label or target output.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 191


## Examples

- [[Information Noise Contrastive Estimation as Contrastive Learning]]




-----------
##  Recommended Notes and References


- [[Noise Contrastive Estimation]]
- [[Auto-Encoder and Stochastic Auto-Encoder]]
- [[Artificial Neural Network and Deep Learning]]



- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1054 - 1055
- [[Deep Learning Foundations and Concepts by Bishop]] pp 191
