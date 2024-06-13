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
>\tau_{A} := \inf\left\{n \ge 1: \;\; X_{n} \in A  \right\} 
>$$
>and is called **the stopping time** at $A$, with, by convention, $\tau_{A} = +\infty$ if $X_{n} \not\in A$ for every $n$.

- [[Markov Chain and Markov Process]]
- [[Stopping Time of Filtration]]


>[!info]
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



## Explanation





-----------
##  Recommended Notes and References

- [[Stopping Time of Filtration]]

- [[Markov Chain and Markov Process]]
- [[Filtration]]


- [[Probability and Measure by Billingsley]]
- [[Monte Carlo Statistical Methods by Robert]]
