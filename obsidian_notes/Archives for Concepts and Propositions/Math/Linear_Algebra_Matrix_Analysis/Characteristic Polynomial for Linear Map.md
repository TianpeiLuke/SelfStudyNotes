---
tags:
  - concept
  - math/linear_algebra
keywords:
  - characteristic_polynomial
topics:
  - linear_algebra
name: Characteristic Polynomial for Linear Map
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Characteristic Polynomial for Linear Map

>[!important] Definition
>Let $A\in M_{n,n}$ be an $n\times n$ matrix.
>
>The **characteristic polynomial** $P_A$ of $A$ to be the *determinant*
>$$
>P_{A}(\lambda) := \det \left(\lambda I - A\right)
>$$ 
>
>We can also view $A$ as a linear map $A: V\to V$ with $\text{dim}(V) =n$. Then we say that $P_{A}(\lambda)$ is the **characteristic polynomial** of *linear map*.

^785fd1

>[!important] Definition
>We refer to the equation $$\det(x I - A) = P_{A}(x) = 0$$ as the **characteristic equation** of $A$.


## Explanation



## Eigenvalue as Root

![[Eigenvalue and Eigenvector for Linear Map#^06f8b9]] ^9d1778

![[Eigenvalue and Eigenvector for Linear Map#^fb9212]]

>[!important] Proposition
>Let $A$ be an $n \times n$ matrix. 
>
>A number $\lambda$ is an **eigenvalue** of $A$ *if and only if* $\lambda$ is a **root** of the **characteristic polynomial** of $A$.

^5aa1eb

- [[Eigenvalue and Eigenvector for Linear Map]]


>[!important] Proposition
>Let $A, B$ be two $n \times n$ matrices and assume that $B$ is **invertible**
>
>Then the **characteristic polynomial** of $A$ is equal to  the **characteristic polynomial** of $B^{\text{-1}}AB$, i.e. $$\det \left(\lambda I - A\right) = \det \left(\lambda I - B^{-1} A B\right)$$

- [[Surjective Injective Invertible Linear Map and Rank]]

## Fundamental Theorem of Algebra

>[!important]
>Let $\lambda_{1} \,{,}\ldots{,}\,\lambda_{n}$ be $n$ **eigenvalues** (with possibly repetition) for matrix $A\in \mathbb{R}^{n\times n}$.
>
>According to **fundamental theorem of algebra**, the **characteristic polynomial** of $A$ have decomposition
>$$
>\det(\lambda I - A) = \prod_{k=1}^{n}\left( \lambda - \lambda_{k} \right)
>$$

- [[Fundamental Theorem of Algebra]]


## Determinant and Trace

>[!important]
>Let $\lambda_{1} \,{,}\ldots{,}\,\lambda_{n}$ be $n$ **eigenvalues** (with possibly repetition) for matrix $A\in \mathbb{R}^{n\times n}$. The characteristic polynomial of $A$ is 
>$$
>\det(\lambda I - A) = \prod_{k=1}^{n}\left( \lambda - \lambda_{k} \right)
>$$
>
>- The coefficient of *first-order term* $\lambda$ is the **trace** of $A$ $$\text{tr}(A) = \sum_{k=1}^{n}\lambda_{k}.$$
>- The coefficient of *zero-order term* $1$ is the **determinant** of $A$ $$\det(A) = \prod_{k=1}^{n}\lambda_{k}.$$

^435f9a

- [[Determinant of Linear Transformation]]
- [[Trace of Matrix]]



## Algebraic Multiplicity and Geometric Multiplicity

- [[Algebraic and Geometric Multiplicity of Linear Map]]


## Minimal Polynomial 

- [[Minimal Polynomial for Linear Map]]


## Infinite Dimensional Space

- [[Resolvent Operator and Spectrum of Linear Operator]]
- [[Eigenvalue Point Residual Spectrum of Linear Operator]]
- [[Partition of Spectrum]]




-----------
##  Recommended Notes and References

- [[Fundamental Theorem of Algebra]]

- [[Minimal Polynomial for Linear Map]]
- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Matrix]]
- [[Linear Map]]




- [[Finite Dimensional Vector Spaces by Halmos]] pp 112 -- 115
- [[Matrix Analysis by Horn]] pp 49 - 56