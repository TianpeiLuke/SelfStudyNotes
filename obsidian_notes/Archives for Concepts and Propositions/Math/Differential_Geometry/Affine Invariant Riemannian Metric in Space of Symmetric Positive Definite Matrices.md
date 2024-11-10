---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
  - math/riemannian_geometry
keywords:
  - affine_invariant_riemannian_metric
topics:
  - matrix_analysis
  - riemannian_geometry
  - linear_algebra
name: Affine Invariant Riemannian Metric in Space of Symmetric Positive Definite Matrices
date of note: 2024-11-09
---

## Concept Definition

>[!important]
>**Name**: Affine Invariant Riemannian Metric in Space of Symmetric Positive Definite Matrices

>[!important] Definition
>Let $\mathcal{S}_{++}^{n}$ be the *space of symmetric positive definite matrices* in $M_{n}$.
>
>The **Affine Invariant Riemannian Metric (AIRM)** between two symmetric positive definite matrices $X, Y\in \mathcal{S}_{++}^{n}$ is defined as
>$$
>D_{R}(X, Y) = \left\lVert \log \left(X^{- 1/2}\,Y\,X^{- 1/2}\right) \right\rVert_{F} 
>$$
>where $\log(\cdot)$ is the *principal matrix logarithm*.
>- It can be shown that 
>$$\begin{align*}
>D_{R}(X, Y) &= \left\lVert \log \left(X^{- 1/2}\,Y\,X^{- 1/2}\right) \right\rVert_{F} \\[5pt] 
>&=  \left\lVert \log \left(X^{- 1}\,Y\right) \right\rVert_{F} \\[5pt] 
>&= \sqrt{ \sum_{i=1}^{n}(\log(\lambda_{i}))^2 }
>\end{align*}
>$$
>where $\{\lambda_{i}\}$ is the *eigenvalue* of $X^{-1}Y.$

^773a0d

- [[Space of Symmetric Positive Semidefinite Matrices]]
- [[Hermitian or Symmetric Matrix]]
- [[Positive Semidefinite Transformation]]
- [[Matrix Logarithm]]
- [[Frobenius Norm of Matrix]]
- [[Riemannian Metric and Riemannian Manifold]]

## Explanation




- [[Inverse Covariance Estimation]]
- [[Sparse Inverse Covariance Estimation for GGM with Known Structure]]
- [[Graph LASSO and Structured Learning in Gaussian Graphical Model]]





## Geodesic under Affine Invariant Riemannian Metric




-----------
##  Recommended Notes and References


- [[Log-Euclidean Riemannian Metric in Space of Symmetric Positive Definite Matrices]]

- [[Inner Product Space]]
- [[Semidefinite Programming]]
- [[Convex Function]]
- Cherian, A., Sra, S., Banerjee, A., & Papanikolopoulos, N. (2012). Jensen-bregman logdet divergence with application to efficient similarity search for covariance matrices. _IEEE transactions on pattern analysis and machine intelligence_, _35_(9), 2161-2174.