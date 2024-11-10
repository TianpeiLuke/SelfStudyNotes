---
tags:
  - concept
  - math/matrix_analysis
  - math/differential_equation
  - math/linear_algebra
  - math/differential_geometry
  - math/lie_group_algebra
keywords:
  - matrix_exponential
  - matrix_logarithm
topics:
  - matrix_analysis
  - differential_equation
name: Matrix Logarithm
date of note: 2024-10-14
---

## Concept Definition

>[!important]
>**Name**: Matrix Logarithm

>[!important] Definition
>Let $A\in M_{n}$.
>
>The **matrix logarithm** of $A$ is defined to be the *inverse* of the *matrix exponential* , i.e. it is the  matrix $B$ that satisfies
>$$
> B = \log(A) \quad \iff \quad e^{B} = A
>$$
>- It can also be represented in terms of series $$\log(A) = - \sum_{k=1}^{\infty} \frac{\left(I - A\right)^{k}}{k}$$
>- The series *converges* if  $\lVert I -  A \rVert < 1$.


^437819

>[!important] Definition
>Let $A\in \mathcal{S}_{++}^{n}$ be a *symmetric positive definite matrix*, there exists a **unique logarithm** of $A$,  which is called the **principal logarithm** of $A$ i.e. $$\log(A)$$ 


- [[Space of Symmetric Positive Semidefinite Matrices]]


## Explanation

### Lie Group and Lie Algebra


- [[Exponential Map via Geodesic on Riemannian Manifold]]
- [[Lie Group]]
- [[Lie Algebra as Vector Space with Lie Bracket]]


## Properties

>[!important] Proposition
>Let $A\in M_{n}$, $s, t\in \mathbb{R}$.
>- If $A\in \mathcal{S}_{++}^{n}$ is **positive definite**, then $$\log(\det(A)) = \text{tr}(\log(A))$$
>- If $A, B\in \mathcal{S}_{++}^{n}$ are **positive definite**, then $$\text{tr}\left(\log(A\,B)\right) = \text{tr}\left(\log(A)\right) + \text{tr}\left(\log(B)\right)$$
>- If $A, B\in \mathcal{S}_{++}^{n}$ are **positive definite**, and $A,B$ **commute** i.e. $$AB = BA$$ then $$\log(AB) = \log(A) + \log(B)$$

- [[Trace of Matrix]]
- [[Determinant of Linear Transformation]]
- [[Space of Symmetric Positive Semidefinite Matrices]]

## Non-uniqueness of Matrix Logarithm






-----------
##  Recommended Notes and References


- [[Exponential Map of Linear Operator]]
- [[Jordan Canonical Form]]
- [[Continuous Functional Calculus]]

- [[Lie Group]]
- [[Lie Algebra as Vector Space with Lie Bracket]]
- [[Log-Euclidean Riemannian Metric in Space of Symmetric Positive Definite Matrices]]
- [[Affine Invariant Riemannian Metric in Space of Symmetric Positive Definite Matrices]]


- [[Matrix Analysis by Horn]]
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 109 - 114
- [[Lie Groups Lie Algebra and Representations by Hall]] pp 31 - 45
- [[Introduction to Smooth Manifolds by Lee]] pp 517
- Wikipedia [Logarithm_of_a_matrix](https://en.wikipedia.org/wiki/Logarithm_of_a_matrix)