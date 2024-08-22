---
tags:
  - concept
  - math/linear_algebra
  - math/functional_analysis
keywords:
  - dual_space_finite_dimensional
topics:
  - linear_algebra
  - functional_analysis
name: Dual Space of Finite Dimensional Vector Space
date of note: 2024-05-16
---

## Concept Definition

>[!important]
>**Name**: Dual Space of Finite Dimensional Vector Space

>[!info] Definition
>Let $V$ and $W$ be vector spaces over the same field $F$,  $\varphi: V \to W$ is a **linear map** if it preserve *the linear operations*, i.e.
> 
> - **Additivity**: preservation of *vector addition operation*
>$$
>\begin{align*}
>\varphi(x + y) &= \varphi(x) + \varphi(y), \quad \forall x, y \in V\\
> \end{align*}
>$$
> 
> - **Homogeneity**: preservation of *scalar product operation*
>$$
>\begin{align*}
>\varphi(\lambda x) &= \lambda \varphi(x), \quad \forall \lambda \in F, x\in V 
> \end{align*}
>$$

- [[Linear Map]]
- [[Vector Space over a Field]]
- [[Bounded Linear Operator and Norm of Operator]]
- [[Bounded Linear Functional]]

>[!important]
>The space of **all linear maps (linear functionals)** on a vector space $V$ forms a vector space, which is called the **dual space** of  $V$, denoted $V^{*}$.

- [[Dual Normed Space and Dual Banach Space]]
- [[Covector Space]]


## Explanation

>[!info]
>The dual space of vector space is also called a **covector space**. 
>
>In differential geometry, the covector space is used often for dual space of the tangent space. 





-----------
##  Recommended Notes and References


- [[Vector Space over a Field]]


- [[Finite Dimensional Vector Spaces by Halmos]]
- [[Matrix Analysis by Horn]]