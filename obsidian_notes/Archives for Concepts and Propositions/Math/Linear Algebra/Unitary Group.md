---
tags:
  - concept
  - math/linear_algebra
  - math/algebra
  - math/lie_group_algebra
  - math/differential_geometry
keywords:
  - unitary_group
topics:
  - linear_algebra
  - algebra
  - lie_group
  - differential_geometry
name: Unitary Group
date of note: 2024-05-26
---

## Concept Definition

>[!important]
>**Name**: Unitary Group

>[!important] Definition
>The set of all $n\times n$ *complex unitary matrices* together with matrix multiplication forms a group, called the **unitary group**. It is denoted as $U(n)$.
>
>$$
>U(n) := \left\{ \boldsymbol{U} \in M(n, \mathbb{C}): \left\langle  \boldsymbol{Ux}\,,\,\boldsymbol{Uy} \right\rangle_{\mathbb{C}}  = \left\langle  \boldsymbol{x}\,,\,\boldsymbol{y} \right\rangle_{\mathbb{C}}, \;\;  \forall \boldsymbol{x}, \boldsymbol{y} \in \mathbb{C}^n \right\} 
>$$

- [[Matrix]]
- [[Unitary and Orthogonal Transformation]]
- [[Orthogonality in Inner Product Space]]
- [[Isometry and Isometric isomorphism]]
- [[Orthogonal Group]]

## Explanation



## Algebraic Properties

>[!important]
>The unitary group is a **linear subspace** of general linear group
>$$
>U(n) \subset \text{GL}(n, \mathbb{C})
>$$

- [[Linear Subspace]]
- [[Vector Space over a Field]]

>[!info]
>$U(n)$ is the set of **isometric isomorphism** on $\mathbb{C}^n$, while $\text{GL}(n, \mathbb{C})$ is the set of **isomorphism** on $\mathbb{C}^n$

- [[Isometry and Isometric isomorphism]]

>[!info]
>The determinant of an unitary matrix can be $\pm 1$. Thus $U(n)$ is not a subspace of $\text{SL}(n, \mathbb{C})$


>[!important]
>The unitary group is an **automorphism** on $\mathbb{C}^n$.

- [[Automorphism between Groups]]

>[!info]
>The unitary group is the preimage of $\Phi: \boldsymbol{A} \mapsto \boldsymbol{A}^{*}\boldsymbol{A}$, i.e it is the **level set**
>$$
>O(n) = (\Phi)^{-1}(I_{n})
>$$
>where $I_{n}$ is the identity matrix 



## Geometric Properties

>[!important]
>The unitary group $U(n)$ is a **smooth manifold** and it is an **embedded smooth submanifold** in the general linear group $\text{GL}(n, \mathbb{C}).$ 
>
>
>$$
>U(n) \subset \text{GL}(n, \mathbb{C})
>$$
>

- [[Smooth Manifold]]
- [[Embedded Submanifold]]

>[!important]
>The orthogonal group $U(n)$ is a **Lie group** since it is both a *group* and a *smooth manifold*.

- [[Lie Group]]




-----------
##  Recommended Notes and References

- [[Orthogonal Group]]
- [[General Linear Group]]
- [[Special Linear Group]]

- [[Matrix]]
- [[Determinant of Linear Transformation]]

- [[Lie Group]]
	- [[Topological Group]]
	- [[Group]]
- [[Vector Space over a Field]]


- [[Matrix Analysis by Horn]]
- [[Introduction to Smooth Manifolds by Lee]]