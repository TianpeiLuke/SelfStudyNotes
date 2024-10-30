---
tags:
  - concept
  - math/lie_group_algebra
  - math/differential_geometry
  - math/abstract_algebra
  - math/linear_algebra
keywords:
  - lie_group
topics:
  - lie_group
  - differential_geometry
  - algebra
name: Lie Group
date of note: 2024-05-26
---

## Concept Definition

>[!important]
>**Name**: Lie Group

>[!important] Definition
>A **Lie group** is a *smooth manifold* $G$ (without boundary) that is also a *group* in the algebraic sense, with the property that 
>- the *multiplication map* $m: G \times G \to G$, given by $$m(g, h) = gh$$   
>- and *inversion map* $i: G\to G$, given by $$i(g) = g^{-1}$$ 
>  
>are both *smooth*.

- [[Smooth Manifold]]
- [[Group]]

## Explanation

>[!important]
>A Lie group is a **topological group**.

- [[Topological Group]]

## Examples

>[!example]
>A **general linear group** of vector field $V$, $\text{GL}(V)$  is a *Lie group* with function composition as its *multiplication operation*. 
>
>For finite dimensional space $V$, a **general linear group** of *degree* $n$  $\text{GL}(n, F)$ is a Lie group with *matrix multiplication* as the multiplication operation.

- [[General Linear Group]] 

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


## Matrix Lie Group

![[Matrix Lie Group#^e3a312]]

- [[Matrix Lie Group]]

## Tangent Space as Lie Algebra

- [[Lie Algebra as Vector Space with Lie Bracket]]




-----------
##  Recommended Notes and References


- [[Smooth Manifold]]
- [[Group]]

- [[Topological Group]]

- [[Introduction to Smooth Manifolds by Lee]] pp 151 - 157
- [[Lie Groups Lie Algebra and Representations by Hall]] pp 25