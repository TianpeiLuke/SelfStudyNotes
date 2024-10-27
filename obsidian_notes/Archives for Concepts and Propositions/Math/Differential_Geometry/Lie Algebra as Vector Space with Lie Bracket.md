---
tags:
  - concept
  - math/differential_geometry
  - math/algebra
  - math/linear_algebra
  - math/lie_group_algebra
keywords:
  - lie_algebra
  - lie_group
  - lie_bracket
topics:
  - differential_geometry
  - algebra
  - linear_algebra
name: Lie Algebra associated with Lie Group
date of note: 2024-10-27
---

## Concept Definition

>[!important]
>**Name**: Lie Algebra associated with Lie Group

![[Algebra over Field#^60bc18]]

- [[Algebra over Field]]

>[!important] Definition
>A **finite-dimensional real or complex Lie algebra** is 
>- a finite-dimensional real or complex *vector space* $\mathfrak{g}$, 
>- together with a *map* $[\cdot,\cdot]: \mathfrak{g} \times \mathfrak{g} \to \mathfrak{g}$, with the following properties:
>	- $[\cdot,\cdot]$ is **bilinear**: $$\begin{align*} [a X_{1} + b X_{2}, Y] &= a [X_{1}, Y] + b [ X_{2}, Y] \\[5pt] [X, a Y_{1} + b Y_{2}] &= a [X, Y_{1}] + b [ X, Y_{2}] \end{align*}$$ for any $X,Y, X_{1}, X_{2}, Y_{1}, Y_{2}\in \mathfrak{g}$ and any scalar $a,b\in \mathbb{C}$ or $\mathbb{R}$  
>	-  $[\cdot,\cdot]$ is **skew-symmetric**: $$[X, Y] = - [Y, X]$$ for any $X,Y\in \mathfrak{g}$
>	- The **Jacobi identity** holds: $$[X, [Y, Z]] + [Y, [Z, X]] + [Z, [X, Y]] = 0$$  for any $X,Y, Z\in \mathfrak{g}$
>	
>The map $[\cdot, \cdot]$ is referred to as the **Lie bracket** or simply the **bracket** on $\mathfrak{g}$.   

^cd013a

- [[Vector Space over a Field]]
- [[Lie Bracket of Vector Fields]]
- [[Multilinear Function]]
- [[Skew-Hermitian and Skew-Symmetric Matrix]]

>[!important] Definition
>Two elements $X, Y$ of a *Lie algebra* $\mathfrak{g}$ **commute** if $$[X, Y] = 0$$

>[!important] Definition
>A **Lie algebra** $\mathfrak{g}$ is **commutative** if $$[X, Y] = 0, \quad \forall X, Y \in \mathfrak{g}.$$

- [[Commutative Ring]]
- [[Commutative Ring Algebra]]

## Explanation

>[!important] 
>The **Lie bracket** on $\mathfrak{g}$ is in general **not associative.**

- [[Group]]




-----------
##  Recommended Notes and References



- [[Lie Group]]

- [[Tangent Bundle]]
- [[Tangent Space Definition and Development]]
- [[Smooth Manifold]]
- [[Group]]
- [[Topological Group]]


- [[Introduction to Smooth Manifolds by Lee]] pp 191 - 202
- [[Lie Groups Lie Algebra and Representations by Hall]] pp 49