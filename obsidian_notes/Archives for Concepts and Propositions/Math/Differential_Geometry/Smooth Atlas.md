---
tags:
  - concept
  - math/differential_geometry
keywords:
  - smooth_atlas
topics:
  - differential_geometry
name: Smooth Atlas
date of note: 2024-05-06
---

## Concept Definition

>[!important]
>**Name**: Smooth Atlas

>[!important] Definition
>We define an **atlas** for $M$ to be *a collection of charts* whose domains *cover* $M$. 
>
>An atlas $\mathcal{A}$ is called a **smooth atlas** if *any two charts* in $\mathcal{A}$ are *smoothly compatible* with each other.


## Explanation

>[!info]
>To show that *an atlas is smooth*, we need only verify that each transition map $\psi \circ \varphi^{-1}$ is *smooth* whenever $(U, \varphi)$ and $(V, \psi)$ are *charts* in $\mathcal{A}$. 
>
>Given two particular charts $(U, \varphi)$ and $(V, \psi)$, it is often easiest to show that they are *smoothly compatible* by verifying that $\psi \circ \varphi^{-1}$ is **smooth** and **injective** with **nonsingular Jacobian** *at each point.*




-----------
##  Recommended Notes and References

- [[Topological Manifold]]
- [[Coordinate Chart]]
- [[Transition Map and Smoothly Compatible]]

- [[Introduction to Smooth Manifolds by Lee]]