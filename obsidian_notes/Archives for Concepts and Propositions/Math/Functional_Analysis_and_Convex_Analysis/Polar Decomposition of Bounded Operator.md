---
tags:
  - concept
  - math/matrix_analysis
  - math/linear_algebra
  - math/functional_analysis
keywords:
  - polar_decomposition_operator
topics:
  - functional_analysis
name: Polar Decomposition of Bounded Operator
date of note: 2024-09-24
---

## Concept Definition

>[!important]
>**Name**: Polar Decomposition of Bounded Operator

![[Square Root of Positive Semidefinite Operator and Absolute Value#^b24042]]

![[Partial Isometry#^257335]]

>[!important] Theorem
>Let $A$ be a bounded linear operator on a *Hilbert space*. 
>
>Then there is a **partial isometry** $U$ such that 
>$$
> \begin{align*}
> A = U\,P
> \end{align*}
>$$
>where 
>- $P$ is a **positive semi-definite operator** and $$P = \sqrt{ A^{*}A } := \lvert A \rvert $$
>- $U$ is **uniquely determined** by the condition that $$\text{Ker}(U) = \text{Ker}(A).$$  
>- Moreover, $$\text{R}(U) = \overline{\text{R}(A)}.$$ 

^7e985f

- [[Partial Isometry]]
- [[Positive Semidefinite Operator]]
- [[Square Root of Positive Semidefinite Operator and Absolute Value]]
- [[Range and Kernel of Linear Operator]]


>[!important] Definition
>Let $\mathcal{H}$ be a Hilbert space and $A\in \mathcal{L}(\mathcal{H})$ be a bounded linear operator on $\mathcal{H}$.
>
>The **polar decomposition** of $A$ is given by $$A= U\;|A|$$ where $|A| = \sqrt{ A^{*}A }$ is the *absolute value* of $A$, and $U$ is a *partial isometry*. 


## Explanation


## Polar Decomposition for Linear Map on Finite-Dimensional Space

![[Polar Decomposition of Transformation#^636e45]]

- [[Polar Decomposition of Transformation]]


-----------
##  Recommended Notes and References



- [[Polar Decomposition of Transformation]]
- [[Positive Semidefinite Operator]]




- [[Matrix Analysis by Horn]]
- [[Matrix Computations by Golub]]
- [[Functional Analysis by Reed]]