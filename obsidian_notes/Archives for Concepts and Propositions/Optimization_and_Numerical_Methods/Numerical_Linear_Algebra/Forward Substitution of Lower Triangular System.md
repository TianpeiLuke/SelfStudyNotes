---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
keywords:
  - forward_substitution_lower_triangular_system
  - linear_system
topics:
  - numerical_linear_algebra
name: Forward Substitution of Lower Triangular System
date of note: 2024-09-21
---

## Concept Definition

>[!important]
>**Name**: Forward Substitution of Lower Triangular System

>[!important] Definition
>Consider the following **lower triangular system**
>$$
>\begin{align*}
> \left[ \begin{array}{ccccc}a_{11} & &  &  \\[5pt] a_{21} & a_{22} &  &  \\[5pt] \cdots & \cdots & \ddots \\[5pt] a_{n1} & a_{n2} & \cdots & a_{nn}\end{array} \right]\;\left[ \begin{array}{c}x_{1} \\[5pt] x_{2}\\[5pt] \vdots \\[5pt] x_{n}\end{array} \right]  &= \left[ \begin{array}{c}b_{1} \\[5pt] b_{2}\\[5pt] \vdots \\[5pt] b_{n}\end{array} \right] 
>\end{align*}
>$$
>
>The **row-oriented forward substitution** algorithm that solves the above problem is described as follows:
>- *Require*: $A = [a_{i,j}]_{j\leq i}$ and $b= [b_{i}]$
>- Initialize $$x_{1} = \frac{b_{1}}{a_{11}}$$
>- For $i=2\,{,}\ldots{,}\,n$:
>	- $$x_{i} = \frac{b_{i} - \sum_{j=1}^{i-1}a_{i j}\,x_{j}}{a_{i i}}$$

>[!important] Definition
>**Column-oriented versions** of the above procedures can be obtained by *reversing loop orders*. Note that 
>$$
>\begin{align*}
> \left[ \begin{array}{cc}a_{11} & 0  \\[5pt] A_{2:n,1} & A_{2:n, 2:n} \end{array} \right]\;\left[ \begin{array}{c}x_{1} \\[5pt] x_{2:n}\end{array} \right]  &= \left[ \begin{array}{c}b_{1} \\[5pt] b_{2:n}\end{array} \right] 
>\end{align*}
>$$
>Thus
>$$
>A_{2:n, 2:n}\,x_{2:n} = b_{2:n} - x_{1}\,A_{2:n,1}
>$$
>
>Specifically, the **column-oriented forward substitution** algorithm that solves the *lower triangular system*  is described as follows:
>- *Require*: $A = [a_{i,j}]_{j\leq i}$ and $b= [b_{i}]$
>- For $j=1\,{,}\ldots{,}\,n-1$:
>	- $$x_{j} = \frac{b_{j}}{a_{jj}}$$
>	- For $k=j+1 \,{,}\ldots{,}\,n$:
>		- $$x_{k} \leftarrow x_{k} - a_{k,j}\,x_{j}$$
>- Finallly $$x_{n} = \frac{b_{n}}{a_{nn}}$$



## Explanation

>[!info]
>We can overwrite the vector $b$ as solution
>$$
>b_{i} \leftarrow \frac{b_{i} - \sum_{j=1}^{i-1}a_{i,j}\,b_{j}}{a_{i,i}}
>$$



-----------
##  Recommended Notes and References


- [[Triangular System of Equations]]
- [[System of Linear Equations or Linear System]]
- [[Existence and Uniqueness of Solution of Linear Equations]]
- [[Back Substitution of Upper Triangular System]]


- [[Matrix Computations by Golub]] pp 106 - 109