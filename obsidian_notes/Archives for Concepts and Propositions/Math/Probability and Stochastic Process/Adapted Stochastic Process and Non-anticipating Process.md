---
tags:
  - concept
  - math/probability
  - math/stochastic_process
keywords:
  - adapted_stochastic_process
  - non-anticipating_process
topics:
  - probability
  - stochastic_process
name: Adapted Stochastic Process
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**:  Adapted Stochastic Process and *Non-anticipating Process*


>[!info] Definition
>Let $\{X_n, n \ge 0\}$ be a stochastic process on a measure space $(\Omega, \mathscr{F})$.
>
>A collection of $\sigma$-fields $\{\mathscr{F}_n, n \ge 0\}$ are called a **filtration**, if $\{\mathscr{F}_n, n \ge 0\}$ is an *increasing sub $\sigma$-fields* of $\mathscr{F}$
>$$
> \begin{align*}
> \mathscr{F}_0 \subseteq \mathscr{F}_1 \subseteq \mathscr{F}_2  \,{\subseteq}\ldots{\subseteq}\, \mathscr{F}.
> \end{align*}
>$$  

- [[sigma Algebra Generated by Measurable Functions]]
- [[Monotone Sequence of Nested Sets]]
- [[Filtration]]
- [[Stochastic Process]]


>[!important] Definition
>Let $\{X_n, n \ge 0\}$ be a *stochastic process* on a measure space $(\Omega, \mathscr{F})$, and $\{\mathscr{F}_n, n \ge 0\}$ be a **filtration**.
>
>$X_n$ is **adapted** (also referred to as a **non-anticipating** or **non-anticipative process**) if for each $n$, $$X_n \in \mathscr{F}_n;$$  that is, $X_n$ is **$\mathscr{F}_n$-measurable.**

>[!important] Definition
>Let $\{X_n, n \ge 0\}$ be a *stochastic process* on a measure space $(\Omega, \mathscr{F})$.
>
>A family of $\sigma$-algebras $\{ \mathscr{F}_{n}, n \ge 0 \}$ is called **adapted**  or **non-anticipating** *with respect to* $\{X_n, n \ge 0\}$ if
>- $\{ \mathscr{F}_{n}, n \ge 0 \}$ is a **filtration**, i.e. $$\mathscr{F}_{n-1} \subseteq \mathscr{F}_{n}$$
>- the $\sigma$-algebra *generated by past events* $\sigma(X_{k}, k\le n)$ is contained in $\mathscr{F}_{n}$, i.e. $$\sigma(X_{k}, k\le n) \subseteq \mathscr{F}_{n}$$
>-  the $\sigma$-algebra *generated by future events* $\sigma(X_{k}, k > n)$ is **independent** from $\mathscr{F}_{n}$, i.e. $$\sigma(X_{k}, k > n) \perp \mathscr{F}_{n}$$

- [[Independence of Events]]

## Explanation

>[!important]
>If $((X_{t}, \mathscr{F}_{t}), t\in T)$ is an **adapted** process then the information about the *value of the process* **at a given time** is *available* **at that same time**.

>[!info]
>This is in contrast to the **predictable process** where  each $X_{n}$ is **$\mathscr{F}_{n-1}$-measureable**.
>
>That is, the information about the value of the process at a given time is *available* **before that time**.

- [[Predictable and Increasing Process]]




-----------
##  Recommended Notes and References

- [[Stochastic Process]]
- [[Markov Chain and Markov Process]]
- [[Brownian Motion Wiener Process]]

- [[Predictable and Increasing Process]]

- [[A Probability Path by Resnick]]
- [[Probability and Measure by Billingsley]]
- [[Bandit Algorithms by Lattimore]]
- [[Introduction to Stochastic Differential Equations by Evans]]
- Wikipedia [Adapted process](https://en.wikipedia.org/wiki/Adapted_process)