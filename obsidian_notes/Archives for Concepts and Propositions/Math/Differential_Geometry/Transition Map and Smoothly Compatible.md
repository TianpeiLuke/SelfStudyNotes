---
tags:
  - concept
  - math/differential_geometry
  - math/topology
keywords:
  - transition_map
topics:
  - differential_geometry
name: Transition Map
date of note: 2024-05-06
---

## Concept Definition

>[!important]
>**Name**: Transition Map

>[!important] Definition
>Let $M$ be a *topological $n$-manifold.* If $(U, \varphi)$, $(V, \psi)$ are two *charts* such that $U \cap V \neq \emptyset$, the *composite map* $\psi \circ \varphi^{-1}: \varphi(U \cap V ) \rightarrow \psi(U \cap V)$ is called the **transition map** from $\varphi$ to $\psi$. 

![[transition_map.png]]

>[!info]
>It is a *composition* of *homeomorphisms*, and is therefore itself a *homeomorphism*. 


>[!important] Definition
>Two charts $(U, \varphi)$ and $(V, \psi)$ are said to be **smoothly compatible** if either $U \cap V = \emptyset$ or the *transition map* $\psi \circ \varphi^{-1}$ is a **diffeomorphism**. 

- [[Coordinate Chart]]
- [[Diffeomorphism]]

![[smooth_compatiability_slice_chart.png]]

>[!info]
>Since $\varphi(U \cap V )$ and $\psi(U \cap V )$ are open subsets of $\mathbb{R}^n$, smoothness of this map is to be interpreted in the ordinary sense of having *continuous partial derivatives of all orders.*




## Explanation





-----------
##  Recommended Notes and References

- [[Topological Manifold]]
- [[Coordinate Chart]]
- [[Smooth Map between Euclidean Spaces]]

- [[Introduction to Smooth Manifolds by Lee]]