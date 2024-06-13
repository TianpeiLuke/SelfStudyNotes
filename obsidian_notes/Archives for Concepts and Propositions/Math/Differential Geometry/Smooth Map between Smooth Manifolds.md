---
tags:
  - concept
  - math/differential_geometry
keywords:
  - smooth_map_between_manifolds
topics:
  - differential_geometry
name: Smooth Map between Smooth Manifolds
date of note: 2024-05-06
---

## Concept Definition

>[!important]
>**Name**: Smooth Map between Smooth Manifolds

>[!important] Definition
>Let $M, N$ be *smooth manifolds*, and let $F: M \rightarrow N$ be any map. 
>
>We say that $F$ is a **smooth map** if for every $p \in M$, there exist *smooth charts* $(U, \varphi)$ containing $p$ and $(V, \psi)$ containing $F(p)$ such that $F(U) \subseteq V$ and the *composite map* $\psi \circ F \circ \varphi^{-1}$ is *smooth* from $\varphi(U)$ to $\psi(V)$. 


>[!important] Definition
>If $M$ and $N$ are *smooth manifolds* **with boundary**, smoothness of $F$ is defined in exactly the same way, with the usual understanding that a map whose domain is a subset of $\mathbb{H}^n$ is *smooth* if it admits an *extension to a smooth map* in a neighborhood of each point, and a map whose codomain is a subset of $\mathbb{H}^n$ is smooth if it is smooth as a map into $\mathbb{R}^n$.




## Explanation





-----------
##  Recommended Notes and References

- [[Smooth Manifold]]
- [[Smooth Map]]
- [[Smooth Chart and Smooth Coordinate Map]]
- [[Smooth Function on Smooth Manifold]]