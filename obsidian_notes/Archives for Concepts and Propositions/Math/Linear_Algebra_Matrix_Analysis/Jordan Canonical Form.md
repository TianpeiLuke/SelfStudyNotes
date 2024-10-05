---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
keywords:
  - jordan_decomposition
  - jordan_canonical_form
topics:
  - matrix_analysis
  - linear_algebra
name: Jordan Canonical Form
date of note: 2024-09-15
---

## Concept Definition

>[!important]
>**Name**: Jordan Canonical Form

>[!important] Definition
>The **Jordan block matrix** is a $k_{i} \times k_{i}$ *upper triangular matrix* of the form
>$$J_{k_{i}}(\lambda_{i}) = \left[
>\begin{array}{cccccc}
> \lambda_{i} & 1 & 0 & \cdots & \cdots & 0 \\
> 0 & \lambda_{i}  & 1 & 0 &  & \vdots \\
> \vdots & \ddots & \lambda_{i} & \ddots & \ddots & \vdots \\
> \vdots &  & \ddots & \ddots & 1 & 0 \\
> \vdots &  & & \ddots & \lambda_{i}  & 1 \\
> \vdots & \cdots &   \cdots  &  \cdots  & 0 & \lambda_{i}
>\end{array}
>\right] \in \mathbb{C}^{k_{i}\times k_{i}}
>$$

- [[Triangular Matrix and Block Triangular Matrix]]

>[!important] Theorem (Jordan Canonical Form)
>For all $A\in \mathbb{C}^{n\times n}$ with *eigenvalues* $\lambda_{1} \,{,}\ldots{,}\,\lambda_{n}\in \mathbb{C}$ (*not necessarily distinct*), there exists an *non-singular* $S\in \mathbb{C}^{n\times n}$ such that 
>$$
>S^{-1}\,A\,S = J = \text{diag}\left(J_{k_{1}}(\lambda_{1})\,{,}\ldots{,}\,J_{k_{q}}(\lambda_{q})\right),
>$$
>where each of the **Jordan block matrices** $J_{k_{1}}(\lambda_{1})\,{,}\ldots{,}\,J_{k_{q}}(\lambda_{q})$ is of the form
>$$J_{k_{i}}(\lambda_{i}) = \left[
>\begin{array}{cccccc}
> \lambda_{i} & 1 & 0 & \cdots & \cdots & 0 \\
> 0 & \lambda_{i}  & 1 & 0 &  & \vdots \\
> \vdots & \ddots & \lambda_{i} & \ddots & \ddots & \vdots \\
> \vdots &  & \ddots & \ddots & 1 & 0 \\
> \vdots &  & & \ddots & \lambda_{i}  & 1 \\
> \vdots & \cdots &   \cdots  &  \cdots  & 0 & \lambda_{i}
>\end{array}
>\right] \in \mathbb{C}^{k_{i}\times k_{i}},
>$$
>and $$\sum_{i=1}^{q}k_{i} = n.$$
>
>The Jordan matrix $J = \text{diag}\left(J_{k_{1}}(\lambda_{1})\,{,}\ldots{,}\,J_{k_{q}}(\lambda_{q})\right)$ is **uniquely determined** by $A$ up to *permutations* of its direct sums.
>
>If $A\in \mathbb{R}^{n\times n}$ with only **real eigenvalues**, then $S\in GL(n,\mathbb{R})$.

^44be3f


- [[Similarity Relation between Linear Maps and Matrices]]
- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Algebraic and Geometric Multiplicity of Linear Map]]


>[!important] Definition
>For $A\in \mathbb{C}^{n\times n}$, the **Jordan canonical form (JCF)** is of the form
>$$
> A = S\,\text{diag}\left(J_{1} \,{,}\ldots{,}\,J_{q}\right)\, S^{-1}
>$$
>where $S$ is **invertible** and $J_{i}$ is the **Jordan block matrix** or **canonical blocks for similarity** associated with eigenvalue $\lambda_{i}$.


## Explanation

