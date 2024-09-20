---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
keywords:
  - singular_value_decomposition
  - range_linear_map
  - kernel_linear
  - range_linear
topics:
  - matrix_analysis
  - linear_algebra
name: Singular Value Decomposition and Orthogonal Projection
date of note: 2024-08-21
---

## Concept Definition

>[!important]
>**Name**: Singular Value Decomposition and Orthogonal Projection

![[Fundamental Subspaces from Linear Map and its Projection#^71c730]]

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
>Then the **four fundamental subspaces** of $A$ are given by
>- $$\text{R}(U_{1:r}) = \text{R}(A) =  \left(\text{Ker}(A^{*})\right)^{\perp}$$  
>- $$\text{R}(U_{r+1:m}) = \text{Ker}(A^{*}) = \left(\text{R}(A)\right)^{\perp}$$  
>- $$\text{R}(V_{1:r}) = \text{R}(A^{*}) =  \left(\text{Ker}(A)\right)^{\perp}$$
>- $$\text{R}(V_{r+1:n}) = \text{Ker}(A) =  \left(\text{R}(A^{*})\right)^{\perp}$$

^b13e8a

- [[Singular Value Decomposition of Linear Map]]
- [[Fundamental Subspaces from Linear Map and its Projection]]
- [[Orthogonal Complement of Hilbert Spaces]]

![[svd_fundamental_subspaces.png]]


## Explanation





-----------
##  Recommended Notes and References


- [[Fundamental Subspaces from Linear Map and its Projection]]
- [[Singular Value Decomposition of Linear Map]]
- [[Range and Kernel of Linear Map]]
- [[Projection Map onto Linear Subspace]]
- [[Orthogonal Complement of Hilbert Spaces]]



- [[Matrix Analysis by Horn]]
- [[Matrix Computations by Golub]] pp 82
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 36