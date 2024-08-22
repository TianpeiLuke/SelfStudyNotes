---
tags:
  - concept
  - math/linear_algebra
  - optimization/theory
keywords:
  - conjugate_vector_positive_definite
topics:
  - linear_algebra
  - optimization/theory
name: Conjugate Vector wrt Positive Definite Matrix
date of note: 2024-07-03
---

## Concept Definition

>[!important]
>**Name**: Conjugate Vector with respect to Positive Definite Matrix

>[!important] Definition
>Let $V$ be a *finite-dimensional inner product space* and $A \in L(V)$ is a **self-adjoint positive definite linear transformation**
>
>A set of vectors $\{ d_{1} \,{,}\ldots{,}\, d_{k}\}$ in $V$ is said to be **conjugate** *with respect to* $A$ (or **$A$-conjugate**) if
>$$
>\left\langle  A\,d_{i}\,,\, d_{j}  \right\rangle = 0, \quad \forall i \neq j \in \{ 1 \,{,}\ldots{,}\,k \}
>$$

- [[Positive Semidefinite Transformation]]
- [[Self-Adjoint Linear Map]]
- [[Inner Product Space]]

>[!important] Definition (Matrix Version)
>Let $\boldsymbol{A} \in \mathbb{R}^{n\times n}$ be a **symmetric positive definite matrix**
>
>A set of vectors $\{ \boldsymbol{d}_{1} \,{,}\ldots{,}\, \boldsymbol{d}_{k}\}$ in $\mathbb{R}^n$ is said to be **conjugate** *with respect to* $\boldsymbol{A}$ if
>$$
> \boldsymbol{d}_{i}^T\boldsymbol{A}\,\boldsymbol{d}_{j} = 0, \quad \forall i \neq j \in \{ 1 \,{,}\ldots{,}\,k \}
>$$

## Explanation

>[!info]
>The concept of *conjugate vector* with respect to *positive semi-definite transform* is equivalent to **orthogonality** under an **inner product space induced by $A$** 
>$$
>\left\langle  x\,,\, y   \right\rangle_{A} := \left\langle  A x\,,\,y    \right\rangle
>$$
>The **positive definiteness** of $A$ guarantees the **positive definiteness** of inner product
>$$
>\left\langle  x\,,\, x \right\rangle_{A} \ge 0\; 
>$$
>with *equality* holds *if and only if* $x=0.$

- [[Inner Product Space]]


## Linear Independence


>[!important] Proposition
>Let $V$ be a *finite-dimensional inner product space* and $A \in L(V)$ is a **self-adjoint positive definite linear transformation.**
>
>If  $\{ d_{1} \,{,}\ldots{,}\, d_{k}\}$ is **conjugate** *with respect to* $A$ then $\{ d_{1} \,{,}\ldots{,}\, d_{k}\}$ are **linearly independent**.

- [[Linear Independence]]





-----------
##  Recommended Notes and References



- [[Vector Space over a Field]]

- [[Numerical Optimization by Nocedal]] pp 103
- [[Nonlinear Programming by Bertsekas]] pp 131