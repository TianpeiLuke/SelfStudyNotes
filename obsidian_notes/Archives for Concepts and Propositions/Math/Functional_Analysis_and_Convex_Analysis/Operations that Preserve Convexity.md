---
tags:
  - concept
  - math/convex_analysis
keywords:
  - convex_operation
topics:
  - convex_analysis
name: Operations that Preserve Convexity
date of note: 2024-05-16
---

## Concept Definition

>[!important]
>**Name**: Operations that Preserve Convexity

### Non-negative Sum

>[!important] Proposition
>Let $\left\{ f_{k}: \mathcal{X} \to \mathbb{R}, k=1,2,\,{}\ldots{}\,n \right\}$ be a set of **convex functions**. And suppose that $\left\{ w_{k}, k=1,2,\,{}\ldots{}\,n \right\}$ is a set of **non-negative scalars**.
>
>Then $$\sum_{k=1}^{n}w_{k}\,f_{k}(\cdot)$$ is a **convex function**.
>
>In general, if $f: \mathcal{X} \times \mathcal{Y} \to \mathbb{R}$ is **convex** in its *first argument*, and $w: \mathcal{Y} \to [0, \infty)$ is a *non-negative function*, such that
>$$
> \int_{\mathcal{X}}\int_{\mathcal{Y}}|w(y)\,f(x, y)|\,dy\,dx < \infty,
>$$
>then 
>$$
>g(x) :=  \int_{\mathcal{Y}}w(y)\,f(x, y)\,dy
>$$
>is **convex** in $x\in \mathcal{X}$

### Composition with Affine Mapping




### Pointwise Maximum or Supremum

![[Legendre Transform#^fff1cb]]

- [[Convex Conjugate Function]]
- [[Legendre Transform]]




### Minimization of Jointly Convex Function Over Convex Set

>[!important] Proposition
>Let $C \subset \mathbb{R}^{d}$ be a **convex set**, and $f: \mathbb{R}^{d} \times  \mathbb{R}^{d} \to \mathbb{R}$ be a **proper jointly convex function**.
>
>Then 
>$$
>g(x) := \inf_{y \in C}f(x, y)
>$$
>is **convex** in $x$ given that $$g(x) > - \infty, \;\;\text{ for some }x.$$ The domain of $g$ is
>$$
>\text{dom}(g) := \left\{ x: (x,y)\in \text{dom}(f), \;\; \text{ for some }y \right\} 
>$$





### Perspective Function

![[Perspective Function#^4c8078]]

![[Perspective Function#^7f2372]]

- [[Perspective Function]]


>[!example]





## Explanation





-----------
##  Recommended Notes and References

- [[Convex Function]]

- [[Convex Optimization by Boyd]]