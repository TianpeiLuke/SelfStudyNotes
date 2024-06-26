---
tags:
  - concept
  - math/differential_geometry
keywords:
  - local_diffeomorphism
topics:
  - differential_geometry
name: Local Diffeomorphisms
date of note: 2024-05-20
---

## Concept Definition

>[!important]
>**Name**: Smooth Embedding

>[!important] Definition
>If $M$ and $N$ are smooth manifolds with or without boundary. 
>
>A map $F: M \rightarrow N$ is called a **local diffeomorphism** if *every point* $p \in M$ has a *neighborhood* $U$ such that $F(U)$ is *open* in $N$ and the *restriction* $F|_{U}: U \rightarrow F(U)$ is a *diffeomorphism*. 

- [[Diffeomorphism]]
- [[Open Map]]

## Explanation

>[!info]
>The **bijection** from local diffeomorphism is defined **within local neighborhood**. If it is global, then we have diffeomoprhism.


## Properties

>[!important] Proposition
>- Every **composition** of *local diffeomorphisms* is a *local diffeomorphism*.
>- Every **finite product** of local diffeomorphisms between smooth manifolds is a local diffeomorphism.
>- Every local diffeomorphism is a **local homeomorphism** and an **open map**.
>- The **restriction** of a *local diffeomorphism* to an **open submanifold** with or without boundary is a *local diffeomorphism*.
>- Every **diffeomorphism** is a local diffeomorphism.
>- Every **bijective local diffeomorphism** is a **diffeomorphism**.
>- A map between smooth manifolds with or without boundary is a local diffeomorphism **if and only if** in a neighborhood of each point of its domain, it has a **coordinate representation** that is a *local diffeomorphism*.

- [[Homeomorphism]]
- [[Open Map]]

## Inverse Function Theorem for Manifolds

>[!important] Inverse Function Theorem for Manifolds
> Suppose $M$ and $N$ are *smooth manifolds*, and $F: M \rightarrow N$ is a *smooth map.* 
> 
> If  $p \in M$ is a *point* such that $dF_p$ is **invertible**, then there are **connected neighborhoods** $U_0$ of $p$ and $V_0$ of $F(p)$ such that $$F|_{U_0}: U_0 \rightarrow V_0$$ is a **diffeomorphism.**

>[!info]
>From this theorem
>$$
>dF_{p} \text{ is *bijective* at some point} \implies F \text{ *locally smooth bijective* with *smooth inverse*}
>$$
>
>Thus **the differential of a smooth map** fully characterizes **the local property** of map.

>[!info]
>$$
>F \text{ diffeomorphism } \implies dF_{p} \text{ bijective at every point}
>$$


>[!important]
>It is important to notice that we have stated Theorem above **only for manifolds without boundary**. 
>
>In fact, it can **fail** for a map whose domain has nonempty boundary.

## From Submersion and Immersion

>[!important] Proposition
>Suppose $M$ and $N$ are smooth manifolds (without boundary), and $F: M \rightarrow N$ is a *map*.
>
> 
> - $F$ is a **local diffeomorphism** *if and only if* it is *both* a **smooth immersion** and a **smooth submersion**.
> - If $$\text{dim }M = \text{dim }N$$ and $F$ is *either* a **smooth immersion** or a **smooth submersion**, then it is a **local diffeomorphism.**

- [[Smooth Submersion]]
- [[Smooth Immersion]]

>[!info]
>By [[Smooth Submersion#Property of Smooth Submersion]], a smooth submersion is an *open map*. 
>
>Then if $F$ is both smooth submersion and smooth immersion, it has an *invertible differential* $dF_{p}$ everywhere. Thus it is a local diffeomorphism by definition. 





-----------
##  Recommended Notes and References


- [[Diffeomorphism]]

- [[Introduction to Smooth Manifolds by Lee]]