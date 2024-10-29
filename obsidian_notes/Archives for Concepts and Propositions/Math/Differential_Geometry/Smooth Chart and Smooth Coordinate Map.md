---
tags:
  - concept
  - math/differential_geometry
  - math/topology
keywords:
  - smooth_chart
  - smooth_coordinate_map
topics:
  - differential_geometry
name: Smooth Chart and Smooth Coordinate Map
date of note: 2024-05-06
---

## Concept Definition

>[!important]
>**Name**: Smooth Chart and Smooth Coordinate Map

>[!important] Definition
>If $M$ is a smooth manifold, any chart $(U, \varphi)$ contained in the given *maximal smooth atlas* is called a **smooth chart**, and the corresponding coordinate map $\varphi$ is called a **smooth coordinate map**. 

^4b2910

>[!important] Definition
>It is useful also to introduce the terms **smooth coordinate domain** or **smooth coordinate neighborhood** for the domain of a smooth coordinate chart. 
>
>- A **smooth coordinate ball** means a *smooth* coordinate domain whose image under a *smooth* coordinate map is a *ball* in Euclidean space. 
>
>- A **smooth coordinate cube** is defined similarly.

>[!info]
>We say a set $B \subseteq M$ is a **regular** *coordinate ball* if there is a *smooth* coordinate ball $B' \supseteq \overline{B}$ and a *smooth* coordinate map $\varphi: B' \rightarrow \mathbb{R}^n$ such that for some positive real numbers $r < r'$,
> $$
> \begin{align*}
> \varphi(B) = B_{r}(0), \quad \varphi(\overline{B}) = \overline{B_{r}}(0), \quad \varphi(B') = B_{r'}(0)
> \end{align*}
> $$

## Explanation





-----------
##  Recommended Notes and References

- [[Smooth Manifold]]
- [[Coordinate Chart]]
- [[Maximal Smooth Atlas]]
- [[Transition Map and Smoothly Compatible]]