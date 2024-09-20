---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
keywords:
  - range_linear
  - kernel_linear
  - normal_transform
topics:
  - matrix_analysis
  - linear_algebra
name: Range and Kernel of Product Map and Normal Map
date of note: 2024-09-20
---

## Concept Definition

>[!important]
>**Name**: Range and Kernel of Product Map and Normal Map

![[Range and Kernel of Linear Map#^e3c09c]]

 ![[Range and Kernel of Linear Map#^50b63e]]

>[!important] Proposition
>Let $A\in \mathbb{R}^{m\times n}$, $B\in \mathbb{R}^{n\times p}$.
>
>Then
>- $$\text{R}(A\,B) \subseteq \text{R}(A).$$
>- $$\text{Ker}(A\,B) \supseteq \text{Ker}(B).$$
>- $$\text{R}((A\,B)^{*}) \subseteq \text{R}(B^{*}).$$
>- $$\text{Ker}((A\,B)^{*}) \supseteq \text{Ker}(A^{*}).$$

^7125e4

- [[Fundamental Subspaces from Linear Map and its Projection]]
- [[Range and Kernel of Linear Map]]
- [[Normal Transformation]]

### Range and Kernel of Normal Transformation 

![[Normal Transformation#^8471b1]]

>[!important] Proposition
>Let $A\in \mathbb{R}^{m\times n}$.
>
>Then 
>-  the **range** of **normal transformation** $A\,A^{*}$ is equal to the **range** of $A$ $$\text{R}(A\,A^{*}) = \text{R}(A).$$
>- the **range** of **normal transformation**  $A^{*}\,A$ is equal to the **range** of $A^{*}$ $$\text{R}(A^{*}\,A) = \text{R}(A^{*}).$$
>- the **kernel** of **normal transformation**  $A\,A^{*}$ is equal to the **kernel** of $A^{*}$ $$\text{Ker}(A\,A^{*}) = \text{Ker}(A^{*}).$$
>- the **kernel** of **normal transformation** $A^{*}\,A$ is equal to the **kernel** of $A$$$\text{Ker}(A^{*}\,A) = \text{Ker}(A).$$

- [[Normal Transformation]]
- [[Least Square Estimation Solution and Geometric Interpretation]]
- [[Existence and Uniqueness of Solution of Linear Equations]]
- [[Moore–Penrose Pseudo Inverse of Matrix]]


## Explanation




-----------
##  Recommended Notes and References



- [[System of Linear Equations or Linear System]]
- [[Singular Value Decomposition of Linear Map]]

- [[Rank–Nullity Theorem]]
- [[Rank and Nullity of Linear Map]]
- [[Range and Kernel of Linear Map]]
- [[Moore–Penrose Pseudo Inverse of Matrix]]

- [[Linear Subspace]]
- [[Normal Transformation]]
- [[Matrix]]
- [[Linear Map]]
- [[Vector Space over a Field]]



- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 25