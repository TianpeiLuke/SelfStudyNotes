---
tags:
  - concept
  - math/matrix_analysis
  - numerical_methods/numerical_linear_algebra
  - math/linear_algebra
keywords:
  - priniciple_biorthogonality
topics:
  - matrix_analysis
  - numerical_linear_algebra
  - linear_algebra
name: Principle of Biorthogonality
date of note: 2024-09-29
---

## Concept Definition

>[!important]
>**Name**: Principle of Biorthogonality

### Orthogonality of Eigenvectors for Different Eigenvalues

![[Eigenvalue and Eigenvector for Linear Map#^1b8cf8]]

![[Eigenvalue and Eigenvector for Linear Map#^bec9fb]]

- [[Eigenvalue and Eigenvector for Linear Map]]

![[Eigenspace and Spectrum for Linear Map#^3d4672]]

- [[Eigenspace and Spectrum for Linear Map]]

![[Spectral Theorem of Self-Adjoint Map and Eigen decomposition#^7617c3]]

- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]

### Orthogonality of Left and Right Eigenvectors for Different Eigenvalues

>[!important] Theorem (Principle of Biorthogonality)
>Let $A\in M_{n}$.  Suppose that
>- $x$ is the **right eigenvector** of $A$ associated with **eigenvalue** $\lambda$, i.e. $$Ax= \lambda x,$$
>- $y$ s the **left eigenvector** of $A$ associated with **eigenvalue** $\mu$, i.e. $$y^{*}A= \mu y^{*}.$$
>  
>Then
>- If the corresponding **eigenvalues are different** $\lambda\neq \mu$, the $x$ and $y$ are **orthogonal** to each other $$\left\langle  y\,,\,x \right\rangle = 0.$$
>- If the corresponding **eigenvalues are same** $\lambda = \mu$, and $\left\langle  x\,,\,y \right\rangle \neq 0,$ then there exists a **nonsingular** $S\in M_{n}$ of the form $$S = [x, S_{1}]$$ such that $$(S^{-1})^{*} = \left[ \frac{y}{\left\langle  x\,,\,y    \right\rangle}, Z_{1}\right] $$ and $$A = S\left[\begin{array}{cc}\lambda & 0\\[5pt] 0& B\end{array} \right]S^{-1},\quad B\in M_{n-1}$$
>
>Conversely, if $A$ is similar to a **block matrix** of the above form, then it has a **non-orthogonal pair** of **left** and **right eigenvectors** associated with the **eigenvalue** $\lambda.$

- [[Surjective Injective Invertible Linear Map and Rank]]
- [[Diagonal Matrix and Block Diagonal Matrix]]
- [[Diagonalizable Matrix]]

### The Complete Principle of Biorthogonality

>[!important] Theorem (Complete Principle of Biorthogonality)
>Let $A\in M_{n}$.  Suppose that
>- $x\in \mathbb{C}^{n}$ is the **right eigenvector** of $A$ associated with **eigenvalue** $\lambda$, i.e. $$Ax= \lambda x,$$
>- $y\in \mathbb{C}^{n}$ s the **left eigenvector** of $A$ associated with **eigenvalue** $\mu$, i.e. $$y^{*}A= \mu y^{*}.$$
>  
>Suppose that
>-  the corresponding **eigenvalues are different** $\lambda\neq \mu$, the $x$ and $y$ are **orthogonal** to each other $$\left\langle  x\,,\,y \right\rangle = 0.$$ Let $$U = [x, y, u_{3}\,{,}\ldots{,}\,u_{n}]\in \mathcal{U}(n).$$ Then $A$ is **unitarily similar to** $$U^{*}AU = \left[ \begin{array}{ccc}\lambda & \star & \star \\ 0 & \mu & 0 \\ 0 & \star & A_{n-2} \end{array} \right],\quad A_{n-2}\in M_{n-2}.$$
>- the corresponding **eigenvalues are same** $\lambda = \mu$, and $x$ and $y$ are *orthogonal to each other* $$\left\langle  x\,,\,y \right\rangle = 0.$$ Let $$U = [x, y, u_{3}\,{,}\ldots{,}\,u_{n}]\in \mathcal{U}(n).$$ Then $A$ is **unitarily similar to** $$U^{*}AU = \left[ \begin{array}{ccc}\lambda & \star & \star \\ 0 & \lambda & 0 \\ 0 & \star & A_{n-2} \end{array} \right],\quad A_{n-2}\in M_{n-2},$$ and the **algebraic multiplicity** of $\lambda$ is at least $2$.
>- the corresponding **eigenvalues are same** $\lambda = \mu$, and $$\left\langle  x\,,\,y \right\rangle \neq 0.$$ Let $$S = [x, S_{1}]\in M_{n}$$ in which the columns of $S_{1}$ are any given *basis* for the **orthogonal complement** of $y$.  Then $S$ is **nonsingular**, and the first column of  $(S^{-1})^{*}$ is a nonzero *scalar multiple* of $y$  and $$S^{-1}AS = \left[\begin{array}{cc}\lambda & 0\\[5pt] 0& A_{n-1}\end{array} \right],\quad A_{n-1}\in M_{n-1}$$ If the **geometric multiplicity** of $\lambda$ is $1$, then its **algebraic multiplicity** is also $1$.
>
>Conversely, if $A$ is similar to a **block matrix** of the above form, then it has a **non-orthogonal pair** of **left** and **right eigenvectors** associated with the **eigenvalue** $\lambda.$

- [[Algebraic and Geometric Multiplicity of Linear Map]]



## Explanation

>[!quote]
>The **principle of biorthogonality** says that **left and right eigenvectors** associated with **different eigenvalues** are **orthogonal**;
>
>-- [[Matrix Analysis by Horn]] pp 123




-----------
##  Recommended Notes and References


- [[Eigenspace and Spectrum for Linear Map]]
- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]
- [[Algebraic and Geometric Multiplicity of Linear Map]]


- [[Finite Dimensional Vector Spaces by Halmos]] pp 156 - 157
- [[Matrix Analysis by Horn]] pp 79, 123, 134, 529
- [[Numerical Linear Algebra by Trefethen]] pp 303
- [[Matrix Computations by Golub]]