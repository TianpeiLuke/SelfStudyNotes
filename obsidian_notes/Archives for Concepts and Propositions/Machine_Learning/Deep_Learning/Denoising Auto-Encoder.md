---
tags:
  - concept
  - machine_learning/models
  - deep_learning/generative_models
  - deep_learning/representation_learning
keywords:
  - autoencoder
  - representation_learning
  - denoising_autoencoder
topics:
  - representation_learning
name: Denoising Auto-Encoder
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Denoising Auto-Encoder

![[Auto-Encoder and Stochastic Auto-Encoder#^53810a]]

- [[Auto-Encoder and Stochastic Auto-Encoder]]

>[!important] Definition
>Let $X_{i}$ be $n$ i.i.d samples from unknown distribution and $\widetilde{X}_{i}$ be a copy of $X_{i}$ that has been **corrupted** by some *noise*. $$\widetilde{X}_{i} \sim K(X_{i}, \widetilde{X}_{i})$$
>
>The **denoising autoencoder (DAE)** learns both *encoder function* $f$ and *decoder function* $g$ that minimize the *reconstruction error* between 
>$$
>\min_{f, g}\sum_{i=1}^{n}L(X_{i} , g(h(\widetilde{X}_{i})) ) 
>$$   
>where $L: \mathbb{R}^{d} \times \mathbb{R}^{d} \to \mathbb{R}$ is the loss function that measures the *similarity* between the *input* and the *reconstructed input* from *corrupted copy*.

^e81e41

- [[Auto-Encoder and Stochastic Auto-Encoder]]
- [[Markov Transition Kernel and Transition Function]]


## Explanation



## Stochastic Autoencoder

- [[Auto-Encoder and Stochastic Auto-Encoder#Stochastic Auto-Encoder]]







-----------
##  Recommended Notes and References


- [[Latent Variable Models]]
- [[Artificial Neural Network and Deep Learning]]

- [[Principle Component Analysis]]
- [[Probabilistic Principle Component Analysis]]
- [[Factor Analysis]]

- [[Denoising Diffusion Probabilistic Models]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Deep Learning by Goodfellow]] pp 496 - 498, 501 - 505 
- [[Deep Learning Foundations and Concepts by Bishop]] pp 563 - 567