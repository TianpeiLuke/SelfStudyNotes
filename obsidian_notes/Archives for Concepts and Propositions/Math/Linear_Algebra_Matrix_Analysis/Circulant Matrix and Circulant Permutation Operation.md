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

- [[Matrix Polynomial]]

>[!info]
>This representation reveals that the circulant matrices of size $n$ are a **commutative algebra**: 
>- *linear combinations* and *products* of circulants are circulants; 
>- the *inverse* of a nonsingular circulant is a circulant; 
>- any two circulants of the same size *commute*.

- [[Commutative Ring Algebra]]


## Spectrum, Eigenvectors and Discrete Fourier Transform

>[!important] Theorem
>Let $C_{n}$ be a **basic circulant permuation matrix** i.e.
>$$
>C_{n} = \left[ \begin{array}{ccccc}0 & 1 & \cdots & \cdots & 0 \\ \vdots & 0 & 1 &  & 0 \\  \vdots & \vdots & \ddots &  \ddots & \vdots \\ 0 &  &  & 0 & 1 \\ 1 &  0 & \cdots &  & 0 \end{array} \right] = \left[ \begin{array}{cc}0 & I_{n-1} \\[5pt] 1 & 0 \end{array} \right] 
>$$
>
>Then 
>- $C_{n}$ is **unitary** (or **real orthogonal**)
>- Let $$D = \text{diag}\left(1,\, \omega_{n} \,{,}\ldots{,}\,\omega_{n}^{n-1}\right)$$ where $$\omega_{n} := \exp \left(i \frac{2\pi}{n}\right)$$ and let $F_{n}$ be the **(inverse) DFT matrix**.  $$\begin{align*} F_{n} &= \frac{1}{\sqrt{ n }} \left[ \begin{array}{cccc} 1 & 1 & \ldots & 1 \\[5pt] 1 & \omega_{n} & \ldots & \omega_{n}^{n-1} \\[5pt] \vdots  & \ldots & \ldots & \ldots \\[5pt] 1 & \omega_{n}^{n-1} & \ldots & \omega_{n}^{(n-1)(n-1)} \\[5pt] \end{array} \right] \\[10pt]  &=  \frac{1}{\sqrt{ n }} \left[ \begin{array}{cccc} 1 & 1 & \ldots & 1 \\[5pt] 1 & \omega_{n} & \ldots & \omega_{n}^{n-1} \\[5pt] \vdots  & \ldots & \ldots & \ldots \\[5pt] 1 & \omega_{n}^{n-1} & \ldots & \omega_{n} \\[5pt] \end{array} \right]\end{align*}$$ Then $$C_{n}F_{n} = F_{n}D$$ That is, the **spectral decomposition** of $C_{n}$ is given by $$C_{n} = F_{n}\,D\,F_{n}^{*}$$
>	- So the **eigenvector** of $C_{n}$ corresponds to **eigenvalue** $\omega_{n}^{k}$ is **the Fourier modes** $$v_{k} := \frac{1}{\sqrt{ n}}\left[ 1,\,\omega_{n}^{k}\,{,}\ldots{,}\,\omega_{n}^{k(n-1)} \right]^{T}$$

^174342

- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]
- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Fourier Series and Fourier Transform]]
- [[Discrete Fourier Transform]]
- [[Polynomial Ring]]

