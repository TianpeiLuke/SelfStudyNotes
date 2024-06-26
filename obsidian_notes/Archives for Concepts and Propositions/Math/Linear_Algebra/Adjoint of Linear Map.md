---
tags:
  - concept
  - math/linear_algebra
keywords:
  - adjoint_operator_finite_linear_map
topics:
  - linear_algebra
name: Adjoint of Linear Map
date of note: 2024-05-09
---

## Concept Definition

>[!important]
>**Name**:  Adjoint of Linear Map

>[!important] Definition
>Let $V$ and $W$ be  *finite-dimensional vector spaces*, and  $A: V \to W$ be a linear transformation.  
>
>The **adjoint** of $A$, denoted by $A^{*}$, is the *linear map* from $W^{*}$ to $V^{*}$ defined by 
>$$
> \begin{align*}
>  \left(A^{*}f\right)(x) &= f\left(Ax\right)
> \end{align*} 
>$$ 
>for all $f \in W^{*}$, $x \in V$, or
>$$
>\left\langle  A^{*}f\,,\,  x  \right\rangle = \left\langle  f\,,\,Ax    \right\rangle
>$$
>where $\left\langle \,,\,\right\rangle$ is the *canonical dual pair*. 

- [[Dual Space of Finite Dimensional Vector Space]]
- [[Canonical Dual Pairing]]


## Explanation




## Matrix Representation

>[!important] 
>For *complex-valued* *finite dimensional vector space* $V$ and $W$, with given coordinate systems, $A$ is represented by matrix $\boldsymbol{A} = [a_{i,j}]$.
>
>The *adjoint* of $A$, $A^{*}$, is represented by the **complex conjugate transpose** of matrix $\boldsymbol{A}$:
>$$
>\boldsymbol{A}^{*} := \boldsymbol{A}^{H} = [\,\overline{a_{j,i}}\,] = \overline{\boldsymbol{A}^{T}}
>$$
>
>Note that
>$$
>\begin{align*}
>\left\langle \boldsymbol{x} \,,\,  \boldsymbol{A}^{*} \boldsymbol{f}   \right\rangle_{\mathbb{C}} = \left\langle  \boldsymbol{A}\boldsymbol{x} \,,\, \boldsymbol{f}     \right\rangle_{\mathbb{C}}
>\end{align*}
>$$

- [[Inner Product Space]]

>[!important]
>If $V$ and $W$ are all *real-valued* vector space, the *adjoint* of $A$ is represented by the **transpose** of matrix $\boldsymbol{A}$ 
>$$
>\boldsymbol{A}^{*} := \boldsymbol{A}^{T} = [\,a_{j,i}\,] 
>$$
>and
>$$
>\left\langle  \boldsymbol{x}\,,\,\boldsymbol{A}^{*}\boldsymbol{f}    \right\rangle = \left\langle  \boldsymbol{A}\boldsymbol{x}\,,\,\boldsymbol{f}    \right\rangle
>$$
>where $\left\langle \,,\, \right\rangle$ is the *bilinear form inner product*.



-----------
##  Recommended Notes and References

- [[Canonical Dual Pairing]]
- [[Linear Map]]

- [[Dual Space of Finite Dimensional Vector Space]]
- [[Vector Space over a Field]]

- [[Matrix Analysis by Horn]]
- [[Finite Dimensional Vector Spaces by Halmos]]