---
tags:
  - concept
  - statistics/concentration_inequality
keywords:
  - hoeffding_inequality_functional
topics:
  - statistics
name: Functional Hoeffding Inequality
date of note: 2024-05-07
---

## Concept Definition

>[!important]
>**Name**: Functional Hoeffding Inequality


>[!important] Functional Hoeffding's Inequality
>For each $f \in \mathcal{F}$ and $i = 1 \,{,}\ldots{,}\, n$, assume that there are real numbers $a_{i,f} \le b_{i,f}$ such that $$f(x) \in [a_{i,f},  b_{i,f}]$$ for all $x \in \mathcal{X}_i$.
>
> Then for all $t \ge 0$, we have
> $$
> \begin{align}
> \mathcal{P}\left\{ Z \ge \mathbb{E}\left[  Z \right] + t \right\}  \le \exp\left(-\frac{n t^2}{4 L^2}\right)
> \end{align}
>$$  
>where $$Z :=\sup_{f \in \mathcal{F}}\left\{\frac{1}{n}\sum_{i=1}^n f(X_i)\right\},$$ and $$L^2 := \sup_{f \in \mathcal{F}}\left\{\frac{1}{n}\sum_{i=1}^{n}\left(a_{i,f} - b_{i,f}\right)^2\right\}.$$

^3e5445

- [[Empirical Process and Empirical Measure]]
- [[Hoeffding Inequality]]




## Explanation










-----------
##  Recommended Notes and References

- [[Empirical Process and Empirical Measure]]
- [[Hoeffding Inequality]]


- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]