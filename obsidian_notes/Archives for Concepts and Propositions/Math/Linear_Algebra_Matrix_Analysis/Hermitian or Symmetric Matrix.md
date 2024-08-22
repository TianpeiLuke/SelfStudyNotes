---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
keywords:
  - self_adjoint_linear_map
  - hermitian_matrix
  - symmetric_matrix
topics:
  - linear_algebra
name: Self-Adjoint Linear Map
date of note: 2024-05-09
---

## Concept Definition

>[!important]
>**Name**:  Hermitian or Symmetric Matrix

>[!important] Definition (Hermitian Matrix)
>For *complex-valued* *finite dimensional inner product space* $V$, with given coordinate systems.
>
>A *self-adjoint* $A$  is represented by the **Hermitian matrix** $\boldsymbol{A}$:
>$$
> \boldsymbol{A} = \boldsymbol{A}^{H} \iff   a_{i,j} = \overline{a_{j,i}}, \quad \forall i,j=1 \,{,}\ldots{,}\,n
>$$
>
>Note that for self-adjoint $A$
>$$
>\begin{align*}
>\left\langle \boldsymbol{x} \,,\,  \boldsymbol{A} \boldsymbol{y}   \right\rangle_{\mathbb{C}} = \left\langle  \boldsymbol{A}\boldsymbol{x} \,,\, \boldsymbol{y}     \right\rangle_{\mathbb{C}}
>\end{align*}
>$$

^9ff922

- [[Self-Adjoint Linear Map]]

>[!important] Definition
>If $V$ is a *real-valued* inner product space, the *self-adjoint* $A$ is represented by the **symmetric matrix**  $\boldsymbol{A}$ 
>$$
>\boldsymbol{A} = \boldsymbol{A}^{T} \iff  a_{i,j} = a_{j,i}, \quad i,j=1 \,{,}\ldots{,}\, n
>$$
>and
>$$
>\begin{align*}
>\left\langle \boldsymbol{x} \,,\,  \boldsymbol{A} \boldsymbol{y}   \right\rangle_{\mathbb{R}} = \left\langle  \boldsymbol{A}\boldsymbol{x} \,,\, \boldsymbol{y}     \right\rangle_{\mathbb{R}}
>\end{align*}
>$$

^d8f505

>[!important] Proposition
>A matrix $M\in \mathbb{R}^{2n \times 2n}$ is a **symmetric matrix** if it satisfies the following *equation*
>$$
>J\,M\,J^{T} = M^{T} 
>$$
>where $$J = \left[ \begin{array}{cc}0 & I_{n} \\ I_{n} &0\end{array} \right] $$ is the **permutation matrix**.

^657918



- [[Adjoint of Linear Map]]
- [[Dual Space of Finite Dimensional Vector Space]]
- [[Inner Product Space]]


## Explanation

>[!info]
>For self-adjoint $A$,
>$$
>\left\langle  x\,,\,Ay    \right\rangle = \left\langle Ax \,,\,y    \right\rangle
>$$





-----------
##  Recommended Notes and References

- [[Canonical Dual Pairing]]
- [[Linear Map]]

- [[Dual Space of Finite Dimensional Vector Space]]

- [[Normal Transformation]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]

- [[Inner Product Space]]
- [[Vector Space over a Field]]

- [[Matrix Analysis by Horn]]
- [[Finite Dimensional Vector Spaces by Halmos]]
- [[Matrix Computations by Golub]] pp 29