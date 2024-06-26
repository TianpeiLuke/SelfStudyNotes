---
tags:
  - concept
  - math/stochastic_process
keywords:
  - foster_theorem
  - discrete_state_markov_chain
  - positive_recurrent_state
topics:
  - stochastic_process
name: Foster Theorem
date of note: 2024-06-19
---

## Concept Definition

>[!important]
>**Name**: Foster Theorem

>[!important] Foster Theorem
>Consider an **irreducible** Markov chain $(X_n)_{n\in \mathbb{N}}$ with **countable state space** $\mathcal{X} = \set{0,1,\ldots}$ and transition kernel $K$.
>
>Suppose there *exists* a function $h: \mathcal{X} \rightarrow \mathbb{R}$ such that
>- $h$ is a **proper function**: $$\inf_{x\in \mathcal{X}}h(x) > -\infty$$
>- **Boundednes**: $$\sum_{y\in \mathcal{X}}K(x, y)\,h(y) < \infty  \quad \forall x \in \mathcal{S}$$
>- **Approximately Invariant** $$\sum_{y\in \mathcal{X}}K(x, y)\,h(y) < h(x) - \epsilon  \quad \forall x \not\in \mathcal{S}$$
>
>for some **finite set** $\mathcal{S} \subset \mathcal{X}$ and some $\epsilon >0$, then the Markov chain $(X_n)_{n\in \mathbb{N}}$ is **positive recurrent**.

- [[Positive Recurrent Markov Chain]]
- [[Invariant Measure and Stationary Distribution]]
- [[Markov Transition Kernel and Transition Function]]


## Explanation


>[!info]
>This theorem in fact state that if the countable state Markov chain has **finite invariant measure**, then it is **positive recurrent**.

![[Positive Recurrent Markov Chain#^17e86b]]




-----------
##  Recommended Notes and References

- [[Poke Lemma for Discrete State Markov Chain]]
- [[Positive Recurrent Markov Chain]]

- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]

- [[Monte Carlo Statistical Methods by Robert]]