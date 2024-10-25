---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
  - numerical_methods/numerical_linear_algebra
keywords:
  - dft_matrix
  - discrete_fourier_transform
topics:
  - matrix_analysis
  - linear_algebra
  - numerical_linear_algebra
name: Discrete Fourier Transform Matrix or DFT Matrix
date of note: 2024-10-24
---

## Concept Definition

>[!important]
>**Name**: Discrete Fourier Transform Matrix or DFT Matrix

### DFT Matrix


>[!important] Definition
>A matrix $F \in M_{n}(F)$ is called **Discrete Fourier Transform (DFT) matrix** if it has the form
>$$
>\begin{align*}
> F_{n} &= \frac{1}{\sqrt{ n }} \left[ \begin{array}{cccc} 1 & 1 & \ldots & 1 \\[5pt] 1 & \omega_{n} & \ldots & \omega_{n}^{n-1} \\[5pt] \vdots  & \ldots & \ldots & \ldots \\[5pt] 1 & \omega_{n}^{n-1} & \ldots & \omega_{n}^{(n-1)(n-1)} \\[5pt] \end{array} \right] \\[10pt]
> &=  \frac{1}{\sqrt{ n }} \left[ \begin{array}{cccc} 1 & 1 & \ldots & 1 \\[5pt] 1 & \omega_{n} & \ldots & \omega_{n}^{n-1} \\[5pt] \vdots  & \ldots & \ldots & \ldots \\[5pt] 1 & \omega_{n}^{n-1} & \ldots & \omega_{n} \\[5pt] \end{array} \right]
>\end{align*}
>$$
>where
>- the **discrete Fourier basis factor** is $$\omega_{n} := \exp \left(- i\left(\frac{2\pi}{n}\right)\right)$$
>- That is, $$F= \frac{1}{\sqrt{ n }} [f_{k,j}], \quad f_{k,j} = \omega_{n}^{(k-1)(j-1)}$$

- [[Discrete Fourier Transform]]

## Explanation

>[!info]
>Conventional **DFT matrix** is **non-unitary**
>$$
>\begin{align*}
> F_{n} &=  \left[ \begin{array}{cccc} 1 & 1 & \ldots & 1 \\[5pt] 1 & \omega_{n} & \ldots & \omega_{n}^{n-1} \\[5pt] \vdots  & \ldots & \ldots & \ldots \\[5pt] 1 & \omega_{n}^{n-1} & \ldots & \omega_{n}^{(n-1)(n-1)} \\[5pt] \end{array} \right] 
>\end{align*}
>$$
>and
>$$
>F_{n}^{-1} = \frac{1}{n}\,F_{n}^{*} = \frac{1}{n} \overline{F}_{n}
>$$



### Vandermonde Matrix

>[!important]
>A **DFT** matrix can be seen as a **Vandermonde matrix** i.e.
>$$
>F_{n} = \frac{1}{\sqrt{ n }} V\left(\omega_{n}^{0}, \omega_{n}^{1} \,{,}\ldots{,}\, \omega_{n}^{n-1}\right)
>$$

## Properties

>[!important] Proposition
>Let $F \in M_{n}(F)$ be a **Discrete Fourier Transform (DFT) matrix**.
>
>Then
>- $F$ is **unitary**, **symmetric** and **coninvolutory** i.e. $$F_{n}\,F_{n}^{*} = F_{n}\,\overline{F}_{n} = I$$ or $$F_{n}^{-1} = F_{n}^{*} = \overline{F}_{n}.$$

^6c0327

- [[Unitary and Orthogonal Transformation]]
- [[Hermitian or Symmetric Matrix]]
- [[Involutory and Coninvolutory Transformations]]

## Circulant Matrix and Eigenvectors

![[Circulant Matrix and Circulant Permutation Operation#^174342]]

![[Circulant Matrix and Circulant Permutation Operation#^a24c39]]

- [[Circulant Matrix and Circulant Permutation Operation]]

## Fast Fourier Transform for Efficient Matrix-Vector Multiplication and Solution of Linear system

>[!important]
>With **fast Fourier transform (FFT)**, the *matrix-vector multiplication* $$F_{n}x= X$$ requires only $$O(n\log (n)) \quad \text{ v.s. tranditional }\quad O(n^2)$$
>
>Similarly, *solving the DFT system* $$F_{n}x = X$$ also only requires $$O(n\log (n)) \quad \text{ v.s. tranditional }\quad O(n^3)$$

- [[Fast Fourier Transform]]




-----------
##  Recommended Notes and References


- [[Discrete Fourier Transform]]


- [[Matrix Computations by Golub]] pp 33 - 35
- [[Numerical Linear Algebra by Trefethen]]
- [[Discrete Time Signal Processing by Oppenheim]]
- [[Signals and Systems by Oppenheim]]
