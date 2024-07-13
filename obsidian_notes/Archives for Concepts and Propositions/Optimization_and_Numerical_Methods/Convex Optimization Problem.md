---
tags:
  - concept
  - optimization/theory
keywords:
  - convex_optimization
topics:
  - optimization
name: Convex Optimization Problem
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Convex Optimization Problem

>[!important] Definition
>A  **convex optimization problem** (or **convex programming**) is defined as below
>$$
>\begin{align*}
>\min_{x \in X}\; & f_{0}(x) \\
>\text{s.t.}\;& f_{i}(x) \leq 0, \quad i =1 \,{,}\ldots{,}\, m\\
>&h_{j}(x) = 0, \quad j =1 \,{,}\ldots{,}\, p\\
\end{align*}
>$$
>where both the *objective function* $f_{0}$ and *inequality constraint functions* $f_{i}$ are **convex** functions.
>
>Moreover, the **equality constraint functions** $h_{j}(x)$ must be **linear**.

^bc3f9c

- [[Constrained Optimization Problem]]

>[!important]
>The **domain** of convex optimization problem 
>$$
>X := \text{dom}(f_{0}) \; \cap \; \bigcap_{i=1}^{m}\text{dom}(f_{i})
>$$ 
>is **convex**.


>[!important] 
>The **feasible set** of a convex optimization problem
>$$
>\Omega := \left\{ x\in X:  f_{i}(x) \leq 0, \; i =1 \,{,}\ldots{,}\, m;\quad h_{j}(x) = 0, \; j =1 \,{,}\ldots{,}\, p \right\}
>$$
>is a **convex set**.

## Explanation

>[!important] General Definition
>An  **abstract convex optimization problem**  is defined as the problem of minimizing a *convex function* $f: X \to \mathbb{R}$ over a *convex set* $C \subset X.$
>$$
>\begin{align*}
>\min_{x \in X}\; & f(x) \\
>\text{s.t.}\;& x \in C
\end{align*}
>$$


## Bifunction Representation

![[Bifunction and Convex Bifunction#^64bafd]]

- [[Bifunction and Convex Bifunction]]


-----------
##  Recommended Notes and References

- [[Constrained Optimization Problem]]
- [[Unconstrained Global Minimization]]
- [[Unconstrained Local Minimization]]
- [[Necessary and Sufficient Condition for Local Minimum of Smooth Function]]

- [[Convex Analysis by Rockafellar]] pp 273
- [[Convex Optimization by Boyd]]
- [[Numerical Optimization by Nocedal]]
- [[Nonlinear Programming by Bertsekas]]