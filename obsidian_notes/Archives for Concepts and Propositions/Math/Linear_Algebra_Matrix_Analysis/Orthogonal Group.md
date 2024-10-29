---
tags:
  - concept
  - math/linear_algebra
  - math/abstract_algebra
  - math/lie_group_algebra
  - math/differential_geometry
keywords:
  - orthogonal_group
topics:
  - linear_algebra
  - algebra
  - lie_group
  - differential_geometry
name: Orthogonal Group
date of note: 2024-05-26
---

## Concept Definition

>[!important]
>**Name**: Orthogonal Group

>[!important] Definition
>The set of all $n\times n$ *real orthogonal matrices* together with matrix multiplication forms a group, called the **orthogonal group** of *degree $n$*. It is denoted as $O(n)$.
>
>$$
>O(n) := \left\{ U \in M(n, \mathbb{R}): \left\langle  Ux\,,\,Uy \right\rangle  = \left\langle  x\,,\,y \right\rangle, \;\; \forall x, y \in \mathbb{R}^n \right\} 
>$$
>or
>$$
>O(n) := \left\{ U \in M(n, \mathbb{R}): UU^{T} = U^{T}U = I_{n} \right\} 
>$$

- [[Unitary and Orthogonal Transformation]]
- [[Orthogonality in Inner Product Space]]
- [[Isometry and Isometric isomorphism]]
- [[Inner Product Space]]

## Explanation



## Algebraic Properties

>[!important]
>The orthogonal group is a **linear subspace** of general linear group
>$$
>O(n) \subset \text{GL}(n, \mathbb{R})
>$$

- [[Linear Subspace]]
- [[Vector Space over a Field]]

>[!info]
>$O(n)$ is the set of **isometric isomorphism** on $\mathbb{R}^n$, while $\text{GL}(n, \mathbb{R})$ is the set of **isomorphism** on $\mathbb{R}^n$

- [[Isometry and Isometric isomorphism]]

>[!info]
>The determinant of an orthogonal matrix can be $\pm 1$. Thus $O(n)$ is not a subspace of $\text{SL}(n, \mathbb{R})$


>[!important]
>The orthogonal group is an **automorphism** on $\mathbb{R}^n$.

- [[Automorphism between Groups]]

>[!info]
>The orthogonal group is the preimage of $\Phi: \boldsymbol{A} \mapsto \boldsymbol{A}^T\boldsymbol{A}$, i.e. it is the **level set**
>$$
>O(n) = (\Phi)^{-1}(I_{n})
>$$
>where $I_{n}$ is the identity matrix 



## Geometric Properties

>[!important]
>The orthogonal group $O(n)$ is a **smooth manifold** and it is an **embedded smooth submanifold** in the general linear group $\text{GL}(n, \mathbb{R}).$ 
>
>
>$$
>O(n) \subset \text{GL}(n, \mathbb{R})
>$$
>

- [[Smooth Manifold]]
- [[Embedded Submanifold]]
- [[Linear Subspace]]

>[!important]
>The orthogonal group $O(n)$ is a **Lie group** since it is both a *group* and a *smooth manifold*.






-----------
##  Recommended Notes and References

- [[Unitary Group]]
- [[General Linear Group]]
	- [[Special Linear Group]]

- [[Matrix]]
- [[Linear Map]]
- [[Determinant of Linear Transformation]]
- [[Vector Space over a Field]]
- [[Stiefel Manifold]]
- [[Lie Group]]
	- [[Topological Group]]
	- [[Group]]


- [[Matrix Analysis by Horn]]
- [[Introduction to Smooth Manifolds by Lee]]