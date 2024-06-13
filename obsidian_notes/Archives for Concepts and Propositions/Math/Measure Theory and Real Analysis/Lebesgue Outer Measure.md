---
tags:
  - concept
  - math/measure_theory
keywords:
  - lebesgue_outer_measure
topics:
  - measure_theory
name: Lebesgue outer measure
date of note: 2024-05-07
---

## Concept Definition

>[!important]
>**Name**:  Lebesgue Outer Measure $m^{*}$


>[!important] Definition
>Define the **Lebesgue outer measure** as
> $$
>  \begin{align}
>  m^{*}(E) &= \inf\limits_{E \subseteq \cup_{k=1}^{\infty}G_{k}, \atop {\forall G_{k}\in \mathscr{A}_{0}}}\sum_{k=1}^{\infty}m(G_{k})
>  \end{align} 
>  $$

>[!info]
 >- That is, if $E$ has **a countable covering of elementary sets** $\left\{G_k\right\}  \subset \mathscr{A}_{0}$, then **the Lebesgue outer measure** is the **infimum** of *the countable sum* of *the elementary measures* of these sets. 
 >- Here *the countable sum* is defined as the *supremum* over $k\ge 1$ of the $k$-summation 
>$$ 
> \begin{align*}
> \sum_{n=1}^{\infty}a_{n} &= \sup_{k\ge 1}\sum_{n=1}^{k}a_{n}
> \end{align*}
>$$


## Explanation






-----------
##  Recommended Notes and References

- [[Elementary Measure]]
- [[Jordan Measure]]