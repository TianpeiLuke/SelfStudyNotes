---
tags:
  - concept
  - optimization/algorithm
  - optimization/convex_optimization
  - optimization/linear_optimization
keywords:
  - bundle_methods
topics:
  - optimization/algorithm
name: Bundle Methods
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Bundle Methods

![[Proximal Cutting-Plane Algorithm#^b82379]]

>[!important] Definition
>Consider the following *convex optimization problem*
>$$
> \min_{x\in \mathcal{X}} f(x)
>$$
>where $f: \mathbb{R}^{n} \to \mathbb{R}$ is a *convex function* and $\mathcal{X}$ is a *closed convex set*.
>
>The **bundle method** generates $x_{k+1}$ by minimizing the *cutting plane approximation* $F_{k}$ of $f$, and a *quadratic term* $p_{k}(x)$ 
>$$x_{k+1} \in \arg\min_{x\in \mathcal{X}}\left\{ F_{k}(x) + p_{k}(x) \right\} $$ where
>- $F_{k}(x)$ is the *polyhedra approximation* of $f$.
>- the *quadratic form* $$p_{k}(x) = \frac{1}{2c_{k}}\lVert x - y_{k} \rVert^2$$ 
>- $y_{k}$ is the **proximal center** of $\{ x_{i}: i \le k \}.$

- [[Polyhedral Approximation for Optimization]]
- [[Proximal Cutting-Plane Algorithm]]
- [[Closed Convex Function and Closure Operation]]



## Explanation





-----------
##  Recommended Notes and References

- [[Proximal Cutting-Plane Algorithm]]
- [[Proximal Algorithm]]
- [[Cutting Plane Methods and Outer Linearization]]



- [[Convex Optimization Algorithms by Bertsekas]] pp 272