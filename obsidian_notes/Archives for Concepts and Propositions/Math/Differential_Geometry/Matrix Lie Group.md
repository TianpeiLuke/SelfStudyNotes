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

- [[Subgroup]]
- [[General Linear Group]]


## Explanation

>[!important]
>The condition above means that a *matrix Lie group* is a **closed subgroup** of $\text{GL}(n; \mathbb{C})$.

- [[Topological Group]]
- [[Closed Set]]

## Examples

>[!example]
>A **general linear group** of vector field $V$, $\text{GL}(V)$  is a *Lie group* with function composition as its *multiplication operation*. 
>
>For finite dimensional space $V$, a **general linear group** of *degree* $n$  $\text{GL}(n, F)$ is a Lie group with *matrix multiplication* as the multiplication operation.

[[General Linear Group]] 

>[!example]
>A **special linear group** of degree $n$, $\text{SL}(n, F)$  is a *Lie group* with *matrix multiplication* as its multiplication operation. 
>
>It is a subgroup of $\text{GL}(n, F)$.

- [[Special Linear Group]]

>[!example]
>An **orthogonal group** of degree $n$, $\text{O}(n)$  is a *Lie group* with *matrix multiplication* as its multiplication operation. 
>
>It is a subgroup of $\text{GL}(n, \mathbb{R})$.

- [[Orthogonal Group]]

>[!example]
>An **unitary group** of degree $n$, $\text{U}(n)$  is a *Lie group* with *matrix multiplication* as its multiplication operation. 
>
>It is a subgroup of $\text{GL}(n, \mathbb{C})$.

- [[Unitary Group]]

>[!example]
>A  $n$-dimensional **Euclidean space** $\mathbb{R}^n$ is a *Lie Group* with *vector addition* as its multiplication operation. 
>
>Similarly, $\mathbb{C}^n$ is also a *Lie Group*.


>[!example]
>A one-dimensional **circle** $\mathbb{S}^1$ is a *smooth manifold* and a group under *complex multiplication*.
>
>With appropriate *angle functions as local coordinates*  on open subsets of $\mathbb{S}^1$, multiplication and inversion have the smooth coordinate representation
>$$
>(\theta_{1}, \theta_{2}) \mapsto \theta_{1} + \theta_{2}, \qquad \theta \mapsto -\theta
>$$ 
>Thus $\mathbb{S}^1$ is a Lie group, called the **cycle group**.


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