---
tags:
  - concept
  - statistics/concentration_inequality
  - math/stochastic_process
keywords:
  - entropy_integral_inequality
topics:
  - concentration_inequality
  - stochastic_process
name: Dudley Discrete Entropy Integral Inequality
date of note: 2024-06-02
---

## Concept Definition

>[!important]
>**Name**: Dudley Discrete Entropy Integral Inequality

>[!important] Dudley's Entropy Integral Inequality (Discrete)
>Let $\set{X_{t}, t \in T}$ be a **zero-mean** random process on a **metric space** $(T, d)$ with **sub-gaussian increments** with constant $K$.
>
> Then
>$$ 
> \begin{align}
>  \mathbb{E}\left[  \sup_{t\in T}X_t  \right]\, \le \, C\,K \sum_{k=1}^{\infty}2^{-k}\sqrt{\log \mathcal{N}(T, d, 2^{-k})}. 
> \end{align}
>$$ 

^d4f02e

- [[Sub-Gaussian Process]]
- [[Stochastic Process]]
- [[Metric Space]]


## Explanation





-----------
##  Recommended Notes and References

- [[epsilon-Cover and epsilon-Net of Metric Space]]
- [[Covering Number of Metric Space]]
- [[Metric Entropy of Metric Space]]

- [[Dudley Entropy Integral Inequality]]
- [[Chaining Method as Multi-Scale epsilon-Net Argument]]


- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[High Dimensional Probability An Introduction by Vershynin]]
- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]