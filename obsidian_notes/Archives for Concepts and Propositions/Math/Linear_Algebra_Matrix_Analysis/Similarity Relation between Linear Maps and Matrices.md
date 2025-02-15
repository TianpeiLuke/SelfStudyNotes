---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
keywords:
  - similarity_relation_linear_map
topics:
  - matrix_analysis
  - linear_algebra
name: Similarity Relation between Linear Maps and Matrices
date of note: 2024-09-16
---

## Concept Definition

>[!important]
>**Name**: Similarity Relation between Linear Maps and Matrices

>[!important] Definition
>Let $A, B\in M_{n}$ be $n\times n$ matrix. 
>
>We say $A$ **is similar to** $B$ if there exists a *nonsingular* $S\in M_{n}$ such that 
>$$
> A = S\,B\,S^{-1}
>$$
>
>- The transformation $$B \to S\,B\,S^{-1}$$ is called a **similarity transformation** by the **similarity matrix** $S$
>- The similarity relation is represented as $$A \sim B$$

^5ebca6

- [[Surjective Injective Invertible Linear Map and Rank]]
- [[General Linear Group]]


>[!important] Definition
>Let $A, B\in M_{n}$ be $n\times n$ matrix. 
>
>We say that $B$ is **permutation similar to** $A$ if there exits a **permutation matrix** $P$ such that 
>$$
> B = P\,A\,P^{T}
>$$

- [[Permutation Matrix and Reversal Matrix]]
- [[Symmetric Group]]

## Explanation

>[!important]
>The **similarity relation** $\sim$ is an **equivalence relation**.

- [[Equivalence Relation]]

>[!important]
>Two **similar matrices** are the different **representations** of **same linear map** under **different basis**.

- [[Linear Map]]
- [[Basis of Vector Space]]
- [[Linear Isomorphism]]


## Characteristic Polynomial

>[!important] Proposition
>Let $A, B\in M_{n}$ be $n\times n$ matrix. 
>
>If $B$ is **similar** to $A$, then $A$ and $B$ have the same **characteristic polynomial**.
>$$
>B\sim A \implies P_{B} = P_{A}
>$$

- [[Characteristic Polynomial for Linear Map]]

## Eigenvalues

>[!important] Corollary
>Let $A, B\in M_{n}$ be $n\times n$ matrix and suppose that $A$ is **similar** to $B$. 
>
>Then  
>- $A$ and $B$ have the **same eigenvalues.**
>- If $B$ is a **diagonal matrix**, its main diagonal entries are the **eigenvalues** of $A$. 
>- $B = 0$ (a *diagonal matrix*) *if and only if* $A = 0$. 
>- $B = I$ (a *diagonal matrix*) *if and only if* $A = I$.

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Spectral Theorem of Normal Map and Eigen decomposition]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]

![[Eigenvalue and Eigenvector for Linear Map#^1a14c3]]

## Change of Basis




## Diagonalizable Matrix

- [[Diagonalizable Matrix]]

## Unitary Similarity

![[Unitary Similarity and Unitary Diagonalizable#^9aed0a]]

- [[Unitary Similarity and Unitary Diagonalizable]]



-----------
##  Recommended Notes and References


- [[Matrix]]
- [[Linear Map]]


- [[Equivalence Relation]]
- [[Equivalence Class]]


- [[Jordan Canonical Form]]
- [[Invariant under Change of Variable]]



- [[Matrix Analysis by Horn]] pp 57 - 59
- [[Matrix Analysis for Scientists and Engineers by Laub]]
- [[Finite Dimensional Vector Spaces by Halmos]]