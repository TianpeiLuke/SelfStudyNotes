---
tags:
  - concept
  - math/information_theory
  - deep_learning/generative_models
keywords:
  - fisher_metric
  - fisher_information
  - fisher_divergence
  - score_matching
topics:
  - information_theory
  - deep_learning/generative_models
name: Fisher Divergence
date of note: 2024-09-08
---

## Concept Definition

>[!important]
>**Name**: Fisher Divergence

>[!important] Definition
>Let $(\Omega, \mathscr{F},\mu)$ be a $\sigma$-finite measure space and $p, q$ be two *smooth probability density functions* with respect to $\mu$.
>
>The **Fisher divergence** between $p$ and $q$ is defined as 
>$$
>\mathbb{D}_{F}\left( p \left\|\right. q \right) = \mathbb{E}_{ p }\left[  \lVert \nabla \log p(X) - \nabla \log q (X) \rVert_{2}^2  \right] 
>$$
>where $$\nabla \log p(X), \quad \nabla \log q(x)$$ is the **score function** of $p(x)$ and $q(x)$.

- [[Probability Density Function of Random Variable]]
- [[Lp Space]]


## Explanation


### Score Matching

![[Score Matching and Denoising Score Matching#^6a12a8]]

- [[Denoising Diffusion Probabilistic Models and Diffusion Network]]
- [[Score Matching and Denoising Score Matching]]


## Wasserstein Distance

- [[Wasserstein Distance]]



-----------
##  Recommended Notes and References



- [[Kullback-Leibler Divergence]]
- [[Divergence Function on Manifold]]
- [[Measure Space and Countably Additive Measure]]
- [[Probability Space]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 846
- Yang, Y., Martin, R., & Bondell, H. (2019). Variational approximations using Fisher divergence. _arXiv preprint arXiv:1905.05284_.