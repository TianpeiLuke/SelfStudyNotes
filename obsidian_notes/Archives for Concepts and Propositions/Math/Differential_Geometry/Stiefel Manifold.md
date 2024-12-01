---
tags:
  - concept
  - math/differential_geometry
  - optimization/theory
  - math/matrix_analysis
  - numerical_methods/numerical_linear_algebra
keywords:
  - stiefel_manifold
topics:
  - differential_geometry
  - matrix_analysis
  - numerical_linear_algebra
  - optimization
name: Stiefel Manifold
date of note: 2024-10-02
---

## Concept Definition

>[!important]
>**Name**: Stiefel Manifold

>[!important] Definition
>The **(compact) Stiefel manifold** $V_{k}(\mathbb{R}^{n})$ is the set of *all orthonormal $k$-frames* in $\mathbb{R}^n$. 
>
>That is, it is the set of *ordered $k$-tuples* of *orthonormal vectors* in $\mathbb{R}^n$.  
>$$
> \begin{align*}
> V_{k}(\mathbb{R}^{n}) &\equiv \{U\in \mathbb{R}^{n\times k}:\;  U^{T}U =  I_{k} \},\quad k\le n.
> \end{align*}
>$$ 
>- The dimension of a *Stiefel manifold* $$\text{dim}(V_{k}(\mathbb{R}^{n})) = kn - \frac{k(k+1)}{2}.$$

- [[Orthogonal Group]]
- [[Complete Orthonormal Basis of Hilbert Space]]
- [[Compactness]]
- [[Subspace Topology]]


>[!example]
>- $$V_{n}(\mathbb{R}^{n}) = \mathcal{O}(n) \equiv \{U\in \mathbb{R}^{n\times n}:\;  U^{T}U =  I_{n} = UU^{T} \}$$ 
>- $$V_{n}(\mathbb{C}^{n}) = \mathcal{U}(n) \equiv \{U\in \mathbb{C}^{n\times n}:\;  U^{*}U =  I_{n} = UU^{*} \}$$ 
>- $$V_{n-1}(\mathbb{R}^{n}) = \mathcal{SO}(n) := \{ u\in \mathcal{O}(n): \det(U) = 1  \}.$$
>- $$V_{n-1}(\mathbb{C}^{n}) = \mathcal{SU}(n) := \{ u\in \mathcal{U}(n) : \det(U) = 1   \}.$$
>- $$V_{1}(\mathbb{R}^{n}) = \mathcal{S}^{n-1} := \{ u\in \mathbb{R}^{n}: \lVert u \rVert_{2} = 1  \}.$$
>- $$V_{1}(\mathbb{C}^{n}) = \mathcal{S}^{2n-1} := \{ u\in \mathbb{C}^{n}: \lVert u \rVert_{2} = 1  \}.$$

- [[Unitary Group]]
- [[Orthogonal Group]]
- [[Special Orthogonal Group and Special Unitary Group]]


## Explanation





-----------
##  Recommended Notes and References


- [[Grassmann Manifold as Quotient Manifold]]

- [[Tangent Space to Submanifold]]
- [[Parallel Transport of Tensor Field along Curve]]
- [[Geodesic on Manifolds]]

- [[Local and Global Frame for Tangent Bundle]]
- [[Local and Global Coframes for Cotangent Bundle]]
- [[Riemannian Metric and Riemannian Manifold]]
- [[Smooth Manifold]]

- [[Retraction on Smooth Manifold]]
- [[Retraction Map onto a Subspace]]

- [[Principal Component Analysis]]
- [[Invariance under Linear Transformation]]
- [[Rayleigh Quotient for Eigenvalue Problem]]
- [[Convex Optimization for Eigenvalue Problem]]


- [[Homogeneous Space]]

- [[General Linear Group]]

- [[Linear Subspace]]
- [[Vector Space over a Field]]
- [[Topology of Set]]


- [[An Introduction to Optimization on Smooth Manifolds by Boumal]] pp 8 - 11
- Wikipedia [Stiefel_manifold](https://en.wikipedia.org/wiki/Stiefel_manifold)
- [[edelmanGeometryAlgorithmsOrthogonality1998]] Edelman, A., Arias, T. A., & Smith, S. T. (1998). The geometry of algorithms with orthogonality constraints. _SIAM journal on Matrix Analysis and Applications_, _20_(2), 303-353.