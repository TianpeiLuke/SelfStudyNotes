---
tags:
  - concept
  - math/linear_algebra
keywords:
  - dual_space
  - annihilator
topics:
  - linear_algebra
name: Annihilator of Subset of Vector Space
date of note: 2024-05-26
---

## Concept Definition

>[!important]
>**Name**: Annihilator of Subset of Vector Space

>[!important] Definition
>The **annihilator** $S^{0}$ of any subset $S$ of a vector space $V$ is the set of all vectors (i.e. *covectors*) $h$  in the *dual* of $V$, $V^{*}$,  such that
>$$
>\left\langle  h\,,\, x   \right\rangle := h(x) = 0, \quad \forall x \in S.
>$$
>where $\left\langle  \cdot\,,\, \cdot \right\rangle: V^{*} \times V \to \mathbb{R}$ is the *canonical dual pair*.
>
>That is,
>$$
>S^{0} := \left\{ h \in V^{*}: \left\langle  h\,,\, x   \right\rangle = 0, \quad \forall x \in S. \right\} 
>$$


- [[Dual Space of Finite Dimensional Vector Space]]
- [[Covector on Vector Space]]
- [[Covector Space]]
- [[Canonical Dual Pairing]]

## Explanation

>[!info]
>$S$ need **not to be subspace**.

>[!info]
>If the kernel of $A$ contains $S$
>$$
>\text{ker}(A) = \{ v \in V: Av = 0 \} \supseteq S
>$$
>then $A$ is in the annihilator of $S$
>$$
>A \in S^{0}
>$$

- [[Range and Kernel of Linear Map]]

## Property

>[!important] Proposition 
>If $S$ is an **$m$-dimensional** *subspace* of an $n$-dimensional vector space $V$, then $S^{0}$ is an **$(n-m)$-dimensional subspace** of $V$



-----------
##  Recommended Notes and References


- [[Dual Space of Finite Dimensional Vector Space]]
- [[Covector on Vector Space]]
- [[Covector Space]]

- [[Vector Space over a Field]]


- [[Matrix Analysis by Horn]]
- [[Finite Dimensional Vector Spaces by Halmos]]