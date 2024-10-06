---
tags:
  - concept
  - optimization/algorithm
  - optimization/convex_optimization
  - optimization/linear_optimization
keywords:
  - polyhedral_approximation
  - convex_function
topics:
  - optimization/algorithm
name: Polyhedral Approximation for Optimization
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Polyhedral Approximation for Optimization

>[!important] Definition
>Consider a *closed convex function* $f: \mathbb{R}^{n} \to \mathbb{R}$.
>
>Given a collection of points $x_{0} \,{,}\ldots{,}\,x_{k}$,  and associated *subgradients* $$g_{i} \in \partial f(x_{i}), \quad i=1 \,{,}\ldots{,}\,k,$$  a **polyhedral approximation** of $f$, $F_{k}$, is defined as
>$$
>F_{k}(x) = \max\left\{ \ell(x; x_{0}) \,{,}\ldots{,}\,\ell(x; x_{k})  \right\} 
>$$
>where $\ell(x;x_{i})$ is the *first-order approximation* of $f$ at $x_{i}$ (or the *supporting hyperplane* of the *epigraph* of $f$), i.e. $$\ell(x; x_{i}) := f(x_{i}) + \left\langle  g_{i}\,,\, x - x_{i}    \right\rangle, \quad i=1 \,{,}\ldots{,}\,k$$

^923ee3

- [[Subdifferential of Convex Function]]
- [[Supporting Hyperplane of Convex Set]]
- [[Polyhedron and Polytope]]

## Explanation

>[!important]
>The function $F_{k}$ is defined by an intersection of $k$ **supporting hyperplane** to the **epigraph** of $f$.
>
>$$
>\text{epi}(f) \subseteq \bigcap_{i=1}^{k}\text{epi}(\ell(\cdot; x_{k}))
>$$
>
>By [[Separation Theorem]] and [[Hahn-Banach Theorem Geometric Form and Mazur Theorem]], any closed convex set can be represented as the intersection of all half-spaces that contains it. [[Dual Representation of Convex Set]]. 

- [[Epigraph or Supergraph of Function]]
- [[Supporting Hyperplane of Convex Set]]
- [[Support functional of Convex Set]]



-----------
##  Recommended Notes and References

- [[Approximation Method for Optimization]]

- [[Cutting Plane Methods and Outer Linearization]]
- [[Proximal Cutting-Plane Algorithm]]
- [[Bundle Methods]]

- [[Convex Optimization Algorithms by Bertsekas]] pp 91