---
tags:
  - concept
  - math/differential_geometry
  - math/riemannian_geometry
keywords:
  - metric_connection
  - riemannian_manifold
topics:
  - differential_geometry
  - riemannian_geometry
name: Metric Connection
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Metric Connection

>[!important] Definition
>Let $g$ be a *Riemannian* or *pseudo-Riemannian metric* on a *smooth manifold* $M$ (with or without boundary). 
>
>A connection $\nabla$ on $TM$ is said to be **compatible with** $g$, or to be a **metric connection**, if it satisfies the following *product rule* for all $X, Y, Z \in \mathfrak{X}(M)$:
>$$
> \begin{align}
>  \nabla_{Z}(\left\langle X\,,\,Y \right\rangle_{g}) &= \left\langle \nabla_{Z}X\,,\, Y \right\rangle_{g} + \left\langle  X\,,\,  \nabla_{Z}Y \right\rangle_{g} \\[5pt]
> \Leftrightarrow Z\left\langle  X\,,\, Y   \right\rangle_{g} &= \left\langle \nabla_{Z}X\,,\, Y \right\rangle_{g} + \left\langle  X\,,\,  \nabla_{Z}Y \right\rangle_{g} 
> \end{align}
>$$  

- [[Riemannian Metric and Riemannian Manifold]]
- [[Connection in Vector Bundle]]
- [[Tangent Bundle]]
- [[Vector Field on Manifold]]
- [[Space of all Smooth Vector Fields on a Manifold]]


## Explanation





-----------
##  Recommended Notes and References

- [[Symmetric Connection]]
- [[Levi Civita Connection and Riemannian Connection]]
- [[Inner Product Space]]

- [[Introduction to Smooth Manifolds by Lee]]
- [[Introduction to Riemannian Manifolds by Lee]] pp 118