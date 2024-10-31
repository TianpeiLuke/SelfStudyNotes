---
tags:
  - concept
  - math/convex_analysis
  - optimization/theory
  - optimization/algorithm
  - optimization/convex_optimization
keywords:
  - saddle_point
  - lagrangian_function
topics:
  - optimization/theory
name: Saddle Point of Lagrangian Function
date of note: 2024-07-02
---

## Concept Definition

>[!important]
>**Name**: Saddle Point of Lagrangian Function

![[Constrained Optimization Problem#^0430c8]]

![[Methods of Lagrangian Multipliers#^d5f5f8]]

>[!important] Definition
>Consider the *Lagrangian function* $L: \mathcal{X} \times \mathbb{R}^{m+p}$ associated with a *convex program* $(P)$
>$$
>\begin{align*}
>L(x, \lambda) = f_{0}(x) + \sum_{i=1}^{m}\lambda_{i}\, f_{i}(x) + \sum_{j=1}^{p}\lambda_{m+j}\,h_{j}(x)
\end{align*}
>$$ 
>Suppose the *primal and dual feasible regions* are defined as 
>$$
>\begin{align*}
>\Omega &:= \left\{ x\in \mathcal{X}:  f_{i}(x) \leq 0, \; i =1 \,{,}\ldots{,}\, m;\quad h_{j}(x) = 0, \; j =1 \,{,}\ldots{,}\, p \right\} \\[5pt]
> \mathcal{M}&:= \left\{\lambda \in \mathbb{R}^{m+p}: \lambda_{i} \ge 0, \quad i =1 \,{,}\ldots{,}\, m \right\}.  
>\end{align*}
>$$
>Observe that
>-  $L$ is **convex** in $x\in \Omega$
>- $L$ is **concave** in $\lambda \in \mathcal{M}.$
>  
>A vector $(x^{*}, \lambda^{*})$ is said to be a **saddle-point** of $L$ (with respect to *maximizing in* $\lambda$ and *minimizing in $x$*) if
>$$
> L(x^{*}, \lambda) \le L(x^{*}, \lambda^{*}) \le L(x, \lambda^{*}), \quad \forall x\in \Omega, \; \forall \lambda \in \mathcal{M}.
>$$

- [[Von Neumann Min-Max Theorem]]

### Min-max Theorem

![[Von Neumann Min-Max Theorem#^8777e4]]



## Explanation





-----------
##  Recommended Notes and References


- [[Methods of Lagrangian Multipliers]]
- [[Karush-Kuhn-Tucker Optimality Condition]]


- [[Constrained Optimization Problem]]

- [[Numerical Optimization by Nocedal]] pp 
- [[Convex Analysis by Rockafellar]] pp 281