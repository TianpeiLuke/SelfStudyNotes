---
tags:
  - concept
  - math/stochastic_process
keywords:
  - recurrent_state
  - Markov_Chain
topics:
  - stochastic_process
name: Recurrent Markov Chain
date of note: 2024-06-19
---

## Concept Definition

>[!important]
>**Name**: Recurrent Markov Chain

### Discrete State Markov Chain

![[Classification of States of Markov Chain#^89b449]]


>[!important] Definition (Discrete State)
>Let $(X_{n})$ be a *discrete-state Markov chain*. 
>
>-  $(X_{n})$ is **recurrent** if $(X_{n})$ is *irreducible*, and *all* states are recurrent.
>- $(X_{n})$ is **transient** if $(X_{n})$ is *irreducible*,  and *all* states are transient.

### Harris Chain

![[Classification of States of Markov Chain#^50067d]]

>[!important] Definition (Harris Chain)
>Let $(X_{n})$ be a *Markov chain* with possibly *uncountable state*, and $\mathcal{B}(\mathcal{X})$ be Borel $\sigma$-algebra on $\mathcal{X}$
>
> $(X_{n})$ is **recurrent** if
> - there exists a *measure* $\mu$ such that $(X_{n})$ is **$\mu$-irreducible**, and
> - for every $A\in \mathcal{B}(\mathcal{X})$ such that $\mu(A) >0$, $$\mathbb{E}\left[  \eta_{A} | X_{0} = x \right] = \infty, \quad \forall x\in A.$$

>[!important] Definition (Harris Chain)
>Let $(X_{n})$ be a *Markov chain* with possibly *uncountable state*, and $\mathcal{B}(\mathcal{X})$ be Borel $\sigma$-algebra on $\mathcal{X}$
>
> $(X_{n})$ is **transient** if
> - there exists a *measure* $\mu$ such that $(X_{n})$ is **$\mu$-irreducible**, and
> - the state space $\mathcal{X}$ is **transient**.


- [[Classification of States of Markov Chain]]
- [[Irreducibility of Markov Chain]]

- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]
- [[Number of Passages and Probability of Finite Return]]

### Harris Recurrent Chain

- [[Harris Recurrent Set and Harris Recurrent Markov Chain]]




## Explanation




## Criterion for Recurrence


>[!important] Proposition
>A **$\mu$-irreducible** chain $(X_{n})$ is **recurrent** if there exists a **small set** $C$ with $\mu(C) >0$ such that $$\mathcal{P}(\tau_{C} < \infty | X_{0} = x)$$ for every $x\in C$.

- [[Small Set of Markov Chain]]




-----------
##  Recommended Notes and References


- [[Classification of States of Markov Chain]]
- [[Harris Recurrent Set and Harris Recurrent Markov Chain]]

- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]
- [[Number of Passages and Probability of Finite Return]]

- [[Borel sigma Field]]

- [[Monte Carlo Statistical Methods by Robert]] pp 220