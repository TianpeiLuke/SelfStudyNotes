---
tags:
  - concept
  - math/differential_geometry
keywords:
  - smooth_function_on_manifold
topics:
  - differential_geometry
name: Smooth real-valued function on Smooth Manifold
date of note: 2024-05-06
---

## Concept Definition

>[!important]
>**Name**: Smooth (real-valued) Function on Smooth Manifold

>[!important] Definition
>Suppose $M$ is a *smooth $n$-manifold*, $k$ is a nonnegative integer, and $f: M \rightarrow \mathbb{R}^k$ is any function. 
>
>We say that $f$ is a **smooth function** if for every $p \in M$, there exists a *smooth chart* $(U, \varphi)$ for $M$ whose domain contains $p$ and such that the *composite function* $f \circ \varphi^{-1}$ is *smooth* on the open subset $\widehat{U} = \varphi(U) \subseteq \mathbb{R}^n$.



>[!important] Definition
>If $M$ is a *smooth manifold* **with boundary**, the definition is exactly the same, except that $\varphi(U)$ is now an *open subset* of either $\mathbb{R}^n$ or $\mathbb{H}^n$, and in the latter case we interpret smoothness of $f \circ \varphi^{-1}$ to mean that each point of $\varphi(U)$ has a *neighborhood* (*in $\mathbb{R}^n$*) on which $f \circ \varphi^{-1}$ **extends** *to a smooth function* in the ordinary sense.




## Explanation





-----------
##  Recommended Notes and References

- [[Smooth Manifold]]
- [[Smooth Map]]
- [[Smooth Chart and Smooth Coordinate Map]]
- [[Smooth Map between Smooth Manifolds]]