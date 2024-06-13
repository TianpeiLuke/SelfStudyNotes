---
tags:
  - concept
  - math/measure_theory
keywords:
  - outer_measure
topics:
  - measure_theory
name: outer measure
date of note: 2024-05-05
---

## Concept Definition

>[!important]
>**Name**:  Outer Measure $\mu^{*}$


>[!important] Defintion
> Let $X$ be a *set*. An **abstract outer measure** (or **outer measure** for short) is a map $\mu^{*}: 2^X \rightarrow [0, +\infty]$ that assigns an *unsigned extended real number* $\mu^{*}(E) \in [0, +\infty]$ to every set $E \subseteq X$ which obeys the following axioms:
> 
> 1. **Empty set**: $\mu^{*}(\emptyset) = 0$.
> 2. **Monotonicity**: If $E \subseteq F$,  then $\mu^{*}(E) \le  \mu^{*}(F)$.
> 3. **Countable subadditivity**: If $E_1, E_2, \ldots \subseteq X$ is a *countable sequence* of subsets of X, then 
> $$
> \begin{align*}
> \mu^{*}\left(\bigcup_{n=1}^{\infty} E_n\right) &\le \sum_{n=1}^{\infty}\mu^{*}(E_n).
> \end{align*}
> $$
>
>Outer measures are also known as **exterior measures**.



## Explanation


>[!important] Proposition
>Let $\mathscr{B} \subset 2^X$ and $\mu_0: \mathscr{B} \rightarrow [0, +\infty]$ be such that 
>- $\emptyset, X \in \mathscr{B}$, and 
>- $\mu_0(\emptyset) = 0$. 
>
>For any $A \subseteq X$, define
>$$ 
> \begin{align*}
> \mu^{*}(A) &:= \inf\left\{\sum_{j=1}^{\infty}\mu_0(E_j): E_j \in \mathscr{B}, \text{ and } A \subseteq \bigcup_{j=1}^{\infty}E_j \right\}. 
> \end{align*} 
>$$
>Then $\mu^{*}$ is an **outer measure**. 

- [[Pre-Measure]]


-----------
##  Recommended Notes and References

- [[Measure Space and Countably Additive Measure]]
- [[Finite and sigma-Finite Measure]]