---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
  - numerical_methods/numerical_linear_algebra
keywords:
  - gauss_seidel_iteration
  - sparse_linear_equations
topics:
  - numerical_linear_algebra
  - linear_algebra
  - matrix_analysis
name: Gauss-Seidel Iteration for Sparse Linear Equations
date of note: 2024-09-21
---

## Concept Definition

>[!important]
>**Name**: Gauss-Seidel Iteration for Sparse Linear Equations

![[Jacobi Iteration for Sparse Linear System#^2e75bb]]

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
>The **Gauss-Seidel iteration** generates a *new approximation* $x^{(k)}$ by computing a **forward pass**
>$$
>\begin{align*}
> x_{i}^{(k)}  &= \dfrac{b_{i} - \sum_{j=1}^{i-1}a_{i,j}\,x_{j}^{(k)} -  \sum_{j=i+1}^{n}a_{i,j}\,x_{j}^{(k-1)}}{a_{i,i}}, \quad i=1\,{,}\ldots{,}\,n
>\end{align*}
>$$

- [[Jacobi Iteration for Sparse Linear System]]

>[!important] Definition
>Consider the *linear system* $$Ax = b$$ where $A = [a_{i,j}] \in M_{m,n}(\mathbb{C})$,  $b = [b_{i}]\in \mathbb{C}^{m}$. 
>
>The **Gauss-Seidel iteration**  generates a *new approximation* $x^{(k)}$ at iteration $k$ by $$M_{GS}\,x^{(k)} = N_{GS}\,x^{(k-1)} + b$$
>where 
>$$
>M_{GS} = D_{A} + L_{A},\quad N_{GS} = - U_{A}
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

>[!info]
>$$
>\begin{align*}
> x_{i}^{(k)}  &= \dfrac{1}{a_{i,i}}\left(b_{i} - \sum_{j=1}^{i-1}a_{i,j}\,x_{j}^{(k)} -  \sum_{j=i+1}^{n}a_{i,j}\,x_{j}^{(k-1)}\right), \quad i=1\,{,}\ldots{,}\,n
>\end{align*}
>$$
>can be interpreted as a **message-passing algorithm** where $x_{1}\,{\succ}\ldots{\succ}\,x_{n}$ defines a **topological ordering**
>- At iteration $k$, all variables $j \le i$ are replaced by *updated value* $x_{j}^{(k)}$, which is the **forward pass**.

- [[Mean Field Approximation for Gaussian Markov Random Field]]




-----------
##  Recommended Notes and References

- [[Classical Iterations to approximate Solution of Sparse Linear System]]
- [[Jacobi Iteration for Sparse Linear System]]

- [[System of Linear Equations or Linear System]]
- [[Existence and Uniqueness of Solution of Linear Equations]]


- [[Gaussian Belief Propagation]]
- [[Gaussian Graphical Model]]
- [[Graph LASSO and Structured Learning in Gaussian Graphical Model]]
- [[Inverse Covariance Estimation]]


- [[Matrix Computations by Golub]] pp 611 - 615
- [[Numerical Linear Algebra by Trefethen]] pp 318, 339