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

^17a742

>[!important] Definition
>The **elementary row/column operations** include the following *three types*:
>- **Type 1: Interchange of two rows**: interchange row $i$ and $j$ results from the left multiplication of $A$ by $$E_{1}(i,j):= \left[\begin{array}{ccccccc}1 & & & & & & & &\\ & \ddots & & & & & & &\\ & & 0& & \cdots & & 1& &\\  & & \vdots & & & & \vdots& &\\& & 1& & \cdots & & 0& &\\ & & & &  & & & \ddots &\\ & & & & & & & & 1  \end{array} \right]$$ where
>	- the only two *nonzero* *off-diagonal entries* are in $(i,j)$ and $(j,i)$ positions, and 
>	- the two *zero diagonal entries* are in $(i,i)$ and $(j,j)$ position  
>	- We can represent the **Type 1 elementary operation matrix** as $$E_{1}(i,j) = I_{n} - (e_{i} - e_{j})(e_{i} - e_{j})^{T}$$ where  $e_{i} = [0\,{,}\ldots{,}\,1_{i}\,,0\,{,}\ldots{,}\,0]$ has one $1$ at $i$-th place. 
>	- $e_{i}$ is the $i$-th column of identity matrix $I$.
>- **Type 2: Multiplication of a row by a Nonzero Scalar**: multiplication of row $i$ by a nonzero scalar $\tau$ results from left multiplication of $A$ by $$E_{2}(i, \tau) := \left[ \begin{array}{ccccccc}1& & & & & & \\ & \ddots & & & & & \\ & & 1 & & & & \\ & & &\tau & & & \\ & & & &1 & & \\ & & & & & \ddots & \\ & & & & & & 1\\ \end{array} \right] $$
>	- The $(i,i)$ place is the **multiplier scalar**  $\tau$.
>	- We can represent the **Type 2 elementary operation matrix** as $$E_{2}(i) = I_{n} + (\tau -1)\,e_{i}\,e_{i}^T.$$
>- **Type 3: Addition of a Scalar Multiple of one row to another row**: addition of $\tau$ times row $i$ of $A$ to row $j$ of $A$ results from left multiplication of $A$ by $$E_{3}(i,j, \tau) = \left[ \begin{array}{cccccc}1 & & & & & \\  & \ddots & & & & \\ &  & 1 & & & \\ &  & & 1 & & \\ &  & \tau & & \ddots & \\ &  & & &  & 1\\ \end{array} \right] $$
>	- The $(j,i)$ place is the **multiplier scalar** $\tau$. In above display $j > i$.
>	- We can represent the **Type 3 elementary operation matrix** as $$E_{3}(i,j) = I_{n} + \tau\,e_{j}\,e_{i}^T.$$

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


## Examples
### Gaussian Elimination

>[!example]
>Consider a vector $v = [v_{1} \,{,}\ldots{,}\,v_{n}]$.
>
>A **Gaussian transformation** is a matrix of the form $$M_{k} = I_{n} - \sum_{i=k+1}^{n}\tau_{i}^{(k)}e_{i}\,e_{k}^{T} = I_{n} - \tau^{(k)}\,e_{k}^{T}, \quad k=1\,{,}\ldots{,}\,n$$ where 
>- $e_{i}$ is the $i$-th column of identify matrix with only one $1$ at position $i$ of  the vector and all zeros in other places;
>- and $$\tau_{i}^{(k)} = \frac{v_{i}}{v_{k}},\quad i=k+1\,{,}\ldots{,}\,n,$$ are called **multipliers.**
>
>  
>Then left-multiplying the Gaussian transform gives $$M_{k}\,v = \left[ \begin{array}{cccccc}1 & \cdots & 0 & 0 & \cdots & 0 \\ \vdots & \ddots & \vdots & \vdots &  & \vdots \\ 0 & \cdots & 1 & 0 & \cdots & 0 \\ 0 & \cdots & -\tau_{k+1}^{(k)} & 1 & \cdots & 0 \\ \vdots & \ddots & \vdots & \vdots & \ddots & \vdots \\ 0 & \cdots & -\tau_{n}^{(k)} & 0 & \cdots & 1 \end{array} \right]\;\left[ \begin{array}{c}v_{1} \\ \vdots \\ v_{k} \\ v_{k+1} \\ \vdots \\ v_{n}\end{array} \right] =  \left[ \begin{array}{c}v_{1} \\ \vdots \\ v_{k} \\ 0 \\ \vdots \\ 0\end{array} \right]$$ 
>- Applying the Gaussian transformation $M_{k}$ on the vector $v_{k}$ will *set all rows below $k$* to $zero$. 

- [[Gaussian Elimination to solve Linear System]]

### Pivoting

>[!example]
>**Pivoting** refers to technique that choose a proper entry in each column $k$ as the pivot for *Gaussian transformation* by **interchange permutation** of chosen row with the current *pivot row* $k$.
>
>The benefit of pivoting is that the ratio $\tau^{(k)}$ can be bounded. 

- [[Gaussian Elimination with Partial Pivoting]]




-----------
##  Recommended Notes and References


- [[Reduced Row Echelon Form]]
- [[Matrix Transformation]]
- [[Matrix]]


- [[Matrix Analysis by Horn]] pp 10 
- [[Matrix Analysis for Scientists and Engineers by Laub]]
- [[Matrix Computations by Golub]] pp 112