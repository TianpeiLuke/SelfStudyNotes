---
tags:
  - concept
  - math/measure_theory
keywords:
  - sigma_field
topics:
  - measure_theory
name: sigma field
date of note: 2024-04-18
---

## Concept Definition

>[!important]
>**Name**:  $\sigma$-Algebra


>[!important] Defintion
> Given space $\mathcal{X}$, a ***$\sigma$-field*** (or, *$\sigma$-algebra*} $\mathscr{F}$ is a non-empty collection of *subsets* in $\mathcal{X}$ such that :
> 1. $\emptyset \in \mathscr F$; $\mathcal X \in \mathscr F$;
> 2. **Complements**:  For any $B\in \mathscr F$, then $B^{c} \equiv (\mathcal X - B) \in \mathscr F$;
> 3. **Countable union**: for any *sub-collection* $\set{B_{k}}_{k=1}^{\infty} \subset \mathscr F$, 
> $$
> \bigcup_{k=1}^{\infty}B_{k} \in \mathscr F;
> $$
> 
> 4. **Countable intersection**: by **de Morgan's law**, 
>    $$\bigcap_{k=1}^{\infty}B_{k} \in \mathscr F.$$  
> 
> We refer to the pair $(\mathcal{X}, \mathscr{F})$ of a set $\mathcal X$ *together* with a $\sigma$-algebra on that set as **a measurable space**.

- [[Set Operations]]
- [[Countable Set and Uncountable Set]]
- [[Indexed Family of Sets]]


>[!info]
>$\sigma$ usually denotes the **countable union**: e.g.
>- $\sigma$-field [[sigma Algebra]]
>- $\sigma$-compact topological spaces [[sigma-Compactness]]
>- $\sigma$-finite measure space [[Finite and sigma-Finite Measure]]
>- $\sigma$-locally finite [[Countably Locally Finiteness]]

- [[Countable Set and Uncountable Set]]

## Explanation

- $\sigma$-Algebra is an algebraic structure that concerns the closedness of measurable sets under countable union operation

## Examples

- [[Discrete Algebra]]
- [[Atomic Algebra]]
- [[Dyadic Algebra]]
- [[Lebesgue and Jordan and Null Algebra]]





-----------
##  Recommended Notes and References

- [[Countable Set and Uncountable Set]]

- [[Boolean Algebra]]
- [[Borel sigma Field]]
- [[Compare Sigma Field with Topology]]