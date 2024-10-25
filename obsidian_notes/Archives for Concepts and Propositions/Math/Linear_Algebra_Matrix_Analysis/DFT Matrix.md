---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
  - numerical_methods/numerical_linear_algebra
keywords:
  - vandermonde_matrix
  - matrix_polynomial
  - characteristic_polynomial
  - dft_matrix
  - discrete_fourier_transform
topics:
  - matrix_analysis
  - linear_algebra
  - numerical_linear_algebra
name: Vandermonde Matrix and DFT Matrix
date of note: 2024-10-24
---

## Concept Definition

>[!important]
>**Name**: DFT Matrix

### DFT Matrix


>[!important] Definition
>A matrix $F \in M_{n}(F)$ is called **Discrete Fourier Transform (DFT) matrix** if it has the form
>$$
>\begin{align*}
> F_{n} &= \left[ \begin{array}{cccc} 1 & 1 & \ldots & 1 \\[5pt] 1 & W_{n} & \ldots & W_{n}^{n-1} \\[5pt] \vdots  & \ldots & \ldots & \ldots \\[5pt] 1 & W_{n}^{n-1} & \ldots & W_{n}^{(n-1)(n-1)} \\[5pt] \end{array} \right] \\[10pt]
> &=  \left[ \begin{array}{cccc} 1 & 1 & \ldots & 1 \\[5pt] 1 & W_{n} & \ldots & W_{n}^{n-1} \\[5pt] \vdots  & \ldots & \ldots & \ldots \\[5pt] 1 & W_{n}^{n-1} & \ldots & W_{n} \\[5pt] \end{array} \right]
>\end{align*}
>$$
>where
>- the **discrete Fourier basis factor** is $$W_{n} := \exp \left(- i\left(\frac{2\pi}{n}\right)\right)$$
>- That is, $$F= [f_{k,j}], \quad f_{k,j} = W_{n}^{(k-1)(j-1)}$$



## Explanation

### Vandermonde Matrix

>[!important]
>A **DFT** matrix can be seen as a **Vandermonde matrix** i.e.
>$$
>F_{n} = V\left(W_{n}^{0}, W_{n}^{1} \,{,}\ldots{,}\, W_{n}^{n-1}\right)
>$$



## Circulant Matrix and Eigenvectors






-----------
##  Recommended Notes and References

- [[Circulant Matrix and Circulant Permutation Operation]]
- [[Discrete Fourier Transform]]


- [[Matrix Computations by Golub]] pp 33 - 35
- [[Numerical Linear Algebra by Trefethen]]