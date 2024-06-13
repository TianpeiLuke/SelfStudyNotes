---
tags:
  - concept
  - math/probability
keywords:
  - strong_law_large_number
topics:
  - probability
name: Kolmogorov Strong Law of Large Numbers
date of note: 2024-05-31
---

## Concept Definition

>[!important]
>**Name**: Kolmogorov Strong Law of Large Numbers (SLLN)

>[!important] Kolmogorov's Strong Law of Large Numbers (SLLN)
>Let $\left\{ X_{n}, n \ge 1 \right\}$ be an **independent identically distributed (i.i.d.)** sequence of random variables and set $$S_{n} = \sum_{i=1}^n X_{i}.$$
>
>There exists $\mu \in \mathbb{R}$ such that
>$$
>\bar{X}_{n} := \frac{1}{n}S_{n} \stackrel{a.s.}{\longrightarrow} \mu
>$$
>**if and only if** 
>$$
> \mathbb{E}\left[ |X_{1}| \right] < \infty
>$$
>in which case $\mu =  \mathbb{E}\left[ X_{1} \right].$


## Explanation



## Corollary

>[!important] Corollary
>If $\left\{ X_{n}, n \ge 1 \right\}$ is an i.i.d. sequence, then 
>$$
>\mathbb{E}\left[ |X_{1}| \right] < \infty \; \implies \; \bar{X}_{n} := \frac{1}{n}S_{n} \stackrel{a.s.}{\longrightarrow}  \mathbb{E}\left[ X_{1} \right],
>$$
>and
>$$
>\mathbb{E}\left[ X_{1}^2 \right] < \infty \; \implies \; \frac{1}{n}\sum_{j=1}^n\left( X_{j} - \bar{X}_{n} \right)^2 \stackrel{a.s.}{\longrightarrow} \sigma^2 := \text{Var}(X_{1}).
>$$





-----------
##  Recommended Notes and References

- [[Weak Law of Large Numbers]]

- [[Independent Random Variables]]
- [[Expectation of Random Variable]]
- [[Empirical Process and Empirical Measure]]
- [[Random Element and Random Variable]]



- [[A Probability Path by Resnick]]
- [[Probability and Measure by Billingsley]]