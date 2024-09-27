---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
  - math/linear_algebra
keywords:
  - ldu_factorization_symmetric
  - symmetric_matrix
topics:
  - matrix_analysis
  - numerical_linear_algebra
name: LDU Factorization of Symmetric Matrix
date of note: 2024-08-08
---

## Concept Definition

>[!important]
>**Name**: $LDL^T$ Factorization of Symmetric Matrix

![[LU Factorization of Matrix#^62518f]]

>[!important] Proposition ($LDL^{T}$ Factorization)
>Let $A\in M_{n}$ be a **Hermitian matrix** and all of its **leading principal submatrices** are nonsingular $$\det \left( A[1:k, 1:k] \right) \neq 0, \quad k=1\,{,}\ldots{,}\,n-1.$$
>
>Then there exists a **unit lower triangular matrix** $L$ and a **diagonal matrix** $$D = \text{diag}(d_{1}\,{,}\ldots{,}\,d_{n})$$ such that $$A = L\,D\,L^{*}.$$
>
>And the factorization is **unique**.

^951558

- [[Hermitian or Symmetric Matrix]]
- [[LU Factorization of Matrix]]

>[!important] Definition
>Let $A\in \mathbb{R}^{n\times n}$ be *symmetric matrix* with *all nonsingular leading principal submatrices*.
>
>Then the **$LDL^{T}$ factorization** of $A$ is given by $$A = L\,D\,L^{T}.$$


### Algorithms

![[Gaussian Elimination for Solving Linear System#^057350]]

- [[Gaussian Elimination for Solving Linear System]]


>[!important] Definition
>Consider the task to solve the *$LDL^{T}$ factorization* $$A= L\,D\,L^{T}$$ where $A\in \mathbb{R}^{n\times n}$ is *symmetric* whose *all leading principle submatrices* are *nonsingular*, $L\in M_{n}$ is *lower triangular matrix* with *unit diagonal* and $D = \text{diag}(d_{1}\,{,}\ldots{,}\,d_{n})$ be diagonal matrix.
>
>The **$LDL^{T}$ factorization algorithm** is described as follow:
>- *Require*: symmetric matrix $A$
>- Initialize: $v = [v_{1}\,{,}\ldots{,}\,v_{n}]=0\in \mathbb{R}^{n}$,
>- Initialize: $L = I$, $d=[d_{1}\,{,}\ldots{,}\,d_{n}]\in \mathbb{R}^{n}$
>- For $j=1\,{,}\ldots{,}\,n$:
>	- For $i=1\,{,}\ldots{,}\,j-1$:
>		- Collect previous columns of $L$ and $d$ to update $v$ $$v_{i} = d_{i}\,L_{j,i}$$
>	- Compute the $j$-th **diagonal term** $d_{j}$ $$d_{j} = a_{j,j} - L_{j, \{ 1:j-1 \}}\,v_{\{ 1:j-1 \}}$$
>	- Compute the **off-diagonal term** in $j$-th column of $L$ $$L_{\{ j+1:n \},j} = \frac{1}{d_{j}} \left\{   A_{\{ j+1:n \}, j} - L_{\{ j+1:n \}, \{ 1:j-1 \}}\,v_{\{ 1:j-1 \}} \right\} $$

- [[LU Factorization of Matrix]]
- [[Triangular Matrix and Block Triangular Matrix]]
- [[Diagonalizable Matrix]]

>[!info]
>We can overwrite $a_{i,j}$ by $L_{i,j}$ for $i>j$, and by $d_{i}$ for $i=j$.

>[!important] 
>The algorithm requires $$\frac{n^3}{3}$$ flops. 
>- It is about **half the number of flops** involved in Gaussian elimination.
>- This is the same number of operations as the **Cholosky factorization**.

- [[Gaussian Elimination for Solving Linear System]]
- [[Cholesky Factorization of Hermitian Positive Definite Matrices]]

## Explanation

>[!info] Proof
>The *LU factorization* of $A$ is $$A = L\,U$$ Then $$L^{-1}\,A\,L^{-T} = U\,L^{-T}.$$
>
>Note that the RHS is an *upper triangular matrix* as it is the *product of two upper triangular matrices.*
>
>Also the LHS is a *symmetric matrix* since $A$ is symmetric.
>
>Thus $U\,L^{-T}$ is both **symmetric and upper triangular**. Thus it is a **diagonal matrix** $D$ i.e. $$D = U\,L^{-T} \implies D\,L^{T} = U$$ Thus $$A = L\,U = L\,D\,L^{T}$$ By *uniqueness* of *LU factorization* based on conditions in theorem, this factorization is unique. 
>
>This is the end of the proof.

>[!info]
>Using $LDL^{T}$ factorization to solve the **symmetric system of equations** such as the **normal equation** or the **scant equation**, we can solve it in three steps
>$$
>Lz = b, \quad Dy = z, \quad L^{T}x = y
>$$

- [[System of Linear Equations or Linear System]]
- [[Forward Substitution of Lower Triangular System]]
- [[Back Substitution of Upper Triangular System]]

>[!info]
>According to factorization $A = L\,D\,L^{T}$ we have the *lower triangular part* of $A$
>$$
>\begin{align*}
>A_{\{ j:n \}, j} &= \sum_{k=1}^{n}L_{\{ j:n \}, k}\,[DL^{T}]_{k, j}\\[5pt]
>&= \sum_{k=1}^{j}L_{\{ j:n \}, k}\,[DL^{T}]_{k, j}\\[5pt]
>&= \sum_{k=1}^{j}L_{\{ j:n \}, k}\,d_{k}L^{T}_{k,j}\\[5pt]
>&= \sum_{k=1}^{j}L_{\{ j:n \}, k}\,d_{k}L_{j,k}\\[5pt]
>&= L_{\{ j:n \}, \{ 1:j \}}\,v_{\{ 1:j \}} 
>\end{align*}
>$$
>where $v_{k} = d_{k}\,L_{j,k}$ and $v_{j}= d_{j}\,L_{j,j} = d_{j}$ since $L_{j,j}=1$.
>
>Thus we can compute the *diagonal term* $d_{j}$ using first $j-1$ $d_{k}$ and the first $j-1$ columns of $L$
>$$
>\begin{align*}
> a_{j,j} &= \sum_{k=1}^{j}d_{k}L_{j,k}^2 \\[5pt] 
> &= d_{j}L_{j,j}^2 + \sum_{k=1}^{j-1}d_{k}L_{j,k}^2\\[5pt] 
> &= d_{j}  + \sum_{k=1}^{j-1}d_{k}L_{j,k}^2 \quad (\text{ note that }L_{j,j} = 1)\\[5pt]
> \implies d_{j}& = a_{j,j} - \sum_{k=1}^{j-1}d_{k}L_{j,k}^2 
>\end{align*}
>$$
>
>Given $d_{j}$, we can rearrange the equation to have the *off-diagonal entries* in *$j$-th column* of $L$ $L_{\{ j+1:n \},j}$ 
>$$
>\begin{align*}
> A_{\{ j+1:n \}, j} &= L_{\{ j+1:n \}, \{ 1:j \}}\,v_{\{ 1:j \}} \\[5pt]
> &=  L_{\{ j+1:n \}, \{ 1:j-1 \}}\,v_{\{ 1:j-1 \}} + L_{\{ j+1:n \},j}\,v_{j}\\[5pt]
> &=  L_{\{ j+1:n \}, \{ 1:j-1 \}}\,v_{\{ 1:j-1 \}} + L_{\{ j+1:n \},j}\,d_{j}\\[5pt]
> \implies L_{\{ j+1:n \},j}&= \frac{1}{d_{j}} \left\{   A_{\{ j+1:n \}, j} - L_{\{ j+1:n \}, \{ 1:j-1 \}}\,v_{\{ 1:j-1 \}} \right\} 
>\end{align*}
>$$




-----------
##  Recommended Notes and References


- [[Hermitian or Symmetric Matrix]]
- [[LU Factorization of Matrix]]
- [[Triangular Matrix and Block Triangular Matrix]]
- [[Matrix]]
- [[Orthogonal Group]]
- [[Unitary Group]]
- [[Gaussian Elimination for Solving Linear System]]


- [[Numerical Linear Algebra by Trefethen]] pp 
- [[Matrix Computations by Golub]] pp 156 - 159
- [[Matrix Analysis by Horn]] pp 218 - 221