---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
keywords:
  - trace_matrix
topics:
  - matrix_analysis
  - linear_algebra
name: Trace of Matrix
date of note: 2024-09-16
---

## Concept Definition

>[!important]
>**Name**: Trace of Matrix


>[!important] Definition
>Let $A = [a_{i,j}] \in M_{n}$ be a $n\times n$ matrix.
>
>The **trace** of matrix $A$ is the *sum of diagonal entries* of $A$ $$\text{tr}(A) = \sum_{i=1}^{n}a_{i,i}.$$

## Explanation

## Properties

>[!important] Proposition
>Let $A, B\in M_{n}$ and $c\in F$.  The following properties hold:
>- **Linearity**: trace function is a linear operation $$\text{tr}(A + B) = \text{tr}(A) + \text{tr}(B);$$ $$\text{tr}(c A) = c\text{tr}(A)$$
>- **Transpose/Hermitian**: trace function is *invariant under transpose or Hermitian operation* $$\text{tr}(A) = \text{tr}(A^{*})$$
>- **Cyclic Property**: trace function between two matrices is invariant under the **circular shift** of ordering in matrix product.
>	- In particular, for **binary product** $$\text{tr}(A\,B) = \text{tr}(B\,A).$$  
>	- In general $$\text{tr}\left(A_{i_{1}}\,{}\ldots{}\,A_{i_{k}}\right) = \text{tr}\left(A_{j_{1}}\,{}\ldots{}\,A_{j_{k}}\right)$$ if $$(i_{1}\,{,}\ldots{,}\,i_{k}) \to (i_{2} \,{,}\ldots{,}\,i_{k},\,i_{1}) \,{\to}\ldots{\to}\,(j_{1}\,{,}\ldots{,}\,j_{k})$$

## Characterization of Trace Functional

>[!important] Theorem
>Let $A, B\in M_{n}$ and $c\in F$.  
>
>A **linear functional** $f: M_{n} \to F$ satisfies the three conditions:
>- **Cyclic Property**: $$f(A\,B) = f(B\,A).$$  
>  
>Then $$f(\cdot) = c\,\text{tr}(\cdot)$$ where $$c = \frac{f(I)}{n}$$ is a constant. 
>- $c = 1$ if $f(I) = n.$

- [[Bounded Linear Functional]]

## Trace via Eigenvalues and Characteristic Polynomial


- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Trace of Positive Semi-Definite Operator]]

![[Characteristic Polynomial for Linear Map#^435f9a]]

- [[Characteristic Polynomial for Linear Map]]

## Trace Class Operators

![[Trace Class Operator#^051e95]]

![[Trace of Positive Semi-Definite Operator#^ca68f5]]

- [[Trace of Positive Semi-Definite Operator]]
- [[Trace Class Operator]]


## Trace of Tensor

![[Trace of Mixed Tensor#^efc0e0]]



-----------
##  Recommended Notes and References


- [[Schatten Norm and Nuclear Norm of Matrix]]
- [[Trace of Mixed Tensor]]
- [[Trace of Positive Semi-Definite Operator]]
- [[Trace Class Operator]]


- [[Matrix]]
- [[Linear Map]]


- [[Finite Dimensional Vector Spaces by Halmos]]
- [[Matrix Analysis by Horn]]
- [[Matrix Analysis for Scientists and Engineers by Laub]]
- [[Matrix Computations by Golub]]
- Wikipedia [Trace](https://en.wikipedia.org/wiki/Trace_(linear_algebra))