---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
  - numerical_methods/numerical_linear_algebra
keywords:
  - hadamard_product_matrix
topics:
  - matrix_analysis
  - linear_algebra
name: Hadamard Product of Matrices
date of note: 2024-10-01
---

## Concept Definition

>[!important]
>**Name**: Hadamard Product of Matrices

>[!important] Definition
>Let $A, B\in M_{m,n}$.
>
>The **Hadamard product** of $A$ and $B$ is the *pointwise multiplication* of entries of $A$ and $B$, i.e.
>$$
>A \odot B \in M_{m,n} \implies [A \odot B ]_{i,j} = A_{i,j}\,B_{i,j}
>$$


## Explanation


## Properties

>[!important] Proposition
>Let $A \in M_{m, n}$ and $B\in M_{m, n}$ be two *matrices*.  
>
>Then
>- **Bilinearity**: $$A\odot (\alpha B + \beta C) = \alpha A \odot B + \beta A \odot C.$$ and $$(\alpha A + \beta B) \odot C= \alpha A \odot C + \beta B \odot C,$$ where $$(\alpha A) \odot B = A \odot (\alpha B)  = \alpha (A \odot B)$$ 
>- **Associativity**: $$(A \odot  B) \odot C = A \odot ( B \odot  C)$$
>- **Commutative**: $$(A \odot  B) = (B \odot A)$$
>- **Mixed Product Property**:  the Hadamard product of Kronecker product is equal to the Kronecker product of Hadamard product. $$(A \otimes  B) \odot (C \otimes  D) = (A \odot C) \otimes  (B  \odot D).$$
>- **Diagonal Operator**: 
>	- For $v\in F^{n}$ $$\text{diag}(v) = (v\,\boldsymbol{1}^{T}) \odot I$$
>	- For $A\in M_{n}$, $$\text{diag}(A) = A \odot I.$$
>- **Trace Formula**: Let $x,y\in F^{n}$ and $D_{x} = \text{diag}(x)$, $D_{y} = \text{diag}(y)$. Then the following identity holds $$x^{*} (A \odot B) y = \text{tr}\left(D_{x}^{*}AD_{y}B^{*}\right)$$
>	- $$(x\,y^{*}) \odot A = D_{x}\,A\,D_{y}^{*}$$
>	- **Inner Product** between Matrices: $$\left\langle  B\,,\, A   \right\rangle_{tr} = \text{tr}(B^{*} A) = \text{tr}(AB^{*}) = \boldsymbol{1}^{T}\left(A \odot B\right)\boldsymbol{1}.$$
>- **Hadamard Product of Vectors** Let $x,y\in F^{n}$ and $D_{x} = \text{diag}(x)$, $D_{y} = \text{diag}(y)$. Then $$x \odot y = D_{x}y = D_{y}x$$
>- **Determinant**: If $A, B\in M_{m}$, then $$\det(A \odot B) \ge \det(A)\,\det(B)$$


- [[Kronecker Product of Matrices]]
- [[Determinant of Linear Transformation]]
- [[Trace of Matrix]]
- [[Inner Product Space]]



-----------
##  Recommended Notes and References



- [[Vectorization Operation of Matrix]]
- [[Kronecker Product of Matrices]]


- [[Linear Map]]
- [[Matrix Transformation]]
- [[Matrix]]


- [[Matrix Analysis by Horn]] pp 371, 477 - 484
- [[Matrix Computations by Golub]] pp 710
- [[Numerical Linear Algebra by Trefethen]] pp 16
- Wikipedia [Hadamard_product](https://en.wikipedia.org/wiki/Hadamard_product_(matrices))