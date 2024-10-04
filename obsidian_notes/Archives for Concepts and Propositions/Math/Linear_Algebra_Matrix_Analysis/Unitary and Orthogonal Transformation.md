---
tags:
  - concept
  - math/linear_algebra
keywords:
  - unitary_transform
  - orthogonal_transform
topics:
  - linear_algebra
name: Unitary and Orthogonal Transformation
date of note: 2024-05-09
---

## Concept Definition

>[!important]
>**Name**: Unitary and Orthogonal Transformation

>[!important] Definition
>Let $V$ be a *complex-valued* finite-dimensional inner product space. A *linear transformation* $A$ on $V$ is said to be an **unitary transformation**  if
>$$
> \begin{align*}
> A^{*} = A^{-1}
> \end{align*}
>$$ 
>or, equivalently
>$$
> \begin{align*}
> A^{*}A = A\,A^{*} = I
> \end{align*}
>$$

- [[Adjoint of Linear Map]]
- [[Inner Product Space]]

>[!important] Definition
>If $V$ is a *real-valued* finite dimensional inner product space, $A: V\to V$ is said to be an **orthogonal transformation** if 
>$$
>A^T = A^{-1}
>$$
>or
>$$
>A^T A = A A^T = I
>$$


>[!important]
>- The matrix representation of a *unitary transform* is called a **unitary matrix** $\boldsymbol{U}$, i.e.
>$$
>\boldsymbol{U}^H \boldsymbol{U} = \boldsymbol{U} \boldsymbol{U}^H = \boldsymbol{I}
>$$ 
>- The matrix representation of an *orthogonal transform* is called an **orthogonal matrix** $\boldsymbol{U}$, i.e.
>$$
>\boldsymbol{U}^T \boldsymbol{U} = \boldsymbol{U} \boldsymbol{U}^T = \boldsymbol{I}
>$$ 

## Explanation

>[!info]
>- The space of all orthogonal matrix of degree $n$ is called the **orthogonal group** $O(n)$
>- The space of all unitary matrix of degree $n$ is called the **unitary group** $U(n)$

- [[Orthogonal Group]]
- [[Unitary Group]]

>[!info]
>Both *unitary transform* and *orthogonal transform* are **isometries** in their corresponding inner product space.
>
>That is, for any $x, y \in V$,
>$$
>\left\langle  Ax\,,\,Ay    \right\rangle = \left\langle  x\,,\,y    \right\rangle
>$$
>

- [[Isometry and Isometric isomorphism]]

## Equivalent Definition


>[!important] Proposition (Equivalent Definition)
>The following conditions on a *linear transformation* $A$ on an *inner product space* $V$ are **equivalent**:
>- $A$ is **unitary**, i.e.
>  $$
>  A^{*}A = I
> $$
>- $A$ is an **isometry** on $V$, i.e. for any $x, y \in V$ 
>  $$
>  \left\langle Ax\,,\,Ay \right\rangle = \left\langle  x\,,\,y \right\rangle
> $$
> where $\left\langle  \,,\,    \right\rangle$ is the inner product defined in $V$
>- $A$ **preserve length** on $V$, i.e. for any $x\in V$
>  $$
>  \lVert A x\rVert = \lVert x \rVert  
> $$ 
> where $\lVert \cdot \rVert$ is the induced norm by inner product.

- [[Finite Dimensional Vector Spaces by Halmos]] pp 142


>[!important] Proposition
>If $U\in M_{n}$, the following are **equivalent**:
>- $U$ is **unitary**.
>- $U$ is **nonsingular** and $U^{*} = U^{-1}$.
>- $$UU^{*} = I.$$
>- $U^{*}$ is **unitary**.
>- The *columns* of $U$ are **orthonormal**.
>- The *rows* of $U$ are **orthonormal**.
>- For all $x\in \mathbb{C}^{n}$, $$\lVert x \rVert_{2} = \lVert Ux \rVert_{2},$$ that is, $x$ and $Ux$ have the **same Euclidean norm**.

- [[Isometry and Isometric isomorphism]]
- [[Matrix Analysis by Horn]] pp 84


## Examples

![[Givens Rotations and Jacobi Rotations#^956c04]]

- [[Givens Rotations and Jacobi Rotations]]

![[Householder Transformation and Householder Reflection#^bc2fa5]]

- [[Householder Transformation and Householder Reflection]]





-----------
##  Recommended Notes and References

- [[Adjoint of Linear Map]]
- [[Inner Product Space]]

- [[Normal Transformation]]

- [[Linear Map]]
- [[Vector Space over a Field]]


- [[Matrix Analysis by Horn]] pp 83 - 85
- [[Finite Dimensional Vector Spaces by Halmos]] pp 143
- [[Matrix Computations by Golub]]
- [[Matrix CookBook by Petersen]] pp 49