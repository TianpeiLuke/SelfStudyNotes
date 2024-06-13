---
tags:
  - concept
  - math/measure_theory
keywords:
  - signed_measure
topics:
  - measure_theory
name: signed measure
date of note: 2024-05-07
---

## Concept Definition

>[!important]
>**Name**: Signed Measure


>[!important] Defintion
>Let $(X, \mathscr{B})$ be a *measurable space*. A **signed measure** $\nu$ on $\mathscr{B}$, is a map $\nu: \mathscr{B} \rightarrow [-\infty, +\infty]$ that obeys the following axioms:
> 
> 1. **Empty set**: $\nu(\emptyset) = 0$.
> 2. **Finiteness in one direction**:  $\nu$ assumes at most one of the values $\pm \infty.$
> 3. **Countable additivity**: Whenever $E_1, E_2, \ldots \in \mathscr{B}$ are a *sequence* of *disjoint* sets in $\mathscr{B}$, then 
> $$
> \begin{align*}
> \nu\left(\bigcup_{n=1}^{\infty} E_n\right) &= \sum_{n=1}^{\infty} \nu(E_n),
> \end{align*}
> $$
> where the latter *converges absolutely* if $\nu\left(\bigcup_{n=1}^{\infty} E_n\right)$ is *finite.*



## Explanation






-----------
##  Recommended Notes and References

- [[Measure Space and Countably Additive Measure]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]