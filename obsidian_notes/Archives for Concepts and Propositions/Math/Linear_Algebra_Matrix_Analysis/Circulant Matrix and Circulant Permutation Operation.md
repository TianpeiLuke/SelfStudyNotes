---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
  - math/linear_algebra
keywords:
  - circulant_matrix
topics:
  - matrix_analysis
  - linear_algebra
  - numerical_linear_algebra
name: Circulant Matrix
date of note: 2024-08-08
---

## Concept Definition

>[!important]
>**Name**: Circulant Matrix and Circulant Permutation Operation

>[!important] Definition
>Let $$a := (a_{1} \,{,}\ldots{,}\,a_{n})$$ be a sequence of length $n$. 
>
>A **circulant matrix** $A\in M_{n}$ of **size** $n$ is of the form
>$$
>A = \left[ \begin{array}{cccc}a_{1} & a_{2} & \cdots & a_{n} \\ a_{n} & a_{1} & \cdots & a_{n-1} \\ \vdots & \vdots & \ddots & \vdots \\ a_{2} & a_{3} & \cdots & a_{1} \\ \end{array} \right] 
>$$
>where each row is the previous row *cycled forward one step*.
>- The entries in each row are a **cyclic permutation** of those in the first.

- [[Permutation Matrix and Reversal Matrix]]

>[!important] Definition
>A **basic circulant permutation matrix** $C_{n}\in M_{n}$ is of the form
>$$
>C_{n} = \left[ \begin{array}{ccccc}0 & 1 & \cdots & \cdots & 0 \\ \vdots & 0 & 1 &  & 0 \\  \vdots & \vdots & \ddots &  \ddots & \vdots \\ 0 &  &  & 0 & 1 \\ 1 &  0 & \cdots &  & 0 \end{array} \right] = \left[ \begin{array}{cc}0 & I_{n-1} \\[5pt] 1 & 0 \end{array} \right] 
>$$

- [[Permutation Matrix and Reversal Matrix]]

## Explanation

>[!important] Proposition
>A matrix $A\in M_{n}$ can be written in the form
>$$
>A = \sum_{k=0}^{n-1}a_{k+1}\,C_{n}^{k}
>$$
>where  $C_{n}\in M_{n}$ is **basic circulant permutation matrix** *if and only if* $A$ is a **circulant matrix**.


>[!info]
>This representation reveals that the circulant matrices of size $n$ are a **commutative algebra**: 
>- *linear combinations* and *products* of circulants are circulants; 
>- the *inverse* of a nonsingular circulant is a circulant; 
>- any two circulants of the same size *commute*.

- [[Commutative Ring Algebra]]


## Spectrum, Eigenvectors and Fourier Series

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Fourier Series and Fourier Transform]]
- [[Polynomial Ring]]


## Determinant

- [[Determinant of Linear Transformation]]

## Matrix Polynomial

- [[Matrix Polynomial]]
- [[Continuous Functional Calculus]]
- [[Matrix Exponential]]


## Circulant Graph

- [[Cycles in Graph]]


-----------
##  Recommended Notes and References


- [[Toeplitz Matrix and Backward Forward Shift Operation]]
- [[Permutation Matrix and Reversal Matrix]]
- [[Discrete Fourier Transform]]
- [[Matrix]]
- [[Symmetric Group]]



- [[Numerical Linear Algebra by Trefethen]] 
- [[Matrix Computations by Golub]] pp 
- [[Matrix Analysis by Horn]] pp 33 - 34