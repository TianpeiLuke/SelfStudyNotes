---
tags:
  - concept
  - math/differential_geometry
keywords:
  - coordinate_representation
  - tangent_bundle_coordinate_system
topics:
  - differential_geometry
name: Coordinate Representation of Element in Tangent Bundle
date of note: 2024-05-06
---

## Concept Definition

>[!important]
>**Name**: The Coordinate Representation of Element in Tangent Bundle $TM$

>[!info] Definition 
>Given a *smooth manifold* $M$ with or without boundary, the **tangent bundle** of $M$, denoted by $TM$, is defined as the **disjoint union** of *the tangent spaces* **at all points** of $M$:
>$$
> \begin{align*}
> TM &= \bigsqcup_{p \in M}T_{p}M.
> \end{align*}
>$$ 

- [[Tangent Bundle]]

>[!important] Definition
>The **coordinates** $(x^i, v^i)$ given by 
>$$
> \begin{align*}
> \widetilde{\varphi}\left(v^{i} \frac{\partial}{\partial x^i}\Bigr|_{p}\right)  &= (x^{1}(p), \ldots, x^{n}(p), v^{1}, \ldots, v^{n}). 
> \end{align*}  
>$$ 
> are called **natural coordinates** on $TM$.

- [[Einstein Summation Convention]]

>[!info]
>This representation is called **phase space** in physics, where $p$ is the *position* of particle, and $v$ is the *velocity (momentum)*. 
>
>So think of a **tangent bundle** is a *physical system of particles* moving on a surface $M$.

>[!info]
>Interestingly, this suggests that the **derivative** $v$ at $p$ is **linearly independent** from **the position** vector $p$ .










-----------
##  Recommended Notes and References

- [[Tangent Bundle]]

- [[Coordinate Representation of Element in Vector Bundle]]

