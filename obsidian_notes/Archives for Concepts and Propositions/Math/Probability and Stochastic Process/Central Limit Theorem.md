---
tags:
  - concept
  - math/probability
keywords:
  - central_limit_theorem
topics:
  - probability
name: Classical Central Limit Theorem
date of note: 2024-06-04
---

## Concept Definition

>[!important]
>**Name**: Classical Central Limit Theorem

>[!important] Classical Central Limit Theorem (I.I.D. Version)
>Let $(X_{1} \,{,}\ldots{,}\, X_{n})$ be a sequence of **independent identically distributed** random variables with mean $\mathbb{E}\left[ X_{1} \right] = \mu$ and $\text{Var}\left[ X_{1} \right]=\sigma^2.$ 
>
>Let $$S_{n} = \sum_{i=1}^{n}X_{i}$$ be the sum of random variables.
>
>Then
>$$
>\frac{S_{n} - n\mu}{\sigma \sqrt{ n }} \stackrel{d}{\longrightarrow} \mathcal{N}(\mu, \sigma^2),
>$$
>where $\mathcal{N}(\mu, \sigma^2)$ is the **Gaussian distribution** with mean parameter $\mu$ and variance parameter $\sigma^2.$

- [[Gaussian Measure]]
- [[Gaussian Random Variable]]
- [[Convergence in Distribution]]


## Explanation

- [[Characteristic Function of Random Variable]]
- [[Continuity Theorem for Convergence in Distribution]]
- [[Dominated Convergence Theorem]]


-----------
##  Recommended Notes and References


- [[Gaussian Measure]]
- [[Gaussian Random Variable]]
- [[Convergence in Distribution]]


- [[A Probability Path by Resnick]]
- [[Probability and Measure by Billingsley]]