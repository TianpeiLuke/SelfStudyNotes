---
tags:
  - concept
  - math/measure_theory
keywords:
  - finitely_additive_measure
topics:
  - measure_theory
name: Finitely Additive Measure
date of note: 2024-05-13
---

## Concept Definition

>[!important]
>**Name**: Finitely Additive Measure


>[!important] Defintion
>Let $\mathscr{B}$ be a *Boolean algebra* on a space $X$. An **(unsigned) finitely additive measure** $\mu$ on $\mathscr{B}$ is a map $\mu : \mathscr{B} \rightarrow [0,+\infty]$ that obeys the following axioms
> 
> 1. **Empty set**: $\nu(\emptyset) = 0$.
> 2. **Finite union**: Whenever $E_1, E_2 \in \mathscr{B}$ are *disjoint* sets in $\mathscr{B}$, then 
> $$
> \begin{align*}
> \mu\left(E_{1} \cup E_{2} \right) &= \mu(E_1) + \mu(E_{2}).
> \end{align*}
> $$
> 

- [[Boolean Algebra]]

## Explanation



## Property

>[!important] Proposition
>Let $\mu: \mathscr{B} \rightarrow [0, +\infty]$be a **finitely additive measure** on a *Boolean algebra* $\mathscr{B}$. 
> 
>- **Monotonicity** If $E, F$ are $\mathscr{B}$-measurable and $E \subseteq F$, then
>$$ 
> \begin{align*}
> \mu(E) \le \mu(F).
> \end{align*}
>$$ 
>- **Finite additivity** If $k$ is a natural number, and $E_1 \,{,}\ldots{,}\, E_k$ are $\mathscr{B}$-measurable and **disjoint**, then 
>$$ 
> \begin{align*}
> \mu\left(\bigcup_{i=1}^k E_i\right) = \sum_{i=1}^{k} \mu(E_i).
> \end{align*}
>$$ 
>- **Finite subadditivity** If $k$ is a natural number, and $E_1 \,{,}\ldots{,}\, E_k$ are $\mathscr{B}$-measurable, then
>$$ 
> \begin{align*}
> \mu\left(\bigcup_{i=1}^k E_i\right) \le \sum_{i=1}^{k} \mu(E_i).
> \end{align*}
>$$ 
>- **Inclusion-exclusion for two sets** If $E, F$ are $\mathscr{B}$-measurable, then
>$$
> \begin{align*}
> \mu(E \cup F ) + \mu(E \cap F ) = \mu(E) + \mu(F).
> \end{align*}
>$$
>
>(Caution: remember that the cancellation law $a+c = b+c \Rightarrow a = b$ does not hold in [0; +1] if c is infinite, and so the use of cancellation
> (or subtraction) should be avoided if possible.)





-----------
##  Recommended Notes and References

- [[Measure Space and Countably Additive Measure]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]