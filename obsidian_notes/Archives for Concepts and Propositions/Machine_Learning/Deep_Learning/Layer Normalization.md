---
tags:
  - concept
  - machine_learning/algorithms
  - deep_learning/algorithms
  - deep_learning/regularization
keywords:
  - layer_normalization
topics:
  - deep_learning/algorithm
  - deep_learning/regularization
name: Layer Normalization
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Layer Normalization




- [[Batch Normalization]]




## Explanation

>[!quote]
>With *batch normalization*, if the **batch size** is too small then the estimates of the mean and variance become too *noisy*. Also, for very *large training sets*, the mini-batches may be **split across different GPUs**, making global normalization across the mini-batch *inefficient*. An alternative to normalizing across examples within a mini-batch for each hidden unit *separately* is to **normalize across the hidden-unit values** for *each data point separately*. This is known as **layer normalization** (Ba, Kiros, and Hinton, 2016). It was introduced in the context of recurrent neural networks where the distributions change after each time step making batch normalization infeasible. However, it is useful in other architectures such as transformer networks.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 229




-----------
##  Recommended Notes and References

- [[Batch Normalization]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 627
- [[Deep Learning Foundations and Concepts by Bishop]] pp 229