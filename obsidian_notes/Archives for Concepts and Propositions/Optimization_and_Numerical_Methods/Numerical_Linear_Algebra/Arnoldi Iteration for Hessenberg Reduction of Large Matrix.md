---
tags:
  - concept
  - math/matrix_analysis
  - numerical_methods/numerical_linear_algebra
keywords:
  - arnoldi_iteration_eigenvalue
  - krylov_subspace
  - hessenberg_reduction
topics:
  - numerical_linear_algebra
  - matrix_analysis
name: Arnoldi Iteration for Hessenberg Reduction of Large Matrix
date of note: 2024-09-29
---

## Concept Definition

>[!important]
>**Name**: Arnoldi Iterations for Large Eigenvalue Problems

### Arnoldi Process as Modified Gram-Schmidt Process for Hessenberg Reduction

>[!info]
>Consider the problem of **Hessenberg reduction** $$A = QHQ^{*} \iff AQ = QH$$ 
>
>We can represent the above equation in terms of columns of $Q$, i.e. $$A [q_{1}\,{,}\ldots{,}\,q_{n}] = [q_{1}\,{,}\ldots{,}\,q_{n}]\,\left[ H_{i,j} \right]$$ where $H_{\{ i+2:n \},i} = 0, \quad i=1\,{,}\ldots{,}\,n-2.$ 
>
>Thus we can obtain the following **recurrent equation**
>$$
>A\,q_{i} = \sum_{k=1}^{i+1}H_{k,i}\,q_{k} \in \text{span}\{ q_{1}\,{,}\ldots{,}\,q_{i+1} \}
>$$

^d58c5f

- [[Hessenberg Decomposition of Matrix]]

>[!info]
>For $A$ *large*, computing the full reduction is not possible. Thus, let us consider the first $m$ columns of $Q$ as $$Q_{m} = [q_{1}\,{,}\ldots{,}\,q_{m}]$$
>Computing the Hessenberg reduction of first $m$ columns only involve the $(m+1)\times m$ upper left section of $H$ $$H = \left[\begin{array}{cc}\hat{H}_{m} & \star \\ \star & \star \end{array}\right] $$ where $$\hat{H}_{m} = \left[ \begin{array}{ccccc}H_{11} & \cdots & \cdots  &  H_{1m} \\[5pt] H_{21} & H_{22} & \cdots &  \vdots \\[5pt]   & \ddots & \ddots &   \vdots \\[5pt] 0 &    & H_{m,m-1} & H_{m, m}\\[5pt]   &    & & H_{m+1, m}\end{array} \right] \in \mathbb{R}^{(m+1)\times m}$$



>[!important] Definition
>Consider the task of *thin Hessenberg reduction* $$AQ_{k} = Q_{k}\hat{H_{k}} = Q_{k}H_{k} + r_{k}e_{k}^{T}$$ where $Q_{k} = [q_{1}\,{,}\ldots{,}\,q_{k}]$ is the first $k$ columns of *unitary matrix* $Q$ and $\hat{H}_{k}$ is the top-left $(k+1)\times k$ blocks of *Hessenberg matrix* $H$ $$\hat{H}_{k} = \left[ \begin{array}{ccccc}H_{11} & \cdots & \cdots  &  H_{1m} \\[5pt] H_{21} & H_{22} & \cdots &  \vdots \\[5pt]   & \ddots & \ddots &   \vdots \\[5pt] 0 &    & H_{k,k-1} & H_{k, k}\\[5pt]   &    & & H_{k+1, k}\end{array} \right] = \left[ \begin{array}{c}H_{k} \\ 0 \quad H_{k+1,k} \end{array} \right]  \in \mathbb{C}^{(k+1)\times k}$$
>- Specifically, we can obtain the following **recurrent equation** $$A\,q_{i} = \sum_{k=1}^{i+1}H_{k,i}\,q_{k} \in \text{span}\{ q_{1}\,{,}\ldots{,}\,q_{i+1} \},\quad i=1\,{,}\ldots{,}\,k$$
>- The $(k+1)$-th column of *unitary matrix* $Q$ can be obtained given $Q_{k}$ and $A$: $$H_{k+1,k}\,q_{k+1} = A q_{k} - \sum_{i=1}^{k}H_{i,k}\,q_{i} $$
>  
>The **Arnoldi iteration** algorithm *iteratively compute* the columns of *unitary matrix* $Q$ $\{ q_{1}, q_{2}\,{,}\ldots{,}\,q_{k}, q_{k+1},\,{}\ldots{}\, \}$ and the entry $H_{i,j}$ of *Hessenberg matrix* as follow  
>- *Require*: $A\in \mathbb{C}^{n\times n}$
>- *Require*: initial random vector $b\in \mathbb{C}^{n}$
>- Initialize $q_{1}$ by **normalization** $$q_{1} = \frac{b}{\lVert b \rVert_{2}}$$
>- For $k=1,\,2\,{,}\ldots{,}\,$
>	- Compute the vector in the *range of* $A$ $$v = Aq_{k}$$
>	- For $j=1\,{,}\ldots{,}\,k$:
>		- Compute the $(j,k)$ entry of $H$ as the *cosine similarity* between $q_{j}$ and $Aq_{k}$ $$H_{j,k} = \left\langle  q_{j}\,,\,v \right\rangle$$
>		- Compute the **residual** of $v$ after **projecting** onto the span of first $j$ columns of $Q$ $$v \leftarrow v - H_{j,k}\,q_{j}$$
>	- Set $H_{k+1,k}$ as the **norm** of residual $$H_{k+1,k} = \lVert v \rVert_{2}$$
>	- Set $q_{k+1}$ by **normalization** of **residual**  $$q_{k+1} = \frac{v}{H_{k+1,k}}$$

