---
tags:
  - concept
  - math/differential_geometry
keywords:
  - regular_point_smooth_map
  - regular_value_smooth_map
topics:
  - differential_geometry
name: Regular Point and Regular Value of Smooth Map
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Regular Point and Regular Value of Smooth Map

>[!important] Defintion
>If $\Phi: M \to N$ is a smooth map, a point $p \in M$ is said to be a **regular point** of $\Phi$ if 
>$$
>d\Phi_{p}: T_{p}M \to T_{\Phi(p)}N
>$$
>is **surjective**.

- [[Differential of a Smooth Map at Point]]
- [[Surjective Function]]

>[!important] Definition
>A point $c\in N$ is said to be a **regular value** of $\Phi$ if every point of *the level set*
>$$
>\Phi^{-1}(c)
>$$
>is a *regular point*.

>[!important] Definition
>A level set $\Phi^{-1}(c)$ is called a **regular level set** if $c$ is a *regular value* of $\Phi$.

>[!info]
>A *regular level set* is a level set consisting *entirely of regular points* of $\Phi$ (points $p$ such that $d\Phi_{p}$ is *surjective*).


## Explanation

>[!important]
>Every point of $M$ is a regular point of $\Phi$ if $\Phi$ is a **smooth submersion**.

- [[Smooth Submersion]]



>[!important] 
>The set of **regular points** of $\Phi$ is always an **open subset** of $M$. See [[Embedded Submanifold]]






-----------
##  Recommended Notes and References

- [[Rank of Smooth Map]]
- [[Differential of a Smooth Map at Point]]
- [[Smooth Map]]

- [[Critical Point and Critical Value of Smooth Map]]

- [[Introduction to Smooth Manifolds by Lee]]