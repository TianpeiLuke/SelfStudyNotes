---
tags:
  - concept
  - math/differential_geometry
  - math/topology
keywords:
  - coordinate_chart
topics:
  - differential_geometry
name: Coordinate Chart
date of note: 2024-05-05
---

## Concept Definition

>[!important]
>**Name**: Coordinate Chart

>[!important] Definition
>Let $M$ be a *topological n-manifold*. A **coordinate chart** (or just a **chart**) on $M$ is a *pair* $(U, \varphi)$, where $U$ is an **open subset** of $M$ and $\varphi: U \rightarrow \widehat{U}$ is a **homeomorphism** from $U$ to an *open subset* $\widehat{U} = \varphi(U) \subseteq \mathbb{R}^n.$

^1c8d37


>[!important] Definition
>- By definition of a topological manifold, each point $p \in M$ is contained in the **domain** of some chart $(U, \varphi)$. 
>- If $\varphi(p) = 0$, we say that the chart is *centered at* $p$. 
>- If $(U, \varphi)$ is any chart whose domain contains $p$, it is easy to obtain a new chart centered at $p$ by *subtracting the constant vector* $\varphi(p)$.




## Explanation

![[coordinate_chart.png]]



-----------
##  Recommended Notes and References

- [[Transition Map and Smoothly Compatible]]
- [[Smooth Atlas]]
- [[Maximal Smooth Atlas]]
- [[Topological Manifold]]
- [[Homeomorphism]]

- [[Introduction to Smooth Manifolds by Lee]]