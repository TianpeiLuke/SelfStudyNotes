---
tags:
  - concept
  - math/functional_analysis
keywords:
  - singular_value_decompositino
  - compact_operator
topics:
  - functional_analysis
name: Singular Value Decomposition of Compact Operator
date of note: 2024-05-29
---

## Concept Definition

>[!important]
>**Name**: Singular Value Decomposition of Compact Operator

![[Singular Value Decomposition of Linear Map#^bebe11]]

- [[Singular Value Decomposition of Linear Map]]

>[!important] Theorem (Canonical Form of Compact Operator)
>Let $A$ be a **compact operator** on $\mathcal{H}$. 
>
>Then there exist 
>- (*not necessarily complete*) **orthonormal sets** $\{\psi_n\}_{n=1}^{N}$ and 
>- $\{\phi_n\}_{n=1}^{N}$ and
>- **positive** *real numbers* $\{\sigma_n\}_{n=1}^{N}$ with $$\sigma_n \rightarrow 0$$ 
>
>so that 
>$$
> \begin{align}
> A &= \sum_{n=1}^{N}\sigma_n\,\left\langle \cdot , \psi_{n} \right\rangle\,\phi_n 
> \end{align}
>$$ 
>
>The sum, which may be finite or infinite, **converges in norm**. 

- [[Compact Operator]]
- [[Hilbert-Schmidt Theorem for Compact Self-Adjoint Operator]]



>[!important] Definition
>The numbers, $\{\lambda_n\}_{n=1}^{N}$, in 
>$$
>A = \sum_{n=1}^{N}\sigma_n\,\left\langle \cdot , \psi_{n} \right\rangle\,\phi_n 
>$$
>are called the **singular values** of $A$. 


## Explanation


>[!info]
>For finite dimension space, we have **singular value decomposition**
>$$
>\boldsymbol{ A } = \sum_{n=1}^{N}\sigma_{n}\,\boldsymbol{\phi}_{n}\,\boldsymbol{\psi}_{n}^{*}
>$$





-----------
##  Recommended Notes and References

- [[Hilbert-Schmidt Theorem for Compact Self-Adjoint Operator]]
- [[Complete Orthonormal Basis of Hilbert Space]]
- [[Hilbert Space]]


- [[Functional Analysis by Reed]]