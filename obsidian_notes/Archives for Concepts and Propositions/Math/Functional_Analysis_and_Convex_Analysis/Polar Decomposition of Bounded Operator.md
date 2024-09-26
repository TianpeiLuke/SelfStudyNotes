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
> A = U \;\lvert A \rvert 
> \end{align*}
>$$
> 
>$U$ is **uniquely determined** by the condition that $$\text{Ker}(U) = \text{Ker}(A).$$  Moreover, $$\text{R}(U) = \overline{\text{R}(A)}.$$ 

- [[Partial Isometry]]
- [[Square Root of Positive Semidefinite Operator and Absolute Value]]
- [[Range and Kernel of Linear Operator]]


>[!important] Definition
>Let $\mathcal{H}$ be a Hilbert space and $A\in \mathcal{L}(\mathcal{H})$ be a bounded linear operator on $\mathcal{H}$.
>
>The **polar decomposition** of $A$ is given by $$A= U\;|A|$$ where $|A| = \sqrt{ A^{*}A }$ is the *absolute value* of $A$, and $U$ is a *partial isometry*. 


## Explanation





-----------
##  Recommended Notes and References



- [[Polar Decomposition of Transformation]]
- [[Positive Semidefinite Operator]]




- [[Matrix Analysis by Horn]]
- [[Matrix Computations by Golub]]
- [[Functional Analysis by Reed]]