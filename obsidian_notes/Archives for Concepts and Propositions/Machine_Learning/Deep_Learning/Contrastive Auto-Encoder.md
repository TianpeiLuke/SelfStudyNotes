---
tags:
  - concept
  - machine_learning/models
  - deep_learning/generative_models
  - deep_learning/representation_learning
keywords:
  - autoencoder
  - representation_learning
  - contrastive_autoencoder
topics:
  - representation_learning
name: Contrastive Auto-Encoder
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Contrastive Auto-Encoder

![[Auto-Encoder and Stochastic Auto-Encoder#^53810a]]

- [[Auto-Encoder and Stochastic Auto-Encoder]]

![[Sparse Auto-Encoder and Regularized Auto-Encoder#^e81e41]]

- [[Sparse Auto-Encoder and Regularized Auto-Encoder]]
- [[Regularized Loss Minimization]]

>[!important] Definition
>The **contrastive autoencoder (CAE)** learns both *encoder function* $f$ and *decoder function* $g$ that minimize the *reconstruction error* with **regularization penalty** on the **derivative** of *hidden units*
>$$
>\min_{f, g}\sum_{i=1}^{n}L(X_{i} , g(h(X_{i})) ) + \lambda\,\sum_{i}\lVert \nabla_{x} h_{i}\rVert^2 
>$$   
>where 
>- $L: \mathbb{R}^{d} \times \mathbb{R}^{d} \to \mathbb{R}$ is the loss function that measures the *similarity* between the *input* and the *reconstructed input*.



## Explanation











-----------
##  Recommended Notes and References


- [[Latent Variable Models]]
- [[Contrastive Learning]]

- [[Artificial Neural Network and Deep Learning]]



- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Deep Learning by Goodfellow]] pp 496 - 498
- [[Deep Learning Foundations and Concepts by Bishop]] pp 563 - 567