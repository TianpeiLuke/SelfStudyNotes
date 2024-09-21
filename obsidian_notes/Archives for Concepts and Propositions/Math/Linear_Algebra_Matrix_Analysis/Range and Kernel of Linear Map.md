---
tags:
  - concept
  - math/linear_algebra
keywords:
  - kernel_linear
  - image_linear
topics:
  - linear_algebra
name: Kernel and Image of Linear Map
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Kernel and Image of Linear Map

>[!important] Definition
>If $A$ is a linear transformation on a vector space $V$ and if $S$ is a *subspace* of $V$, then the **image** *of* $S$ *under* $A$ is the set of all $Av$ for $v \in S$:
>$$
>A(S) := \left\{ Av: v\in S \right\} 
>$$ 


>[!important] Definition
>The **range** or **image** of linear map $A: V \to W$ is defined as
>$$
>\text{R}(A) := \text{Im}(A) := A(V) = \left\{ Av: v\in V \right\} 
>$$

^e3c09c

- [[Image of Group Homomorphism]]


>[!important] Definition
>The **kernel** or **null-space** of linear map $A: V \to W$ is defined as
>$$
>\text{Ker}(A) := \text{N}(A) := \left\{v\in V: Av = 0 \right\} 
>$$

^50b63e

- [[Kernel of Group Homomorphism]]

## Explanation

>[!info]
>- The *kernel* of $A$ is a linear **subspace** in the **domain** of $A$, i..e $V$. 
>- The *range* of $A$ is a linear **subspace** in the **codomain** of $A$, i.e. $W$.

- [[Linear Subspace]]


## Range and Kernel of Product 

![[Range and Kernel of Product Map and Normal Map#^7125e4]]

- [[Range and Kernel of Product Map and Normal Map]]



-----------
##  Recommended Notes and References

- [[Linear Map]]
- [[Vector Space over a Field]]

- [[Kernel of Group Homomorphism]]
- [[Image of Group Homomorphism]]


- [[Rank and Nullity of Linear Map]]
- [[Rank–Nullity Theorem]]
- [[Fundamental Subspaces from Linear Map]]
- [[Singular Value Decomposition and Fundamental Subspaces]]


- [[Matrix Analysis by Horn]]
- [[Finite Dimensional Vector Spaces by Halmos]] pp 88