^0f19e1

>[!important] Definition
>The **Arnoldi iteration** is simply the **Modified Gram-Schmidt process** that implements 
>$$
>A\,q_{i} = \sum_{k=1}^{i+1}H_{k,i}\,q_{k}, \quad i=1\,{,}\ldots{,}\,k\,{,}\ldots{,}\,
>$$
>- The vectors $\{ q_{k} \}$ generated by the *Arnoldi process* are called the **Arnoldi vectors**.
>- The *Arnoldi vectors* form an *orthonormal basis* for the **Krylov space** $$\text{span}\{q_{1}\,{,}\ldots{,}\,q_{k}\} = \text{span}\{q_{1},\, Aq_{1}\,{,}\ldots{,}\, A^{k-1}q_{1} \}$$
>- At $k$ iteration, the Arnoldi process solves the equation $$AQ_{k} = Q_{k}H_{k} + r_{k}e_{k}^{T}.$$ 
>	- The decomposition of the above form is called the **Arnoldi decomposition** if
>		- $Q_{k}$ has *orthonormal columns*
>		- $H_{k}\in \mathbb{C}^{k\times k}$ is an *upper Hessenberg matrix*
>		- the *residual is orthogonal to basis* $$Q_{k}^{*}r_{k} = 0$$

- [[Krylov Subspace and Krylov Matrix]]
- [[Modified Gram-Schmidt Algorithm for QR Factorization]]
- [[QR Factorization of Matrix]]

