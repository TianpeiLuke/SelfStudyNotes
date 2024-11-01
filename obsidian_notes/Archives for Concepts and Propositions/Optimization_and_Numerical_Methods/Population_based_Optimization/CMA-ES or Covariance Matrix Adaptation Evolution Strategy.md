---
tags:
  - concept
  - optimization/theory
  - evolutionary_algorithm
  - evolutionary_computation
keywords:
  - cma_es_algorithm
  - covariance_matrix_adaptation_evolutionary_strategy
topics:
  - evolutionary_algorithm
name: CMA-ES or Covariance Matrix Adaptation Evolution Strategy
date of note: 2024-08-24
---

## Concept Definition

>[!important]
>**Name**: CMA-ES or *Covariance Matrix Adaptation Evolution Strategy*

![[EDA or Estimation of Distribution Algorithm#^ad5721]]



- [[EDA or Estimation of Distribution Algorithm]]
- [[Gaussian Random Vector]]

## Explanation

>[!quote]
>The **CMA-ES** method of [Han16], which stands for “**covariance matrix adaptation evolution strategy**” is a kind of NES. It is very similar to **CEM** except it updates the parameters in a special way. In particular, instead of computing the new mean and covariance using *unweighted MLE* on the elite set, we attach *weights* to the elite samples based on their *rank*. We then set the new mean to the *weighted MLE* of the elite set. 
>
>The update equations for the covariance are more complex. In particular, “**evolutionary paths**” are also used to accumulate the search directions across successive generations, and these are used to update the covariance. It can be shown that the resulting updates approximate the **natural gradient** of $L(\theta)$ without explicitly modeling the **Fisher information matrix**.

- [[Natural Evolutionary Strategies]]
- [[Cross-Entropy Method for EDA]]
- [[Fisher Metric or Information Metric of Statistical Manifold]]



-----------
##  Recommended Notes and References


- [[EDA or Estimation of Distribution Algorithm]]
- [[Cross-Entropy Method for EDA]]
- [[Gaussian Random Vector]]
- [[Covariance Function of Gaussian Process]]
- [[Positive Semidefinite Transformation]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]


- [[Evolutionary Strategies]]
- [[Derivative-Free Optimization]]



- [[BFGS Algorithm]]
- [[Limited Memory BFGS]]
- [[Conjugate Gradient Algorithm Nonlinear]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 298 - 307
- [[Introduction to Evolutionary Computing by Eiben]] 
- Hansen, N. (2016). The CMA evolution strategy: A tutorial. _arXiv preprint arXiv:1604.00772_.
- Wikipedia [CMA-ES](https://en.wikipedia.org/wiki/CMA-ES)