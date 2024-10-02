---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
  - numerical_methods/numerical_linear_algebra
keywords:
  - givens_rotation
  - givens_transformation
  - givens_qr_factorization
topics:
  - numerical_linear_algebra
  - matrix_analysis
name: Givens QR Factorization
date of note: 2024-09-25
---

## Concept Definition

>[!important]
>**Name**: Givens QR Factorization

![[Givens Transformation and Givens Rotation#^956c04]]

>[!important] Definition
>Let $A\in \mathbb{R}^{m\times n}$ with $m\ge n$.
>
>The **Givens QR Factorization** is described as follows
>- *Require*: $A$
>- For $j=1\,{,}\ldots{,}\,n$:
>	- For $i=m\,{,}\ldots{,}\,j+1$:
>		- Compute the **Givens rotations** $$[\cos(\theta), \sin(\theta)] = \text{Givens}(A_{i-1, j}\,,\,A_{i,j})$$ 
>		- Apply the *Given rotations* to annihilate $(i,j)$ entry $$A_{\{ i-1:i \}, \{ j:n \}} \leftarrow \left[ \begin{array}{cc}\cos(\theta) & -\sin(\theta) \\  \sin(\theta) & \cos(\theta) \end{array} \right]\,A_{\{ i-1:i \}, \{ j:n \}} $$
>- *Return*: the **upper triangular matrix** $$R = Q^{T}A$$ is given by the upper triangular part of $A$, $$[A_{\{ j+1:m \}, j}]$$

- [[Givens Transformation and Givens Rotation]]

>[!important]

## Explanation

>[!quote]
>Givens rotations can also be used to compute the **QR factorization**.

- [[QR Factorization of Matrix]]

>[!quote]
>With the Givens approach to the QR factorization, there is **flexibility** in terms of the *rows* that are involved in each update and also the *order* in which the *zeros are introduced*.
>-- [[Matrix Computations by Golub]] pp 252
  - givens_rotation
  - givens_transformation
  - givens_qr_factorization
topics:
  - numerical_linear_algebra
  - matrix_analysis
name: Givens QR Factorization
date of note: 2024-09-25
---

## Concept Definition

>[!important]
>**Name**: Givens QR Factorization

![[Givens Rotations and Jacobi Rotations#^956c04]]

![[Givens Rotations and Jacobi Rotations#^05b457]]

![[Givens Rotations and Jacobi Rotations#^77e0de]]

>[!important] Definition
>Let $A\in \mathbb{R}^{m\times n}$ with $m\ge n$.
>
>The **Givens QR Factorization** is described as follows
>- *Require*: $A$
>- For $j=1\,{,}\ldots{,}\,n$:
>	- For $i=m\,{,}\ldots{,}\,j+1$:
>		- Compute the **Givens rotations** $$[c, s] = \text{Givens}(A_{i-1, j}\,,\,A_{i,j})$$ 
>		- Apply the *Given rotations* to annihilate $(i,j)$ entry $$A_{\{ i-1:i \}, \{ j:n \}} \leftarrow \left[ \begin{array}{cc}c & s \\  -s & c \end{array} \right]^{T}\,A_{\{ i-1:i \}, \{ j:n \}} $$
>- *Return*: the **upper triangular matrix** $$R = Q^{T}A$$ is given by the upper triangular part of $A$, $$[A_{\{ j+1:m \}, j}]$$

- [[Givens Rotations and Jacobi Rotations]]



## Explanation

>[!quote]
>Givens rotations can also be used to compute the **QR factorization**.

- [[QR Factorization of Matrix]]

>[!quote]
>With the Givens approach to the QR factorization, there is **flexibility** in terms of the *rows* that are involved in each update and also the *order* in which the *zeros are introduced*.
>-- [[Matrix Computations by Golub]] pp 252



-----------
##  Recommended Notes and References


- [[Givens Rotations and Jacobi Rotations]]


- [[Linear Span over a Set of Vectors]]
- [[Orthogonal Complement of Hilbert Spaces]]
- [[QR Factorization of Matrix]]


- [[Elementary Row and Column Operations]]

- [[Matrix Analysis by Horn]]
- [[Matrix Computations by Golub]] pp 252 - 253