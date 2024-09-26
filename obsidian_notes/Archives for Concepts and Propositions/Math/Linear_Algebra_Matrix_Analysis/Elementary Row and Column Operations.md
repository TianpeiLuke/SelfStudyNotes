---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
  - numerical_methods/numerical_linear_algebra
keywords:
  - elementary_operation_matrix
topics:
  - matrix_analysis
  - numerical_linear_algebra
name: Elementary Row and Column Operations
date of note: 2024-09-24
---

## Concept Definition

>[!important]
>**Name**: Elementary Row and Column Operations

>[!info] 
>*Three simple and fundamental operations* on rows or columns, called **elementary row** and **column operations**, can be used to transform a matrix (square or not) into a simple form that facilitates such tasks as 
>- solving linear equations, 
>- determining rank, and 
>- calculating determinants and 
>- inverses of square matrices.

>[!important] Definition
>The **elementary row/column operations** include the following *three types*:
>- **Type 1: Interchange of two rows**: interchange row $i$ and $j$ results from the left multiplication of $A$ by $$E_{1}:= \left[\begin{array}{ccccccc}1 & & & & & & & &\\ & \ddots & & & & & & &\\ & & 0& & \cdots & & 1& &\\  & & \vdots & & & & \vdots& &\\& & 1& & \cdots & & 0& &\\ & & & &  & & & \ddots &\\ & & & & & & & & 1  \end{array} \right]$$ where
>	- the only two *nonzero* *off-diagonal entries* are in $(i,j)$ and $(j,i)$ positions, and 
>	- the two *zero diagonal entries* are in $(i,i)$ and $(j,j)$ position  
>	- We can represent the **Type 1 elementary operation matrix** as $$E_{1} = I_{n} - (e_{i} - e_{j})(e_{i} - e_{j})^{T}$$ where  $e_{i} = [0\,{,}\ldots{,}\,1_{i}\,,0\,{,}\ldots{,}\,0]$ has one $1$ at $i$-th place. 
>	- $e_{i}$ is the $i$-th column of identity matrix $I$.
>- **Type 2: Multiplication of a row by a Nonzero Scalar**: multiplication of row $i$ by a nonzero scalar $\tau$ results from left multiplication of $A$ by $$E_{2} := \left[ \begin{array}{ccccccc}1& & & & & & \\ & \ddots & & & & & \\ & & 1 & & & & \\ & & &\tau & & & \\ & & & &1 & & \\ & & & & & \ddots & \\ & & & & & & 1\\ \end{array} \right] $$
>	- The $(i,i)$ place is the **multiplier scalar**  $\tau$.
>	- We can represent the **Type 2 elementary operation matrix** as $$E_{2} = I_{n} + (\tau -1)\,e_{i}\,e_{i}^T.$$
>- **Type 3: Addition of a Scalar Multiple of one row to another row**: addition of $\tau$ times row $i$ of $A$ to row $j$ of $A$ results from left multiplication of $A$ by $$E_{3} = \left[ \begin{array}{cccccc}1 & & & & & \\  & \ddots & & & & \\ &  & 1 & & & \\ &  & & 1 & & \\ &  & \tau & & \ddots & \\ &  & & &  & 1\\ \end{array} \right] $$
>	- The $(j,i)$ place is the **multiplier scalar** $\tau$. In above display $j > i$.
>	- We can represent the **Type 3 elementary operation matrix** as $$E_{3} = I_{n} + \tau\,e_{j}\,e_{i}^T.$$

^92e828


## Explanation

### Determinant

>[!important] 
>- The effect of a **Type 1 operation** on determinant is to **change the sign** of its *determinant* $$\det(E_{1}\,A) = - \det(A)$$
>- The effect of a **Type 2 operation** on determinant is to **multiply** it by $\tau$  $$\det(E_{2}\,A) = \tau\,\det(A)$$
>- The effect of a **Type 3 operation** on determinant is to maintain it **unchanged** $$\det(E_{3}\,A) = \det(A)$$

- [[Determinant of Linear Transformation]]
- [[Alternating Tensor]]
- [[Multilinear Function]]






-----------
##  Recommended Notes and References


- [[Reduced Row Echelon Form]]
- [[Matrix Transformation]]
- [[Matrix]]


- [[Matrix Analysis by Horn]] pp 10 
- [[Matrix Analysis for Scientists and Engineers by Laub]]
- [[Matrix Computations by Golub]] pp 112