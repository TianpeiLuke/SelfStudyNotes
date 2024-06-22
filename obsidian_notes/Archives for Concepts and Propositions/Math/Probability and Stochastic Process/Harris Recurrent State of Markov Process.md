---
tags:
  - concept
  - math/stochastic_process
keywords:
  - harris_recurrent
  - markov_process
topics:
  - stochastic_process
name: Harris Recurrent State of Markov Process
date of note: 2024-06-19
---

## Concept Definition

>[!important]
>**Name**: Harris Recurrent State of Markov Process

>[!important] Definition
>Let $(X_{n})$ be a *discrete-time* (but may be *uncountable state*) *Markov chain*.
>
>A *set* $A$ is **Harris recurrent** if $$\mathcal{P}\left(\eta_{A} = \infty \;|\; X_{0} = x\right) = 1$$ for all $x \in A$, where $\eta_{A}$ is *the number of passages* to set $A$.


- [[Classification of States of Markov Chain]]

- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]
- [[Number of Passages and Probability of Finite Return]]

>[!important] Definition
>The chain $(X_{n})$ is **Harris recurrent** if there exists a *measure* $\mu$ such that 
>- $(X_{n})$ is *$\mu$-irreducible* and 
>- for every set $A$ with $\mu(A) > 0$, $A$ is *Harris recurrent*.


## Explanation





-----------
##  Recommended Notes and References


- [[Classification of States of Markov Chain]]

- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]
- [[Number of Passages and Probability of Finite Return]]



- [[Monte Carlo Statistical Methods by Robert]] pp 222