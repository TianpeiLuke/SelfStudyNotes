---
tags:
  - concept
  - optimization/theory
  - math/convex_analysis
keywords:
  - lagrangian_function
topics:
  - optimization
name: Lagrangian Dual Function
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Lagrangian Dual Function

![[Methods of Lagrangian Multipliers#^d5f5f8]]

- [[Methods of Lagrangian Multipliers]]
- [[Constrained Optimization Problem]]


>[!important] Definition
>Given the Lagrangian $L$, we can define the **Lagrangian dual function** (or just **dual function**) $g: \mathbb{R}^m \times \mathbb{R}^{n} \to \mathbb{R}$ as the minimal value of the Lagrangian over $x\in X$. 
>
>That is, for $\lambda = [\lambda_{1} \,{,}\ldots{,}\, \lambda_{m}] \in \mathbb{R}^m$ and $\nu = [\nu_{1} \,{,}\ldots{,}\, \nu_{p}] \in \mathbb{R}^n$ ,
>$$
>g(\lambda, \nu) := \inf_{x\in X}L(x, \lambda, \nu) = \inf_{x \in X}\left(f_{0}(x) + \sum_{i=1}^{m}\lambda_{i}\, f_{i}(x) + \sum_{j=1}^{p}\nu_{j}\,h_{j}(x)\right)
>$$ 

^4397cf


## Explanation

>[!important] Proposition
>The *dual function* yields **lower bound** for the *optimal value* $p^{*}$ of the original problem in [[Constrained Optimization Problem]].
>
>$$
>g(\lambda, \nu) \leq p^{*}, \quad \forall \lambda \in \mathbb{R}^m, \nu \in \mathbb{R}^p.
>$$
>
>[](Constrained%20Optimization%20Problem.md)-trivial only when $\lambda_{i} \ge 0$ for each $i$ and $(\lambda, \nu) \in \text{dom}(g)$, i.e. $g(\lambda, \nu) > - \infty$.
>
>A pair $(\lambda, \nu) \in \text{dom}(g)$ with $\lambda \ge 0$ is called **dual feasible**.

## Examples







-----------
##  Recommended Notes and References

- [[Legendre Transform]]
- [[Convex Conjugate Function]]
- [[Theorems of Alternatives]]

- [[Convex Analysis by Rockafellar]]
- [[Convex Optimization by Boyd]]
- [[Numerical Optimization by Nocedal]]
- [[Nonlinear Programming by Bertsekas]]