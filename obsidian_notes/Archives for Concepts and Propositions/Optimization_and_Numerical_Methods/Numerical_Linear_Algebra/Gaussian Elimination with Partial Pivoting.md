---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
keywords:
  - gaussian_elimination
  - pivoting_gaussian_elimination
topics:
  - numerical_linear_algebra
  - matrix_analysis
name: Gaussian Elimination with Partial Pivoting
date of note: 2024-09-21
---

## Concept Definition

>[!important]
>**Name**: Gaussian Elimination with Partial Pivoting

![[Gaussian Elimination for Solving Linear System#^057350]]

- [[Gaussian Elimination for Solving Linear System]]

>[!important] Definition
>In *Gaussian elimination*, the diagonal entry $A_{k,k}$ of matrix $A$ plays a critical role. We call $A_{kk}$ the **pivot.**
>
>For each row $j \in \{ k+1:n \}$ of $A$, $$A_{j,\{ k+1:n \}} \leftarrow A_{j,\{ k+1:n \}} - \frac{A_{j,k}}{A_{k,k}}\,A_{k, \{ k+1:n \}}$$

### Pivoting via Interchange Permutation

>[!quote]
>However, there is *no reason* *why the $k$-th row and column must be chosen* for the elimination. For example, we could just as easily introduce zeros in column $k$ by adding multiples of some row $i$ with $k < i < m$ to the other rows $k \,{,}\ldots{,}\, m$. In this case, the entry $x_{i,k}$ would be the *pivot*.
>
>...
>
>The structure of the *elimination process* quickly becomes *confusing* if zeros are introduced in *arbitrary patterns* through the matrix. To see what is going on, we want to *retain the triangular structure* described in the last lecture, and there is an easy way to do this. We shall not think of the pivot $x_{i,i}$  as left in place, as in the illustrations above. Instead, at step $k$, we shall imagine that the rows and columns of the working matrix are **permuted** so as to move $x_{i,i}$ into the $(k, k)$ *position*. Then, when the elimination is done, zeros are introduced into entries $k +1 \,{,}\ldots{,}\, m$ of column $k$, just as in *Gaussian elimination without pivoting*. This **interchange of rows** and perhaps columns is what is usually thought of as **pivoting**.
>
>-- [[Numerical Linear Algebra by Trefethen]] pp 156

>[!important] Definition
>The **interchange permutation** of element of vector $x\in \mathbb{R}^n$ is achieved below:
>- For $k=1\,{,}\ldots{,}\,n$ :
>	- $$\text{swap}\left(x_{k}, x_{\pi(k)}\right)$$ where $\pi(k)$ is the *pivot row* to be permuted.

>[!info]
>The permutation matrix is the product of **type 1 elementary matrices** $$P = E_{1}(n, \pi(n)) \,{}\ldots{}\, E_{1}(1, \pi(1))$$

- [[Symmetric Group]]
- [[Elementary Row and Column Operations]]
- [[Permutation Matrix and Reversal Matrix]]

### Partial Pivoting

>[!important] Definition
>Interchange permutations can be used in $LU$ computations to guarantee that *no multiplier is greater than $1$* in absolute value.
>
>To get the *smallest possible multipliers* in the *Gauss transformation*, we need $a_{i,k}$ to be the *largest entry* in the $k$-th column.
>
>This particular row interchange strategy is called **partial pivoting**.
>- The resulting **Gaussian elimination with pivoting** corresponds to the factorization $$M_{n-1}P_{n-1}\,{}\ldots{}\,M_{1}P_{1}A = U,$$ where $M_{k}$ is the *Gaussian transformation* at $k$ step, and $P_{k}$ is the *interchange permutation*  
>









## Explanation

>[!quote]
>The analysis in the previous section shows that we must take steps to ensure that **no large entries** *appear* in the computed triangular factors $\hat{L}$ and $\hat{U}$.
>
>-- [[Matrix Computations by Golub]] pp 125 - 126


## PLU Factorization

>[!info]
>The **Gaussian elimination with pivoting** corresponds to the factorization 
>$$M_{n-1}P_{n-1}\,{}\ldots{}\,M_{1}P_{1}A = U,$$ where $M_{k}$ is the *Gaussian transformation* at $k$ step, and $P_{k}$ is the *interchange permutation*.
>
>Note that both $M_{k}$ and $P_{k}$ are *elementary matrices*.  
>
>The product of elementary operation matrix can be *reordered*. $$M_{n-1}P_{n-1}\,{}\ldots{}\,M_{1}P_{1} = M_{n-1}'\,{}\ldots{}\,M_{1}'P_{n-1}\,{}\ldots{}\,P_{1}$$ where $$M_{k}' = \left(P_{n-1}\,{}\ldots{}\,P_{k+1}\right)\,M_{k}\,\left(P_{n-1}\,{}\ldots{}\,P_{k+1}\right)^{-1}$$  
>- Write $$L = \left(M_{n-1}'\,{}\ldots{}\,M_{1}'\right)^{-1}, \quad P = \left(P_{n-1}\,{}\ldots{}\,P_{k+1}\right)^{-1}$$ we can obtain the **$PLU$ factorization** $$A = P\,L\,U$$
>

- [[Elementary Row and Column Operations]]

![[PLU Factorization with Pivoting#^0aac00]]

- [[PLU Factorization with Pivoting]]

>[!info]
>If $$M_{k} = I - \tau^{(k)}\,e_{k}^{T},$$ then 
>$$\begin{align*}
>M_{k}' &= \left(P_{n-1}\,{}\ldots{}\,P_{k+1}\right)\,\left( I - \tau^{(k)}\,e_{k}^{T}\right)\,\left(P_{n-1}\,{}\ldots{}\,P_{k+1}\right)^{-1} \\[5pt]
>&= I - \hat{\tau}^{(k)}\,e_{k}^{T}
>\end{align*}
>$$
>where $$\hat{\tau}^{(k)} = \left(P_{n-1}\,{}\ldots{}\,P_{k+1}\right)\,\tau^{(k)}.$$
>
>This shows that $M_{k}'$ is also a **Gaussian transformation**.




-----------
##  Recommended Notes and References


- [[Gaussian Elimination with Complete Pivoting]]
- [[PLU Factorization with Pivoting]]
- [[System of Linear Equations or Linear System]]
- [[Existence and Uniqueness of Solution of Linear Equations]]
- [[Back Substitution of Upper Triangular System]]
- [[LU Factorization of Matrix]]


- [[Matrix Computations by Golub]] pp 127 - 130
- [[Numerical Linear Algebra by Trefethen]] pp 155 - 162 