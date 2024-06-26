---
tags:
  - concept
  - math/stochastic_process
keywords:
  - poke_lemma
  - discrete_state_markov_chain
topics:
  - stochastic_process
name: Poke Lemma for Discrete State Markov Chain
date of note: 2024-06-19
---

## Concept Definition

>[!important]
>**Name**: Poke Lemma for Discrete State Markov Chain

>[!important] Poke Lemma
>Consider an **irreducible** Markov chain $(X_n)_{n\in \mathbb{N}}$ with **discrete state space** $\mathcal{X}=\set{0,1,\ldots}$ and transition kernel $K$. 
>
>Assume that for all $x\in \mathcal{X}$ and all $n\ge 0$,  the chain satisfies the following properties
>- **Boundedness** $$\mathbb{E}\left[  X_{n+1} | X_n = x \right] < \infty$$  
>- **Asymptotically Negative Expected Increment** $$\lim_{m\rightarrow \infty}\sup_{x \ge m}\mathbb{E}\left[  X_{n+1} - X_{n} | X_n = x \right] < 0.$$ 
>  
>Then the Markov chain $(X_n)_{n\in \mathbb{N}}$ is **positive recurrent**.

- [[Irreducibility of Markov Chain]]
- [[Markov Transition Kernel and Transition Function]]



## Explanation





-----------
##  Recommended Notes and References

- [[Positive Recurrent Markov Chain]]
- [[Invariant Measure and Stationary Distribution]]

- [[Foster Theorem for Discrete State Markov Chain]]

- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]

- [[Monte Carlo Statistical Methods by Robert]]