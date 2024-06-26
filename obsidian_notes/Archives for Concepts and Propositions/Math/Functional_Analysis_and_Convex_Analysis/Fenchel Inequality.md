---
tags:
  - concept
  - math/convex_analysis
  - optimization/theory
  - statistics/concentration_inequality
keywords:
  - fenchel_young_inequality
topics:
  - convex_analysis
  - optimization
name: Fenchel Inequality
date of note: 2024-05-14
---

## Concept Definition

>[!important]
>**Name**: Fenchel's Inequality


>[!important]
>Let $X$ be a real *topological vector space*, and $X^{*}$ be the *dual space* of $X$. 
>
>Define a function $f: X \to \mathbb{R}$ and $f^{*}$ is its *convex conjugate* function $f^{*}: X^{*} \to \mathbb{R}$. 
>$$
>f^{*}(p) := \sup_{x \in X}\left\{ \left\langle p,x\right\rangle - f(x) \right\}, 
>$$
>where $\left\langle  \cdot\,,\, \cdot   \right\rangle: X^{*} \times X \to \mathbb{R}$ is the *canonical dual pairing*:
>$$
>\left\langle  p\,,\, x   \right\rangle := p(x).
>$$
>
>The **Fenchel's inequality** (also known as the **Fenchel–Young inequality**) states that
>$$
>f(x) + f^{*}(p) \ge \left\langle p\,,\, x   \right\rangle, \quad \forall x\in X, \; p \in X^{*}
>$$
>
>Furthermore, the *equality* holds only when $p \in \partial f(x).$


- [[Convex Conjugate Function]]
- [[Canonical Dual Pairing]]


## Explanation





-----------
##  Recommended Notes and References

