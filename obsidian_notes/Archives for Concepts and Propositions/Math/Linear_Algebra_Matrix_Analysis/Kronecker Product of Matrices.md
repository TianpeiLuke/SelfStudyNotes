---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
  - math/differential_geometry
  - numerical_methods/numerical_linear_algebra
keywords:
  - kronecker_product
topics:
  - matrix_analysis
  - linear_algebra
  - differential_geometry
  - numerical_linear_algebra
name: Kronecker Product of Matrices
date of note: 2024-10-01
---

## Concept Definition

>[!important]
>**Name**: Kronecker Product of Matrices

>[!important] Definition
>Let $A \in M_{m, n}$ and $B\in M_{p, q}$ be two *matrices*.  
>
>Then **Kronecker product** between $A$ and $B$ is a $pm\times nq$ block matrix
>$$
>A\otimes B = \left[ \begin{array}{ccc}a_{11}B & \cdots & a_{n1}B \\[5pt] \vdots & \ddots & \vdots \\[5pt] a_{n1}B & \cdots & a_{nn}B \end{array} \right] \in M_{pm, nq}
>$$
>- $$(A\otimes B)_{p(r-1)+v, q(s-1)+w} = a_{r,s}\,b_{v,w}$$

- [[Partition of Matrix and Block Matrix]]

## Explanation


## Tensor Product

>[!important]
>Let $\boldsymbol{A} \in M_{m, n}$ and $\boldsymbol{B}\in M_{p, q}$ be two *matrices*. 
>
>There is a one-to-one correspondence between *matrices* and *linear maps* $$\boldsymbol{A} \mapsto A\in \mathcal{L}(V, X)$$ and $$\boldsymbol{B} \mapsto B\in \mathcal{L}(W, Y)$$ where $V$, $X$, $W$, $Y$ are vector spaces with dimensionality $n$, $m$, $p$, $q$.
>
>
>Then the **Kronecker product** between $\boldsymbol{A}$ and $\boldsymbol{B}$, $\boldsymbol{A} \otimes \boldsymbol{B}$, is the *matrix representation* of the **abstract tensor product** between linear maps $A$ and $B$ 
>$$
>\begin{align*}
>(\boldsymbol{A} \otimes \boldsymbol{B}) &\mapsto (A \otimes B) \in \mathcal{L}(V\otimes W, X\otimes Y)
>\end{align*}
>$$
>where the **abstract tensor product** is defined as 
>$$
>(A \otimes B)(v_{i} \otimes w_{j}) = (Av_{i}) \otimes (Bw_{j})
>$$
>for any $v_{i}\in V_{1}$  and $w_{j}\in W$.
>
>- Thus $(\boldsymbol{A} \otimes \boldsymbol{B}) \in M_{m_{1}+m_{2}, n_{1}+n_{2}}$
  
- [[Abstract Tensor Product]]
- [[Linear Map]]
- [[Matrix]]
- [[Coordinate Representation of Tensor]]

## Properties

>[!important] Proposition
>Let $A \in M_{m, n}$ and $B\in M_{p, q}$ be two *matrices*.  
>
>Then
>- **Bilinearity**: $$A\otimes(\alpha B + \beta C) = \alpha A \otimes B + \beta A \otimes C.$$ and $$(\alpha A + \beta B) \otimes C= \alpha A \otimes C + \beta B \otimes C,$$ where $$(\alpha A) \otimes B = A \otimes (\alpha B)  = \alpha (A \otimes B)$$ 
>- **Associativity**: $$(A \otimes  B) \otimes C = A\otimes( B \otimes  C)$$
>- **Non-Commutative**: $$(A \otimes  B) \neq (B \otimes A)$$ but two matrices are **permutation equivalent**: i.e. there exists permutation matrices $P, Q$ such that $$(B \otimes A) = P(A \otimes  B)Q$$
>- **Mixed Product Property**: the (normal) product of Kronecker product is equal to the Kronecker product of (normal) product. $$(A \otimes  B)\,(C \otimes  D) = (AC \otimes  BD).$$
>	- An immediate consequence is $$A \otimes  B = (I_{m} \otimes  B)\,(A \otimes  I_{q}) = (A \otimes  I_{p})\,(I_{n} \otimes  B)$$
>	- **Mixed Kronecker Matrix-Vector Product**: $$\left( A^{T} \otimes B \right)\,\text{vec}(V) = \text{vec}\left( BVA\right)$$ where $\text{vec}(\cdot)$ is the **vectorization operator** on $A$ 
>	- **Hadamard Product**:  the Hadamard product of Kronecker product is equal to the Kronecker product of Hadamard product. $$(A \otimes  B) \odot (C \otimes  D) = (A \odot C) \otimes  (B  \odot D).$$
>- **Inverse**: $A\otimes B$ is *invertible* *if and only if* both $A$ and $B$ are *invertible*. $$\left( A\otimes B \right)^{-1} = A^{-1} \otimes B^{-1}$$
>	- **Pseudo-inverse**: the property holds for the *Moore-Penrose pseudo-inverse* as well $$\left( A\otimes B \right)^{+} = A^{+} \otimes B^{+}$$
>- **Adjoint**: the adjoint of Kronecker product is equal to the Kronecker product of adjoints $$\left( A \otimes B \right)^{*} = A^{*} \otimes B^{*}.$$
>- **Determinant**: For $A\in M_{n}$ and $B\in M_{p}$, we have $$\det \left( A\otimes B \right) = \det(A)^{p}\,\det(B)^{n}.$$
>- **Trace**: $$\text{tr}(A\otimes B) = \text{tr}(A)\,\text{tr}(B).$$
>- **Vectorization of Kronecker Product** $$\text{vec}\left( A\otimes B \right) = \left( I_{n} \otimes K_{qm} \otimes I_{p} \right)\,(\text{vec}(A) \otimes \text{vec}(B))$$


- [[Similarity Relation between Linear Maps and Matrices]]
- [[Permutation Matrix and Reversal Matrix]]
- [[Vectorization Operation of Matrix]]
- [[Hadamard Product of Matrices]]
- [[Surjective Injective Invertible Linear Map and Rank]]
- [[Moore–Penrose Pseudo Inverse of Matrix]]
- [[Determinant of Linear Transformation]]
- [[Trace of Matrix]]
- [[Adjoint of Linear Map]]


>[!info]
>We can rewrite the matrix equation $$AXB = C$$ by **vec trick** i.e. $$\text{vec}(C) = \text{vec}(AXB) = (B^{T} \otimes A)\,\text{vec}(X)$$





-----------
##  Recommended Notes and References


- [[Multilinear Function]]
- [[Tensor Product]]
- [[Abstract Tensor Product]]

- [[Determinant of Linear Transformation]]
- [[Vectorization Operation of Matrix]]
- [[Hadamard Product of Matrices]]

- [[Linear Map]]
- [[Matrix]]
- [[Matrix Transformation]]



- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 139 - 144
- [[Matrix Computations by Golub]] pp 27 - 28, 707, 712, 715
- [[Finite Dimensional Vector Spaces by Halmos]] pp 98
- Wikipedia [Kronecker_product](https://en.wikipedia.org/wiki/Kronecker_product)