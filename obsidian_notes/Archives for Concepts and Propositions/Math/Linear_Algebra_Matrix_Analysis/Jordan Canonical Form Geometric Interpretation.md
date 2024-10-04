---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
keywords:
  - jordan_canonical_form
  - krylov_subspace
  - nilpotent_linear_transform
topics:
  - linear_algebra
  - matrix_analysis
name: Jordan Canonical Form Geometric Interpretation
date of note: 2024-10-03
---

## Concept Definition

>[!important]
>**Name**: Jordan Canonical Form Geometric Interpretation

![[Nilpotent Linear Transformation and Matrix#^a1b57c]]

![[Nilpotent Linear Transformation Geometric Characterization#^bfe541]]



>[!important] Theorem
>Let $A\in \mathcal{L}(V)$ be a *linear transformation* on a finite dimensional space $V$. 
>- Let $\lambda_{1}\,{,}\ldots{,}\,\lambda_{p}$ be **distinct eignvalues** of $A$ with respective **algebraic multiplicity** $m_{1}\,{,}\ldots{,}\,m_{p}$, i.e. $$\det(\lambda I - A) = \prod_{i=1}^{p}(\lambda - \lambda_{i})^{m_{i}}$$
>
>Then $V$ is the **direct sum** of $p$ subspaces $\mathcal{S}_{1}\,{,}\ldots{,}\,\mathcal{S}_{p}$ of respective dimensions $m_{1}\,{,}\ldots{,}\,m_{p}$,  $$V = \mathcal{S}_{1}\,{\oplus}\ldots{\oplus}\,\mathcal{S}_{p}$$ such that 
>- each $\mathcal{S}_{i}$ is **invariant** under $A$
>- and the linear map $(A - \lambda_{i}I)$ *restricted* on $\mathcal{S}_{i}$ is **nilpotent**.
>  

- [[Nilpotent Linear Transformation Geometric Characterization]]
- [[Nilpotent Linear Transformation and Matrix]]
- [[Direct Sum of Subspaces]]
- [[Reducibility of Linear Transformation]]
- [[Invariance under Linear Transformation]]



## Explanation

>[!important]
>This theorem states that for any linear transformation $A\in \mathcal{L}(V)$ on a  finite dimensional space $V$. 
>
>$$V= \bigoplus_{j=1}^{r_{i}}\text{Ker}(A - \lambda_{1}I)^{q_{1,j}} \,{\oplus}\ldots{\oplus}\,\bigoplus_{j=1}^{r_{p}}\text{Ker}(A - \lambda_{p}I)^{q_{p,j}}$$  
>- $$\sum_{j=1}^{r_{i}}\text{dim}(\text{Ker}(A - \lambda_{i}I)^{q_{i,j}}) = m_{i}$$

![[Jordan Canonical Form#^44be3f]]

- [[Jordan Canonical Form]]


-----------
##  Recommended Notes and References



- [[Eigenspace and Spectrum for Linear Map]]
- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Algebraic and Geometric Multiplicity of Linear Map]]


- [[Krylov Subspace and Krylov Matrix]]

- [[Similarity Relation between Linear Maps and Matrices]]
- [[Linear Isomorphism]]
- [[Linear Map]]
- [[Vector Space over a Field]]

- [[Finite Dimensional Vector Spaces by Halmos]] pp 112  - 115