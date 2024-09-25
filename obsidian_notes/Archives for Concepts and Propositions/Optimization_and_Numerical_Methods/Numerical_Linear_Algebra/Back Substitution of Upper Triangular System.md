---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
keywords:
  - back_substitution_upper_triangular_system
  - system_of_linear_equations
topics:
  - numerical_linear_algebra
name: Back Substitution of Upper Triangular System
date of note: 2024-09-21
---

## Concept Definition

>[!important]
>**Name**: Back Substitution of Upper Triangular System

>[!important] Definition
>Consider the following **upper triangular system**
>$$
>\begin{align*}
> \left[ \begin{array}{ccccc}a_{11} & a_{12} & \cdots & a_{1n} \\[5pt]  & a_{22} & \cdots & a_{2n} \\[5pt]  &  & \ddots & \vdots \\[5pt] &  &  & a_{nn}\end{array} \right]\;\left[ \begin{array}{c}x_{1} \\[5pt] x_{2}\\[5pt] \vdots \\[5pt] x_{n}\end{array} \right]  &= \left[ \begin{array}{c}b_{1} \\[5pt] b_{2}\\[5pt] \vdots \\[5pt] b_{n}\end{array} \right] 
>\end{align*}
>$$
>
>The **row-oriented back substitution** algorithm that solves the above problem is described as follows:
>- *Require*: $A = [a_{i,j}]_{j\geq i}$ and $b= [b_{i}]$
>- Initialize $$x_{n} = \frac{b_{n}}{a_{nn}}$$
>- For $i=n-1\,{,}\ldots{,}\,1$:
>	- $$x_{i} = \frac{b_{i} - \sum_{j=i+1}^{n}a_{i j}\,x_{j}}{a_{i i}}$$

- [[Triangular Matrix and Block Triangular Matrix]]

>[!important] Definition
>**Column-oriented versions** of the above procedures can be obtained by *reversing loop orders*. Note that 
>$$
>\begin{align*}
> \left[ \begin{array}{cc}A_{1:n-1,1:n-1}   & A_{1:n-1,n}  \\[5pt]  0 & a_{nn} \end{array} \right]\;\left[ \begin{array}{c}x_{1:n-1} \\[5pt] x_{n}\end{array} \right]  &= \left[ \begin{array}{c}b_{1:n-1} \\[5pt] b_{n}\end{array} \right] 
>\end{align*}
>$$
>Thus
>$$
>A_{1:n-1,1:n-1}\,x_{1:n-1}  = b_{1:n-1} - A_{1:n-1,n}\,x_{n}
>$$
>
>Specifically, the **column-oriented back substitution** algorithm that solves the *upper triangular system*  is described as follows:
>- *Require*: $A = [a_{i,j}]_{j\leq i}$ and $b= [b_{i}]$
>- For $j=n\,{,}\ldots{,}\,2$:
>	- $$x_{j} = \frac{b_{j}}{a_{jj}}$$
>	- For $k=1 \,{,}\ldots{,}\,j-1$ *in parallel*:
>		- $$b_{k} \leftarrow b_{k} - a_{k,j}\,x_{j}$$
>- Finally $$x_{1} = \frac{b_{1}}{a_{11}}$$

- [[Principal Submatrix]]
- [[Partition of Matrix and Block Matrix]]
### Parallel Formulation

>[!important] Definition
>Specifically, the **column-oriented back substitution** algorithm that solves the *upper triangular system*  is described as follows:
>- *Require*: $A = [a_{i,j}]_{j\leq i}$ and $b= [b_{i}]$
>- For $j=n\,{,}\ldots{,}\,2$:
>	- $$x_{j} = \frac{b_{j}^{(n-j+1)}}{a_{jj}}$$
>	- $$b_{1:j-1}^{(n-j+2)} = b_{1:j-1}^{(n-j+1)} - a_{1:j-1,j}\;x_{j}$$
>- Finally $$x_{1} = \frac{b_{1}^{(n)}}{a_{11}}$$



## Explanation

>[!info]
>We can overwrite the vector $b$ as solution
>$$
>b_{i} \leftarrow \frac{b_{i} - \sum_{j=i+1}^{n}a_{i,j}\,b_{j}}{a_{i,i}}
>$$


## Algorithm Complexity Analysis

>[!important]
>Since the algorithm need to access each entry $a_{i,j}$ by row, the **time complexity** of the algorithm is $$O\left( n^2 \right)$$
>
>The **space complexity** is $O(1)$ since we can substitute $b$ into $x$ in place.





-----------
##  Recommended Notes and References


- [[Triangular System of Equations]]
- [[System of Linear Equations or Linear System]]
- [[Existence and Uniqueness of Solution of Linear Equations]]
- [[Forward Substitution of Lower Triangular System]]
- [[Triangular Matrix and Block Triangular Matrix]]


- [[Matrix Computations by Golub]] pp 106  - 109
- [[Matrix Analysis by Horn]] pp 216