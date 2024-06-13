---
tags:
  - concept
  - math/stochastic_process
keywords:
  - predictable_process
  - increasing_process
topics:
  - stochastic_process
name: Predictable and Increasing Process
date of note: 2024-05-21
---

## Concept Definition

>[!important]
>**Name**: Predictable and Increasing Process

>[!important] Definition
>Given a process $\set{X_n, n \ge 0}$ and an increasing family of $\sigma$-algebras $\{ \mathscr{B}_{n}, n \ge 0\}$. 
>
>We call $\set{X_n, n \ge 0}$ **predictable** if 
>- $X_0 \in \mathscr{B}_0 =  \set{\emptyset, \Omega}$ and  
>- $X_n$ is $\mathscr{B}_{n-1}$-*measurable* for each $n =1, 2, \ldots$.

>[!important] Definition
>Call a process $\set{X_n, n \ge 0}$ an **increasing process** if $\set{X_n}$ is **predictable** and 
>$$
> \begin{align*}
>  0 = X_0 \leq X_1  \,{\leq}\ldots{\leq}\, X_n \leq \ldots. \quad \text{a.s.}
> \end{align*}
>$$

- [[Filtration]]


## Explanation

>[!important]
>Compare  the **predictable stochastic process** with **adapted stochastic process**
>- **predictable process**: the information about the value of process at $n$, $X_{n}$, is *available* **before** $n$, in $\mathscr{F}_{n-1}$, thus  $$X_{n} \in \mathscr{F}_{n-1}$$
>- **adapted (non-anticipating) process**: the information about the value of process at time $n$, $X_{n}$ is *available* **only at that same time** $$X_{n} \in \mathscr{F}_{n}.$$ 

- [[Adapted Stochastic Process and Non-anticipating Process]]

## Example

>[!example]
>If a **martingale** $((X_{n}, \mathscr{F}_{n}), n\in T)$ is a **predictable process**, then $$X_{n} = X_{0}, \text{ a.s.}$$
>
>Note that 
> $$
> \begin{align}
> \mathbb{E}\left[ X_{n+1} \;|\; \mathscr{F}_{n} \right] &= X_n, \quad \text{a.s.} 
> \end{align}
> $$
> and if $X_{n}$ is predictable, then 
>$$
>\mathbb{E}\left[ X_{n+1} \;|\; \mathscr{F}_{n} \right]
>$$
>is $\mathscr{F}_{n}$-measurable, therefore
>$$
>\mathbb{E}\left[ X_{n+1} \;|\; \mathscr{F}_{n} \right] = X_{n+1}, \text{ a.s.}
>$$
>so 
>$$
>X_{n+1} = X_{n}, \quad \text{ a.s.}
>$$

- [[Martingale]]







-----------
##  Recommended Notes and References

- [[Doob Decomposition of Submartingale]]

- [[Adapted Stochastic Process and Non-anticipating Process]]
- [[Filtration]]
- [[Stochastic Process]]