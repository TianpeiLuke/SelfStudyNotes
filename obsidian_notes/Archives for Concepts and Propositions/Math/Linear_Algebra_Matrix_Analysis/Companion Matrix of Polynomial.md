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
>Let $p_{n}(x)$ be a *polynomial* of *degree* $n$, i.e. $$p_{n}(x) = x^n + a_{n-1}x^{n-1} \,{+}\ldots{+}\,a_{1}x + a_{0},$$ where $a_{i}\in F$ is some *field*.
>
>A **companion matrix** or the **companion form** of $p_{n}(x)$ is of the form $$C = \left[ \begin{array}{ccccc}0 & 0 & \cdots & 0 & -a_{0} \\ 1 & 0 & \cdots & 0& -a_{1} \\  0 & 1 & \ddots & \vdots & \vdots \\ \vdots &  & \ddots & 0 & -a_{n-2} \\ 0 & \cdots & 0 & 1 & -a_{n-1} \end{array} \right] \in M_{n}(F)$$


>[!important] Proposition
>- The **characteristic polynomial** of $C$ is $p_{n}(\lambda)$ $$\det \left(\lambda I - C\right) = \lambda^n + a_{n-1}\lambda^{n-1} \,{+}\ldots{+}\,a_{1}\lambda + a_{0} := p_{n}(\lambda)$$
>- The **minimal polynomial** of $C$ is equal to the **characteristic polynomial** of $C$.

- [[Characteristic Polynomial for Linear Map]]
- [[Minimal Polynomial for Linear Map]]

## Explanation

>[!info]
>$$C = \left[ \begin{array}{cc}0 &  -a_{0} \\ I_{n-1} & -a_{1:n-1} \end{array} \right] $$




-----------
##  Recommended Notes and References


- [[Minimal Polynomial for Linear Map]]
- [[Characteristic Polynomial for Linear Map]]
- [[Matrix]]


- [[Matrix Analysis by Horn]] pp 197- 199, 404, 457
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 105 - 106
- [[Matrix Computations by Golub]] pp 382
- Wikipedia [Companion_matrix](https://en.wikipedia.org/wiki/Companion_matrix)
