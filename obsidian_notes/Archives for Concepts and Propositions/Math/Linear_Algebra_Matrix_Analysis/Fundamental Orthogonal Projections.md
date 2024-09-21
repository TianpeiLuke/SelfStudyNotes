---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
keywords:
  - range_linear_map
  - kernel_linear
  - fundamental_subspaces
  - orthogonal_projection
topics:
  - linear_algebra
  - matrix_analysis
name: Fundamental Orthogonal Projection
date of note: 2024-09-05
---

## Concept Definition

>[!important]
>**Name**: Fundamental Orthogonal Projection


![[Fundamental Subspaces from Linear Map#^71c730]]

- [[Fundamental Subspaces from Linear Map]]
- [[Linear Map]]
- [[Adjoint of Linear Map]]
- [[Range and Kernel of Linear Map]]
- [[Dual Space of Hilbert Space]]

![[Singular Value Decomposition and Fundamental Subspaces#^b13e8a]]

- [[Singular Value Decomposition and Fundamental Subspaces]]

>[!important] Proposition
>Let $A \in M_{m,n}$ be a $m\times n$ matrix and the **singular value decomposition (SVD)** of $A$ is given by $$A = U \,\Sigma\,V^{*},$$ where 
>- $U = [u_{1} \,{,}\ldots{,}\,u_{m}] \in \mathcal{U}(m)$ and 
>- $V = [v_{1} \,{,}\ldots{,}\,v_{n}] \in \mathcal{U}(n)$ and 
>- $\Sigma = [\text{diag}(\sigma_{1}\,{,}\ldots{,}\,\sigma_{min\{m,n\}}); 0]\in M_{m,n}$. 
>  
>Furthermore,  the left singular matrix and right singular matrix can be partitioned as 
>- Denote $U_{1:r}= [u_{1} \,{,}\ldots{,}\,u_{r}]$ as the matrix formed by the *first $r$ left singular vectors*, where $r= rank(A)$.
>- Denote $U_{r+1:m}= [u_{r+1} \,{,}\ldots{,}\,u_{m}]$ as the matrix formed by the *rest left singular vectors*, 
>- Denote $V_{1:r}= [v_{1} \,{,}\ldots{,}\,v_{r}]$ as the matrix formed by the *first $r$ right singular vectors*, where $r= rank(A)$.
>- Denote $V_{r+1:n}= [v_{r+1} \,{,}\ldots{,}\,v_{n}]$ as the matrix formed by the *rest right singular vectors*.  
>  
>Then  the **orthogonal projection map** on four **fundamental subspaces** are given by 
>- $$P_{\text{R}(A)} = P_{\text{Ker}(A^{*})^{\perp}} = A\,A^{+} = U_{1:r}\,U_{1:r}^{*} = \sum_{i=1}^{r}u_{i}\,u_{i}^{*}$$
>- $$P_{\text{Ker}(A^{*})} = P_{\text{R}(A)^{\perp}} = I - A\,A^{+} = U_{r+1:m}\,U_{r+1:m}^{*} = \sum_{i=r+1}^{m}u_{i}\,u_{i}^{*}$$
>- $$P_{\text{R}(A^{*})} = P_{\text{Ker}(A)^{\perp}} = A^{+}\,A = V_{1:r}\,V_{1:r}^{*} = \sum_{i=1}^{r}v_{i}\,v_{i}^{*}$$
>- $$P_{\text{Ker}(A)} = P_{\text{R}(A^{*})^{\perp}} = I - A^{+}\,A = V_{r+1:n}\,V_{r+1:n}^{*} = \sum_{i=r+1}^{n}v_{i}\,v_{i}^{*}$$


^6010c1

- [[Moore–Penrose Pseudo Inverse of Matrix]]
- [[Projection Map onto Linear Subspace]]
- [[Orthogonal Complement of Hilbert Spaces]]

![[fundamental_subspaces.png]]

![[svd_fundamental_subspaces.png]]

## Explanation

>[!info]
>Note that for general Hilbert space, the above four subspaces exist, and the **orthogonal complementary** relation still hold. But the direct sum decomposition may not hold.

- [[Hilbert Space]]

![[Fundamental Subspaces from Linear Map#^3f989c]]

- [[Fundamental Subspaces from Linear Map]]

>[!info]
>For every $x\in V$, the following decomposition exists
>$$
>\begin{align*}
> x&= P_{\text{Ker}(A)^{\perp}}\,x + P_{\text{Ker}(A)}\,x  \\[5pt]
> &=  A^{+}A\,x  + \left(I - A^{+}A\right)\,x \\[5pt]
> &= V_{1:r} V_{1:r}^{*}\,x + V_{r+1:n}\,V_{r+1:n}^{*}\,x
>\end{align*}
>$$

^64a8f0

>[!info]
>For every $w\in W$, the following decomposition exists
>$$
>\begin{align*}
> w&= P_{\text{R}(A)}\,w + P_{\text{R}(A)^{\perp}}\,w \\[5pt]
> &= AA^{+}\,w + \left(I - AA^{+}\right)\,w \\[5pt]
> &= U_{1:r} U_{1:r}^{*}\,w + U_{r+1:n}\,U_{r+1:n}^{*}\,w
>\end{align*}
>$$


## Solution of System of Linear Equations

![[Existence and Uniqueness of Solution of Linear Equations#^1dcd93]]

>[!important] 
>The **solution** of linear system $$AX = B$$ is of the form
>$$
>X = P_{\text{Ker}(A)^{\perp}}(A^{+}B) + P_{\text{Ker}(A)}(Y)
>$$
>where $Y\in \mathbb{R}^{n\times k}$ is arbitrary.

^3d1aa0

- [[Existence and Uniqueness of Solution of Linear Equations]]
- [[System of Linear Equations or Linear System]]

## Solution of Linear Least Square Estimation

![[Least Square Estimation Solution and Geometric Interpretation#^0bdae8]]

- [[Least Square Estimation Solution and Geometric Interpretation]]




-----------
##  Recommended Notes and References


- [[Fundamental Subspaces from Linear Map]]
- [[Projection Map onto Linear Subspace]]
- [[Singular Value Decomposition of Linear Map]]
- [[Orthogonal Complement of Hilbert Spaces]]

- [[Rank–Nullity Theorem]]
- [[Rank and Nullity of Linear Map]]

- [[Range and Kernel of Linear Operator]]
- [[Space of Bounded Linear Operators]]

- [[Linear Subspace]]
- [[Riesz Representation Theorem]]
- [[Inner Product Space]]
- [[Vector Space over a Field]]


- [[Finite Dimensional Vector Spaces by Halmos]]
- [[Matrix Analysis by Horn]]
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 22 - 24