---
tags:
  - concept
  - math/measure_theory
keywords:
  - pre-measure
topics:
  - measure_theory
name: pre-measure
date of note: 2024-05-05
---

## Concept Definition

>[!important]
>**Name**:  Pre-Measure $\mu_0$


>[!important] Defintion
>A **pre-measure** on a *Boolean algebra* $\mathscr{B}_{0}$  is a function $\mu_0 : \mathscr{B}_0 \rightarrow [0, +\infty]$ that satisfies the conditions:
> 
> 1. **Empty Set**: $\mu_0(\emptyset) = 0$
> 2. **Countably Additivity**: If $E_1, E_2, \ldots \in \mathscr{B}_0$ are *disjoint* sets such that $\bigcup_{n=1}^{\infty} E_n  \in \mathscr{B}_0,$
>  $$
>  \begin{align*}
> \mu_0\left(\bigcup_{n=1}^{\infty} E_n\right) &= \sum_{n=1}^{\infty} \mu_0(E_n).
> \end{align*} 
> $$

- [[Boolean Algebra]]
- [[Measure Space and Countably Additive Measure]]

## Explanation

>[!info]
>The **countably additivity** condition for **pre-measure** can be releaxed to be the **countably subadditivity** $$\mu_0\left(\bigcup_{n=1}^{\infty} E_n \right) \le \sum_{n=1}^{\infty} \mu_0(E_n)$$ without affecting the definition of a pre-measure.

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

- [[Outer Measure]]


-----------
##  Recommended Notes and References

- [[Boolean Algebra]]

- [[Measure Space and Countably Additive Measure]]
- [[Finite and sigma-Finite Measure]]

- [[Outer Measure]]