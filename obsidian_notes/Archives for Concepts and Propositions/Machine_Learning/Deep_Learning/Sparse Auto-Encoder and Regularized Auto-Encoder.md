---
tags:
  - concept
  - machine_learning/models
  - deep_learning/generative_models
  - deep_learning/representation_learning
keywords:
  - autoencoder
  - representation_learning
  - sparse_autoencoder
topics:
  - representation_learning
name: Sparse Auto-Encoder
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Sparse Auto-Encoder

![[Auto-Encoder and Stochastic Auto-Encoder#^53810a]]

- [[Auto-Encoder and Stochastic Auto-Encoder]]

>[!important] Definition
>The **regularized autoencoder** learns both *encoder function* $f$ and *decoder function* $g$ that minimize the *reconstruction error* with **regularization penalty**
>$$
>\min_{f, g}\sum_{i=1}^{n}L(X_{i} , g(h(X_{i})) ) + \, \Omega\left(h\right)
>$$   
>where $L: \mathbb{R}^{d} \times \mathbb{R}^{d} \to \mathbb{R}$ is the loss function that measures the *similarity* between the *input* and the *reconstructed input*.
>
>- If $$\Omega(h) = \lambda \sum_{i}|h_{i}|$$ is a *sparsity inducing regularization* term, it is called the **sparse autoencoder.**

^e81e41

- [[LASSO and Sparsity-Induced Least Square]]
- [[Regularized Loss Minimization]]
- [[Laplace Distribution]]



## Explanation











-----------
##  Recommended Notes and References


- [[Latent Variable Models]]
- [[Variational Auto-Encoder]]
- [[Artificial Neural Network and Deep Learning]]

- [[Principle Component Analysis]]
- [[Probabilistic Principle Component Analysis]]
- [[Factor Analysis]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Deep Learning by Goodfellow]] pp 496 - 498
- [[Deep Learning Foundations and Concepts by Bishop]] pp 566 - 567