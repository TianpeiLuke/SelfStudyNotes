---
tags:
  - concept
  - math/linear_algebra
  - math/abstract_algebra
  - math/lie_group_algebra
  - math/differential_geometry
keywords:
  - special_othogonal_group
topics:
  - linear_algebra
  - algebra
  - lie_group
  - differential_geometry
name: Special Orthogonal Group
date of note: 2024-05-26
---

## Concept Definition

>[!important]
>**Name**: Special Orthogonal Group

>[!important] Definition
>The set of all $n\times n$ *real orthogonal matrices* whose *determinant equal to $1$*, together with matrix multiplication forms a group, called the **special orthogonal group** *of degree $n$*. It is denoted as $SO(n)$.
>
>$$
>SO(n) := \left\{ U \in M(n, \mathbb{R}): \det(U)=1,\quad \left\langle Ux\,,\,Uy \right\rangle  = \left\langle  x\,,\,y \right\rangle, \;\; \forall x, y \in \mathbb{R}^n \right\} 
>$$

- [[Matrix]]
- [[Isometry and Isometric isomorphism]]
- [[Determinant of Linear Transformation]]

>[!important] Definition
>The set of all $n\times n$ *unitary matrices* whose *determinant equal to $1$*, together with matrix multiplication forms a group, called the **special unitary group** *of degree $n$*. It is denoted as $SU(n)$.
>
>$$
>SU(n) := \left\{U \in M(n, \mathbb{C}): \det(U)=1,\quad \left\langle  Ux\,,\,Uy \right\rangle  = \left\langle  x\,,\,y\right\rangle, \;\; \forall x, y \in \mathbb{C}^n \right\} 
>$$


## Explanation



## Algebraic Properties

>[!important]
>The orthogonal group is an intersection of **two linear subspaces** of general linear group
>$$
>SO(n) =  O(n) \cap \text{SL}(n, \mathbb{R})
>$$
>and
>$$
>SU(n) =  U(n) \cap \text{SL}(n, \mathbb{C})
>$$

- [[Orthogonal Group]]
- [[Unitary Group]]
- [[Special Linear Group]]
- [[Linear Subspace]]



-----------
##  Recommended Notes and References

- [[Orthogonal Group]]
- [[Unitary Group]]
- [[Special Linear Group]]
- [[Linear Subspace]]
- [[Stiefel Manifold]]

- [[Matrix]]
- [[Determinant of Linear Transformation]]
- [[Vector Space over a Field]]

- [[Lie Group]]
	- [[Topological Group]]
	- [[Group]]

- [[Matrix Analysis by Horn]]
- [[Introduction to Smooth Manifolds by Lee]]