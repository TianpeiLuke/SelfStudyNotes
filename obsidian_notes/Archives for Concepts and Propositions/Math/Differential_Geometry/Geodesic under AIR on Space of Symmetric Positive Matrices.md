---
tags:
  - concept
  - math/differential_geometry
  - math/riemannian_geometry
  - math/matrix_analysis
  - math/linear_algebra
keywords:
  - geodesic_curve
  - affine_invariant_riemannian_metric
  - symmetric_matrix
  - positive_semidefinite_matrix
topics:
  - matrix_analysis
  - riemannian_geometry
name: Geodesic under AIR on Space of Symmetric Positive Matrices
date of note: 2024-11-09
---

## Concept Definition

>[!important]
>**Name**:  Geodesic under AIR on Space of Symmetric Positive Matrices

>[!important] Definition
>Let $\mathcal{S}_{++}^{n}$ be the *space of symmetric positive definite matrices* and $X_{0}\in \mathcal{S}_{++}^{n}$. 
>- Denote $(\mathcal{S}_{++}^{n}, g_{R})$ be the *Riemannian manifold* with the *Affine Invariant Riemannian (AIR) metric* $$(g_{P})_{i,j} = \left\langle  X\,,\, Y   \right\rangle_{P} :=  \text{tr}\left(P^{-1}\,X\,P^{-1}\,Y\right)$$
> 
>
>The **geodesic** **in the direction** of $S\in \mathcal{S}_{++}^{n}$ with respect to *Riemannian connection* on $\mathcal{S}_{++}^{n}$ is given by 
>$$
>X(t) = X_{0}^{1/2}\,\exp \left(t\;X_{0}^{-1/2}SX_{0}^{-1/2}\right)\,X_{0}^{1/2}\, \quad t\in \mathbb{R}
>$$
>where
>- $\exp(\cdot)$ is the *matrix exponential*. 


- [[Geodesic in Riemannian Manifold]]
- [[Levi Civita Connection and Riemannian Connection]]
- [[Riemannian Metric and Riemannian Manifold]]
- [[Space of Symmetric Positive Semidefinite Matrices]]

- [[Affine Invariant Riemannian Distance in Space of Symmetric Positive Definite Matrices]]
- [[Metric Tensor on Space of Positive Semidefinite Matrices]]


## Explanation





-----------
##  Recommended Notes and References


- [[Christoffel Symbols]]
- [[Smooth Manifold]]
- [[Tangent Space Definition and Development]]
- [[Tangent Bundle]]


- [[Matrix Exponential as Global Flow in General Linear Group]]
- [[Matrix Exponential]]
- [[Matrix Lie Group]]
- [[Lie Algebra as Vector Space with Lie Bracket]]
- Moakher, M. (2005). A differential geometric approach to the geometric mean of symmetric positive-definite matrices. _SIAM journal on matrix analysis and applications_, _26_(3), 735-747.

