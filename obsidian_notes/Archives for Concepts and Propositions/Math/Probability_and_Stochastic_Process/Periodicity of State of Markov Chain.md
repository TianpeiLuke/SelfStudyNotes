---
tags:
  - concept
  - math/stochastic_process
keywords:
  - periodicity_markov_chain
topics:
  - stochastic_process
name: Periodicity of State of Markov Chain
date of note: 2024-06-19
---

## Concept Definition

>[!important]
>**Name**: Periodicity of State of Markov Chain

>[!important] Definition (Harris Chain)
>A *discrete-time $\mu$-irreducible chain* $(X_{n})$ has a **cycle of length (periodicity of) $d$** if there exists a *small set* $C$, an associated integer $M \in \mathbb{N}$, and a *probability measure* $\nu_{M}$ such that 
>$$
>d = \text{g.c.d.}\left\{ n \ge 1: \;\; \exists \delta_{n} > 0 \text{ such that } C \text{ is small for }\nu_{n} \ge \delta_{n}\,\nu_{M} \;\right\}. 
>$$
>where $\text{g.c.d.}$ is the *greatest common divisor*. 
>
>The **period** of $(X_{n})$ is then defined as the *largest integer* $d$ satisfying above condition.

^85f964

- [[Small Set of Markov Chain]]
- [[Irreducibility of Markov Chain]]
- [[Markov Chain and Markov Process]]


>[!important] Definition (Discrete-Time Discrete-State Markov Chain)
>Let $(X_{n})$ be a *discrete-time discrete-state Markov chain* on $\mathcal{X}$.
>
>The **periodicity** of a *state* $x \in \mathcal{X}$ is defined as
>$$ 
> \begin{align}
> d(x) &= \text{g.c.d.}\set{n \ge 1: K^{n}(x, x) > 0}
> \end{align}
>$$  
>where $\text{g.c.d.}$ is the *greatest common divisor*. 

^934b9a


- [[Markov Transition Kernel and Transition Function]]



## Explanation


## Proposition

>[!important] Proposition
>Let $(X_{n})$ be a Markov chain with discrete state space $\mathcal{X}$.
>
>For any $x ,y \in \mathcal{X}$, if $$x\leftrightarrow y$$ i.e. $$\mathcal{P}(\tau_{y} < \infty | X_{0} = x) > 0 \text{ and } \mathcal{P}(\tau_{x} < \infty | X_{0} = y) > 0,$$ 
>then  $x,y$ has the **same periodicity** $$d(x) = d(y).$$

- [[Communicate as Equivalence State Relation for Markov Chain]]





-----------
##  Recommended Notes and References


- [[Irreducibility of Markov Chain]]
- [[Markov Chain and Markov Process]]


- [[Monte Carlo Statistical Methods by Robert]]