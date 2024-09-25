---
tags:
  - concept
  - math/linear_algebra
  - math/matrix_analysis
keywords:
  - adjugate_matrix
  - cofactor_matrix
topics:
  - matrix_analysis
  - linear_algebra
name: Adjugate of Matrix
date of note: 2024-09-23
---

## Concept Definition

>[!important]
>**Name**: Adjugate of Matrix

![[Partition of Matrix and Block Matrix#^91291d]]

![[Minor and Principal Minor#^b43d82]]


>[!important] Definition
>Let $A\in M_{n}(F)$ and $n \ge 2$. 
>
>The **adjugate** of $A$ is defined as the *transposed matrix* of *cofactors* of $A$, i.e. $$\text{adj}(A) = \left[ (-1)^{i+j}\,\det\left(A\left[ j^{c}, i^c \right]   \right) \right].$$
>It is also called the **classical adjoint** of $A$.

^8344b6

- [[Partition of Matrix and Block Matrix]]
- [[Minor and Principal Minor]]
- [[Adjoint of Linear Map]]

## Explanation




## Determinant

![[Laplace Expansion Theorem#^b65d26]]

>[!important] Proposition (Identity of Adjugate)
>The **Laplace expansion for determinant** reveals the basic property of adjugate 
>$$
>\begin{align*}
>(\text{adj}(A))\,A = A\,(\text{adj}(A)) = \det(A)\,I.
>\end{align*}
>$$

^b4ad1a

- [[Laplace Expansion Theorem]]
- [[Determinant of Linear Transformation]]

>[!important] Proposition
>If $A$ is **nonsingular**, then $\text{adj}(A)$ is **nonsingular**. 
>
>And the **determinant of adjugate** of $A$ is $$\det\left(\text{adj}(A)\right) = \left( \det(A) \right)^{n-1}.$$

- [[Surjective Injective Invertible Linear Map and Rank]]

### Inverse

>[!important] Corollary
>If $A$ is **nonsingular**, then 
>$$
>\text{adj}(A) = \left( \det(A) \right)\,A^{-1}.
>$$
>Thus, the **inverse** $A^{-1}$ is given by
>$$
>A^{-1} = \left( \det(A) \right)^{-1}\,\text{adj}(A).
>$$


## Gradient of Determinant

>[!important] Proposition
>Let $A\in M_{n}$.
>
>The **adjugate** of $A$ is the **transpose of gradient of $\det A$**
>$$
> \text{adj}(A) = \left( \frac{ \partial  }{ \partial A } \det(A) \right)^{T}
>$$ 






-----------
##  Recommended Notes and References


- [[Cramer Rule]]
- [[Partition of Matrix and Block Matrix]]
- [[Determinant of Linear Transformation]]
- [[Matrix]]

- [[Matrix Analysis by Horn]] pp 22- 24