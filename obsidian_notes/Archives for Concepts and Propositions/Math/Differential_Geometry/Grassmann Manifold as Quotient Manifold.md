---
tags:
  - concept
  - math/differential_geometry
  - optimization/theory
  - math/matrix_analysis
  - numerical_methods/numerical_linear_algebra
keywords:
  - grassmann_manifold
topics:
  - differential_geometry
  - matrix_analysis
  - optimization
  - numerical_linear_algebra
name: Grassmann Manifold as Quotient Manifold
date of note: 2024-10-02
---

## Concept Definition

>[!important]
>**Name**: Grassmann Manifold as Quotient Manifold

>[!important] Definition
>The **Grassmannian** (or, **Grassmann manifold**}  $Gr(k, \mathbb{R}^{n})$ or $Gr(k, n)$ is a space which parameterizes *all linear subspaces* of a vector space $\mathbb{R}^{n}$ of *given dimension* $k$. 
>
>$$
>Gr(k, \mathbb{R}^{n}) = \left\{ S \subset \mathbb{R}^{n}:\; \text{dim}(S) = k \right\} 
>$$

- [[Linear Subspace]]
- [[Vector Space over a Field]]


>[!example]
>The **Grassmann manifold** $Gr(1, \mathbb{R}^{n})$ is the *space of lines* through the origin in $\mathbb{R}^{n}$, so it is the same as the **projective space** of one dimension lower than $\mathbb{R}^{n}$.

>[!important]
>$Gr(k, \mathbb{R}^{n})$ is a **compact smooth manifold**. 
>
>Equipped with *topological* and *differential structure*, via $Gr(k,n)$, a *continuous and smooth* choice of subspace or *open and closed* collections of subspaces.

- [[Smooth Manifold]]
- [[Smooth Atlas]]


## Explanation

### Tangent Bundle and Grassmann Manifold

>[!important]
> The Grassmann manifold has a natural motivation: 
> 
> Consider the **tangent bundle** $T\mathcal{S}$ of a smooth manifold $$\mathcal{S}^{k} \subset \mathbb{R}^{n}$$ of *dimension* $k$, which assign for each point $p\in \mathcal{S}$, the **tangent space** $$T_{p}\mathcal{S} \simeq \mathbb{R}^{k}.$$ 
> 
> It defines a map $$F: \mathcal{S}^{k} \rightarrow Gr(k, n).$$ 
> The property of **tangent bundle** is related to the properties of the *corresponding map* $F$ viewed as **continuous map**. 

- [[Tangent Bundle]]
- [[Concepts related to Tangent Space and Tangent Bundle]]




-----------
##  Recommended Notes and References


- [[Stiefel Manifold]]
- [[Tangent Space to Submanifold]]
- [[Parallel Transport of Tensor Field along Curve]]
- [[Geodesic on Manifolds]]
- [[Riemannian Metric and Riemannian Manifold]]
- [[Smooth Manifold]]


- [[Principle Component Analysis]]
- [[Invariance under Linear Transformation]]
- [[Rayleigh Quotient for Eigenvalue Problem]]
- [[Convex Optimization for Eigenvalue Problem]]

- [[Retraction on Smooth Manifold]]
- [[Retraction Map onto a Subspace]]

- [[Unitary Group]]
- [[Orthogonal Group]]
- [[General Linear Group]]
- [[Orbit Space of Topological Group Action]]
- [[Quotient Space of Vector Space]]

- [[Topology of Set]]
- [[Topological Manifold]]

- [[An Introduction to Optimization on Smooth Manifolds by Boumal]]
- [[edelmanGeometryAlgorithmsOrthogonality1998]] Edelman, A., Arias, T. A., & Smith, S. T. (1998). The geometry of algorithms with orthogonality constraints. _SIAM journal on Matrix Analysis and Applications_, _20_(2), 303-353.