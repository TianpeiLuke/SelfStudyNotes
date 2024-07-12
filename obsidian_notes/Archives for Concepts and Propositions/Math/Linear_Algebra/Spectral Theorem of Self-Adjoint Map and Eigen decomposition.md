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


>[!important] Spectral Theorem (Unitarily Diagonalization Form)
>Let $A = [a_{i,j}] \in \mathbb{C}^{n \times n}$ be **Hermitian** and have **eigenvalues** $\lambda_{1} \,{,}\ldots{,}\,\lambda_{n}$. 
>
>Then:
>- All the eigenvalues $\lambda_{1} \,{,}\ldots{,}\,\lambda_{n} \in \mathbb{R}$ are **real**.
>- $A$ is **unitarily diagonalizable**
>- There exists a *unitary matrix* $U\in U(n)$ such that $$A = U\,\boldsymbol{\Lambda}\,U^{*}$$ where $\boldsymbol{\Lambda} =\text{diag}\left\{\lambda_{1} \,{,}\ldots{,}\,\lambda_{n}\right\}.$

- [[Spectral Theorem of Normal Map and Eigen decomposition]]
- [[Self-Adjoint Linear Map and Hermitian or Symmetric Matrix]]

>[!important] Spectral Theorem (Spectral Projection)
>Let $A = [a_{i,j}] \in \mathbb{C}^{n \times n}$ be **Hermitian** and have **eigenvalues** $\lambda_{1} \,{,}\ldots{,}\,\lambda_{n}$. 
>
>Then
>$$A = \sum_{i=1}^{n}\lambda_{i}\,u_{i}\,u_{i}^{*} = \sum_{i=1}^{n}\lambda_{i}\,P_{\mathcal{E}_{\lambda_{i}}}$$ where $u_{i} \in \mathcal{E}_{\lambda_{i}}$ is an *eigenvector* associated with *eigenvalue* $\lambda_{i} \in \mathbb{R}$ of $A$, and $P_{\mathcal{E}_{\lambda_{i}}}$ is the **(spectral) projection map** onto the eignspace $\mathcal{E}_{\lambda_{i}}$ associated with *eigenvalue* $\lambda_{i}$.

- [[Eigenspace and Spectrum for Linear Map]]
- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Projection Map onto Linear Subspace]]
- [[Finite Dimensional Vector Spaces by Halmos]]

## Explanation





-----------
##  Recommended Notes and References

- [[Spectral Theorem of Normal Map and Eigen decomposition]]


- [[Self-Adjoint Operator in Hilbert Space]]
- [[Spectral Theorem in Projection-Valued Measure Form]]
- [[Spectral Theorem in Multiplication Operator Form]]




- [[Finite Dimensional Vector Spaces by Halmos]]
- [[Matrix Analysis by Horn]] pp 135