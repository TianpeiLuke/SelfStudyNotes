---
tags:
  - concept
  - math/stochastic_process
  - machine_learning_models/mc
keywords:
  - first_hitting_time
  - stopping_time
  - Markov_Chain
topics:
  - stochastic_process
name: Stopping Time for Markov Chain
date of note: 2024-05-24
---

## Concept Definition

>[!important]
>**Name**: Stopping Time of Markov Chain

>[!important] Definition
>Let $\{(X_{n}, \mathscr{F}_{n}), n\ge 0\}$ be a *Markov chain* of random variables on measurable space $(\Omega, \mathscr{F})$. 
>
>Consider $A \in \mathscr{F}$. The **first time** at which the chain *enters the set* $A$ is denoted by 
>$$
>\tau_{A} := \inf\left\{n \ge 0: \;\; X_{n} \in A  \right\} 
>$$
>and is called **the stopping time (or hitting time)** at $A$, with, by convention, $\tau_{A} = +\infty$ if $X_{n} \not\in A$ for every $n$.

^61fb49

- [[Markov Chain and Markov Process]]
- [[Stopping Time of Filtration]]


>[!important] Definition
>For a **discrete state** *Markov chain*, and $A = \{ j \}$,  the stopping time at $A$ is
>$$
>\tau_{j} :=  \inf\left\{n \ge 1: \;\; X_{n} = j \right\} 
>$$
 >is called the *state* $j$'s **first hitting time**.


>[!important] Definition
>More generally, a function $\zeta(x_{1} \,{,}\ldots{,}\, x_{n})$ is called a **stopping rule** if the set 
>$$
>\{ \zeta(x_{1} \,{,}\ldots{,}\, x_{n}) = n \}
>$$
>is *measurable* for the $\sigma$-algebra induced by $(X_{0} \,{,}\ldots{,}\, X_{n})$. 

## Stopping Time

>[!important] Proposition
>Let $(X_{t})$ be a Markov process with transition function $p$ and $A \subset \mathbb{R}^n$ be a non-empty closed subset of $\mathbb{R}^n$.
>
>For any $s\in T$, define **the first hitting time** at $A$ after $s$
>$$
>\tau(\omega) := \inf\left\{t \ge s: \;\; X(\omega, t) \in A  \right\}. 
>$$
>
>Then $\tau$ is **stopping time** with respect to $\left\{ \sigma(X_{s}, s\le t), \; t\in T \right\}$.

- Friedman, A. (1987). _Stochastic Differential Equations and Applications, Vol. 1_ (Vol. 1). Academic Press. pp 25
- [[Stopping Time of Filtration]]







-----------
##  Recommended Notes and References

- [[Stopping Time of Filtration]]

- [[Markov Chain and Markov Process]]
- [[Filtration]]

- Friedman, A. (1987). _Stochastic Differential Equations and Applications, Vol. 1_ (Vol. 1). Academic Press.
- [[Probability and Measure by Billingsley]]
- [[Monte Carlo Statistical Methods by Robert]]
