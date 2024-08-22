---
tags:
  - concept
  - math/linear_algebra
  - math/functional_analysis
keywords:
  - dual_basis
topics:
  - linear_algebra
  - functional_analysis
name: Dual Basis
date of note: 2024-05-16
---

## Concept Definition

>[!important]
>**Name**: Dual Basis

>[!important] Theorem
>Let $V$ be a $n$-dimensional vector space, and $(\epsilon_{1} \,{,}\ldots{,}\, \epsilon_{n})$ is a *basis* in $V$. Let $(\alpha_{1} \,{,}\ldots{,}\, \alpha_{n})$ be any set of $n$ scalars in $F$.
>
>Then there exists *one and only one* **linear functional** $A$ on $V$ such that 
>$$
>\left\langle  A\,,\,\epsilon_{i}    \right\rangle = \alpha_{i}, \quad i=1 \,{,}\ldots{,}\,n.
>$$
>where $\left\langle  \cdot\,,\, \cdot   \right\rangle: V^{*} \times V \to F$ is the **canonical dual pair**.

- [[Linear Map]]
- [[Basis of Vector Space]]
- [[Dual Space of Finite Dimensional Vector Space]]
- [[Canonical Dual Pairing]]

>[!important] Theorem
>Let $V$ be a $n$-dimensional vector space, and $E := (\epsilon_{1} \,{,}\ldots{,}\, \epsilon_{n})$ is a *basis* in $V$. 
>
>Then there exists a **uniquely determined basis** $E^{*} = (\omega^{1} \,{,}\ldots{,}\, \omega^{n})$ on $V^{*}$  such that 
>$$
>\left\langle \omega^{j}\,,\,\epsilon_{i}    \right\rangle = \delta_{i,j}, \quad i=1 \,{,}\ldots{,}\,n.
>$$
>where $\left\langle  \cdot\,,\, \cdot   \right\rangle: V^{*} \times V \to F$ is the **canonical dual pair**.
>
>Consequently, the **dual space** of an $n$-dimensional space is **$n$-dimensional**.

- [[Dual Space of Finite Dimensional Vector Space]]

>[!important] Definition
>The basis $E^{*}$ is called **the dual basis** of $E$.


## Explanation





-----------
##  Recommended Notes and References

- [[Vector Space over a Field]]
- [[Basis of Vector Space]]
- [[Covector Space]]


- [[Finite Dimensional Vector Spaces by Halmos]]