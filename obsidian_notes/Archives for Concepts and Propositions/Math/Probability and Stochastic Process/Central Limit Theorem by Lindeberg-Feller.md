---
tags:
  - concept
  - math/probability
keywords:
  - central_limit_theorem
topics:
  - probability
name: Lindeberg-Feller Central Limit Theorem
date of note: 2024-06-04
---

## Concept Definition

>[!important]
>**Name**: Lindeberg-Feller's Central Limit Theorem

>[!important] Lindeberg-Feller's Central Limit Theorem
>Let $(X_{1} \,{,}\ldots{,}\, X_{n})$ be a sequence of **independent** (*not necessarily identically distributed*) random variables with mean $\mathbb{E}\left[ X_{1} \right] = 0$ and $\text{Var}\left[ X_{i} \right] = \sigma_{i}^2,$ for $i=1, \,{,}\ldots{,}\,n.$ 
>
>Let $$S_{n} = \sum_{i=1}^{n}X_{i}$$ be the sum of random variables. We say $(X_{i}, i \ge 1)$ satisfies **the Lindeberg's condition** if for any $t > 0$, we have
>$$
> \lim_{ n \to \infty } \frac{1}{\sum_{i=1}^n\sigma_{i}^2}\sum_{i=1}^{n} \mathbb{E}\left[X_{i}^2\; \mathbb{1}\left\{ \left\lvert \frac{X_{i}}{S_{n}} \right\rvert   > t\right\}   \right]  = 0.
>$$
>
>Then
>$$
>\frac{S_{n} - n\mu}{\sigma \sqrt{ n }} \stackrel{d}{\longrightarrow} \mathcal{N}(0, \sigma^2),
>$$
>where $\mathcal{N}(\mu, \sigma^2)$ is the **zero-mean Gaussian distribution** with variance parameter $\sigma^2.$


- [[Characteristic Function of Random Variable]]
- [[Central Limit Theorem]]
## Explanation





-----------
##  Recommended Notes and References


- [[Gaussian Measure]]
- [[Gaussian Random Variable]]
- [[Convergence in Distribution]]


- [[A Probability Path by Resnick]]
- [[Probability and Measure by Billingsley]]