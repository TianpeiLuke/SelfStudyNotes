---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
keywords:
  - range_linear_map
  - kernel_linear
topics:
  - linear_algebra
  - matrix_analysis
name: Fundamental Subspaces from Linear Map and its Projection
date of note: 2024-09-05
---

## Concept Definition

>[!important]
>**Name**: Fundamental Subspaces from Linear Map and its Projection

>[!important] Definition
>Let $V$ be a $n$-dimensional *inner product space* and $W$ be a $m$-dimensional inner product space.  Let $A\in L(V, W)$ be a *linear map* from $V$ to $W$ (with matrix representation $A\in \mathbb{R}^{m\times n}$). 
>
>Denote $A^{*}\in L(W^{*}, V^{*})$ as the *adjoint* of $A$ where the *dual space* is *isometric isomorphic* to *primal space* $$W^{*}\simeq W, \quad V^{*}\simeq V.$$ The matrix representation of $A^{*}$ is denoted as $A^{*}\in \mathbb{R}^{n\times m}$. 
>
>The **four fundamental subspaces** from linear map $A$ include
>- **Range/Image of linear map $A$**: $$\text{R}(A) = \text{Im}(A) := \left\{Av\in W:\; v\in V \right\}  \subseteq W.$$
>- **Kernel of linear map $A$**: $$\text{Ker}(A) := \left\{v\in V: Av = 0 \right\}  \subseteq V.$$
>- **Range/Image of adjoint $A^{*}$**:  $$\text{R}(A^{*}) = \text{Im}(A^{*}) := \left\{A^{*}w \in V^{*}:\; w\in W^{*}\simeq W \right\}  \subseteq V^{*} \simeq V.$$
>- **Kernel of adjoint $A^{*}$**:  $$\text{Ker}(A^{*}) := \left\{w\in W^{*}: A^{*}w = 0 \right\}  \subseteq  W^{*} \simeq W.$$

^71c730

- [[Inner Product Space]]

- [[Linear Map]]
- [[Adjoint of Linear Map]]
- [[Range and Kernel of Linear Map]]
- [[Dual Space of Hilbert Space]]


## Explanation

>[!info]
>Note that for general Hilbert space, the above four subspaces exist, and the **orthogonal complementary** relation still hold. But the direct sum decomposition may not hold.

- [[Hilbert Space]]

## Direct Sum Decomposition of Domain and Codomain

>[!important] Proposition
>Let $A\in M_{m,n}$ be matrix representation of linear map $A: V\to W$, where $V,W$ are vector spaces with dimension $n$ and $m$ respectively.
>
>Then the **four fundamental subspaces** have the following relationship:
>- The **range** of $A$ and the **kernel** of its **adjoint** $A^{*}$ are **orthogonal complement** to each other  $$\begin{align*}\text{R}(A) &=  \left(\text{Ker}(A^{*})\right)^{\perp} \\[5pt] \text{Ker}(A^{*}) &= \left(\text{R}(A)\right)^{\perp}\end{align*}$$  
>- The **kernel** of $A$ and the **range** of its **adjoint** $A^{*}$ are **orthogonal complement** to each other  $$\begin{align*}\text{R}(A^{*}) &=  \left(\text{Ker}(A)\right)^{\perp}\\[5pt] \text{Ker}(A) &=  \left(\text{R}(A^{*})\right)^{\perp}\end{align*}$$

- [[Orthogonal Complement of Hilbert Spaces]]

>[!important] Proposition
>Let $A\in M_{m,n}$ be matrix representation of linear map $A: V\to W$, where $V,W$ are vector spaces with dimension $n$ and $m$ respectively.
>
>Then
>- the **codomain** of $A$ has the following **direct sum decomposition** $$W = \text{R}(A) \;\oplus\; \text{Ker}(A^{*})$$  where $$\text{dim}(\text{R}(A)) = \text{rank}(A) = r; \quad \text{dim}\left(\text{Ker}(A^{*})\right) = m -r.$$
>- the **domain** of $A$ has the following **direct sum decomposition** $$V = \text{Ker}(A) \;\oplus\; \text{R}(A^{*})$$  where $$\text{dim}(\text{Ker}(A)) = \text{dim}(V) - \text{rank}(A) = n - r; \quad \text{dim}\left(\text{R}(A^{*})\right) = r.$$ 

^3f989c

- [[Direct Sum of Subspaces]]
- [[Direct Sum of Hilbert Spaces]]
- [[Rank–Nullity Theorem]]

>[!info]
>The **range** of both $A$ and its **adjoint** $A^{*}$ has the **same dimension** $r$.
>
>The **kernel** of both $A$ and its **adjoint** $A^{*}$ has the **same codimension** $r$.
 

## SVD and Fundamental Subspaces

![[Singular Value Decomposition and Fundamental Subspaces#^b13e8a]]

- [[Singular Value Decomposition and Fundamental Subspaces]]

![[svd_fundamental_subspaces.png]]

## Projections on Fundamental Subspaces

![[Projection Map onto Linear Subspace#^38f848]]

- [[Projection Map onto Linear Subspace]]









-----------
##  Recommended Notes and References


- [[Projection Map onto Linear Subspace]]
- [[Singular Value Decomposition of Linear Map]]

- [[Rank–Nullity Theorem]]
- [[Rank and Nullity of Linear Map]]

- [[Range and Kernel of Linear Operator]]
- [[Space of Bounded Linear Operators]]

- [[Linear Subspace]]
- [[Riesz Representation Theorem]]
- [[Vector Space over a Field]]


- [[Finite Dimensional Vector Spaces by Halmos]]
- [[Matrix Analysis by Horn]]
- [[Matrix Analysis for Scientists and Engineers by Laub]]