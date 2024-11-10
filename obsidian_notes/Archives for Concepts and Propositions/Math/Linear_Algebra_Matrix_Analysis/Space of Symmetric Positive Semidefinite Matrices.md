---
tags:
  - concept
  - math/differential_geometry
  - math/linear_algebra
  - math/matrix_analysis
  - math/riemannian_geometry
keywords:
  - space_symmetric_positive_semidefinite_matrices
topics:
  - matrix_analysis
  - differential_geometry
  - riemannian_geometry
  - linear_algebra
name: Space of Symmetric Positive Definite Matrices
date of note: 2024-11-09
---

## Concept Definition

>[!important]
>**Name**:  Space of Symmetric Positive Definite Matrices

>[!important] Definition
>The **space of symmetric matrices** in $M_{n}(\mathbb{R})$  is denoted as
>$$
>\mathcal{S}^{n} := \mathcal{S}^{n}(\mathbb{R}) := \left\{ A \in M_{n}(\mathbb{R}): A = A^{T} \right\} 
>$$
>
>Similarly the **space of Hermitian matrices** in $M_{n}(\mathbb{C})$  is denoted as
>$$
>\mathcal{S}^{n}:= \mathcal{S}^{n}(\mathbb{C})  := \left\{ A \in M_{n}(\mathbb{C}): A = A^{*}\, \right\} 
>$$

- [[Hermitian or Symmetric Matrix]]


>[!important] Definition
>The **space of symmetric positive semi-definite matrices** in $M_{n}(\mathbb{R})$  is denoted as
>$$
>\mathcal{S}_{+}^{n} := \left\{ A \in M_{n}(\mathbb{R}): A = A^{T}\, \; A \succeq 0 \right\} 
>$$
>
>Similarly the **space of Hermitian positive semi-definite matrices** in $M_{n}(\mathbb{C})$  is denoted as
>$$
>\mathcal{S}_{+}^{n} := \left\{ A \in M_{n}(\mathbb{C}): A = A^{*}\, \; A \succeq 0 \right\} 
>$$

>[!important] Definition
>The **space of symmetric positive definite matrices** in $M_{n}(\mathbb{R})$  is denoted as
>$$
>\mathcal{S}_{++}^{n} := \left\{ A \in M_{n}(\mathbb{R}): A = A^{T}\, \; A \succ 0 \right\} 
>$$
>
>Similarly the **space of Hermitian positive definite matrices** in $M_{n}(\mathbb{C})$  is denoted as
>$$
>\mathcal{S}_{++}^{n} := \left\{ A \in M_{n}(\mathbb{C}): A = A^{*}\, \; A \succ 0 \right\} 
>$$


- [[Positive Semidefinite Transformation]]


## Explanation



## Topology and Geometry

>[!info]
>$$
>\mathcal{S}_{++}^{n} \subset \mathcal{S}_{+}^{n} \subset \mathcal{S}^{n} \subset M_{n}(F)
>$$

### Vector Space


>[!important] Proposition
>The **space of symmetric matrices** $\mathcal{S}^{n}(\mathbb{R})$  in $M_{n}(\mathbb{R})$ forms a **vector space** of dimension $$\frac{n(n+1)}{2}$$ i.e. $$\mathcal{S}^{n}(\mathbb{R}) \simeq \mathbb{R}^{n(n+1)/2}$$

- [[Vector Space over a Field]]

### Convex Cone

>[!important] Proposition
>The **space of self-adjoint positive semi-definite matrices** $\mathcal{S}_{+}^{n}$ in $M_{n}$ forms a **convex cone**, i.e. the following properties hold:
>- For every $A \in \mathcal{S}_{+}^{n} \setminus \{ 0 \}$,  and any $\lambda \ge 0$, the **ray** $$\lambda A \in \mathcal{S}_{+}^{n}$$
>- For any two matrices $A, B\in \mathcal{S}_{+}^{n}$, and $t\in [0,1]$, we have $$t\,A + (1-t)\,B \in \mathcal{S}_{+}^{n}.$$

- [[Convex Cone Set]]
- [[Ray in Order Topology]]

### Smooth Manifold

>[!important] Theorem
>The  **space of self-adjoint positive definite matrices** $\mathcal{S}_{++}^{n}$ is a **smooth manifold** of dimension $$\frac{n(n+1)}{2}.$$
>
>In particular, define the **spectrum map** $$\lambda: \mathcal{S}^{n} \to \mathbb{R}^{n}$$ as $$\lambda(A) := [\lambda_{1}(A) \,{,}\ldots{,}\,\lambda_{n}(A)]$$ where $\lambda_{i}(A)$ is the $i$-th *eigenvalue* of $A$.
>- By *spectral theorem*, for every matrix $A$ in $\mathcal{S}^{n}$, $\lambda(A)$ exists in $\mathbb{R}^{n}$
>- $\lambda$ is a **continuous map**.
>
>Then the *space of symmetric/Hermitian positive definite matrix* is seen as the *preimage* of $\lambda$ over an **open subset** $(0,\infty)^{n}$, i.e. $$\mathcal{S}_{++}^{n} = \lambda^{-1}((0,\infty)^{n}).$$
>- Since $\mathcal{S}^{n}_{++}$ is the continuous preimage of an open set, it is an open subset of $\mathcal{S}^{n}$. 
>- Since an open subset of a smooth manifold is a smooth manifold, $\mathcal{S}_{++}^{n}$ is a smooth manifold.

- [[Smooth Manifold]]
- [[Riemannian Metric and Riemannian Manifold]]
- [[Spectrum of Self-Adjoint Linear Operator]]
- [[Embedded Submanifold via Level Sets]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]


>[!important] Definition
>Let $\mathcal{S}_{++}^{n}$ be the *space of symmetric positive definite matrices*. 
>
>Define the *matrix exponential* map  $$\exp: \mathcal{S}_{++}^{n} \to \mathcal{S}^{n} \simeq \mathbb{R}^{n(n+1)/2} \implies A \mapsto e^{A}$$ 
>- The exponential map is a *local diffeomorphism*, thus for an open subset $U \subset \mathcal{S}_{++}^{n}$, the pair $(U, \exp)$ forms a **smooth coordinate chart**. 
>
>The *principal matrix logarithm* $$B = \log(A)$$ defines a **coordinate** of $A$ in $\mathbb{R}^{n(n+1)/2}.$

- [[Matrix Exponential]]
- [[Matrix Logarithm]]
- [[Local Diffeomorphisms]]
- [[Smooth Atlas]]
- [[Smooth Chart and Smooth Coordinate Map]]

### Lie Group

>[!important] Theorem
>The  **space of self-adjoint positive definite matrices** $\mathcal{S}_{++}^{n}$ is a **Lie group** under the matrix multiplication.

- [[Lie Algebra as Vector Space with Lie Bracket]]
- [[Lie Group]]


### Riemannian Manifold


- [[Affine Invariant Riemannian Metric in Space of Symmetric Positive Definite Matrices]]
- [[Log-Euclidean Riemannian Metric in Space of Symmetric Positive Definite Matrices]]




-----------
##  Recommended Notes and References





- [[Semidefinite Programming]]

- [[General Linear Group]]
- [[Matrix Ring]]
- [[Convex Set]]


- [[Matrix Analysis by Horn]]
- [[Introduction to Riemannian Manifolds by Lee]]
- [[Convex Optimization by Boyd]]
- [[An Introduction to Optimization on Smooth Manifolds by Boumal]]