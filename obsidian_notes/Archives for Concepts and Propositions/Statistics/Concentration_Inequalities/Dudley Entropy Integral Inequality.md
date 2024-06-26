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
name: Dudley Entropy Integral Inequality
date of note: 2024-06-02
---

## Theorem

>[!important]
>**Name**: Dudley Entropy Integral Inequality


![[Sub-Gaussian Process#^61c82d]]

- [[Sub-Gaussian Process]]

![[Dudley Discrete Entropy Integral Inequality#^d4f02e]]


- [[Dudley Discrete Entropy Integral Inequality]]

>[!important] Dudley's Entropy Integral Inequality
>Let $\set{X_{t}, t \in T}$ be a **zero-mean** random process on a **metric space** $(T, d)$ with **sub-gaussian increments** with constant $K$.
>
> Then
> $$
> \begin{align}
>  \mathbb{E}\left[ \sup_{t\in T}X_t  \right] \le C\,K\int_{0}^{\infty} \sqrt{\log \mathcal{N}(T, d, \epsilon)} d\epsilon. 
> \end{align}
>$$ 

^9e072c

- [[Sub-Gaussian Process]]
- [[Gaussian Process]]
- [[Stochastic Process]]
- [[Metric Entropy of Metric Space]]


## Explanation

>[!important]
>The upper bound of the integral is not $\infty$ but the **diameter** of  the metric space $T$
> $$
> \begin{align}
>  \mathbb{E}\left[ \sup_{t\in T}X_t  \right] \le C\,K\int_{0}^{\text{diam}(T)} \sqrt{\log \mathcal{N}(T, d, \epsilon)} d\epsilon. 
> \end{align}
>$$ 
>where 
>$$
>\text{diam}(T) = \sup\{ d(x, y): x, y \in T \}.
>$$







-----------
##  Recommended Notes and References

- [[epsilon-Cover and epsilon-Net of Metric Space]]
- [[Covering Number of Metric Space]]
- [[Metric Entropy of Metric Space]]

- [[Dudley Discrete Entropy Integral Inequality]]
- [[Chaining Method as Multi-Scale epsilon-Net Argument]]

- [[Supremum of Empirical Process indexed by VC Class]]
- [[Metric Entropy Bound of VC Class]]

- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[High Dimensional Probability An Introduction by Vershynin]]
- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]