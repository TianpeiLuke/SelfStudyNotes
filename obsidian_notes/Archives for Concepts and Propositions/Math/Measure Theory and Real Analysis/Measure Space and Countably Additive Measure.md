---
tags:
  - concept
  - math/measure_theory
keywords:
  - measure_space
  - countably_additive_measure
  - borel_measure
topics:
  - measure_theory
name: countably additive measure and measure space
date of note: 2024-05-05
---

## Concept Definition

>[!important]
>**Name**:  Countably Additive Measure $\mu$ and Measure Space $(X, \mathscr{B}, \mu)$,


>[!important] Definition
>Let $(X, \mathscr{B})$ be a *measurable space*. An (unsigned) **countably additive measure** $\mu$ on $\mathscr{B}$, or **measure** for short, is a map $\mu: \mathscr{B} \rightarrow [0, +\infty]$ that obeys the following axioms:
> 
> 1. **Empty set**: $\mu(\emptyset) = 0$.
> 2. **Countable additivity**: Whenever $E_1, E_2, \ldots \in \mathscr{B}$ are a *countable sequence* of *disjoint* measurable sets, then 
> $$
> \begin{align*}
> \mu\left(\bigcup_{n=1}^{\infty} E_n\right) &= \sum_{n=1}^{\infty} \mu(E_n).
> \end{align*}
> $$
> 
>A triplet $(X, \mathscr{B}, \mu)$, where $(X, \mathscr{B})$ is a **measurable space** and $\mu: \mathscr{B} \rightarrow [0, +\infty]$ is a *countably additive measure*, is known as **a measure space**.

- [[sigma Algebra]]

>[!info]
>Note the distinction between a **measure space** $(X, \mathscr{B}, \mu)$ and a **measurable space** $(X, \mathscr{B})$. The latter has the *capability* to be equipped with a **measure**, but the former is *actually* equipped with a measure.


## Explanation



## Properties

>[!important] Proposition
>Let $(X, \mathscr{B}, \mu)$ be a **measure space**.
>- **Countable subadditivity**: If $E_1, E_2, \ldots$ are $\mathscr{B}$-measurable, then 
>$$ 
> \begin{align*}
> \mu \left(\bigcup_{n=1}^{\infty} E_n\right) &\le \sum_{n=1}^{\infty} \mu(E_n).
> \end{align*}
>$$ 
>- **Upwards monotone convergence** If $E_1 \subseteq E_2 \subseteq \ldots$ are $\mathscr{B}$-measurable, then
>$$ 
> \begin{align}
> \mu \left(\bigcup_{n=1}^{\infty} E_n\right) &= \lim\limits_{n\rightarrow \infty}\mu(E_n) = \sup\limits_{n}\mu(E_n). 
> \end{align}
>$$ 
>- **Downwards monotone convergence** If $E_1 \supseteq E_2 \supseteq \ldots$ are $\mathscr{B}$-measurable, and **$\mu(E_n) < \infty$** for **at least one $n$**, then
>$$
> \begin{align}
> \mu\left(\bigcap_{n=1}^{\infty} E_n\right) &= \lim\limits_{n\rightarrow \infty}\mu(E_n) = \inf\limits_{n}\mu(E_n). 
> \end{align}
>$$ 
> 

- [[Monotone Sequence of Nested Sets]]
- [[Supremum and Infimum of Sets]]
- [[Limits of Sets]]

>[!info]
>Use supremum and infimum of sets, we can write the properties as
>$$
>\mu \left(\sup\limits_{n} E_n\right) =  \sup\limits_{n}\mu(E_n).
>$$
>and for at least one $\mu(E_{n}) < +\infty$,
>$$
>\mu \left(\inf\limits_{n} E_n\right) =  \inf\limits_{n}\mu(E_n),
>$$
>for monotone sequence of $\{E_{n}\}$.

>[!info]
>Use limit of sets, we can write the properties as
>$$
>\mu \left(\limsup\limits_{n} E_n\right) =  \limsup\limits_{n}\mu(E_n).
>$$
>and for at least one $\mu(E_{n}) < +\infty$,
>$$
>\mu \left(\liminf\limits_{n} E_n\right) =  \liminf\limits_{n}\mu(E_n).
>$$
>


>[!info]
>The following theorem provides a similar result as the [[Dominated Convergence Theorem]].

>[!important] Theorem
>Let $(X, \mathscr{B}, \mu)$ be a *measure space*. Let $E_1, E_2, \ldots$ be a sequence of $\mathscr{B}$-measurable sets that **converge** to another set $E$, in the sense that $\mathbb{1}_{E_n}$ **converges pointwise** to $\mathbb{1}_{E}$. Then 
>- $E$ is **also $\mathscr{B}$-measurable**.
>- If there exists a $\mathscr{B}$-measurable set $F$ of **finite measure** (i.e. $\mu(F) < \infty$) that **contains all of the $E_n$**, then
>$$
> \begin{align*}
> \lim\limits_{n \rightarrow \infty} \mu(E_n) = \mu(E). 
> \end{align*}
>$$ 
>
>(Hint: Apply downward monotonicity to the sets $\bigcup_{n>N}(E_n \Delta E)$.)
>- The previous part of this proposition can **fail** if the hypothesis that all the $E_n$ are contained in a set of **finite measure** is **omitted**.




## Borel Measure

- [[Borel Measure]]



-----------
##  Recommended Notes and References

- [[sigma Algebra]]
- [[Probability Space]]

- [[Finitely Additive Measure]]