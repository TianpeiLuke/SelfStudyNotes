---
tags:
  - concept
  - math/information_theory
keywords:
  - gibbs_inequality
topics:
  - information_theory
name: Gibbs Inequality
date of note: 2024-05-14
---

## Concept Definition

>[!important]
>**Name**: Gibbs's Inequality

>[!important] Gibbs's Inequality
>Given $n$-dimensional *unit non-negative vectors* $\boldsymbol{p} = [p_{1} \,{,}\ldots{,}\, p_{n}]$ and $\boldsymbol{q} = [q_{1} \,{,}\ldots{,}\, q_{n}]$, i.e. $p_{i} \ge 0$, and $q_{i} \ge 0$ and 
>$$
>\sum_{i=1}^{n}p_{i} = 1, \quad \sum_{i=1}^{n}q_{i} = 1,
>$$
>then the following inequality holds
>$$
>\begin{align*}
> -\sum_{i=1}^n p_{i} \log(p_{i}) &\le -\sum_{i=1}^n p_{i} \log(q_{i}),
\end{align*}
>$$
>with equality holds $p_{i} = q_{i}$ for $i=1 \,{,}\ldots{,}\,n.$

^2ff4a4

- [[Cross-Entropy Loss Function]]
- [[Kullback-Leibler Divergence]]

## Explanation

![[Cross-Entropy Loss Function#^8e6b5a]]


![[Cross-Entropy Loss Function#^c4fbc4]]

>[!info]
>This is basically directly from **nonnegative** of *KL divergence* and decomposition of LLM divergence into cross entropy and entropy
>$$
>\begin{align*}
>&\left(-\sum_{i=1}^n p_{i} \log(q_{i})\right) -\left(-\sum_{i=1}^n p_{i} \log(p_{i}) \right)\\[5pt]
>& = H_{ce}(p, q) - H(p) \\[5pt] 
>& = \mathbb{KL}\left( p \left\|\right.  q \right) \ge 0
\end{align*}
>$$





-----------
##  Recommended Notes and References

