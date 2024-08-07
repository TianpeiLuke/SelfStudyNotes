---
tags:
  - concept
  - optimization/theory
keywords:
  - dual_optimization
topics:
  - optimization
name: Lagrange Dual Problem
date of note: 2024-05-17
---

## Concept Definition

>[!important]
>**Name**: Lagrange Dual Problem

![[Lagrangian Dual Function#^4397cf]]

- [[Lagrangian Dual Function]]

>[!important] Definition
>Given the Lagrangian dual function $g: \mathbb{R}^m \times \mathbb{R}^n \to \mathbb{R}$, we can formulate the following optimization problem
>$$
>\begin{align*}
>\min_{\lambda \in \mathbb{R}^m,\; \nu \in \mathbb{R}^n}\; & g(\lambda, \nu) \\
>\text{s.t.}\;&\, \lambda_{i} \ge 0, \quad i =1 \,{,}\ldots{,}\, m.
\end{align*}
>$$
>
>This problem is called the **Lagrange dual problem**.

>[!info]
>WIth respect to dual problem, the problem in [[Constrained Optimization Problem]] is called the **primal problem**.

>[!important] Definition
>The set of *dual feasible* $(\lambda, \nu)$ is **the dual feasible set** 
>$$
>\mathcal{M} := \left\{(\lambda, \nu) \in \mathbb{R}^m \times \mathbb{R}^n: \lambda_{i} \ge 0, \quad i =1 \,{,}\ldots{,}\, m; \quad g(\lambda, \nu) > -\infty \right\} 
>$$

>[!important] Definition
>The *optimal point* $(\lambda^{*}, \nu^{*})$ that solves the Lagrange dual problem is said to be **dual optimal**, or the **optimal Lagrangian multipliers.**


## Explanation

>[!important]
>The Lagrange dual problem is **convex problem** given that the *Lagrangian dual function* is **concave** and the inequality constraints are all convex.
>
>This statement is **always true** *whether or not the primal problem is convex*.






-----------
##  Recommended Notes and References

- [[Methods of Lagrangian Multipliers]]
- [[Constrained Optimization Problem]]
- [[Theorems of Alternatives]]

- [[Convex Analysis by Rockafellar]]
- [[Convex Optimization by Boyd]]
- [[Numerical Optimization by Nocedal]]
- [[Nonlinear Programming by Bertsekas]] pp 487