---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
  - numerical_methods/numerical_linear_algebra
keywords:
  - companion_matrix_polynomial
topics:
  - matrix_analysis
  - numerical_linear_algebra
  - linear_algebra
name: Companion Matrix of Polynomial
date of note: 2024-09-25
---

## Concept Definition

>[!important]
>**Name**: Companion Matrix of Polynomial

>[!important] Definition
>Let $p(x)$ be a *polynomial* of *degree* $(n-1)$, i.e. $$p_{n-1}(x) = a_{n-1}x^{n-1} \,{+}\ldots{+}\,a_{1}x + a_{0},$$ where $a_{i}\in F$ is some *field*.
>
>A **companion matrix** or the **companion form** associated with $p_{n-1}(x)$ is of the form $$C = \left[ \begin{array}{ccccc}0 & 1 & 0 & \cdots & 0 \\ 0 & 0 & 1 & \ddots & \vdots \\ \vdots &  & \ddots & \ddots & 0 \\ 0 & \cdots & \cdots & 0 & 1 \\ a_{0} & a_{1} & \cdots & a_{n-2} & a_{n-1} \\ \end{array} \right] \in M_{n}(F)$$



## Explanation

>[!info]
>$$C = \left[ \begin{array}{cc}0 & I_{n-1} \\ a_{0} & a_{1:n-1} \end{array} \right] $$




-----------
##  Recommended Notes and References


- [[Minimal Polynomial for Linear Map]]
- [[Characteristic Polynomial for Linear Map]]
- [[Matrix]]


- [[Matrix Analysis by Horn]] pp 197- 199, 404, 457
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 105 - 106
- [[Matrix Computations by Golub]] pp 382
