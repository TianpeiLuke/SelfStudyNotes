---
tags:
  - concept
  - machine_learning/algorithms
  - deep_learning/algorithms
  - deep_learning/regularization
keywords:
  - residual_connection
  - residual_network
topics:
  - deep_learning/network_block
  - deep_learning/discriminative_models
name: Residual Connection for Deep Learning
date of note: 2024-08-16
---

## Concept Definition

>[!important]
>**Name**: Residual Connection for Deep Learning

### Vanishing Gradients and Exploding Gradients





![[residual_connections.png]]

## Explanation

>[!quote]
>If we stack a *large number* of nonlinear layers together, the signal may get *squashed* to zero or may *blow up to infinity*, depending on the magnitude of the weights, and the nature of the nonlinearities. Similar problems can plague *gradients* that are passed backwards through the network (see Section 6.2).
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 626





-----------
##  Recommended Notes and References


- [[Residual Neural Network]]


- [[Deep Learning by Goodfellow]] pp 368
- [[Deep Learning Foundations and Concepts by Bishop]] pp 274 - 277
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 626
- Torralba, A., Isola, P., & Freeman, W. T. (2024). _Foundations of Computer Vision_. The MIT Press.