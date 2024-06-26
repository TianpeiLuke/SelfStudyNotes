---
tags:
  - concept
  - math/stochastic_process
keywords:
  - positive_recurrent_state
  - Markov_Chain
topics:
  - stochastic_process
name: Positive Recurrent Markov Chain
date of note: 2024-06-22
---

## Concept Definition

>[!important]
>**Name**: Positive Recurrent Markov Chain

### Discrete State Markov Chain

>[!important] Definition
>A **recurrent state** $x\in \mathcal{X}$ is 
>- **positive recurrent** if the *expected returning time* $$\mathbb{E}\left[  \tau_{x} | X_0 = x \right] < \infty;$$
>
>- otherwise we say it is **null recurrent**.

^de7c69

- [[Classification of States of Markov Chain]]
- [[Stopping Time of Markov Chain]]

### Harris Chain

>[!important] Definition
>Let $(X_{n})$ be a *$\mu$-irreducible chain*.
>
>If there exists an *invariant probability measure* $\pi$ such that 
>$$
>\pi(B) = \int_{\mathcal{X}}K(x,B)\,\pi(dx),\quad \forall B\in \mathcal{B}(\mathcal{X}),
>$$
>then the chain is **positive**.

^17e86b

>[!important] Definition
>Let $(X_{n})$ be a *$\mu$-irreducible chain*.
>
>If $(X_{n})$ is *recurrent* but there does *not exists* a **finite invariant measure** $\pi$, then the chain is **null recurrent**.

^4850a2

- [[Invariant Measure and Stationary Distribution]]
- [[Classification of States of Markov Chain]]

## Explanation


## Classification of States

>[!important] Proposition
>If $i$ is **positive recurrent**, and $i \leftrightarrow j$, then $j$ is also **positive recurrent**.



## Harris Recurrent

>[!important] Theorem
>If a Harris chain is **positive**, then it is **recurrent**.

- [[Harris Recurrent Set and Harris Recurrent Markov Chain]]



-----------
##  Recommended Notes and References


- [[Stopping Time of Markov Chain]]
- [[Recurrent Markov Chain]]
- [[Invariant Measure and Stationary Distribution]]

- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]

- [[Monte Carlo Statistical Methods by Robert]] pp 223