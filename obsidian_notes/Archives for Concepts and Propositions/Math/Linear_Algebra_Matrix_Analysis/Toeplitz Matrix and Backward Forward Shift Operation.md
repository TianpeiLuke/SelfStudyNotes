---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
  - math/linear_algebra
keywords:
  - toeplitz_matrix
topics:
  - matrix_analysis
  - linear_algebra
  - numerical_linear_algebra
name: Toeplitz Matrix
date of note: 2024-08-08
---

## Concept Definition

>[!important]
>**Name**: Toeplitz Matrix

>[!important] Definition
>Let $$a := (a_{-n} \,{,}\ldots{,}\,a_{-1},\, a_{0},\,a_{1} \,{,}\ldots{,}\,a_{n})$$ be a sequence of length $2n+1$. 
>
>A **Toeplitz matrix** $A\in M_{n+1}$ is of the form
>$$
>A = \left[ \begin{array}{cccc}a_{0} & a_{1} & \cdots & a_{n} \\ a_{-1} & a_{0} & \cdots & a_{n-1} \\ \vdots & \ddots & \ddots & \vdots \\ a_{-n} & a_{-n+1} & \cdots & a_{0} \\ \end{array} \right] 
>$$
>where each entry $$a_{i,j} = a_{j-i}.$$
>- The entries of $A$ are **constant** down the *diagonals* **parallel to** *the main diagonal*.

>[!important] Definition
>The *Toeplitz matrix* $B\in M_{n+1}$ of the form
>$$
>B = \left[ \begin{array}{cccc}0 & 1 & \cdots & 0 \\  & 0 & \ddots &  \\ \vdots &  & \ddots & 1 \\ 0 &  & \cdots & 0 \end{array} \right] 
>$$
>is called the **backward shift**.

>[!important] Definition
>The *Toeplitz matrix* $F\in M_{n+1}$ of the form
>$$
>F = \left[ \begin{array}{cccc}0 &  & \cdots & 0 \\ 1 & 0 &  &  \\  &  \ddots & \ddots &  \\ 0 &  & 1  & 0 \end{array} \right] 
>$$
>is called the **forward shift**.

>[!info]
>Note that $$F = B^{T}, \quad B = F^{T}.$$ The **forward shift** and **backward shift** are *adjoint* to each other.

- [[Adjoint of Linear Map]]

## Explanation

>[!important] Proposition
>A matrix $A\in M_{n}$ can be written in the form
>$$
>A = \sum_{k=1}^{n}a_{-k}\,F^{k} + \sum_{k=0}^{n}a_{k}B^{k}
>$$
>where  $F, B\in M_{n}$ are **forword and backward shift matrix** *if and only if* $A$ is a **Toeplitz matrix**.


>[!info]
>Toeplitz matrices arise naturally in problems involving **trigonometric moments**.

- [[Discrete Fourier Transform]]



## Digital Convolution

![[Convolution Operation#^f03102]]

>[!important] Definition
>The **convolution operation** is a linear transformation. 
>
>Given $x = [x_{1}\,{,}\ldots{,}\,x_{n}]$, and $h = [h_{1}\,{,}\ldots{,}\,h_{m}]$, the **convolution** between $x$ and $h$ can be seen as multiplying $x$ with a **Toeplitz matrix** from $h$, i.e.
>$$
>\begin{align*}
> y &= h * x \\[5pt]
> &= \left[ \begin{array}{ccccc}h_{1} & 0 & \cdots & & 0 \\ h_{2} & h_{1} & \vdots & & \vdots \\ h_{3} & h_{2} & \ddots & &  \\ \vdots &  \ddots & \ddots & \ddots & 0 \\ h_{m-1} &  \ldots & \ldots & h_{2} & h_{1} \\ h_{m} &  \ddots & \ldots & h_{3} & h_{2} \\ 0 &  h_{m} & \ddots & \ddots & \vdots  \\   \vdots & \ddots & \ddots & \ddots & \vdots  \\ 0 & 0 & \cdots & 0 & h_{m} \end{array} \right]\;\left[ \begin{array}{c} x_{1} \\ x_{2} \\ \vdots \\ x_{n} \end{array}\right]  \\[5pt]
> &= T_{h}\,x
>\end{align*}
>$$

- [[Convolution Operation]]

>[!info]
>$$
>\begin{align*}
>y[i] &= (x * h)[i] = \sum_{l=-\infty}^{\infty}h[i - l]\,x[l]
>\end{align*}
>$$




-----------
##  Recommended Notes and References


- [[Skew-Hermitian and Skew-Symmetric Matrix]]
- [[Circulant Matrix and Circulant Permutation Operation]]
- [[Permutation Matrix and Reversal Matrix]]
- [[Discrete Fourier Transform]]
- [[Matrix]]



- [[Numerical Linear Algebra by Trefethen]] pp 68, 318, 337, 342
- [[Matrix Computations by Golub]] pp 208 - 218
- [[Matrix Analysis by Horn]] pp 34
- [[Matrix CookBook by Petersen]] pp 54