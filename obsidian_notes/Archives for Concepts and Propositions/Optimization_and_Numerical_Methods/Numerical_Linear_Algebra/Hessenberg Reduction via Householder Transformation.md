---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
keywords:
  - hessenberg_reduction
topics:
  - matrix_analysis
  - linear_algebra
  - numerical_linear_algebra
name: Hessenberg Reduction via Householder Transformation
date of note: 2024-08-08
---

## Concept Definition

>[!important]
>**Name**: Hessenberg Reduction via Householder Transformation

![[Hessenburg QR Iteration for Unsymmetric Eigenvalue Problem#^71e8e1]]

![[Householder Transformation and Householder Reflection#^082feb]]

>[!important] Definition
>Consider the task of **Hessenberg decomposition** of a matrix $A\in \mathbb{R}^{n\times n}$ as $$H = U_{0}^{T}\,A\,U_{0}$$ where $U_{0}$ is a product of *Householder transformations*.
>
>The **Hessenberg Reduction** via *Householder transformations* is described as follows
>- *Require*: $A\in \mathbb{R}^{n\times n}$
>- For $k=1\,{,}\ldots{,}\,n-2$:
>	- Compute the **Householder vector** and **scalar** $$(\beta^{(k)}, v^{(k)}) = \text{Householder}(A_{\{ k+1:n \}, k})$$
>	- Apply the *Householder transformation* on **rows** of $A$ via the *rank-1 update* $$A_{\{ k+1:n \}, \{ k:n \}} \leftarrow A_{\{ k+1:n \}, \{ k:n \}} - \beta^{(k)}\,v^{(k)}\left((v^{(k)})^{T} A_{\{ k+1:n \}, \{ k:n \}}\right)$$
>	- Apply the *Householder transformation* on **columns** of $A$ via the *rank-1 update* $$A_{\{ 1:n \}, \{ k+1:n \}} \leftarrow A_{\{ 1:n \}, \{ k+1:n \}} - \beta^{(k)}\,\left(A_{\{ 1:n \}, \{ k+1:n \}} v^{(k)}\right)(v^{(k)})^{T} $$
>- *Return* the **upper Hessenberg matrix** that overwrites $A$ as $$H = U_{0}^{T}\,A\,U_{0}$$

^44a0a9

- [[Hessenberg Decomposition of Matrix]]
- [[Hessenberg Matrix]]
- [[Householder Transformation and Householder Reflection]]
- [[Householder QR Factorization]]
- [[QR Iteration for General Eigenvalue Problem]]

>[!important]
>This algorithm takes $$\frac{10 n^3}{3}$$ flops,  with additional $$\frac{4n^3}{3}$$ flops to form $U_{0}.$


### Hessenberg QR Iteration

- [[Hessenburg QR Iteration for Unsymmetric Eigenvalue Problem]]


## Explanation

>[!quote]
>We now turn our attention to the efficient execution of a **single QR step** in (7.4. 1).  In this regard, the most glaring shortcoming associated with (7.4.1) is that each step requires a **full QR factorization** *costing $O(n^3)$ flops*. Fortunately, the amount of work per iteration can be *reduced* by an order of magnitude if the orthogonal matrix $U_{0}$ is *judiciously chosen*. In particular, if $U_{0}^{T}AU_{0} = H_{0} = (h_{i,j})$ is **upper Hessenberg** ($h_{i,j} = 0$,  $i > j + 1$) , then each subsequent $H_k$ requires **only** $O(n^2)$ flops to calculate. To see this we look at the computations $H = QR$ and $H_{+} = RQ$ when $H$ is *upper Hessenberg*. As described in §5.2.5, we can *upper triangularize* $H$ with a sequence of $n - 1$ **Givens rotations**: $Q^{T}H \equiv G_{n-1}^{T} \,{}\ldots{}\, G_{1}^{T}H = R$. Here, $G_{i} = G(i, i+1, \theta_{i}).$
>
>-- [[Matrix Computations by Golub]] pp 377

- [[Hessenberg Matrix]]
- [[Hessenberg QR Factorization via Given Transformation]]

### Hessenberg Reduction for Submatrix using Arnoldi Process

- [[Arnoldi Iteration for Hessenberg Reduction of Large Matrix]]

|                              | $A = QR$ <br>**QR Factorization**                                      | $A= QHQ^{*}$ <br>**Henssenberg Factorization**                                                |
| ---------------------------- | ---------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| Orthogonal Structuring       | **Householder Transformation**<br><br>[[Householder QR Factorization]] | **Householder Transformation**<br><br>[[Hessenberg Reduction via Householder Transformation]] |
| Structured Orthogonalization | **Gram-Schmidt process**<br><br>[[Gram-Schmidt Orthogonalization]]     | **Arnoldi process**<br><br>[[Arnoldi Iteration for Hessenberg Reduction of Large Matrix]]               |






-----------
##  Recommended Notes and References


- [[Householder Transformation and Householder Reflection]]
- [[Hessenburg QR Iteration for Unsymmetric Eigenvalue Problem]]
- [[QR Iteration for General Eigenvalue Problem]]
- [[Hessenberg QR Factorization via Given Transformation]]
- [[Hessenberg Matrix]]
- [[Matrix]]
- [[Gaussian Elimination for General Linear System]]


- [[Numerical Linear Algebra by Trefethen]] pp 196 - 199
- [[Matrix Computations by Golub]] pp 378 - 383
- [[Matrix Analysis by Horn]]