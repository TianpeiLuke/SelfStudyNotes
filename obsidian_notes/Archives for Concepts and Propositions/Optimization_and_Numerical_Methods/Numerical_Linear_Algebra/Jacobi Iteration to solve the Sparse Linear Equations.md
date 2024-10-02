---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
keywords:
  - jacobi_iteration_sparse_linear_system
topics:
  - numerical_linear_algebra
name: Jacobi Iteration to solve the  - numerical_methods/numerical_linear_algebra
keywords:
  - jacobi_iteration_sparse_linear_system
topics:
  - numerical_linear_algebra
name: Jacobi Iteration to solve the Sparse Linear Equations
date of note: 2024-09-21
---

## Concept Definition

>[!important]
>**Name**: Jacobi Iteration to solve the Sparse Linear Equations

![[Classical Iterations to approximate Solution of Sparse Linear System#^39280e]]

![[System of Linear Equations or Linear System#^818e89]]

>[!important] Definition
>Consider the *linear system* $Ax = b$ where $A = [a_{i,j}] \in M_{m,n}(\mathbb{C})$,  $b = [b_{i}]\in \mathbb{C}^{m}$. That is,
>$$
>\begin{align*}
> a_{1,1}x_{1} \,{+}\ldots{+}\,a_{1,n}x_{n} &= b_{1}\\[5pt]
> a_{2,1}x_{1} \,{+}\ldots{+}\,a_{2,n}x_{n} &= b_{2}\\[5pt]
> \ldots& \\[5pt]
> a_{m,1}x_{1} \,{+}\ldots{+}\,a_{m,n}x_{n} &= b_{m}
>\end{align*}
>$$
>Suppose $x^{(k-1)}$ is an *approximation* to $x = A^{-1}b$. 
>
>The **Jacobi iteration** generates a *new approximation* $x^{(k)}$ by computing 
>$$
>\begin{align*}
> x_{i}^{(k)}  &= \frac{b_{i} - \sum_{j=1}^{i-1}a_{i,j}\,x_{j}^{(k-1)} -  \sum_{j=i+1}^{n}a_{i,j}\,x_{j}^{(k-1)}}{a_{i,i}}, \quad i=1\,{,}\ldots{,}\,n
>\end{align*}
>$$

^2e75bb

- [[System of Linear Equations or Linear System]]
- [[Classical Iterations to approximate Solution of Sparse Linear System]]

>[!important] Definition
>Consider the *linear system* $$Ax = b$$ where $A = [a_{i,j}] \in M_{m,n}(\mathbb{C})$,  $b = [b_{i}]\in \mathbb{C}^{m}$. 
>
>The **Jacobi iteration**  generates a *new approximation* $x^{(k)}$ at iteration $k$ by $$M_{J}\,x^{(k)} = N_{J}\,x^{(k-1)} + b$$
>where 
>$$
>M_{J} = D_{A},\quad N_{J} = -\left(L_{A} + U_{A}\right)
>$$
>and $D_{A}$, $L_{A}$ and $U_{A}$ are *diagonal entries*, *lower triangular entries*, and *upper triangular entries* of $A$, respectively
>$$
>\begin{align*}
> D_{A} &= \text{diag}(A) = \text{diag}(a_{1,1} \,{,}\ldots{,}\,a_{n,n})\\[5pt] 
> L_{A} &= \left[ \begin{array}{cccc}0&  &  & 0 \\ a_{2,1}& 0 &  & \vdots\\ \vdots & \ddots & \ddots & \vdots\\ a_{n,1}& \cdots & a_{n,n-1} & 0\end{array} \right]\\[5pt]  
> U_{A} &= \left[ \begin{array}{cccc}0& a_{1,2}  & \cdots  & a_{1,n} \\\vdots & 0 & \ddots & \vdots\\ \vdots &  & \ddots & a_{n-1,n}\\ 0 &  &  & 0\end{array} \right]
\end{align*}
>$$



## Explanation

>[!quote]
>Note that the **most recent solution estimate** is **not fully exploited** in the updating of  a particular component. For example, $x^{(k-1)}$ is used in the calculation of $x_{2}^{(k)}$ even  though $x_{1}^{(k)}$ is available.
>
>-- [[Matrix Computations by Golub]] pp 612




-----------
##  Recommended Notes and References


- [[Classical Iterations to approximate Solution of Sparse Linear System]]
- [[Gauss-Seidel Iteration to solve Sparse Linear Equations]]

- [[System of Linear Equations or Linear System]]
- [[Existence and Uniqueness of Solution of Linear Equations]]


- [[Matrix Computations by Golub]] pp 611 - 617
- [[Numerical Linear Algebra by Trefethen]] pp 