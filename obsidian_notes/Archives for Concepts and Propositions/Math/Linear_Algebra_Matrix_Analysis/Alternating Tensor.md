---
tags:
  - concept
  - math/linear_algebra
  - math/differential_geometry
keywords:
  - alternating_tensor
topics:
  - differential_geometry
  - linear_algebra
name: Alternating Tensors
date of note: 2024-05-14
---

## Concept Definition

>[!important]
>**Name**: Alternating Tensors

>[!important] Definition
>Assume that $V$ is a finite-dimensional real vector space. 
>
>A *covariant k-tensor* $\alpha$ on V is said to be **alternating** (or **antisymmetric** or **skew-symmetric**) if it *changes sign* whenever two of its arguments are *interchanged*.
>
>  This means that for all vectors $v_1,\ldots,v_k \in V$ and every pair of distinct indices $i$, $j$ it satisfies
> $$ 
> \begin{align*}
> \alpha\left(v_1, \ldots, v_i, \ldots, v_j, \ldots, v_k\right) &= -\alpha\left(v_1, \ldots, v_j, \ldots, v_i, \ldots, v_k\right)
> \end{align*}
>$$
>

>[!info]
> **Alternating covariant k-tensors** are also variously called **exterior forms**, **multicovectors**, or **k-covectors**. 

>[!important] Definition
>The subspace of **all alternating covariant $k$-tensors** on $V$ is denoted by $$\Lambda^{k}(V^{*}) \subseteq T^k(V^{*}).$$

- [[Covariant Tensor on Vector Space]]


## Explanation


## Properties

>[!important] Lemma
>The following statements are **equivalent** for a covariant $k$-tensor $\alpha$:
> 
>- $\alpha$ is **alternating**;
>- For any vectors $v_1,\ldots,v_k \in V$, and any *permutation* $\sigma \in S_k$
>$$
> \begin{align*}
> \alpha\left(v_{\sigma(1)}, \ldots,  v_{\sigma(k)}\right) &=(\text{sgn }\sigma)\alpha\left(v_1, \ldots,  v_k\right)
> \end{align*}
>$$ 
>- With respect to any basis, the components $\alpha_{i_1,\ldots,i_k}$ of $\alpha$ *change sign* whenever *two indices are interchanged*.

- [[Sign of Permutation]]
- [[Determinant of Linear Transformation]]

## Examples




-----------
##  Recommended Notes and References

- [[Multilinear Function]]
- [[Symmetric Tensor]]

- [[Introduction to Smooth Manifolds by Lee]]
- [[Finite Dimensional Vector Spaces by Halmos]]