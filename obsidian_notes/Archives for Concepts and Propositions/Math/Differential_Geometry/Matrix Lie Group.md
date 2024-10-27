---
tags:
  - concept
  - math/lie_group_algebra
  - math/differential_geometry
  - math/algebra
  - math/linear_algebra
keywords:
  - lie_group
  - matrix_lie_group
topics:
  - lie_group
  - differential_geometry
  - algebra
name: Matrix Lie Group
date of note: 2024-05-26
---

## Concept Definition

>[!important]
>**Name**: Matrix Lie Group

>[!important] Definition
>A **matrix Lie group** is a *subgroup* $G$ of the *general linear group* $\text{GL}(n; \mathbb{C})$ with the following property: 
>- For $\{A_{n}\}$ is any sequence in $G$, if $$A_{n} \to A$$ then 
>	- either $A\in G$ 
>	- or $A$ is *not invertible* i.e. $A\not\in \text{GL}(n; \mathbb{C})$
>
>In other words, a **matrix Lie group** is a *closed subgroup* of $\text{GL}(n; \mathbb{C})$.  

^e3a312

- [[Subgroup]]
- [[General Linear Group]]
- [[Topological Group]]
- [[Limit Point]]
- [[Closed Set]]


## Explanation

>[!info]
>Since both $\text{GL}(n; \mathbb{C})$ and $\text{GL}(n; \mathbb{R})$ are **Lie group**, all of their **close subgroups** are *Lie groups*.

- [[Lie Group]]

## Examples


>[!example]
>A **special linear group** of degree $n$, $\text{SL}(n, F)$  is a *matrix Lie group* with *matrix multiplication* as its multiplication operation. 
>
>It is a *closed subgroup* of $\text{GL}(n, F)$.

- [[Special Linear Group]]

>[!example]
>An **orthogonal group** of degree $n$, $\text{O}(n)$  is a *matrix Lie group* with *matrix multiplication* as its multiplication operation. 
>
>It is a *closed subgroup* of $\text{GL}(n, \mathbb{R})$.

- [[Orthogonal Group]]

>[!example]
>An **unitary group** of degree $n$, $\text{U}(n)$  is a *matrix Lie group* with *matrix multiplication* as its multiplication operation. 
>
>It is a *closed subgroup* of $\text{GL}(n, \mathbb{C})$.

- [[Unitary Group]]

- [[Special Orthogonal Group and Special Unitary Group]]


## Tangent Space as Lie Algebra

- [[Lie Algebra as Vector Space with Lie Bracket]]




-----------
##  Recommended Notes and References

- [[Matrix Exponential]]
- [[Lie Group]]
- [[Smooth Manifold]]
- [[Group]]
- [[Topological Group]]

- [[Introduction to Smooth Manifolds by Lee]]
- [[Lie Groups Lie Algebra and Representations by Hall]] pp 4