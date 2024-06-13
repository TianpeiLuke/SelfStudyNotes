---
tags:
  - concept
  - math/measure_theory
keywords:
  - hahn_kolmogorov_theorem
topics:
  - measure_theory
name: Hahn-Kolmogorov Extension of Pre-measure
date of note: 2024-05-13
---

## Concept Definitions

>[!important]
>**Name**:  Hahn-Kolmogorov Extension of Pre-measure

>[!info]
>Given a [[Pre-Measure]]  $\mu_0 : \mathscr{B}_0 \rightarrow [0, +\infty]$  on a **Boolean algebra** $\mathscr{B}_{0}$ in $X$,  we can follow the following step to extend it to a **countably additive measure** $\mu : \mathscr{B} \rightarrow [0, +\infty]$.

- [[Pre-Measure]]
- [[Hahn-Kolmogorov Theorem]]

### Step 1 Construct Outer Measure from Pre-Measure

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

### Step 2 Restrict to Caratheodory Measurable Sets

>[!important] Carathéodory Extension Theorem
> Let $\mu^{*}: 2^X \rightarrow [0, +\infty]$ be an **outer measure** on a **set** X. 
> 
> Let $\mathscr{B}$ be the collection of *all subsets* of $X$ that are **Carathéodory measurable with respect to $\mu^{*}$**, and let $\mu: \mathscr{B} \rightarrow [0, +\infty]$ be the **restriction** of $\mu^{*}$ to $\mathscr{B}$ so that  $$\mu(E) := \mu^{*}(E)$$
>whenever $E \in \mathscr{B}$. 
>
>Then $\mathscr{B}$ is a **$\sigma$-algebra**, and  $\mu$ is a **measure**.

- [[Carathéodory Measurability]]
- [[Carathéodory Extension Theorem]]


>[!info]
>The tuple $(X, \mathscr{B}, \mu)$ is what we want in **Hahn-Kolmogorov theorem**. 







-----------
##  Recommended Notes and References


- [[Boolean Algebra]]
- [[Measure Space and Countably Additive Measure]]
- [[sigma Algebra]]
- [[Development of Measures]]
