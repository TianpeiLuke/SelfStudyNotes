---
tags:
  - concept
  - math/matrix_analysis
  - math/algebra
  - math/linear_algebra
keywords:
  - involutory_transformation
  - coninvolutory_transformation
topics:
  - matrix_analysis
  - linear_algebra
name: Involutory and Coninvolutory Transformations
date of note: 2024-10-25
---

## Concept Definition

>[!important]
>**Name**: Involutory and Coninvolutory Transformations

### Involutary

>[!important] Definition
>Let $A\in L(V)$ be a linear map on a finite dimensional vector space $V$ over $\mathbb{C}$.
>
>$A$ is said to be **involutary** (or, $A$ is an **involution map**) if $$A^2 = I$$ that is, $A$ is *invertible* and $$A = A^{-1}$$

- [[Surjective Injective Invertible Linear Map and Rank]]

>[!important] Definition (Matrix Version)
>Let $A\in M_{n}(\mathbb{C})$ be a $n\times n$ matrix.
>
>$A$ is said to be **involutary** (or, $A$ is an **involution matrix**) if $$A^2 = I$$ that is, $A$ is *invertible* and $$A = A^{-1}$$

### Coninvolutary

>[!important] Definition
>Let $A\in L(V)$ be a linear map on a finite dimensional vector space $V$ over $\mathbb{C}$.
>
>$A$ is said to be **coinvolutary** (or, $A$ is an **coinvolution map**) if $$A\,\overline{A} = I$$ that is, $A$ is *invertible* and the **complex conjugate** is its inverse $$\overline{A} = A^{-1}$$

>[!info]
>$$
>A = [a_{k,j} + i\,b_{k,j} ]_{k,j} \implies \overline{A} = [a_{k,j} - i\,b_{k,j} ]_{k,j}
>$$
>It is the transpose of *adjoint*
>$$
>A = [a_{k,j} + i\,b_{k,j} ]_{k,j} \implies A^{*} = [a_{j,k} - i\,b_{j,k} ]_{k,j} = (\overline{A})^{T}
>$$

>[!important] Definition
>Let $A\in M_{n}(\mathbb{C})$ be a $n\times n$ matrix.
>
>$A$ is said to be **coinvolutary** (or, $A$ is an **coinvolution map**) if $$A\,\overline{A} = I$$ that is, $A$ is *invertible* and the **complex conjugate** is its inverse $$\overline{A} = A^{-1}$$


## Explanation



## Example

![[DFT Matrix#^6c0327]]

- [[DFT Matrix]]

## Similar Concepts

### Projection or Idempotent Map

![[Projection Map onto Linear Subspace#^b88860]]

- [[Projection Map onto Linear Subspace]]

### Nilpotent Map

![[Nilpotent Linear Transformation and Matrix#^a1b57c]]

- [[Nilpotent Linear Transformation and Matrix]]

### Orthogonal Projection or Hermitian 


- [[Hermitian or Symmetric Matrix]]




-----------
##  Recommended Notes and References


- [[Continuous Functional Calculus]]
- [[Spectral Theorem in Functional Calculus Form]]




- [[Normal Transformation]]
- [[Unitary and Orthogonal Transformation]]

- [[Matrix]]
- [[Linear Map]]
- [[Vector Space over a Field]]


- [[Matrix Analysis by Horn]] pp 38, 70, 278, 308