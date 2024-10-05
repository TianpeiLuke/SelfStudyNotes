---
tags:
  - concept
  - math/matrix_analysis
  - numerical_methods/numerical_linear_algebra
  - optimization/algorithm
keywords:
  - invariant_subspace_approximation
topics:
  - matrix_analysis
name: Invariant Subspaces Approximation for Self-Adjoint Matrix
date of note: 2024-10-02
---

## Concept Definition

>[!important]
>**Name**: Invariant Subspaces Approximation for Self-Adjoint Matrix

![[Spectral Theorem of Self-Adjoint Map and Eigen decomposition#^e5de5d]]

- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]

>[!important] Theorem (Invariant Subspace Approximation)
>Let $A\in \mathbb{R}^{n\times n}$ be a **symmetric** matrix. Let $U\in \mathbb{R}^{n\times r}$ with **orthonormal columns**, i.e. $U^{T}U = I_{r}$. 
>
>Then the following minimization problem $$\min_{S\in \mathbb{R}^{r\times r}}\lVert AU - US \rVert_{F}^2 $$ has a **unique solution** $$S^{*} = U^T\,A\,U$$ with **optimal value** $$\lVert AU - US \rVert_{F}^2 = \lVert \left( I - UU^{T} \right)AU \rVert_{F}^2$$

^6a3a8f

- [[Hermitian or Symmetric Matrix]]
- [[Unitary and Orthogonal Transformation]]
- [[Positive Semidefinite Transformation]]
- [[Frobenius Norm of Matrix]]
- [[Fundamental Orthogonal Projections]]

>[!important] Definition
>Let $A\in \mathbb{R}^{n\times n}$ be a **symmetric** matrix. Let $U\in \mathbb{R}^{n\times r}$ with **orthonormal columns**, i.e. $U^{T}U = I_{r}$. 
>
>Define the **residual matrix** for some $S\in \mathbb{R}^{r\times r}$ as $$R = AU - US$$


## Explanation

>[!info]
>$$
>A = U\,S\,U^{*} \quad \iff \quad AU = US
>$$
>





-----------
##  Recommended Notes and References


- [[Low Rank Approximation of Matrix and Eckhart-Young Theorem]]
- [[Procrustes Problem as Approximation by Unitary Transformation]]
- [[Procrustes Problem via Singular Value Decomposition]]


- [[Congruence Relation between Matrices]]
- [[Diagonalizable Matrix]]
- [[Invariance under Linear Transformation]]
- [[Convex Optimization for Eigenvalue Problem]]

- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]

- [[Stiefel Manifold]]
- [[Grassmann Manifold as Quotient Manifold]]
- [[Hermitian or Symmetric Matrix]]
- [[Matrix]]
- [[Linear Map]]

- [[Matrix Computations by Golub]] pp 443 - 448