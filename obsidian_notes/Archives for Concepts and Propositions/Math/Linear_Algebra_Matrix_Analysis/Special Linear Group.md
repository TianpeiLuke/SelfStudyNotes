---
tags:
  - concept
  - math/linear_algebra
  - math/abstract_algebra
  - math/lie_group_algebra
  - math/differential_geometry
keywords:
  - special_linear_group
topics:
  - linear_algebra
  - algebra
  - lie_group
  - differential_geometry
name: Special Linear Group
date of note: 2024-05-26
---

## Concept Definition

>[!important]
>**Name**: Special Linear Group

>[!important] Definition
>The **special linear group** of degree $n$, denoted as $\text{SL}(n, F)$, is a *sub-group* of the *general linear group* consisting of matrices with a **determinant** equal to $1$
>
>$$
>\text{SL}(n. F) := \left\{ \boldsymbol{A} \in F^{n \times n}: \det(\boldsymbol{A}) = 1 \right\} 
>$$

- [[Matrix]]
- [[Determinant of Linear Transformation]]
- [[General Linear Group]]
- [[Surjective Injective Invertible Linear Map and Rank]]

## Explanation




## Algebraic Properties

>[!info]
>The *special linear group* is the **kernel** of the *Lie Homomorphism* $\det: \text{GL}(n, F) \to F$
>$$
>\text{SL}(n,F) = (\det)^{-1}(1)
>$$
>It is the **level set** under the *determiant map*

- [[Kernel of Group Homomorphism]]



>[!important]
>The special linear group is an **automorphism** on $V$.

- [[Automorphism between Groups]]




## Geometric Properties

>[!important]
>The special linear group $\text{SL}(V)$ is a **smooth manifold** and it is an **open smooth submanifold** in the general linear group $\text{GL}(V).$ 
>
>
>$$
>\text{SL}(n, F) \subset \text{GL}(n, F)
>$$
>

- [[Smooth Manifold]]
- [[Embedded Submanifold]]
- [[Linear Subspace]]

>[!important]
>The special linear group $\text{SL}(V)$ is a **Lie group** since it is both a *group* and a *smooth manifold*.

- [[Lie Group]]




-----------
##  Recommended Notes and References

- [[General Linear Group]]

- [[Matrix]]
- [[Determinant of Linear Transformation]]
- [[Vector Space over a Field]]
- [[Lie Group]]
	- [[Topological Group]]
	- [[Group]] 

- [[Matrix Analysis by Horn]]
- [[Introduction to Smooth Manifolds by Lee]]