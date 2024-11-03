---
tags:
  - concept
  - probabilistic_graphical_models/theory
  - statistics/inference
  - math/probability
  - machine_learning/theory
  - deep_learning/models
  - math/information_geometry
keywords:
  - score_log_likelihood
topics:
  - information_geometry
  - machine_learning_theory
  - deep_learning/models
  - statistics/inference
  - probabilistic_graphical_model
name: Log-Likelihood Score Function
date of note: 2024-06-24
---

## Concept Definition

>[!important]
>**Name**: Log-Likelihood Score Function

![[Likelihood Function#^f6d78c]]

>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a *$\sigma$-finite measure space*.  
>
>Denote $\mathcal{F}_{\Theta}$ as a *parametric family* of probability density functions (p.d.f.) with respect to a common dominating measure $\mu$, i.e.,
>$$
>\mathcal{F}_{\Theta} := \left\{ p(x; \theta) := \frac{d\mathcal{P}_{\theta}}{d\mu} \in L^1(\mathcal{X}, \mu): \theta \in \Theta \subset \mathbb{R}^{d} \right\}. 
>$$
>Let $\ell(\theta; x) = \log p(x; \theta)$ be the *log-likelihood function* of $\theta$ given sample $x\in \mathcal{X}$. 
>
>The **score function** *of parameter* $\theta$ is the *gradient of log-likelihood function* with respect to $\theta$
>$$
>s(\theta) := \nabla_{\theta} \ell(\theta; x) = \left[ \frac{ \partial  }{ \partial \theta^{1} }\log p(x; \theta) \,{,}\ldots{,}\, \frac{\partial}{ \partial \theta^{n} }\log p(x; \theta) \right] 
>$$

- [[Likelihood Function]]

## Explanation

![[Score Matching and Denoising Score Matching#^b18499]]

- [[Score Matching and Denoising Score Matching]]

## Score of Exponential Family

![[Exponential Family of Distributions#^c95a01]]

- [[Exponential Family of Distributions]]
- [[Log-Partition Function of Exponential Family]]


-----------
##  Recommended Notes and References


- [[Riemannian Metric and Riemannian Manifold]]
- [[Inner Product Space]]

- [[Tangent Vector and Differential via Velocity of Smooth Curves]]
- [[Concepts related to Tangent Space and Tangent Bundle]]


- [[Methods of Information Geometry by Amari]] pp 26 - 27
- [[All of Statistics A Concise Course by Wasserman]]
- [[Elements of Information Theory by Cover]]
