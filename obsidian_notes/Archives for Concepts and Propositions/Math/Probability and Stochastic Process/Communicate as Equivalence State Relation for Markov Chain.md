---
tags:
  - concept
  - math/stochastic_process
keywords:
  - communicate_states
  - equivalence_class
  - equivalence_relation
topics:
  - stochastic_process
name: Communicate as Equivalence State Relation for Markov Chain
date of note: 2024-06-19
---

## Concept Definition

>[!important]
>**Name**: Communicate as Equivalence State Relation for Markov Chain

### Accessibility of State from State

>[!important] Definition
>Let $(X_{n})$ be a *discrete-time discrete-state Markov chain*.
>
>For any pair $x, y \in \mathcal{X}$, if there exists $n \in \mathbb{N}_{+}$ so that $$K^{n}(x, y) > 0,$$ then the state $y$ is **accessible** *from state* $x$. 
>
>This is equivalent to say that *the probability of hitting time* of $y$ being *finite* starting from $x$ is *above zero*, i.e. $$\mathcal{P}_{x, s}\left(\tau_{y} < \infty \right) > 0.$$
>where $\tau_{y}$ is the **first hitting time** of state $y$, $$\tau_{y} = \inf\{n: X_{n} = y \}.$$

- [[Markov Chain and Markov Process]]
- [[Markov Transition Kernel and Transition Function]]
- [[Chapman-Kolmogorov Equation]]
- [[Stopping Time of Markov Chain]]

### Communication between States

>[!important] Definition
>If $x$ is *accessible* from $y$, and $y$ is *accessible* from $x$, then we say that $x$ and $y$ **communicate**,$$x \leftrightarrow y.$$ 

>[!info]
>It is easy to check that this is an **equivalence relation**:
> -  $x \leftrightarrow x$;
> - If $x \leftrightarrow y$, then $y \leftrightarrow x$;
> - If $x \leftrightarrow z$ and $z \leftrightarrow y$, then $x \leftrightarrow y$ 

>[!info]
>We can partition the state space $\mathcal{X}$ into cosets according to $\leftrightarrow$ relation.
>$$
>\mathcal{X} = \bigcup_{x\in \mathcal{X}}[x]
>$$

## Explanation





-----------
##  Recommended Notes and References


- [[Irreducibility of Markov Chain]]
- [[Classification of States of Markov Chain]]

- [[Markov Transition Kernel and Transition Function]]
- [[Chapman-Kolmogorov Equation]]
- [[Stopping Time of Markov Chain]]


- [[Monte Carlo Statistical Methods by Robert]] pp 213