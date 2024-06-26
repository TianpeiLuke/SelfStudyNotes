---
tags:
  - concept
  - math/linear_algebra
  - math/differential_geometry
keywords:
  - determinant
topics:
  - linear_algebra
  - differential_geometry
name: Determinant
date of note: 2024-05-14
---

## Concept Definition

>[!important]
>**Name**: Determinant

>[!important]
>Let $V$ be a $n$-dimensional *vector space* and $A: V \to V$ be a *linear transformation* on $V$. Under a set of basis vectors $(\epsilon_{1} \,{,}\ldots{,}\, \epsilon_{n})$, $A$ can be represented as a matrix
>$$
>\left[
>\begin{array}{cccc}
> a_{1,1} & a_{1,2} & \cdots & a_{1,n}\\ 
> a_{2,1} & a_{2,2} & \cdots & a_{2,n}\\ 
> \cdots & \cdots & \cdots & \cdots  \\ 
> a_{n,1} & a_{n,2} & \cdots & a_{n,n}
> \end{array}
\right].
>$$
>
>
>Let $\sigma_{n}$ be a *permutation* of set $\{1 \,{}\ldots{}\, n\}$ and $\text{sgn}(\sigma)$ is the *sign* of permutation group.The set of all such permutations, called the **symmetric group**, is commonly denoted $S_{n}$.
>
>The **determinant** of $A$ is defined as 
>$$
>\begin{align*}
>\det(A) &:= \sum_{\sigma \in S_{n}} \text{sgn}(\sigma) a_{1,\sigma(1)}a_{2,\sigma(2)} \cdots a_{n,\sigma(n)}\\
>&= \sum_{\sigma \in S_{n}}\left(\text{sgn}(\sigma)\prod_{i=1}^{n}a_{i,\sigma(i)}\right) 
\end{align*}
>$$

- [[Linear Map]]
## Explanation

>[!info]
>The **determinant** of $A \in L(V, V)$ is an *alternating covariant n-tensors*.
>
>$$
>\det(A) = \omega_{1} \,{\wedge}\ldots{\wedge}\,\omega_{n}, 
>$$
>where $\omega_{i} := \left\langle  A\epsilon_{i}\,,\, \cdot   \right\rangle$ is a *covector* on $V$ and $A\epsilon_{i}$ is the image of linear map on $i$-th basis vector, i.e. the $i$-th row of $\boldsymbol{A}$.


- [[Alternating Tensor]]

## Generalization to Alternating Covariant k-tensor

- [[Elementary Alternating Tensor]]

## Algebraic Property

>[!important] Proposition
>The **determinant function** $\det: \text{GL}(n, \mathbb{R}) \to \mathbb{R}^{*}$ is a **Lie group homomorphism**.
>
>That is, 
>- it is a  **smooth map**, because $\det(A)$ is a polynomial in matrix entities of $A$.
>- It *preserve* the matrix multiplication
>  $$
>  \det(\boldsymbol{AB}) = \det(\boldsymbol{A})\det(\boldsymbol{B})
> $$
> 
>The same conclusion holds on $\text{GL}(n, \mathbb{C})$. 

- [[Homomorphism between Groups]]




-----------
##  Recommended Notes and References


- [[Sign of Permutation]]
- [[Finite Dimensional Vector Spaces by Halmos]]