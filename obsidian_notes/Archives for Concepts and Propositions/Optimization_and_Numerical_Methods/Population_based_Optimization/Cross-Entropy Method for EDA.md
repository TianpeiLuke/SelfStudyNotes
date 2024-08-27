---
tags:
  - concept
  - optimization/theory
  - genetic_algorithm
  - evolutionary_algorithm
  - evolutionary_computation
keywords:
  - cross_entropy_method
  - eda_algorithm
  - estimation_of_distribution_algorithm
topics:
  - evolutionary_algorithm
name: Cross-Entropy Method for EDA
date of note: 2024-08-24
---

## Concept Definition

>[!important]
>**Name**: Cross-Entropy Method for EDA

![[EDA or Estimation of Distribution Algorithm#^ad5721]]

>[!important] Definition
>The **cross-entropy method (CEM)** is a special case of **EDA** where the population is represented by a *multivariate Gaussian*. 
>
>- In particular, we estimate $\mu_{t+1}, \Sigma_{t+1}$ bases on *selected top $K$ fittest samples* $\mathcal{S}_{t}^{(s)}$
>- This is closely related to **sequential monte carlo (SMC)** methods [[Sequential Importance Sampling]]

- [[EDA or Estimation of Distribution Algorithm]]
- [[Gaussian Random Vector]]
- [[Gaussian Graphical Model]]
- [[Gaussian Bayesian Network]]

## Explanation

>[!quote]
>The *CEM* is sometimes used for **model-based RL** (Section 35.4), since it is simple and can find reasonably good optima of multimodal objectives. It is also sometimes used inside of **Bayesian optimization** (Section 6.6), to optimize the multi-modal acquisition function.
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 306

- [[Model-based Reinforcement Learning]]



-----------
##  Recommended Notes and References


- [[Differentiable Cross-Entropy Method]]
- [[Cross-Entropy Loss Function]]
- [[EDA or Estimation of Distribution Algorithm]]

- [[Evolutionary Algorithms]]
- [[Derivative-Free Optimization]]

- [[REINFORCE Algorithm with Baseline]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 298 - 307
- [[Introduction to Evolutionary Computing by Eiben]]