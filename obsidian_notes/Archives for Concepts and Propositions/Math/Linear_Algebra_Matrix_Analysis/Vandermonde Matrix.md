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
topics:
  - matrix_analysis
  - linear_algebra
  - numerical_linear_algebra
name: Vandermonde Matrix
date of note: 2024-10-24
---

## Concept Definition

>[!important]
>**Name**: Vandermonde Matrix

### Vandermonde Matrix


>[!important] Definition
>A matrix $V \in M_{n}(F)$ is called **Vandermonde matrix** if it has the form
>$$
>\begin{align*}
> V := V(x_{1}\,{,}\ldots{,}\,x_{n}) &=  \left[ \begin{array}{ccccc} 1 & x_{1} & x_{1}^2 & \ldots & x_{1}^{n-1} \\[5pt] 1 & x_{2} & x_{2}^2 & \ldots & x_{2}^{n-1} \\[5pt] \vdots  & \vdots & \vdots & \vdots & \vdots \\[5pt] 1 & x_{n} & x_{n}^2 & \ldots & x_{n}^{n-1} \\[5pt] \end{array} \right]
>\end{align*}
>$$
>where $x_{1}\,{,}\ldots{,}\,x_{n}\in F$.
>- That is, $$V= [v_{i,j}], \quad v_{i,j} = x_{i}^{j-1}$$

### Determinant of Vandermonde Matrix

>[!important] Proposition
>Let $V\in M_{n}(F)$ be a **Vandermonde matrix** with respect to  $x_{1}\,{,}\ldots{,}\,x_{n}\in F$.
>
>Then the **determinant** of $A$ is given by 
>$$
>\det(V(x_{1}\,{,}\ldots{,}\,x_{n})) = \prod_{i \neq j = 1}^{n}(x_{i} - x_{j})
>$$
>- Thus a **Vandermonde matrix** is **nonsingular** *if and only if* $$x_{1} \,{,}\ldots{,}\,x_{n}$$ are all **distinct.**

- [[Determinant of Linear Transformation]]



## Explanation



## Linear Interpolation

>[!important]
>The  **Vandermonde matrix** arises in **interpolation problem** of finding a *polynomial* of degree *at most* $n-1$ with coefficients in $F$ $$p_{n-1}(x) = a_{n-1}x^{n-1} + a_{n-2}x^{n-2} \,{+}\ldots{+}\,a_{1}x + a_{0}$$ such that 
>$$
>\begin{align*}
>p_{n-1}(x_{1}) = a_{n-1}x_{1}^{n-1} + a_{n-2}x_{1}^{n-2} \,{+}\ldots{+}\,a_{1}x_{1} + a_{0} &= y_{1} \\[5pt]
>p_{n-1}(x_{2}) = a_{n-1}x_{2}^{n-1} + a_{n-2}x_{2}^{n-2} \,{+}\ldots{+}\,a_{1}x_{2} + a_{0} &= y_{2} \\[5pt]
>\ldots &\\[5pt]
>p_{n-1}(x_{n}) = a_{n-1}x_{n}^{n-1} + a_{n-2}x_{n}^{n-2} \,{+}\ldots{+}\,a_{1}x_{n} + a_{0} &= y_{n} \\[5pt]
>\end{align*}
>$$
>where $\{x_{1}\,{,}\ldots{,}\,x_{n}\} \subset F$ and $\{y_{1}\,{,}\ldots{,}\,y_{n}\} \subset F$
>
>Thus this corresponds to a **Vandermonde system of equations** for 
>- $a := (a_{0}\,{,}\ldots{,}\,a_{n-1})$  
>- $y: = (y_{1}\,{,}\ldots{,}\,y_{n})$
>
>which is given by 
>$$V(x_{1}\,{,}\ldots{,}\,x_{n})\,a= y$$


## DFT Matrix

- [[DFT Matrix]]


## Vandermonde Similarity and Companion Matrix


- [[Companion Matrix of Polynomial]]






-----------
##  Recommended Notes and References

- [[Circulant Matrix and Circulant Permutation Operation]]
- [[Discrete Fourier Transform]]

- [[Matrix Analysis by Horn]] pp 37, 128
- [[Matrix Computations by Golub]] pp 203
- [[Numerical Linear Algebra by Trefethen]] pp 4, 53, 64, 78, 137, 289, 292, 337