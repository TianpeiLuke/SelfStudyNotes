---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
keywords:
  - singular_value_decomposition
topics:
  - matrix_analysis
  - linear_algebra
name: Singular Value Decomposition of Linear Map
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Singular Value Decomposition of Linear Map

>[!important] Theorem (Singular Value Decomposition)
>Let $A \in M_{m,n}$, and $q= \min\left\{ m, n \right\}$, and suppose that $\text{rank}(A) = r.$
>- There are **unitary matrices** $U \in U(m)$ and $V\in U(n)$, and a **square diagonal matrix** $$\Sigma_{q} = \text{diag}(\sigma_{1} \,{,}\ldots{,}\,\sigma_{q})$$ such that $\sigma_{1} \ge \sigma_{2} \ge \ldots \sigma_{r} >0 = \sigma_{r+1} =  \ldots = \sigma_{q}$ and $$A = U \,\Sigma\,V^{*},$$ in which 
>  $$
>  \begin{align*}
>  \Sigma = \left\{ \begin{array}{cc} \Sigma_{q} & m = n\\[5pt] \left[ \Sigma_{q}, \; 0 \right] \in M_{m,n} & n > m \\[5pt] \left[ \begin{array}{c}\Sigma_{q} \\ 0\end{array} \right] \in M_{m,n} & m > n\end{array}\right.
>  \end{align*}
> $$
>
>- The parameters $\sigma_{1} \,{,}\ldots{,}\,\sigma_{r}$ are the **positive square roots** of the decreasingly ordered *nonzero* **eigenvalues** of $AA^{*}$, which are the same as the decreasingly ordered *nonzero* **eigenvalues** of $A^{*}A$ $$\sigma_{i}(A) = \sqrt{ \lambda_{i}(AA^{*}) } = \sqrt{ \lambda_{i}(A^{*}A) }.$$

- [[Unitary Group]]
- [[Spectral Theorem of Normal Map and Eigen decomposition]]
- [[Matrix Analysis by Horn]] pp 150

>[!important] Definition (Singular Value Decomposition Multiplicative Form)
>The decomposition of a $m\times n$ matrix $$A = U \,\Sigma\,V^{*},$$ is called the **singular value decomposition (SVD)** of $A$, where 
>- $U\in U(m)$ and 
>- $V\in U(n)$ and
>- $\Sigma\in M_{m,n}$ such that 
>$$
>  \begin{align*}
>  \Sigma = \left\{ \begin{array}{cc} \Sigma_{q} & m = n\\[5pt] \left[ \Sigma_{q}, \; 0 \right] \in M_{m,n} & n > m \\[5pt] \left[ \begin{array}{c}\Sigma_{q} \\ 0\end{array} \right] \in M_{m,n} & m > n\end{array}\right.
>  \end{align*}
>$$
>- $\Sigma_{q} = \text{diag}(\sigma_{1} \,{,}\ldots{,}\,\sigma_{q}) \in \mathbb{R}^{q}$
>
>
>Moreover, 
>- Each column vector $u_{i}$ of $V$ is called the **left-singular vector**
>- Each column vector $v_{j}$ of $W$ is called the **right-singular vector**.
>- The parameters $\sigma_{1} \ge \sigma_{2} \ge \ldots \sigma_{r} >0 = \sigma_{r+1} =  \ldots = \sigma_{q}$  are called the **singular values.**

^bebe11

>[!important] Definition (Singular Value Decomposition Projection Form)
>The matrix $A\in M_{m,n}$ has the following **singular value decomposition (SVD)**
>$$
>A = \sum_{i=1}^{r}\sigma_{i}\,u_{i}\,v_{i}^{*}
>$$ 
>where 
>- $\text{rank}(A) = r$,  
>- $\left\{ u_{1} \,{,}\ldots{,}\, u_{r} \right\} \subset \mathbb{C}^{m}$ are *orthogonal*
>-  $\left\{ v_{1} \,{,}\ldots{,}\, v_{r} \right\} \subset \mathbb{C}^{n}$ are *orthogonal*

^bcbfbe

## Explanation

>[!info]
>Using SVD of $A$, we see that
>$$
>A^{*}A\,v_{i} = \sigma_{i}^2\, v_{i}
>$$
>and
>$$
>A\,A^{*}\,u_{i} = \sigma_{i}^2\, u_{i}
>$$

## Properties

>[!important] Corollary
>If $$A = U\,\Sigma\,V^{T}$$ is the **SVD** of $A\in \mathbb{R}^{n\times m}$ and $n \ge m$, then for $i=1 \,{,}\ldots{,}\,m$
>$$
>A\,v_{i} = \sigma_{i}\,u_{i}
>$$
>and
>$$
>A^{T}\,u_{i} = \sigma_{i}\,v_{i}.
>$$

>[!quote]
>There is a nice **geometry** behind this result. The **singular values** of a matrix $A$ are the **lengths of the semiaxes** of the **hyperellipsoid** $E$ defined by $$E = \{ Ax: \lVert x \rVert = 1 \}.$$ The *semiaxis directions* are defined by the $u_{i}$ and their *lengths* are the singular values.
>
>-- [[Matrix Computations by Golub]] PP 77

>[!important] Corollary (Norm)
>If $A\in \mathbb{R}^{n\times m}$,  and $q= \min\left\{ m, n \right\}$  then 
>$$
>\lVert A \rVert_{2} = \sigma_{1} = \sigma_{max} 
>$$
>and
>$$
>\lVert A \rVert_{F} = \sqrt{ \sum_{i=1}^{q} \sigma_{i}^2 } = \lVert \sigma \rVert_{2} 
>$$

- [[Norm and Normed Space]]
- [[Bounded Linear Operator and Norm of Operator]]
- [[Frobenius Norm of Matrix]]

>[!important] Corollary (Perturbation)
>If $A\in \mathbb{R}^{n\times m}$,  and $E\in \mathbb{R}^{n\times m}$  then 
>$$
>\sigma_{max}\left( A + E \right) \le \sigma_{max}\left( A \right) + \lVert E \rVert_{2} 
>$$
>and
>$$
>\sigma_{min}\left( A + E \right) \ge \sigma_{min}\left( A \right) - \lVert E \rVert_{2}. 
>$$

>[!info]
>If a *column* is added to a matrix, then the **largest singular value increases** and the **smallest singular value decreases**.

>[!important] Corollary (Column Augmentation)
>If $A\in \mathbb{R}^{n\times m}$,  $n > m$, and $z \in \mathbb{R}^{n}$  then 
>$$
>\sigma_{max}\left( \left[ A\,,\, z \right]   \right) \ge \sigma_{max}\left( A \right)
>$$
>and
>$$
>\sigma_{min}\left(  \left[ A\,,\, z \right]   \right) \le \sigma_{min}\left( A \right). 
>$$

>[!info]
>The **SVD** neatly characterizes the **rank** of a matrix and **orthonormal bases** for both its **nullspace** and its **range**.

>[!important] Corollary (Range and Kernel Subspace)
>If $A$ has $r$ **positive singular values**, then
>- the **rank** $$\text{rank}(A) = r;$$
>- the **kernel** or **nullspace** of $A$ is the subspace spanned of **right-singular vectors** $\left\{ v_{r+1} \,{,}\ldots{,}\, v_{m} \right\}$  $$\text{Ker}(A) = \text{span}\left\{ v_{r+1} \,{,}\ldots{,}\, v_{m} \right\}$$
>- the **range** of $A$ is the subspace  spanned of **left-singular vectors** $\left\{ u_{1} \,{,}\ldots{,}\, v_{r} \right\}$ $$R(A) := \text{Im}(A) = \text{span}\left\{ u_{1} \,{,}\ldots{,}\, u_{r} \right\}$$


- [[Rank and Nullity of Linear Map]]
- [[Range and Kernel of Linear Map]]
- [[Linear Span over a Set of Vectors]]
- [[Linear Subspace]]

## Low Rank Approximation

![[Low Rank Approximation of Matrix and Eckhart-Young Theorem#^65eeb8]]

- [[Low Rank Approximation of Matrix and Eckhart-Young Theorem]]

## Fundamental Subspaces

![[Singular Value Decomposition and Fundamental Subspaces#^b13e8a]]

- [[Singular Value Decomposition and Fundamental Subspaces]]
- [[Fundamental Subspaces from Linear Map]]

## Polar Decomposition

- [[Polar Decomposition of Transformation]]


-----------
##  Recommended Notes and References


- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]
- [[Spectral Theorem of Normal Map and Eigen decomposition]]
- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Eigenspace and Spectrum for Linear Map]]

- [[Singular Value Decomposition of Compact Operator]]

- [[Principle Component Analysis]]
- [[Least Square Estimation via Singular Value Decomposition]]

- [[Finite Dimensional Vector Spaces by Halmos]]
- [[Matrix Analysis by Horn]] pp 150
- [[Matrix Computations by Golub]] pp 76 - 81
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 35 - 40