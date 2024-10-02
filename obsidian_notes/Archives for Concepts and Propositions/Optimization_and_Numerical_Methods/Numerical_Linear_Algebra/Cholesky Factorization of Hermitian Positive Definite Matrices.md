---
tags:
  - concept
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
keywords:
  - cholesky_factorization_symmetric_matrix
topics:
  - numerical_linear_algebra
  - matrix_analysis
name: Cholesky Factorization of Hermitian Positive Definite Matrices
date of note: 2024-09-21
---

## Concept Definition

>[!important]
>**Name**: Cholesky Factorization of Hermitian Positive Definite Matrices

![[Square Root of Positive Semidefinite Transformation and Absolute Value#^4879e9]]

- [[Square Root of Positive Semidefinite Transformation and Absolute Value]]

>[!important] Corollary (Cholesky factorization)
>Let $A\in M_{n}$ be **Hermitian**.
>
>Then $A \succeq 0$ is **positive semidefinite** (respectively, **positive definite**) *if and only if* there exists a **lower triangular matrix** $G \in M_{n}$ with **nonnegative** (respectively, **positive**) *diagonal entries* such that $$A = G\,G^{*}.$$
>
>- If $A \succ 0$ is **positive definite**, then $G$ is **unique**.
>- If $A\in \mathbb{R}^{n\times n}$ is *real*, then $G$ may be taken to be *real*.

^c9a9c1

 

>[!important] Definition
>Let $A\in M_{n}$ be *Hermitian* and *positive semidefinite*.
>
>Then the **Cholesky factorization** of $A$ is given by 
>$$
>A = G\,G^{*}
>$$
>where  $G\in M_{n}$ is called **Cholesky factor**, which is a *lower triangular matrix*  with *nonnegative diagonal entries*.
>
>- The **Cholesky factorization** is **unique** of $A \succ 0$ and $G$ has *positive diagonal entries*.

- [[Hermitian or Symmetric Matrix]]
- [[Positive Semidefinite Transformation]]
- [[Triangular Matrix and Block Triangular Matrix]]
- [[Adjoint of Linear Map]]

### Algorithm 

>[!important] Definition
>Consider the **Cholesky factorization** $$A = G\,G^{T}$$ of a *positive definite matrix* $A$, i.e. the $j$-th column is $$A_{:,j} = \sum_{k=1}^{j}G_{:,k}\,G_{j,k}.$$ This means that the $j$-th column of $G$ is determined by the equation, where the right hand side defined by first $j-1$ columns of $G$. $$G_{j,j}\,G_{:,j} = A_{:,j} - \sum_{k=1}^{j-1}G_{j,k}\,G_{:,k} := v.$$
>
>The **Cholesky factorization** algorithm is described as below:
>- *Require*: **symmetric positive definite matrix** $A \succ 0$
>- For $j=1\,{,}\ldots{,}\,n$:
>	- Initialize with the *$j$-th column* of *lower triangular part* of $A$ $$v_{j:n}  = A_{\{j:n\}, j}$$
>	- For $k=1\,{,}\ldots{,}\,j-1$:
>		- Update based on *first $j-1$ columns* of $G$ $$v_{j:n} \leftarrow v_{j:n} - G_{j,k}\,G_{\{j:n\},k}$$
>	- The *j-th column* of $G$ is given by $$G_{\{j:n\},j} = \frac{v_{j:n}}{\sqrt{v_{j}}} $$
>- *Return* the **Cholesky factor** as a *lower triangular matrix* $$G = [G_{\{1:n\},1} \,{,}\ldots{,}\,G_{\{j:n\},j} \,{,}\ldots{,}\,G_{n,n}]$$

^770789


>[!important]
>- This is about **half as many operations as** *Gaussian elimination* which needs $$\frac{2}{3}n^3.$$
>- This is the **same** number of operations as compared to the **$LDL^{T}$ factorization**.

- [[LDU Factorization of Symmetric Matrix]]
- [[Gaussian Elimination to solve Linear System]]

>[!important] Definition
>The *Gaxpy implementation* of **Cholesky factorization** algorithm is described as below:
>- *Require*: **symmetric positive definite matrix** $A \succ 0$
>- For $j=1\,{,}\ldots{,}\,n$:
>	- If $j > 1$:
>		- **Update** the *$j$-th columns* of $A$ $$A_{\{j:n\}, j} \leftarrow A_{\{j:n\}, j} - A_{\{j:n\}, \{1:j-1\} }\,A_{j, \{1:j-1\} }^{T}$$
>	- **Reweight** *j-th column* of $A$ by $$A_{\{j:n\}, j} = \frac{A_{\{j:n\}, j}}{\sqrt{A_{j,j}}} $$
>- *Return* the **Cholesky factor** as a *lower triangular part* of $A$ $$G = [A_{\{1:n\},1} \,{,}\ldots{,}\,A_{\{j:n\},j} \,{,}\ldots{,}\,A_{n,n}]$$

## Explanation

>[!info]
>$$
>\begin{align*}
>A_{:,j} &= \sum_{k=1}^{n}G_{:,k}\,G^{T}_{k,j}\\[5pt]
>&\quad (G_{i,j} = 0, \forall j >i)\\[5pt]
>&= \sum_{k=1}^{j}G_{:,k}\,G^{T}_{k,j}\\[5pt]
>&= \sum_{k=1}^{j}G_{:,k}\,G_{j,k}
>\end{align*}
>$$


>[!info] Proof via Square Root and QR Factorization
>Let $A^{1 / 2}$ be the **square root** of $A \succeq 0$, and the **QR factorization** $$A^{1 / 2} = Q\,R.$$ Then 
>$$
>A = (A^{1/2})^{*} A^{1/2} = (Q\,R)^{*}\,Q\,R = R^{*}\,R
>$$
>Let $G = R^{*}$. We have the result. 
>
>Note that the **Cholesky factor** $L$ is not the **square root** $A^{1 / 2}.$


- [[Square Root of Positive Semidefinite Transformation and Absolute Value]]
- [[QR Factorization of Matrix]]

### Proof via $LDL^T$ Factorization

![[LDU Factorization of Symmetric Matrix#^951558]]

>[!info]
>Based on **$LDL^{T}$ factorization** of symmetric matrix, $$A = L\,D\,L^{T}.$$ We have $$D = L^{-1}\,A\,L^{-T}$$ has *nonnegative entries*. 
>
>Let $$G = L\,\text{diag}\left\{ \sqrt{ d_{1} }  \,{,}\ldots{,}\, \sqrt{ d_{n} } \right\}.$$ 
>- $G$ is lower triangular, with *non-negative entries*
>- $$A = L\,D\,L^{T} = G\,G^{T}.$$

- [[LDU Factorization of Symmetric Matrix]]


>[!info]
>The existence of **Cholesky factorization** is a characteristic of **positive semidefinite matrix**.
>
>If $A$ is **positive definite**, then the **Cholesky factorization** is unique.

>[!info]
>It is common to use $G$ to represent the Cholesky factors $$A = G\,G^{*}.$$

## Symmetric Positive Definite System

>[!info]
>To solve equation $$Ax = b$$ with $A\succ 0$ such as the **normal equation**, we can first compute the **Cholesky factorization** and then solve two **triangular system** $$Ax=b \iff GG^{T}x = b \iff Gy = b, \quad G^{T}x = y. $$

- [[Least Square Estimation Solution and Geometric Interpretation]]
- [[Triangular System of Equations]]
- [[Forward Substitution of Lower Triangular System]]
- [[Back Substitution of Upper Triangular System]]


## Stability of Cholesky Factorization

>[!important]
>It can be shown that for $G = [g_{i,j}]$
>$$
>g_{i,j}^2 \le \sum_{k=1}^{i}g_{i,k}^2 = a_{i,i}
>$$
>Thus the entries of Cholesky factor $G$ is **bounded**. And $$\lVert G \rVert_{2}^2 = \lVert A \rVert_{2}.$$
>

- [[Operator p-Norm of Matrix]]

>[!info]
>The stability of symmetric positive definite linear system is determined by the **condition number** $$\kappa(A) = \frac{\lambda_{max}(A)}{\lambda_{min}(A)}$$
>
>Here $\lambda_{min}(A)$ is the "distance to trouble" in the Cholesky setting.
>
>-- [[Matrix Computations by Golub]] pp 165

## Band Cholesky Factorization

- [[Band Cholesky Factorization of Hermitian Positive Definite Matrices]]



-----------
##  Recommended Notes and References




- [[System of Linear Equations or Linear System]]
- [[Existence and Uniqueness of Solution of Linear Equations]]

- [[LDU Factorization of Symmetric Matrix]]
- [[LPDU Factorization of Nonsingular Matrix]]
- [[QR Factorization of Matrix]]
- [[Normal Transformation]]

- [[Least Square Estimation Solution and Geometric Interpretation]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]

- [[Square Root of Positive Semidefinite Operator and Absolute Value]]


- [[Matrix Computations by Golub]] pp 163 - 166
- [[Numerical Linear Algebra by Trefethen]] pp 172 - 178
- [[Matrix Analysis by Horn]] pp 90, 440 - 443, 456