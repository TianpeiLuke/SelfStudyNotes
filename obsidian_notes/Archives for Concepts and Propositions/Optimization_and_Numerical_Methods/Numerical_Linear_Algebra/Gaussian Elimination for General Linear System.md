---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
keywords:
  - gaussian_elimination
  - system_of_linear_equations
  - elementary_operation_matrix
topics:
  - numerical_linear_algebra
  - matrix_analysis
name: Gaussian Elimination for General Linear System
date of note: 2024-09-21
---

## Concept Definition

>[!important]
>**Name**: Gaussian Elimination for General Linear System

![[Elementary Row and Column Operations#^92e828]]

- [[Elementary Row and Column Operations]]

>[!important] Definition
>Consider a vector $v = [v_{1} \,{,}\ldots{,}\,v_{n}]$.
>
>A **Gaussian transformation** is a matrix of the form $$M_{k} = I_{n} - \sum_{i=k+1}^{n}\tau_{i}^{(k)}e_{i}\,e_{k}^{T}, \quad k=1\,{,}\ldots{,}\,n$$ where 
>- $e_{i}$ is the $i$-th column of identify matrix with only one $1$ at position $i$ of  the vector and all zeros in other places;
>- and $$\tau_{i}^{(k)} = \frac{v_{i}}{v_{k}},\quad i=k+1\,{,}\ldots{,}\,n,$$ are called **multipliers.**
>- $v_{k} \neq 0$ in the denominator of the *multipliers* is called the **pivot.**
>- We can write it compactly as $$M_{k} = I_{n} - \tau^{(k)}\,e_{k}^{T} \in \mathbb{R}^{n\times n}$$ where $$\tau^{(k)} := \sum_{i=k+1}^{n}\tau_{i}^{(k)}e_{i} = \left[ \begin{array}{c}0\\ \vdots\\ 0\\ \tau_{k+1}^{(k)}\\ \vdots\\ \tau_{n}^{(k)} \end{array} \right] $$  
>  
>Then left-multiplying the Gaussian transform gives $$M_{k}\,v = \left[ \begin{array}{cccccc}1 & \cdots & 0 & 0 & \cdots & 0 \\ \vdots & \ddots & \vdots & \vdots &  & \vdots \\ 0 & \cdots & 1 & 0 & \cdots & 0 \\ 0 & \cdots & -\tau_{k+1}^{(k)} & 1 & \cdots & 0 \\ \vdots & \ddots & \vdots & \vdots & \ddots & \vdots \\ 0 & \cdots & -\tau_{n}^{(k)} & 0 & \cdots & 1 \end{array} \right]\;\left[ \begin{array}{c}v_{1} \\ \vdots \\ v_{k} \\ v_{k+1} \\ \vdots \\ v_{n}\end{array} \right] =  \left[ \begin{array}{c}v_{1} \\ \vdots \\ v_{k} \\ 0 \\ \vdots \\ 0\end{array} \right]$$ 
>- Applying the Gaussian transformation $M_{k}$ on the vector $v_{k}$ will *set all rows below $k$* to $zero$. 

^cf77f5

>[!important] Definition
>Consider the problem of solving the *system of linear equations* $$Ax = b$$ where $A = [a_{i,j}]\in \mathbb{C}^{n\times n}$ and $b\in \mathbb{C}^{n}.$
>
>The **Gaussian elimination** transforms a full linear system into an *upper triangular matrix* by applying a successive of *Gaussian transformations* to each *row* $$M_{n-1}\,{}\ldots{}\,M_{1}\,A = U.$$ where
>- $$M_{k} := I_{n} - \tau^{(k)}\,e_{k}, \quad k=1\,{,}\ldots{,}\,n-1$$ with $\tau^{(k)} = [0 \,{,}\ldots{,}\,0, \tau_{k+1}^{(k)} \,{,}\ldots{,}\,\tau_{n}^{(k)}]$ and $$\tau_{i}^{(k)} = \frac{a_{i,k}^{(k)}}{a_{k,k}^{(k)}},\quad i=k+1\,{,}\ldots{,}\,n $$
>- Also $a_{i,j}^{(k)}$ is the $(i,j)$ entry in $A^{(k)}$ where $$A^{(k+1)} = M_{k}\,A^{(k)}$$
>- The entry $a_{k,k}^{(k)}$ of $A^{(k)}$ is called the **pivot**.
>
>The **Gaussian elimination** finds the solution $x$ by solving  two *triangular systems of equations* $$y = M_{n-1}\,{}\ldots{}\,M_{1}\,b,\; \quad Ux = y.$$ 

- [[System of Linear Equations or Linear System]]
- [[Triangular Matrix and Block Triangular Matrix]]


### Gaussian Elimination for LU Factorization

>[!important] Definition
>Consider the problem of solving the *$LU$ factorization* $$A= L\,U$$ where $A = [a_{i,j}]\in \mathbb{C}^{n\times n}$, $L$ is an *unit lower triangular matrix* and $U$ is *upper triangular matrix*.
>
>Assume that $$\det(A_{\{1:k\},\{1:k\}}) \neq 0, \quad k=1\,{,}\ldots{,}\,n-1.$$
>
>The **Gaussian Elimination without pivoting** computes the *LU factorization* as follows:
>- *Require*: $A\in \mathbb{R}^{n\times n}$
>- *Initialize*: $L = I$, and $U = A$
>- For $k=1\,{,}\ldots{,}\,n-1$:
>	- For $j=k+1\,{,}\ldots{,}\,n$:
>		- Compute the $(j,k)$ entry of $L$ $$L_{j,k} = \frac{U_{j,k}}{U_{k,k}}$$
>		- Apply **Gaussian transformation** on $j$-th *row* of $U$ $$U_{j, \{k:n\}} \leftarrow U_{j, \{k:n\}} - L_{j,k}\,U_{k, \{k:n\}}.$$
>			- Note that $U_{j,k} = 0$ after update
>			- So we can update $$U_{j, \{k+1:n\}} \leftarrow U_{j, \{k+1:n\}} - L_{j,k}\,U_{k, \{k+1:n\}}.$$

^057350

- [[LU Factorization of Matrix]]


>[!info]
>We can run Gaussian elimination **in place** on $A$, where $A_{i,i:n}$ is overwritten by $U_{i,i:n}$, and $A_{i+1:n,i} = L_{i+1:n,i}$.

>[!important] 
>The algorithm involves $$\frac{2n^3}{3}$$ flops.
>
>Note that the $k$-th step involves an $(n-k)\times(n-k)$ **outer product**
>$$
> U_{k+1:n, k+1:n} - L_{k+1:n, k}\,U_{k, k+1:n}
>$$

- [[Algorithm Big-O Notations and Dominance Relation]]
- [[Algorithm RAM Model and Running-Time Complexity Analysis]]


## Explanation

>[!info]
>The Gaussian transformation is a successive operations of **Type 3 elementary operation**
>$$
>M_{k}(v_{k}; v_{k+1:n}) := \prod_{i=k+1}^{n}E_{3}(k, i, -\tau_{i})
>$$
>- We **substract** $\tau_{i}$ **times** *row* $k$ from row $i$.


>[!quote]
>Triangular system solving is an easy $O(n^2)$ computation. The **idea** behind **Gaussian  elimination** is to *convert* a given system $Ax = b$ to an equivalent **triangular system**. The conversion is achieved by taking appropriate linear combinations of the equations.
>
>-- [[Matrix Computations by Golub]] pp 111

### Outer Product Formulation

>[!important]
>Consider the partition $$A = \left[ \begin{array}{cc}\alpha & w^{T} \\ v & B \end{array} \right] \in M_{n}$$ where $B\in M_{n-1}$, and  $w, v\in F^{n}.$
>
>Then the last step of **Gaussian elimination** corresponds to the following operation
>$$
>\begin{align*}
> A &= \left[ \begin{array}{cc}1 & 0 \\[5pt] v / \alpha & I_{n-1}  \end{array} \right]\; \left[ \begin{array}{cc} 1 & 0 \\[5pt] 0 & L_{1}\,U_{1} \end{array} \right]\; \left[ \begin{array}{cc}\alpha & w^{T} \\[5pt] 0 & I_{n-1}  \end{array} \right] \\[5pt]
> &=  \left[ \begin{array}{cc}1 & 0 \\[5pt] v / \alpha & L_{1}  \end{array} \right]\;  \left[ \begin{array}{cc}\alpha & w^{T} \\[5pt] 0 & U_{1} \end{array} \right] \\[5pt]
> &\equiv L\,U
>\end{align*}
>$$
>where $$B - v\,w^{T} / \alpha = L_{1}\,U_{1} $$ is the **LU factorization** of **rank-1 updated trailing principal submatrix** $B - v\,w^{T} / \alpha$.

^c1fdc9

- [[LDU Factorization of Symmetric Matrix]]

>[!important] Definition
>Consider the problem of solving the *$LU$ factorization* $$A= L\,U$$ where $A = [a_{i,j}]\in \mathbb{C}^{n\times n}$, $L$ is an *unit lower triangular matrix* and $U$ is *upper triangular matrix*.
>
>Assume that $$\det(A_{1:k,1:k}) \neq 0, \quad k=1\,{,}\ldots{,}\,n-1.$$
>
>The **outer product LU factorization** is decribed as follows:
>- *Require*: $A\in \mathbb{R}^{n\times n}$
>- For $k=1\,{,}\ldots{,}\,n-1$:
>	- Collect a list of indices $\rho = \{k+1:n\}$
>	- Replace the $k$-th column of *lower triangular* part of $A$ $$A[\rho, k] \leftarrow \frac{A[\rho, k]}{A[\rho, \rho]}$$
>	- Replace the *$(n-k)$ trailing principal submatrix* by the **outer product** $$A[\rho, \rho] \leftarrow A[\rho, \rho] - A[\rho, k]\,A[k, \rho].$$

^5aee93



## LU Factorization 

>[!important]
>**Gaussian elimination** defines a process to obtain the **LU factorization** of a non-singular matrix $A$ $$A= L\,U$$ where $$L := M_{1}^{-1}\,{}\ldots{}\,M_{n-1}^{-1}.$$

- [[LU Factorization of Matrix]]

## Band LU Factorization

- [[Band Gaussian Elimination and Band LU Factorization]]

## Band LU Factorization

- [[Band Gaussian Elimination and Band LU Factorization]]




-----------
##  Recommended Notes and References


- [[System of Linear Equations or Linear System]]
- [[Existence and Uniqueness of Solution of Linear Equations]]
- [[Back Substitution of Upper Triangular System]]
- [[LU Factorization of Matrix]]
- [[Reduced Row Echelon Form]]


- [[Principal Submatrix]]
- [[Schur Complement and Inversion of Block Matrix]]
- [[System of Linear Equations or Linear System]]
- [[Matrix]]

- [[Gaussian Elimination with Complete Pivoting]]


- [[Matrix Computations by Golub]] pp 111 - 114
- [[Numerical Linear Algebra by Trefethen]] pp 147 - 171 
- [[Matrix CookBook by Petersen]] pp 32