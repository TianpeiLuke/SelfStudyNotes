---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
  - numerical_methods/numerical_linear_algebra
keywords:
  - hessenberg_qr
  - givens_rotation
topics:
  - numerical_linear_algebra
  - matrix_analysis
name: Hessenberg QR Factorization via Given Transformation
date of note: 2024-09-25
---

## Concept Definition

>[!important]
>**Name**: Hessenberg QR Factorization via Given Transformation

![[Givens Rotations and Jacobi Rotations#^05b457]]

![[Givens Rotations and Jacobi Rotations#^77e0de]]

>[!important] Definition
>Let $H\in \mathbb{R}^{n\times n}$ be an **upper Hessenberg matrix**. Consider the *QR factorization* of $H$, $$H = QR \implies Q^{T}H = R$$ where $Q$ is *orthogonal matrix* and $R$ is *upper triangular*
>- $$Q = G_{1}\,{}\ldots{}\,G_{n-1}$$ is a product of *Givens rotations* with $G_{i}= G(i, i+1, \theta_{i})$
>  
>The **Hessenberg QR** algorithm is achieved above factorization as follow:
>- *Require* $H\in \mathbb{R}^{n\times n}$ an *upper Hessenberg matrix*
>- For $j=1\,{,}\ldots{,}\,j-1$:
>	- Compute the **rotation** $c_{j} := \cos(\theta_{j})$ and $s_{j}:= \sin(\theta_{j})$ by calling subrountine $$(c_{j}, s_{j}) = \text{Givens}(H_{j,j}, H_{j+1, j})$$
>	- Apply **Givens rotation** on *the $j$-th and $(j+1)$-th* rows of $H$ $$H_{\{ j:j+1 \}, \{ j:n \}} \leftarrow \left[ \begin{array}{cc}c_{j} & s_{j} \\-s_{j} & c_{j} \end{array} \right]^{T}\, H_{\{ j:j+1 \}, \{ j:n \}}$$
>- *Return* the *upper triangular matrix* as the overwritten $H$ $$R := H$$ and obtain $Q = G_{1}\,{}\ldots{}\,G_{n-1}$ using **backward accumulation.**

- [[QR Factorization of Matrix]]
- [[Hessenberg Matrix]]
- [[Givens Rotations and Jacobi Rotations]]
- [[Householder QR Factorization#Computing $Q$ by Back Accumulation of Householder Transformations]]

## Explanation

>[!info]
>**Givens rotations** can be used in a structured problem by introducing zeros in specific entry.

- [[Givens Rotations and Jacobi Rotations]]

>[!important]
>The **Hessenberg QR factorization** only requires $$3n^2$$ since the Hessenberg matrix is *almost upper triangular* 
>- Since the only difference is the *1st off diagonal entries*, we just **need $n-1$ Given rotations**.
>- The normal **QR factorization** (*Householder*, *Modified-Gram-Schmdit*, and *Givens*) requires $$2n^2\left(m - \frac{n}{3}\right)$$




-----------
##  Recommended Notes and References


- [[Hessenberg Matrix]]
- [[Givens Rotations and Jacobi Rotations]]


- [[Linear Span over a Set of Vectors]]
- [[Orthogonal Complement of Hilbert Spaces]]
- [[QR Factorization of Matrix]]


- [[Elementary Row and Column Operations]]

- [[Matrix Analysis by Horn]]
- [[Matrix Computations by Golub]] pp 253 - 254, 377 - 378