---
tags:
  - concept
  - statistics/concentration_inequality
keywords:
  - hoeffding_inequality
topics:
  - statistics
name: Azuma-Hoeffding Inequality
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Azuma-Hoeffding Inequality


>[!important] Azuma-Hoeffding Inequality
>Let $\set{(D_i, \mathscr{F}_i), i \ge 1}$ be a **martingale difference sequence** for which there are constants $n$, and $\set{(a_i, b_i)}^{n}_{i=1}$ such that $D_i \in [a_i, b_i]$ *almost surely* for all $k = 1 \,{,}\ldots{,}\, n$. 
>
>Then, for all $t \ge 0$,
>$$
> \begin{align}
> \mathcal{P} \left\{\sum_{k=1}^{n}D_k  \ge t  \right\}  &\le \exp\left(- \frac{2 t^2}{ \sum_{k=1}^{n}(b_k - a_k)^2}\right) 
> \end{align}
>$$ 

- [[Hoeffding Inequality]]
- [[Martingale]]
- [[Martingale Differences]]
- [[Sub-Gaussian Random Variable]]

## Explanation

>[!important]
>The concept of a **martingale** is a **generalization** to a sequence of **independent random variables**, since it does not require independence among $X_{n}$ but still maintain the *orthogonality in expectation* among $X_{n} - X_{n-1}$.


>[!info]
>Azuma-Hoeffding Inequality can be proved using the [[Bernstein Inequality for Martingale]].


## Generalization








-----------
##  Recommended Notes and References

- [[Martingale]]
- [[Martingale Differences]]

- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]