>[!quote]
>One application of the Jordan canonical form that is of considerable theoretical importance is the analysis of **solutions** of a **system of first order linear ordinary differential equations** with constant coefficients.
>
>-- [[Matrix Analysis by Horn]] pp 176

- [[Homogeneous Linear Differential Equations]]
- [[Linear ODE with Constant Coefficients]]
- [[Exponential Map of Linear Operator]]

>[!info]
>The **Jordan decomposition** is an *nonunitary analog* to the **Schur decomposition** for unsymmetric matrix.

- [[Schur Triangularization and Schur Form]]


## Characteristic Polynomial and Multiplicity 

![[Algebraic and Geometric Multiplicity of Linear Map#^7049c6]]

- [[Algebraic and Geometric Multiplicity of Linear Map]]
- [[Characteristic Polynomial for Linear Map]]


## Structure of Jordan Matrix and Eigenspaces

>[!important]
>The **Jordan matrix** 
>$$
>J = \text{diag}\left(J_{k_{1}}(\lambda_{1})\,{,}\ldots{,}\,J_{k_{q}}(\lambda_{q})\right)
>$$
>with $\sum_{i=1}^{q}k_{i} = n,$ has several invariant properties that hold for all matrix similar to it:
>- The number $q$ of Jordan blocks (counting multiple occurrences of the same block) is the **maximum number** of **linearly independent eigenvectors** of $J$.
>- The matrix $J$ is **diagonalizable** *if and only if* $k = n$, that is, if and only if all the Jordan blocks are $1$-by-$1$. $$J_{k_{i}}(\lambda_{i}) = [\lambda_{i}]$$
>- The **number** of *Jordan blocks* corresponding to a *given eigenvalue* is the **geometric multiplicity** of *the eigenvalue*, which is the dimension of the associated eigenspace.  $$\text{geometric multiplicity}(\lambda_{i}) = \#\{j: J_{j}(\lambda_{i})\}$$
>- The **sum** of the **sizes** of all the *Jordan blocks* corresponding to a *given eigenvalue* is its **algebraic multiplicity**. $$\text{algebraic multiplicity}(\lambda_{i}) = \sum_{j: J_{j}(\lambda_{i})}k_{j}$$
>- Define $$r_{k}(A, \lambda) = \text{rank}\left(A - \lambda I\right)^{k}$$ Suppose $\lambda$ is an *eigenvalue* of $A$. There exists a positive integer $k^{*}$ such that $$r_{1}(A, \lambda) > r_{2}(A, \lambda) \,{>}\ldots{>}\, r_{k^{*}}(A, \lambda) = r_{k^{*}+1}(A, \lambda)$$ This integer $k^{*}$ is the **size of largest Jordan block** with eigenvalue $\lambda$. And this integer is the **index** of $\lambda$ as an *eigenvalue* of $A$.

^31139a

- [[Nilpotent Linear Transformation and Matrix]]
- [[Eigenspace and Spectrum for Linear Map]]
- [[Diagonalizable Matrix]]
- [[Derogatory Matrix and Defective Matrix]]

## Minimal Polynomials

![[Minimal Polynomial for Linear Map#^5a01ca]]

- [[Minimal Polynomial for Linear Map]]


## Nilpotent Transformation

![[Nilpotent Linear Transformation and Matrix#^a1b57c]]

- [[Nilpotent Linear Transformation and Matrix]]

![[Nilpotent Linear Transformation Geometric Characterization#^bfe541]]

- [[Nilpotent Linear Transformation Geometric Characterization]]


-----------
##  Recommended Notes and References



- [[Nilpotent Linear Transformation and Matrix]]
- [[Krylov Subspace and Krylov Matrix]]
- [[Characteristic Polynomial for Linear Map]]
- [[Minimal Polynomial for Linear Map]]


- [[Matrix Analysis by Horn]] pp 164 - 171
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 82 - 85
- [[Matrix Computations by Golub]] pp 354, 400 - 402
- [[Finite Dimensional Vector Spaces by Halmos]] pp 112 -- 115
- [[Numerical Linear Algebra by Trefethen]] pp 337