---
tags:
  - concept
  - math/stochastic_process
  - math/probability
keywords:
  - stopping_time
topics:
  - probability
  - stochastic_process
name: Stopping Time of Filtration
date of note: 2024-05-15
---

## Concept Definition

>[!important]
>**Name**: Stopping Time of Filtration

>[!info] Definition
>Let $\{X_n, n \ge 0\}$ be a stochastic process on a measure space $(\Omega, \mathscr{F})$.
>
>A collection of $\sigma$-fields $\{\mathscr{F}_n, n \ge 0\}$ is called a **filtration**, if $\{\mathscr{F}_n, n \ge 0\}$ is an *increasing sub $\sigma$-fields* of $\mathscr{F}$
>$$
> \begin{align*}
> \mathscr{F}_0 \subseteq \mathscr{F}_1 \subseteq \mathscr{F}_2  \,{\subseteq}\ldots{\subseteq}\, \mathscr{F}.
> \end{align*}
>$$  

- [[Martingale]]
- [[Filtration]]

>[!important] Definition
>Suppose $\{\mathscr{F}_n, n \ge 0\}$ is a *filtration*. Let $$\mathscr{F}_{\infty} = \bigcup_{n\ge 0}\mathscr{F}_{n}.$$
>
>A random variable $$\tau: (\Omega, \mathscr{F}) \to (\mathbb{N}\cup\{+\infty\}, 2^{\mathbb{N}\cup\{+\infty\}})$$ is called a **stopping time** with respect to $\{\mathscr{F}_n, n \ge 0\}$  if
>- $\mathbb{1}\{\tau \le t\}$ is *$\mathscr{F}_{t}$-measurable* for all $t\in \mathbb{N}\cup \{ +\infty \}$. i.e. for all $t$,
>  $$
>  \{\omega \in \Omega: \tau(\omega) \le t  \} \in \mathscr{F}_{t}.
> $$

- [[Random Element and Random Variable]]



>[!important] Definition
>**The $\sigma$-algebra at stopping time $\tau$**, $\mathscr{F}_{\tau}$, is defined as
>$$
>\mathscr{F}_{\tau} := \{ A \in \mathscr{F}_{\infty}: A \cap \{ \tau \le t \} \in \mathscr{F}_{t}, \quad \forall t \in \mathbb{N}\cup \{ +\infty \} \}
>$$

- [[Intersection of Set Family to Set]]

>[!info]
>We indicate that $\mathcal{F} := \{\mathscr{F}_n, n \ge 0\}$ is a filtration when states that $\tau$ is a "**$\text{}\mathcal{F}$-stopping time"**.

## Explanation

>[!info]
>$\tau$ is a **stopping time** with respect to $(\mathscr{F}_{t})$ means that the query 
>
>"*has the stopping time reached before time $t$?*" 
>
>can be *answered __deterministically__* given all information available at time $t$.
>
>In other word, the information used to determine the stopping time is **in the present** and not relying on **its own history**.


>[!important]
>Using the interpretation of **$\sigma$-algebras encoding information**, if 
>- $\{\mathscr{F}_{t}: t\ge 0\}$ is thought of as **the knowledge available at time $t$**,  then 
>- $\mathscr{F}_{\tau}$ is the information available **at the random time** $\tau$.


## Properties

>[!important] Proposition
>Let $\set{(X_n, \mathscr{F}_n), n \ge 0}$ be a **martingale** and let $\tau$ be a **stopping time** with respect to $\set{\mathscr{F}_n, n \ge 0}$. 
>
>Then 
>$$
> \begin{align*}
> \set{X_{\tau \land n}, \;\; n=0, 1, \ldots}
> \end{align*}
>$$ 
>is a **martingale** with respect to $\set{\mathscr{F}_n, n \ge 0}$, where $n\land \tau = \min\set{n, \tau}$.


## Stopping Time of Martingale

- [[Weak Optional Sampling Theorem]]
- [[Doob Optional Sampling Theorem]]



## Stopping Time of Markov Process

- [[Stopping Time of Markov Chain]]


## Stopping Time of Stochastic Integral

- [[Stopping Time and Stochastic Integral]]

## Local Properties

- [[Local Property of Stochastic Process and Localizing Sequence]]



-----------
##  Recommended Notes and References

- [[Bandit Algorithms by Lattimore]]
- [[Probability and Measure by Billingsley]]
- [[A Probability Path by Resnick]]