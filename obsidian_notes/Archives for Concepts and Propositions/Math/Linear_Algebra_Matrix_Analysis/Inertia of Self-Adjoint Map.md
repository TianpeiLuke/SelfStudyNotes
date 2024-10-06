---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
keywords:
  - inertia_self_adjoint_map
  - sylvester_law_of_inertia
topics:
  - matrix_analysis
  - linear_algebra
name: Inertia of Self-Adjoint Map
date of note: 2024-09-24
---

## Concept Definition

>[!important]
>**Name**: Inertia of Self-Adjoint Map

>[!important] Definition
>Let $A\in M_{n}$ be *Hermitian*.
>
>The **inertia** of $A$ is the *ordered triple* $$i(A) = \left(i_{+}(A), i_{-}(A), i_{0}(A)\right)$$ in which 
>- $i_{+}(A)$ is the *number of positive eigenvalues* of $A$,
>- $i_{-}(A)$ is the *number of negative eigenvalues* of $A$,
>- $i_{0}(A)$ is the *number of zero eigenvalues* of $A$.
>  
>The **signature** of $A$ is the quantity $$i_{+}(A) - i_{-}(A).$$  

^8866a8

- [[Hermitian or Symmetric Matrix]]
- [[Eigenvalue and Eigenvector for Linear Map]]

>[!info]
>$$\text{rank}(A) = i_{+}(A) + i_{-}(A).$$

- [[Rank and Nullity of Linear Map]]

>[!important] Definition
>Let $A\in M_{n}$ be *Hermitian* and $\lambda_{1}\,{,}\ldots{,}\,\lambda_{n}$ be *eigenvalues*. Let the *eigendecomposition* of $A$ as $$A = U\Lambda U^{*}.$$
>
>Define a *real diagonal matrix* $D$ as
>$$D = \text{diag}(\underbrace{ \sqrt{\lambda_{1}} \,{,}\ldots{,}\,\sqrt{\lambda_{i_{+}(A)}} }_{ i_{+}(A)  \text{ entities}}, \underbrace{ \sqrt{-\lambda_{i_{+}(A)+1}} \,{,}\ldots{,}\, \sqrt{\lambda_{i_{+}(A) + i_{-}(A)}}}_{ i_{-}(A) \text{ entities} }, \underbrace{ 1\,{,}\ldots{,}\,1 }_{i_{0}(A) \text{ entities} } )$$
>Then $$\Lambda = D\,I(A)\,D$$ where $$I(A) = I_{i_{+}(A)} \oplus (-I_{i_{-}(A)}) \oplus 0_{i_{0}(A)} = \left[ \begin{array}{ccc}I_{i_{+}(A)} &  & \\ & -I_{i_{-}(A)} & \\ & & 0_{i_{0}(A)}\end{array} \right] $$ is called the **inertia matrix** of $A$.
>- We have $$A = U\Lambda U^{*} =  U  D\,I(A)\,D U^{*} = S\,I(A)\,S^{*}$$ where $S:= UD$ is nonsingular.

^9067ee


>[!important] Proposition
>Each **Hermitian matrix** $A$ is **$*$-congruent** to its **inertia matrix**.
>$$A = S\,I(A)\,S^{*}$$

^2f1958


## Explanation




## Sylvester Law of Inertia

![[Sylvester Law of Inertia#^901bbd]]

- [[Sylvester Law of Inertia]]



-----------
##  Recommended Notes and References


- [[Unitary Congruence Relation between Matrices]]






- [[Matrix Analysis by Horn]] pp 41, 280 - 282
- [[Matrix Analysis for Scientists and Engineers by Laub]] pp 103
- [[Matrix Computations by Golub]] pp 449