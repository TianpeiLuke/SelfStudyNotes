---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
keywords:
  - variational_eigenvalue_problem
  - eigen_value
  - rayleigh_quotient
topics:
  - matrix_analysis
  - linear_algebra
name: Variational Characterization of Eigenvalues of Hermitian Matrix
date of note: 2024-09-23
---

## Concept Definition

>[!important]
>**Name**: Variational Characterization of Eigenvalues of Hermitian Matrix

>[!important] Theorem (Rayleigh)
>Let $A\in M_{n}$ be **Hermitian**, let **eigenvalues** of $A$ be ordered as $$\lambda_{min} = \lambda_{n} \,{\le}\ldots{\le}\,\lambda_{1} = \lambda_{max},$$ let $i_{1}\,{,}\ldots{,}\,i_{k}$ be given integers with $1\le i_{1} \,{\le}\ldots{\le}\,i_{k} \le n,$ let $x_{i_{1}} \,{,}\ldots{,}\,x_{i_{k}}$ be **orthonormal** and such that $$Ax_{i_{p}} = \lambda_{i_{p}}x_{i_{p}}, \quad p=1\,{,}\ldots{,}\,k,$$ and let $S$ be the *linear subspace spanned* by above *eigenvectors* $$S := \text{span}\left\{ x_{i_{1}} \,{,}\ldots{,}\,x_{i_{k}} \right\}.$$
>
>Then
>- The **$i_{k}$-th largest eigenvalue** is given by $$\begin{align*}\lambda_{i_{k}} &= \min_{0\neq x\in S}\frac{\left\langle x\,,\, Ax \right\rangle}{\left\langle  x\,,\,x    \right\rangle} \\[5pt] &= \min_{x\in S,\, \lVert x \rVert = 1 }\left\langle x , Ax \right\rangle \\[5pt] &\le   \max_{x\in S,\, \lVert x \rVert = 1 }\left\langle x , Ax \right\rangle \\[5pt]  &= \max_{0\neq x\in S}\frac{\left\langle x\,,\, Ax \right\rangle}{\left\langle  x\,,\,x    \right\rangle}  = \lambda_{i_{1}}  \end{align*}$$
>- The **bilinear form** $\left\langle x ,Ax  \right\rangle$ is bounded in $S$ by eigenvalues  $$\lambda_{i_{k}} \le \left\langle x ,Ax  \right\rangle \le \lambda_{i_{1}}, \quad \forall x\in S,$$ with **equality** in the **right-hand side** if and only if $Ax= \lambda_{i_{1}}x$. Similarly, the equality in the **left-hand side** hold if and only if $Ax= \lambda_{i_{k}}x.$
>- The **bilinear form** $\left\langle x ,Ax  \right\rangle$ is bounded in $\mathbb{C}^{n}$ by **maximal and minimal eigenvalues**  as $$\lambda_{min} \le \left\langle x ,Ax  \right\rangle \le \lambda_{max}, \quad \forall x\in \mathbb{C}^{n},$$ with **equality** in the **right-hand side** if and only if $Ax= \lambda_{max}x$. Similarly, the equality in the **left-hand side** hold if and only if $Ax= \lambda_{min}x.$ 
>	- Moreover, $$\lambda_{max} = \max_{x\neq 0} \frac{\left\langle  x\,,\, Ax   \right\rangle}{\left\langle  x\,,\,x    \right\rangle}$$
>	- and $$\lambda_{min} = \min_{x\neq 0} \frac{\left\langle  x\,,\, Ax   \right\rangle}{\left\langle  x\,,\,x    \right\rangle}$$

^50523d

- [[Hermitian or Symmetric Matrix]]
- [[Complete Orthonormal Basis of Hilbert Space]]
- [[Linear Span over a Set of Vectors]]
- [[Sesquilinear Form]]
- [[Rayleigh Quotient for Eigenvalue Problem]]



## Explanation

### Proof





## Courant-Fischer Minimax Theorem for Eigenvalues

![[Courant-Fischer Minimax Theorem for Eigenvalue Problem#^3d4e1f]]



-----------
##  Recommended Notes and References

- [[Minimax Theorem]]
- [[Rayleigh Quotient for Eigenvalue Problem]]
- [[Courant-Fischer Minimax Theorem for Eigenvalue Problem]]


- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Eigenspace and Spectrum for Linear Map]]
- [[Spectral Theorem of Normal Map and Eigen decomposition]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]
- [[Principal Component Analysis or PCA]]
- [[Schur Triangularization and Schur Form]]

- [[Stiefel Manifold]]
- [[Grassmann Manifold as Quotient Manifold]]

- [[Matrix Analysis for Scientists and Engineers by Laub]]
- [[Matrix Analysis by Horn]] pp 234 - 236
- [[Matrix Computations by Golub]] pp 441
- [[An Introduction to Optimization on Smooth Manifolds by Boumal]]