---
tags:
  - concept
  - statistics/monte_carlo_simulation
  - optimization/algorithm
keywords: 
topics: 
name: 
date of note: 2024-08-27
---

## Concept Definition

>[!important]
>**Name**: 



## Explanation

>[!quote]
>In situations where $\mathbb{KL}\left( p_{0} \left\|\right. p_{1} \right)$ is large (i.e., where there is *little overlap* between $p_0$ and $p_{1}$), a strategy called **annealed importance sampling (AIS)** attempts to bridge the gap by introducing *intermediate distributions* (Jarzynski, 1997; Neal, 2001).
>
>This approach enables us to estimate the partition function of a multimodal distribution defined over a *high-dimensional space* (such as the distribution defined by a trained RBM). We begin with a **simpler** model with a **known partition function** (such as an RBM with zeros for weights) and estimate the **ratio between the two model’s partition functions**. The estimate of this ratio is based on the estimate of the ratios of a sequence of many similar distributions, such as the sequence of RBMs with weights interpolating between zero and the learned weights.
>
>-- [[Deep Learning by Goodfellow]] pp 617



-----------
##  Recommended Notes and References


- [[Estimating Partition Function via Importance Sampling]]

- [[Importance Sampling]]
- [[Simulated Annealing]]
- [[Sequential Importance Sampling]]
- [[Markov Chain Monte Carlo Methods]]
- [[Gibbs Sampling]]
- [[Metropolis-Hastings Algorithm]]


- [[Log-Partition Function and Score Function of Graphical Models]]
- [[Gibbs Measure and Energy-based Model]]


- [[Deep Learning by Goodfellow]] pp 617
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]  pp 533 - 536
- [[Probabilistic Graphical Models by Koller]] pp 543, 548
- Neal, R. M. (2001). Annealed importance sampling. _Statistics and Computing_, _11_(2), 125–139. [https://doi.org/10.1023/A:1008923215028](https://doi.org/10.1023/A:1008923215028)