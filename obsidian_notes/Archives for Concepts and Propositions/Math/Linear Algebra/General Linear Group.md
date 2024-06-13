---
tags:
  - concept
  - math/linear_algebra
  - math/algebra
  - math/lie_group_algebra
keywords:
  - general_linear_group
topics:
  - linear_algebra
  - algebra
  - lie_group
  - differential_geometry
name: General Linear Group
date of note: 2024-05-26
---

## Concept Definition

>[!important]
>**Name**: General Linear Group

>[!important] Definition
>The set of all $n \times n$ *invertible matrices* with entries from field $F$, together with matrix multiplication operation $\cdot$,  is called the **general linear group** of *degree $n$.*
>
>It is denoted as $\text{GL}(n, F)$.
>
>$$
>\text{GL}(n, F) := \left( \left\{\boldsymbol{A} \in F^{n \times n}: \text{rank}(\boldsymbol{A}) = n  \right\}    \;,\; \cdot\right)
>$$
>where $\cdot: M(n, F) \times M(n, F) \to M(n, F)$ is the *matrix multiplication*:
>$$
>\boldsymbol{A}\cdot \boldsymbol{B} = \left[\sum_{j=1}^n a_{i,j}b_{j, k}  \right]_{i,k}  
>$$

- [[Matrix]]

>[!important] Definition
>Let $V$ be a vector space over field $F$. 
>
>The set of all *bijective linear transformation* $f: V \to V$ on $V$ together with *functional composition* $\circ$ forms a *group*, called the **general linear group** *of* $V$. It is denoted as $\text{GL}(V)$.
>
>$$
>\text{GL}(V) := \left(\left\{f: V\to V: f \text{ bijective, linear}  \right\}, \circ \right)
>$$
>where $\circ: V^V \times V^v \to V^{V}$ is the *function composition*:
>$$
>(f \circ g)(v) = f(g(v)) 
>$$

- [[Linear Isomorphism]]
- [[Linear Map]]
- [[Bijective Function and Inverse Function]]
- [[Group]]



>[!important] Definition
>If $V$ is *finite dimensional* with dimension $n$, then $\text{GL}(V)$ is **isomorphic** to $\text{GL}(n, F)$. 
>$$
>\text{GL}(V) \simeq \text{GL}(n, F)
>$$

- [[Isomorphism between Groups]]
- [[Isometry and Isometric isomorphism]]

## Explanation



## Algebraic Properties


>[!important]
>The general linear group is an **automorphism** on $V$. Thus it is also denoted  $\text{Aut}(V)$

- [[Automorphism between Groups]]


>[!important]
>The general linear group $\text{GL}(V)$ together with function addition $+$ and scalar multiplication  forms a **vector space** over field $F$
>
>If $V$ is $n$-dimensional, then $\text{GL}(V)$ is **$n^2$-dimensional vector space**.

- [[Vector Space over a Field]]

## Geometric Properties

>[!important]
>If $V$ is a *topological* vector space, the general linear group $\text{GL}(V)$ is a **smooth manifold** and it is an **open smooth submanifold** in the space of all linear operators $L(V, V).$ 
>
>Similarly, denote $M(n, F)$ be the space of all $n \times n$ matrices with $F$-field entities, then
>$$
>\text{GL}(n, F) \subset M(n, F)
>$$
>is a **$n^2$-dimensional open submanifold**

- [[Smooth Manifold]]
- [[Embedded Submanifold]]
- [[Linear Subspace]]

>[!important]
>The general linear group $\text{GL}(V)$ is a **Lie group** since it is both a *group* and a *smooth manifold*.

- [[Lie Group]]




-----------
##  Recommended Notes and References

- [[Linear Isomorphism]]
- [[Vector Space over a Field]]

- [[Lie Group]]
	- [[Topological Group]]
	- [[Group]]


- [[Matrix Analysis by Horn]]
- [[Introduction to Smooth Manifolds by Lee]]