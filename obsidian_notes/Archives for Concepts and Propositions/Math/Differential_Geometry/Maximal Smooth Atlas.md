---
tags:
  - concept
  - math/differential_geometry
  - math/topology
keywords:
  - maximal_smooth_atlas
topics:
  - differential_geometry
name: Maximal Smooth Atlas
date of note: 2024-05-06
---

## Concept Definition

>[!important]
>**Name**: Maximal Smooth Atlas

>[!important] Definition
>A *smooth atlas* $\mathcal{A}$ on $M$ is **maximal** if it is *not properly contained* in any *larger* smooth atlas. 
>
>This just means that any chart that is *smoothly compatible* with *every chart* in $\mathcal{A}$ is already in $\mathcal{A}$. (Such a smooth atlas is also said to be **complete.**)


## Explanation

- It is generally *not very convenient* to define a smooth structure by explicitly describing a maximal smooth atlas, because such an atlas contains very many charts. 
- Fortunately, we need only specify *some* smooth atlas, as the next proposition shows.

>[!important] Proposition
>
> Let $M$ be a topological manifold.
> 1. *Every* smooth atlas $\mathcal{A}$ for $M$ is contained in a **unique** *maximal smooth atlas*, called **the smooth structure determined by $\mathcal{A}$**.
> 2. Two smooth atlases for $M$ *determine the same* smooth structure if and only if *their union* is a smooth atlas.




-----------
##  Recommended Notes and References

- [[Smooth Atlas]]
- [[Transition Map and Smoothly Compatible]]

- [[Introduction to Smooth Manifolds by Lee]]