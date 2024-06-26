---
tags:
  - concept
  - math/measure_theory
keywords:
  - intuitive_axioms_of_measure
topics:
  - measure_theory
name: intuitive axioms of measure
date of note: 2024-05-07
---

## Concept Definition

>[!important]
>**Name**:  Intuitive Axioms of Measure on any Subsets

>[!info]
>The basic **motivation**:
>- an extension of  *measure* $m(E)$ in $\mathbb{R}^{1}, \mathbb{R}^{2}, \mathbb{R}^{3}$ as *length, area and volume* of a geometric body $E$. 


>[!info] Intuitive Axioms of Measure on any subsets
> A set of *intuitive axioms* for a measure function $m$ defined on power set $2^{\mathbb{R}}$: 
> 
> 1. The **unit length**of interval: $E= (0,1]$, then $m((0,1]) = 1$;
> 2. If $E$ is **congruent** to $F$: (There exists a proper *translation, rotation or reflection* from $E$ to $F$), then $m(E) = m(F)$;
> 3. The **countably additive**: for a countable union of disjoint sets, $\bigcup_{k=1}^{\infty}E_{k}$, the measure 
> $$
> \begin{align*}
> m\left(\bigcup_{k=1}^{\infty}E_{k}\right) &= \bigcup_{k=1}^{\infty}m\left(E_{k}\right)
> \end{align*}
> $$

>[!important]
>Unfortunately, **these three axioms are inconsistent**: 
>- **no proper definition** of measure function $m$ could satisfies **all these three axioms** for **any subset** in $\mathbb{R}$. 
>- The measure theory should be built on a collection of *"ordinary" subsets*, which motivates the introduction of  **$\sigma$-algebra**. 

- [[sigma Algebra]]

## Explanation






-----------
##  Recommended Notes and References

- [[Measure Space and Countably Additive Measure]]
- [[Finite and sigma-Finite Measure]]