---
tags:
  - concept
  - math/linear_algebra
keywords:
  - spectral_theorem
  - hermitian_matrix
  - self_adjoint_linear_map
topics:
  - linear_algebra
name: Spectral Theorem of Self-Adjoint Map and Eigen decomposition
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Spectral Theorem of Self-Adjoint Map and Eigen decomposition

![[Spectral Theorem of Normal Map and Eigen decomposition#^33ff0c]]

### Matrix Representation

>[!important] Spectral Theorem (Unitarily Diagonalization Form)
>Let $A = [a_{i,j}] \in \mathbb{C}^{n \times n}$ be **Hermitian** and have **eigenvalues** $\lambda_{1} \,{,}\ldots{,}\,\lambda_{n}$. 
>
>Then:
>- All the eigenvalues $\lambda_{1} \,{,}\ldots{,}\,\lambda_{n} \in \mathbb{R}$ are **real**.
>- $A$ is **unitarily diagonalizable**
>- There exists a *unitary matrix* $U\in U(n)$ such that $$A = U\,\Lambda\,U^{*}$$ where $\Lambda =\text{diag}\left\{\lambda_{1} \,{,}\ldots{,}\,\lambda_{n}\right\}.$

^e5de5d

- [[Diagonal Matrix and Block Diagonal Matrix]]
- [[Unitary and Orthogonal Transformation]]
- [[Spectral Theorem of Normal Map and Eigen decomposition]]
- [[Hermitian or Symmetric Matrix]]
- [[Unitary Similarity and Unitary Diagonalizable]]

>[!important] Spectral Theorem (Spectral Projection)
>Let $A = [a_{i,j}] \in \mathbb{C}^{n \times n}$ be **Hermitian** and have **eigenvalues** $\lambda_{1} \,{,}\ldots{,}\,\lambda_{n}$. 
>
>Then
>$$A = \sum_{i=1}^{n}\lambda_{i}\,u_{i}\,u_{i}^{*} = \sum_{i=1}^{n}\lambda_{i}\,P_{\mathcal{E}_{\lambda_{i}}}$$ where $u_{i} \in \mathcal{E}_{\lambda_{i}}$ is an *eigenvector* associated with *eigenvalue* $\lambda_{i} \in \mathbb{R}$ of $A$, and $P_{\mathcal{E}_{\lambda_{i}}}$ is the **(spectral) projection map** onto the eignspace $\mathcal{E}_{\lambda_{i}}$ associated with *eigenvalue* $\lambda_{i}$.

- [[Projection Map onto Linear Subspace]]

### Linear Map Interpretation

>[!important] Spectral Theorem (Linear Map)
>Let $A\in \mathcal{L}(V)$ be a **self-adjoint linear transformation** on a *finite dimensional inner product space* $V.$
>
>Then there exists a set of **real values** $\lambda_{1}\,{,}\ldots{,}\,\lambda_{r}\in \mathbb{R}$, and **orthogonal projection maps** $P_{1}\,{,}\ldots{,}\,P_{r}$ so that 
>- $\lambda_{i}$ are **pairwise distinct**, $$\lambda_{i} \neq \lambda_{j}, \quad i\neq j\in \{ 1\,{,}\ldots{,}\,r\}$$
>- $P_i$ are **pairwise orthogonal** $$P_{i}^{*}P_{j} = 0, \quad i\neq j\in \{ 1\,{,}\ldots{,}\,r \}$$
>- $$\sum_{i=1}^{r}P_{i} = I.$$
>- the linear map $A$ can be decomposed into the linear combination of these orthogonal projections $$A = \sum_{i=1}^{r}\lambda_{i}\,P_{i}$$ where $P_{i} := P_{\mathcal{E}_{\lambda_{i}}}$ is the **orthogonal projection** onto the **eigenspace** $\mathcal{E}_{\lambda_{i}}$ associated with $\lambda_{i}$.

^7617c3


- [[Self-Adjoint Linear Map]]
- [[Eigenspace and Spectrum for Linear Map]]
- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Projection Map onto Linear Subspace]]
- [[Finite Dimensional Vector Spaces by Halmos]] pp 156

## Explanation

>[!info]
>The **eigen-decomposition** of *symmetric matrix* $A$, $$A = U\,D\,U^{T}$$ is a special case of **Schur decomposition** $$A = U\,T\,U^{T}.$$ Thus, it is also called the **symmetric Schur decomposition.** 

- [[Schur Triangularization and Schur Form]]


## Principle of Biorthogonality

- [[Principle of Biorthogonality]]


## Self-Adjoint Bounded Operator in Hilbert Space

![[Spectral Projection#^50c777]]

- [[Spectral Projection]]

![[Projection-Valued Measure#^e2e839]]

- [[Projection-Valued Measure]]

![[Spectral Theorem in Projection-Valued Measure Form#^8e4b3b]]

- [[Spectral Theorem in Projection-Valued Measure Form]]

-----------
##  Recommended Notes and References

- [[Spectral Theorem of Normal Map and Eigen decomposition]]


- [[Self-Adjoint Operator in Hilbert Space]]
- [[Spectral Theorem in Projection-Valued Measure Form]]
- [[Spectral Theorem in Multiplication Operator Form]]




- [[Finite Dimensional Vector Spaces by Halmos]] pp 155 - 158
- [[Matrix Analysis by Horn]] pp 135
- [[Numerical Linear Algebra by Trefethen]] pp 181 - 188