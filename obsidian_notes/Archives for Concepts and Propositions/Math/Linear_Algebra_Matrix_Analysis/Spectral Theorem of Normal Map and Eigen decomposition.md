---
tags:
  - concept
  - math/linear_algebra
keywords:
  - spectral_theorem
  - normal_transform
topics:
  - linear_algebra
name: Spectral Theorem of Normal Map and Eigen decomposition
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Spectral Theorem of Normal Map and Eigen decomposition

>[!important] Spectral Theorem (Normal Transform)
>Let $A = [a_{i,j}] \in \mathbb{C}^{n \times n}$ have **eigenvalues** $\lambda_{1} \,{,}\ldots{,}\,\lambda_{n}$. The following statements are **equivalent**: 
>- $A$ is **normal**, i.e. $$A^{*}A = A A^{*}.$$ 
>- $A$ is **unitarily diagonalizable,** i.e. there exists an *unitary matrix* $U\in U(n)$ such that $$A = U\,\boldsymbol{\Lambda}\,U^{*}$$ where $\boldsymbol{\Lambda} =\text{diag}\left\{\lambda_{1} \,{,}\ldots{,}\,\lambda_{n}\right\}.$
>- $$\sum_{i,j= 1}^{n}\,\lvert a_{i,j} \rvert^2 = \sum_{i=1}^{n} \lvert \lambda_{i} \rvert^2.$$
>- $A$ has $n$ **orthonormal eigenvectors**.

^33ff0c

- [[Diagonalizable Matrix]]
- [[Unitary and Orthogonal Transformation]]
- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Normal Transformation]]
- [[General Linear Group]]
- [[Unitary Similarity and Unitary Diagonalizable]]
- [[Matrix Analysis by Horn]]


>[!important] Definition
>A representation of a *normal matrix* $A \in \mathbb{C}^{n\times n}$  as $$A = U\,\boldsymbol{\Lambda}\,U^{*}$$ where $U\in U(n)$, and $\boldsymbol{\Lambda} =\text{diag}\left\{\lambda_{1} \,{,}\ldots{,}\,\lambda_{n}\right\},$ is called a **spectral decomposition** or **eigen-decomposition** of $A$.

>[!important] Spectral Theorem (Spectral Projection)
>Let $A = [a_{i,j}] \in \mathbb{C}^{n \times n}$ be **normal matrix** and have **eigenvalues** $\lambda_{1} \,{,}\ldots{,}\,\lambda_{n}$. 
>
>Then
>$$A = \sum_{i=1}^{n}\lambda_{i}\,u_{i}\,u_{i}^{*} = \sum_{i=1}^{n}\lambda_{i}\,P_{\mathcal{E}_{\lambda_{i}}}$$ where $u_{i} \in \mathcal{E}_{\lambda_{i}}$ is an *eigenvector* associated with *eigenvalue* $\lambda_{i} \in \mathbb{R}$ of $A$, and $P_{\mathcal{E}_{\lambda_{i}}}$ is the **(spectral) projection map** onto the eignspace $\mathcal{E}_{\lambda_{i}}$ associated with *eigenvalue* $\lambda_{i}$.

- [[Eigenspace and Spectrum for Linear Map]]
- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Projection Map onto Linear Subspace]]
- [[Finite Dimensional Vector Spaces by Halmos]] pp 156
- [[Diagonal Matrix and Block Diagonal Matrix]]

## Explanation


## Uniqueness of Spectral Decomposition

>[!important] Theorem
>Let $A \in \mathcal{L}(\mathbb{C}^{n})$ be **normal** and have **distinct eigenvalues** $\lambda_{1} \,{,}\ldots{,}\,\lambda_{d}$, with respective **multiplicities** $n_{1} \,{,}\ldots{,}\,n_{d}$. Let $$\Lambda = \lambda_{1}I_{n_{1}} \,{\oplus}\ldots{\oplus}\, \lambda_{d}I_{n_{d}},$$ and suppose that $U \in \mathcal{U}(n)$ is **unitary** and $$A = U\,\boldsymbol{\Lambda}\,U^{*}.$$ 
>
>Then
>- $$A = V\,\boldsymbol{\Lambda}\,V^{*}$$  for some **unitary** $V \in \mathcal{U}(n)$ *if and only if* there are **unitary matrices** $W_{1} \,{,}\ldots{,}\,W_{d}$ with each $W_{i} \in \mathcal{U}(n_{i})$ such that $$U = V\left(W_{1} \,{\oplus}\ldots{\oplus}\,W_{d}\right).$$ 
>- Two **normal matrices** are **unitarily similar** *if and only if* they have the **same eigenvalues**.

- [[Matrix Analysis by Horn]]



-----------
##  Recommended Notes and References


- [[Diagonal Matrix and Block Diagonal Matrix]]
- [[Spectral Theorem in Multiplication Operator Form]]
- [[Spectral Theorem in Projection-Valued Measure Form]]


- [[Finite Dimensional Vector Spaces by Halmos]] pp 133
- [[Matrix Analysis by Horn]]