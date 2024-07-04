---
tags:
  - concept
  - math/linear_algebra
keywords:
  - self_adjoint_linear_map
topics:
  - linear_algebra
name: Self-Adjoint Linear Map
date of note: 2024-05-09
---

## Concept Definition

>[!important]
>**Name**:  Self-Adjoint Linear Map

>[!important] Definition
>Let $V$ be a *finite-dimensional inner product spaces*.
>
>A linear transformation  $A: V \to V$ is said to be **self-adjoint** if 
>$$
>A = A^{*}
>$$
>where $A^{*}: V^{*} \to V^{*}$ is the adjoint of $A$. 
>
>Note that $V \simeq V^{*}$ for finite dimensional inner product space.

- [[Adjoint of Linear Map]]
- [[Dual Space of Finite Dimensional Vector Space]]
- [[Inner Product Space]]


## Explanation

>[!info]
>For self-adjoint $A$,
>$$
>\left\langle  x\,,\,Ay    \right\rangle = \left\langle Ax \,,\,y    \right\rangle
>$$


## Matrix Representation

>[!important] 
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


>[!important]
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





-----------
##  Recommended Notes and References

- [[Canonical Dual Pairing]]
- [[Linear Map]]

- [[Dual Space of Finite Dimensional Vector Space]]

- [[Normal Transformation]]

- [[Inner Product Space]]
- [[Vector Space over a Field]]

- [[Matrix Analysis by Horn]]
- [[Finite Dimensional Vector Spaces by Halmos]]