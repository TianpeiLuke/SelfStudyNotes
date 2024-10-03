---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
  - math/linear_algebra
keywords:
  - power_iteration_eigenvalue_problem
  - matrix_analysis
  - inverse_iteration
topics:
  - numerical_linear_algebra
name: Power Iteration to solve Eigenvalue Problem of General Matrix
date of note: 2024-09-25
---

## Concept Definition

>[!important]
>**Name**: Power Iteration to solve Eigenvalue Problem of General Matrix

### Identifying the Eigenvalue

>[!important] Definition
>Consider the *eigenvalue problem* $$Ax = \lambda x$$ where $A\in \mathbb{C}^{n\times n}$ and $\lambda_{1} \,{,}\ldots{,}\,\lambda_{n}$ are eigenvalues of $A$ with $$|\lambda_{1}| > |\lambda_{2}| \,{\ge}\ldots{\ge}\,|\lambda_{n}|.$$
>- Suppose that $A$ is *diagonalizable* i.e. there exists non-singular matrix $X= [x_{1}\,{,}\ldots{,}\,x_{n}]$, such that $$A = X\text{diag}(\lambda_{1}\,{,}\ldots{,}\,\lambda_{n})X^{-1}.$$
>  
>The **power iteration** algorithm *approximates* the **largest eigenvalue** $\lambda_{1}$ by producing a sequence of vectors $q^{(k)}$ with *unit norms* as follow:
>- *Require*: $A\in \mathbb{C}^{n\times n}$
>- *Require*: $q^{(0)}\in \mathbb{C}^{n}$ with **unit norm**
>- For $k=1\,{,}\ldots{,}\,$ until convergence:
>	- Find a vector in **$k$-th power range space** $\text{R}(A^{k})$  $$z^{(k)} = A\,q^{(k-1)}$$
>	- *Normalize* the vector $$q^{(k)} = \frac{z^{(k)}}{\lVert z^{(k)} \rVert_{2} }$$
>	- **Approximate the eigenvalue**  via the bilinear form $$\lambda^{(k)} = (q^{(k)})^{*}\,A\,q^{(k)}$$

^f0b732

- [[Diagonalizable Matrix]]
- [[Similarity Relation between Linear Maps and Matrices]]
- [[Eigenvalue and Eigenvector for Linear Map]]

### Identifying the Eigenspace associated with the Eigenvalue

>[!important] Definition
>Consider the *eigenvalue problem* $$Ax = \lambda x$$ where $A\in \mathbb{C}^{n\times n}$ and $\lambda_{1} \,{,}\ldots{,}\,\lambda_{n}$ are eigenvalues of $A$.
>- Assume that we have obtain the **Schur form** of $A$ as $$T = U^{*}\,A\,U.$$
>- $q^{(0)}$ is the **eigenvector** associated with the largest eigenvalue $\lambda_{1}$
>
>  
>The **inverse iteration** algorithm *identifies* the **eigenspace** associated with the eigenvalue $\mu$  by producing a sequence of vectors $q^{(k)}$ with *unit norms* as follow:
>- *Require*: $A\in \mathbb{C}^{n\times n}$, and eigenvalue $\mu$ of $A$
>- *Require*: $q^{(0)}\in \mathbb{C}^{n}$ with **unit norm**
>- For $k=1\,{,}\ldots{,}\,$ until convergence:
>	- Solve the **resolvent equation** $$\left(A- \mu I\right)\,z^{(k)} = q^{(k-1)}$$
>	- *Normalize* the vector $$q^{(k)} = \frac{z^{(k)}}{\lVert z^{(k)} \rVert_{2} }$$
>	- **Approximate the eigenvalue**  via the bilinear form $$\lambda^{(k)} = (q^{(k)})^{*}\,A\,q^{(k)}$$

^9b3cc4

- [[Resolvent Operator and Spectrum of Linear Operator]]

>[!info]
>The inverse iteration is the the power iteration for $(A - \mu I)^{-1}$.

![[rayleigh_quotient_power_inverse.png]]


## Explanation

>[!info]
>The **key observation** is that the **Rayleigh quotient** is bounded between *largest eigenvalue* $\lambda_{1}$ and *smallest eigenvalue* $\lambda_{n}$, $$\lambda_{n} \le \left\langle  q\,,\,A\,q    \right\rangle \le \lambda_{1}$$

- [[Rayleigh Quotient for Eigenvalue Problem]]
- [[Variational Characterization of Eigenvalues of Hermitian Matrix]]

### Symmetric Power Iteration and Inverse Iteration

>[!info]
>This method can be applied to Hermitian cases, $$A = A^{*},$$ and the Schur form is a **block diagonal matrix** $$T= D = \text{diag}(\lambda_{1} \,{,}\ldots{,}\,\lambda_{n})$$

## QR Iteration

- [[QR Iteration for General Eigenvalue Problem]]
- [[Hessenburg QR Iteration for Unsymmetric Eigenvalue Problem]]





-----------
##  Recommended Notes and References



- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Hermitian or Symmetric Matrix]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]
- [[QR Factorization of Matrix]]




- [[Matrix Computations by Golub]] pp 450 - 452
- [[Numerical Linear Algebra by Trefethen]] pp 204 - 207