>[!important] Corollary
>Let $$a := (a_{1} \,{,}\ldots{,}\,a_{n})$$ be a sequence of length $n$ and a **circulant matrix** $A\in M_{n}$ of **size** $n$ is of the form
>$$
>A = \left[ \begin{array}{cccc}a_{1} & a_{2} & \cdots & a_{n} \\ a_{n} & a_{1} & \cdots & a_{n-1} \\ \vdots & \vdots & \ddots & \vdots \\ a_{2} & a_{3} & \cdots & a_{1} \\ \end{array} \right]. 
>$$
>
>Then the **spectral decomposition** of $A$ is given by $$A = F_{n}\,\Lambda\,F_{n}^{*}$$ where 
>- $F_{n}$ be the **DFT matrix**.  $$\begin{align*} F_{n} &= \frac{1}{\sqrt{ n }} \left[ \begin{array}{cccc} 1 & 1 & \ldots & 1 \\[5pt] 1 & \omega_{n} & \ldots & \omega_{n}^{n-1} \\[5pt] \vdots  & \ldots & \ldots & \ldots \\[5pt] 1 & \omega_{n}^{n-1} & \ldots & \omega_{n}^{(n-1)(n-1)} \\[5pt] \end{array} \right] \\[10pt]  &=  \frac{1}{\sqrt{ n }} \left[ \begin{array}{cccc} 1 & 1 & \ldots & 1 \\[5pt] 1 & \omega_{n} & \ldots & \omega_{n}^{n-1} \\[5pt] \vdots  & \ldots & \ldots & \ldots \\[5pt] 1 & \omega_{n}^{n-1} & \ldots & \omega_{n} \\[5pt] \end{array} \right]\end{align*}$$ 
>- And the **spectrum** of $A$, $\Lambda = \text{diag}(\lambda_{1}\,{,}\ldots{,}\,\lambda_{n})$, is given by the **inverse Fourier transform** of $a$, $$\lambda_{j} = \sum_{k=1}^{n}\,a_{k}\,\omega_{n}^{(k-1)(j-1)}:= (\mathcal{F}^{-1}a)_{j}$$ with $$\omega_{n} := \exp \left(i \frac{2\pi}{n}\right)$$

^a24c39

- [[Discrete Fourier Transform]]
- [[Unitary Similarity and Unitary Diagonalizable]]

>[!important] 
>These two are the same:
>- The **(operator) spectrum** of **circulant matrix** for a **periodic sequence** 
>- the **(Fourier) spectrum** of the **periodic sequence.**


>[!info]
>This can be understood by realizing that **multiplication** with a *circulant matrix* implements a **convolution**. 
>- In **Fourier space**, **convolutions become multiplication**. 
>- Hence the *product of a circulant matrix with a Fourier mode* yields a *multiple of that Fourier mode*, i.e. it is an **eigenvector**. $$A\,\frac{1}{\sqrt{ n}}\left[ 1,\,\omega_{n}^{k}\,{,}\ldots{,}\,\omega_{n}^{k(n-1)} \right]^{T} = (\mathcal{F}^{-1}a)_{j}\,\frac{1}{\sqrt{ n}}\left[ 1,\,\omega_{n}^{k}\,{,}\ldots{,}\,\omega_{n}^{k(n-1)} \right]^{T}$$

- [[Convolution Operation]]

>[!info]
>Due to **fast Fourier transform**, solving the **eigenvalue problem** of **circulant matrix**
> $$
> A\,F_{n} = F_{n}\,\Lambda
> $$
>requires only $$O(n\log(n)) \quad \text{ v.s. traditional } O(n^3)$$

- [[Fast Fourier Transform]]
- [[QR Iteration for General Eigenvalue Problem]]


## Determinant

>[!important]
>The **determinant** of **circulant matrix**
>$$
>A = \left[ \begin{array}{cccc}a_{1} & a_{2} & \cdots & a_{n} \\ a_{n} & a_{1} & \cdots & a_{n-1} \\ \vdots & \vdots & \ddots & \vdots \\ a_{2} & a_{3} & \cdots & a_{1} \\ \end{array} \right]. 
>$$
>is given by
>$$
>\det(A) = \prod_{j=1}^{n}\lambda_{j}  = \prod_{j=1}^{n}(\mathcal{F}^{-1}a)_{j-1} = \prod_{j=1}^{n}\left(\sum_{k=1}^{n}\,a_{k}\,\omega_{n}^{(k-1)(j-1)}\right)
>$$
>with $$\omega_{n} := \exp \left(i \frac{2\pi}{n}\right)$$


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



- [[Numerical Linear Algebra by Trefethen]] pp 187, 305, 318, 342
- [[Matrix Computations by Golub]] pp 220
- [[Matrix Analysis by Horn]] pp 33 - 34, 100, 36