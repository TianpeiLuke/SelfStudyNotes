---
tags:
  - concept
  - optimization/theory
  - math/convex_analysis
keywords:
  - lagrangian_function
topics:
  - optimization
  - convex_analysis
name: Lagrangian Function
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Lagrangian Function or *Methods of Lagrangian Multipliers*

>[!info]
>Consider the general **constrained optimization**
>$$
>\begin{align*}
>\min_{x \in X}\; & f_{0}(x) \\
>\text{s.t.}\;& f_{i}(x) \leq 0, \quad i =1 \,{,}\ldots{,}\, m\\
>&h_{j}(x) = 0, \quad j =1 \,{,}\ldots{,}\, p\\
\end{align*}
>$$

- [[Constrained Optimization Problem]]

>[!important] Definition
>The **Lagrangian** $L: X \times \mathbb{R}^{m} \times \mathbb{R}^{p} \to \mathbb{R}$ associated with the problem above is defined as 
>$$
>\begin{align*}
>L(x, \lambda, \nu) = f_{0}(x) + \sum_{i=1}^{m}\lambda_{i}\, f_{i}(x) + \sum_{j=1}^{p}\nu_{j}\,h_{j}(x)
\end{align*}
>$$ 
>with *domain* $X \times \mathbb{R}^{m} \times \mathbb{R}^{p}$, where
>$$
>X := \text{dom}(f_{0}) \; \cap \; \bigcap_{i=1}^{m}\text{dom}(f_{i}) \; \cap \; \bigcap_{j=1}^{p}\text{dom}(h_{j})
>$$ 

^d5f5f8

- [[Bifunction and Convex Bifunction]]

>[!important] Definition
>- The variables $\lambda_{i}$ are called **the Lagrangian multiplier** *associated with* $i$-th inequality constraint $f_{i}(x) \leq 0$.
>- The variables $\nu_{j}$ are called **the Lagrangian multiplier** *associated with* $j$-th equality constraint $h_{j}(x) = 0$.
>- The variables $\lambda = [\lambda_{1} \,{,}\ldots{,}\, \lambda_{m}]$ and $\nu = [\nu_{1} \,{,}\ldots{,}\, \nu_{p}]$ are called **the dual variables** or the **Lagrangian multiplier vectors** associated with the optimization problem.

- [[Karush-Kuhn-Tucker Optimality Condition]]

## Explanation

>[!info]
>In [[Convex Analysis by Rockafellar]], The variables $\lambda_{i}$ are called the **Kuhn-Tucker coefficients** due to its relationship in [[Karush-Kuhn-Tucker Optimality Condition]].

>[!info]
>In [[Convex Analysis by Rockafellar]], the Lagrangian function would take *extended real values*. Thus
>$$
>L(x, \lambda, \nu) := \left\{ \begin{array}{cc}
>f_{0}(x) + \sum_{i=1}^{m}\lambda_{i}\, f_{i}(x) + \sum_{j=1}^{p}\nu_{j}\,h_{j}(x) & x\in \Omega \land (\lambda, \nu) \in \mathcal{M} \\
>- \infty & x\in \Omega \land  (\lambda, \nu) \not\in \mathcal{M}\\ 
>+ \infty & x\not\in \Omega 
\end{array}  \right.  
>$$
>where $\Omega$ is the **primal feasible region**
>$$
>\Omega := \left\{ x\in X:  f_{i}(x) \leq 0, \; i =1 \,{,}\ldots{,}\, m;\quad h_{j}(x) = 0, \; j =1 \,{,}\ldots{,}\, p \right\}
>$$
>and $\mathcal{M}$ is **the dual feasible region**
>$$
>\mathcal{M} := \left\{(\lambda, \nu) \in \mathbb{R}^m \times \mathbb{R}^n: \lambda_{i} \ge 0, \quad i =1 \,{,}\ldots{,}\, m \right\} 
>$$
>

- [[Constrained Optimization Problem]]
- [[Lagrange Dual Problem]]

>[!important]
>There exists a **one-to-one correspondence** between the *constrained optimization problem* $(P)$ and its associated **Lagrangian** $L$ as
>$$
>\begin{align*}
> f_{0}(x) &= L(x, 0, 0), \quad x\in \Omega \\
> f_{i}(x) &= L(x, e_{i}, 0) - L(x, 0, 0), \quad  x\in \Omega;\;i=1 \,{,}\ldots{,}\,m, \\
> h_{j}(x) &= L(x, 0, e_{j}) - L(x, 0, 0), \quad  x\in \Omega;\;j=1 \,{,}\ldots{,}\,p, \\
> \Omega \times \mathcal{M} &= \left\{(x, \lambda, \nu): - \infty < L(x, \lambda, \nu) < \infty  \right\}
>\end{align*}
>$$

- [[Convex Analysis by Rockafellar]] pp 281


## Lagrangian Dual Function and Dual Problem

- [[Lagrangian Dual Function]]
- [[Lagrange Dual Problem]]


## Necessary and Sufficient Conditions

- [[Karush-Kuhn-Tucker Optimality Condition]]


## Proximal Algorithm and Augmented Lagrangian

- [[Proximal Algorithm]]
- [[Dual Proximal Algorithm]]
- [[Augmented Lagrangian Function]]








-----------
##  Recommended Notes and References

- [[Karush-Kuhn-Tucker Optimality Condition]]

- [[Convex Analysis by Rockafellar]] pp 273, 280
- [[Convex Optimization by Boyd]]
- [[Numerical Optimization by Nocedal]]
- [[Nonlinear Programming by Bertsekas]]
- [[Optimization by Vector Space Methods by Luenberger]] pp 216