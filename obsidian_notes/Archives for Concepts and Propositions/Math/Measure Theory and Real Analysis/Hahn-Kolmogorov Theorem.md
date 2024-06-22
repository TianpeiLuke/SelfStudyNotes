---
tags:
  - concept
  - math/measure_theory
keywords:
  - hahn_kolmogorov_theorem
topics:
  - measure_theory
name: Hahn-Kolmogorov Theorem
date of note: 2024-05-13
---

## Theorem

>[!important]
>**Name**:  Hahn-Kolmogorov Theorem

>[!important] Hahn-Kolmogorov Theorem
> Every **pre-measure** $\mu_0 : \mathscr{B}_0 \rightarrow [0, +\infty]$  on a **Boolean algebra** $\mathscr{B}_{0}$ in $X$ can be **extended** to a **countably additive measure** $\mu : \mathscr{B} \rightarrow [0, +\infty]$.

- [[Hahn-Kolmogorov Extension of Pre-measure]]

- [[Pre-Measure]]
- [[Boolean Algebra]]
- [[Measure Space and Countably Additive Measure]]
- [[sigma Algebra]]


## Explanation


## Proof

>[!info] Proposition
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

>[!info]
>We can construct an **outer measure** $\mu^{*}$ according to Proposition above. 
>
>Let $\mathscr{B}$ be the *collection* of all sets $E \subseteq X$ that are **Carathéodory measurable** *with respect to* $\mu^{*}$ ($\mu^{*}$-measurable)}, and let $\mu$ be the **restriction** of $\mu^{*}$  to $\mathscr{B}$. 
>
>The tuple $(X, \mathscr{B}, \mu)$ is what we want in **Hahn-Kolmogorov theorem**. 

- [[Carathéodory Extension Theorem]]

>[!important]
>The **measure $\mu$** constructed in this way is called **the Hahn-Kolmogorov extension** of the **pre-measure** $\mu_0$. 

## Uniqueness

>[!important] Proposition
>Let $\mu_0 : \mathscr{B}_0 \rightarrow [0, +\infty]$ be a **pre-measure**, let $\mu : \mathscr{B} \rightarrow [0, +\infty]$ be the **Hahn-Kolmogorov extension** of $\mu_0$, and let $\mu' : \mathscr{B}' \rightarrow  [0, +\infty]$ be  *another* **countably additive extension** of $\mu_0$. 
>
>Suppose also that $\mu_0$ is **$\sigma$-finite**, which means that one can express the whole space $X$ as the *countable union of sets* $E_1, E_2, \ldots \in \mathscr{B}_{0}$ for which $\mu_0(E_n) < \infty$ for all $n$. 
>
>Then $\mu$ and $\mu'$ **agree** on their **common domain** of definition. In other words, $$\mu(E) = \mu'(E)$$ for all $E \in \mathscr{B} \cap \mathscr{B}'$.

- [[Finite and sigma-Finite Measure]]




-----------
##  Recommended Notes and References

- [[Development of Measures]]


- [[Real Analysis by Royden]]