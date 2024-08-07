---
tags:
  - concept
  - optimization/algorithm
keywords:
  - proximal_cutting_plane_algorithm
topics:
  - optimization/algorithm
name: Proximal Cutting-Plane Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Proximal Cutting-Plane Algorithm


![[Polyhedral Approximation for Optimization#^923ee3]]

>[!important] Definition
>Consider the following *convex optimization problem*
>$$
> \min_{x\in \mathcal{X}} f(x)
>$$
>where $f: \mathbb{R}^{n} \to \mathbb{R}$ is a *convex function* and $\mathcal{X}$ is a *closed convex set*.
>
>The **proximal cutting plane method** uses a *proximal-like algorithm* where $f$ is replaced by the *cutting plane approximation* $F_{k}$.
>
>At each iteration $k$:
>$$x_{k+1}  \in \arg\min_{x \in \mathcal{X}}\left\{ F_{k}(x) + \frac{1}{2 c_{k}}\lVert x - x_{k} \rVert^2  \right\}.$$

^b82379

- [[Strongly Convex Function]]

- [[Polyhedral Approximation for Optimization]]
- [[Proximal Algorithm]]
- [[Cutting Plane Methods and Outer Linearization]]



## Explanation





-----------
##  Recommended Notes and References

- [[Approximation Method for Optimization]]
- [[Proximal Algorithm]]
- [[Cutting Plane Methods and Outer Linearization]]

- [[Polyhedron and Polytope]]

- [[Bundle Methods]]

- [[Convex Optimization Algorithms by Bertsekas]] pp 270