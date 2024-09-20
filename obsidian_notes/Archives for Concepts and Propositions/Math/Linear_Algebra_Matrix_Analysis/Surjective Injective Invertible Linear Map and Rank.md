---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
keywords:
  - surjective_linear_map
  - injective_linear_map
  - invertible_linear_map
topics:
  - matrix_analysis
  - linear_algebra
name: Surjective Injective Invertible Linear Map and Rank
date of note: 2024-09-20
---

## Concept Definition

>[!important]
>**Name**: Surjective Injective Invertible Linear Map and Rank

>[!important] Definition
>Let $A: V \to W$ where $V$, $W$ are $n$-dimensional and $m$-dimensional vector spaces.
>
>- $A$ is said to have **full row rank** if the matrix representation $A$ has *linear independent rows* 
>- $A$ is said to have **full column rank** if the matrix representation $A$ has *linear independent columns* 

- [[Linear Map]]
- [[Rank and Nullity of Linear Map]]


>[!important] Theorem
>Let $A: V \to W$ where $V$, $W$ are $n$-dimensional and $m$-dimensional vector spaces.
>
>Then 
>- $A$ is **surjective** (**onto**) *if and only if* $$\text{rank}(A) = m$$ i.e. the matrix $A$ has *linear independent rows* or is said to have **full row rank** 
>	- $$A \text{ has full row rank } \iff A\,A^{*} \text{ singular}$$
>- $A$ is **injective** (**1-1**) *if and only if* $$\text{rank}(A) = n$$ i.e. the matrix $A$ has *linear independent columns* or is said to have **full column rank** 
>	- $$A \text{ has full column rank } \iff A^{*}\,A\text{ singular}$$

^5ba812

- [[Surjective Function]]
- [[Injective Function]]

>[!important] Definition
>A linear map $A: V \to W$ is **invertible** or **bijective** if and only if it is *surjective* and *injective*.
>
>The matrix $A$ of *invertible linear map* is said to be **non-singular**.

- [[Bijective Function and Inverse Function]]
- [[General Linear Group]]

>[!important] Proposition
>A linear map  $A: V \to W$ is **invertible** if and only if $$\text{dim}(V) = \text{dim}(W).$$
>
>Also the matrix $A\in \mathbb{R}^{n\times n}$ is **non-singular** if and only if $$\text{rank}(A) = n.$$


## Explanation



## Left Invertible and Right Invertible


- [[Moore–Penrose Pseudo Inverse of Matrix]]



-----------
##  Recommended Notes and References


- [[Range and Kernel of Product Map and Normal Map]]
- [[Rank–Nullity Theorem]]
- [[Rank and Nullity of Linear Map]]
- [[Range and Kernel of Linear Map]]
- [[Moore–Penrose Pseudo Inverse of Matrix]]

- [[Linear Subspace]]
- [[Normal Transformation]]
- [[Matrix]]
- [[Matrix Transformation]]
- [[Linear Map]]
- [[Vector Space over a Field]]


- [[Matrix Analysis by Horn]]
- [[Matrix Computations by Golub]]
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 25 - 26
- [[Finite Dimensional Vector Spaces by Halmos]]