![[Modified Gram-Schmidt Algorithm for QR Factorization#^6afb16]]


### Projection into Krylov Space

![[Krylov Subspace and Krylov Matrix#^27eea3]]

![[Krylov Subspace and Krylov Matrix#^e38b83]]

![[Nilpotent Linear Transformation and Matrix#^ee0cec]]

![[Hessenberg Decomposition of Matrix#^40c613]]

- [[Krylov Subspace and Krylov Matrix]]
- [[Nilpotent Linear Transformation and Matrix]]
- [[Nilpotent Linear Transformation Geometric Characterization]]
- [[Hessenberg Decomposition of Matrix]]

>[!important] Definition
>The **Arnoldi iteration** can be described as the **orthogonal projections** of $A$ onto the **Krylov space** $$\mathcal{K}_{k}:= \mathcal{K}(A, q_{1}, k)$$ in terms of basis $q_{1}\,{,}\ldots{,}\,q_{k}$.
>
>Specifically, at iteration $k$, it can be described as a linear operator $\mathcal{K}_{k} \to \mathcal{K}_{k}$
>- Given $v\in \mathcal{K}_{k}$, apply *linear map* $A$ to obtain $$v \mapsto Av$$ 
>- *Orthogonally project* $Av$ back onto $\mathcal{K}_{k}$ $$Av \mapsto Q_{k}Q_{k}^{*}Av$$
>
>
>We can represent the linear operator $$v \mapsto Q_{k}Q_{k}^{*}Av$$ in terms of basis $\{ q_{1}\,{,}\ldots{,}\,q_{k} \}$ as  $$H_{k} = Q_{k}^{*}AQ_{k} $$
>- The diagonal element of $H_{k}$ is the **Rayleigh quotient** $$H_{i,i} :=\frac{ \left\langle  q_{i}\,,\,A q_{i}\right\rangle}{\left\langle  q_{i}\,,\, q_{i}   \right\rangle} = \left\langle  q_{i}\,,\,A q_{i}\right\rangle.$$

- [[Fundamental Orthogonal Projections]]
- [[Rayleigh Quotient for Eigenvalue Problem]]

>[!important] Proposition
>The *unitary matrix* $Q_{k}$ generated by the **Arnoldi iteration**  are the **reduced QR factors** of the **Krylov matrix**
>$$
>K(A, q_{1}, k) = Q_{k}\,R_{k}
>$$
>- The *Hessenberg matrix* $H_{k}$ are the **projections** of $A$ onto the **Krylov space** $\mathcal{K}_{m}$ in terms of basis $q_{1}\,{,}\ldots{,}\,q_{k}$ $$H_{k} = Q_{k}^{*}AQ_{k}$$
>- In the *Arnoldi process*, neither $K$ nor $R_{k}$ is formed explicitly.
>- The **Arnoldi iteration** is related to the formula $$AQ_{k} = Q_{k+1}\hat{H}_{k}.$$

### Ritz Approximation of Eigenvalues

>[!important] Definition
>Define the **Arnoldi eigenvalue estimates** at step $k$, or **Ritz values** with respect to $\mathcal{K}(A, q_{1},k)$ as the *eigenvalues* of $H_{k}$ generated at the $k$-th step of the *Arnoldi process*. $$\lambda(H_{k}) = \lambda \left(Q_{k}^{*}AQ_{k}\right).$$ 
>- **Ritz values** are used to approximate the *eigenvalues* of $A$
>- We can use **standard QR iteration** to compute the eigenvalue of Hessenburg matrix (i.e. except for the *iniitial Hessenburg reduction*)

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Ritz Pair for Linear Map with respect to Subspace]]
- [[QR Iteration Practical for General Eigenvalue Problem]]

![[arnoldi_eigenvalue_circule.png]]


## Explanation

>[!info]
>**Arnoldi process** is an iterative process that compute **Hessenberg decomposition** of *unsymmetric matrix* using **modified Gram-Schmdit** process.
>- **Arnoldi proces** is a stable version of **QR factorization** of *Krylov matrix* $$K(A, q_{1}, k)= Q_{k}R_{k}$$
>- The *eigenvalue* is **approximated** by the *eigenvalue of Hessenberg matrix* at the end of iteration.
>- **Arnoldi process** reduce the complexity of the direct Hessenberg reduction via *Householder transformation* [[Hessenberg Reduction via Householder Transformation]]

### Gram-Schmidt and Arnoldi Process


>[!quote]
>For computing the QR factorization $$A = QR$$ of a matrix $A$, we have discussed two methods in this book: 
>- **Householder reflections**, which *triangularize* $A$ by a succession of orthogonal operations, 
>- and **Gram—Schmidt orthogonalization**, which *orthogonalizes* $A$ by a succession of triangular operations. 
>  
>Though *Householder reflections* lead to a more *nearly orthogonal matrix* $Q$ in the presence of rounding errors, the *Gram—Schmidt process* has the advantage that it can be **stopped part-way**, leaving one with a **reduced QR factorization** of the first $n$ columns of $A$. 
>
>The problem of computing a **Hessenberg reduction** $$A = QHQ^{*}$$ of a matrix $A$ is exactly analogous. There are two standard methods: 
>- **Householder reflections** (applied now on **two sides** of $A$ rather than *one*) 
>- and the **Arnoldi iteration**. 
>  
>Thus *Arnoldi* is the **analogue** of *Gram-Schmidt* for similarity transformations to **Hessenberg form** rather than *QR factorization*. Like Gram-Schmidt, it has the advantage that it can be **stopped part-way**, leaving one with a *partial reduction* to Hessenberg form that is exploited in various manners to form iterative algorithms for eigenvalues or systems of equations.
>
>-- [[Numerical Linear Algebra by Trefethen]] pp 251

- [[Hessenberg Decomposition of Matrix]]

|                              | $A = QR$ <br>**QR Factorization**                                      | $A= QHQ^{*}$ <br>**Henssenberg Factorization**                                                |
| ---------------------------- | ---------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| Orthogonal Structuring       | **Householder Transformation**<br><br>[[Householder QR Factorization]] | **Householder Transformation**<br><br>[[Hessenberg Reduction via Householder Transformation]] |
| Structured Orthogonalization | **Gram-Schmidt process**<br><br>[[Gram-Schmidt Orthogonalization]]     | **Arnoldi process**<br><br>[[Arnoldi Iteration for Hessenberg Reduction of Large Matrix]]               |

- [[Householder Transformation and Householder Reflection]]
- [[Modified Gram-Schmidt Algorithm for QR Factorization]]

### Lanczos Process

>[!info]
>The **Lanczos iteration** is the **Arnoldi iteration** specialized for **Hermitian case**.

- [[Lanczos Iteration for Tridiagonal Reduction of Large Matrix]]







-----------
##  Recommended Notes and References


- [[Hessenberg Reduction via Householder Transformation]]
- [[System of Linear Equations or Linear System]]

- [[Lanczos Iteration for Tridiagonal Reduction of Large Matrix]]




- [[QR Factorization of Matrix]]
- [[Matrix]]

- [[Matrix Analysis by Horn]]
- [[Numerical Linear Algebra by Trefethen]] pp 303
- [[Matrix Computations by Golub]] pp 579 - 583