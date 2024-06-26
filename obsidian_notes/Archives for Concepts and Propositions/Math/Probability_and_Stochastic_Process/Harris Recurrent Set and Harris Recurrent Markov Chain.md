---
tags:
  - concept
  - math/stochastic_process
keywords:
  - harris_recurrent
  - markov_process
topics:
  - stochastic_process
name: Harris Recurrent Markov Chain
date of note: 2024-06-19
---

## Concept Definition

>[!important]
>**Name**: Harris Recurrent State and Harris Recurrent Markov Chain

>[!important] Definition
>Let $(X_{n})$ be a *Markov chain* with possibly *uncountable state*.
>
>A *set* $A$ is **Harris recurrent** if $$\mathcal{P}\left(\eta_{A} = \infty \;|\; X_{0} = x\right) = 1, \quad x\in A,$$ where $\eta_{A}$ is *the number of passages* to set $A$.

^f40444


- [[Classification of States of Markov Chain]]

- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]
- [[Number of Passages and Probability of Finite Return]]

>[!important] Definition
>The chain $(X_{n})$ is **Harris recurrent** if there exists a *measure* $\mu$ such that 
>- $(X_{n})$ is *$\mu$-irreducible* and 
>- for every set $A$ with $\mu(A) > 0$, $A$ is *Harris recurrent*.


## Explanation

>[!info]
>- **Recurrent Set**:  The **expected total number of returning** is *infinite* $$\mathbb{E}\left[\eta_{A} | X_{0}= x\right] = \infty;\quad \forall x\in A.$$ 
>- **Harris Recurrent Set**: The **probability of infinite total number of visiting** is $1$. $$P(\eta_{A} = \infty |\, X_{0} = x) = 1;\quad \forall x\in A$$ 
>
>- For $\mathcal{X}$ *uncountable*,    
>$$
>\text{Harris Recurrent Collection } \subsetneq \text{Recurrent Collection }
>$$  
>- For $\mathcal{X}$ *countably infinite or finite*,    
>$$
>\text{Harris Recurrent Collection } = \text{Recurrent Collection }
>$$  

- [[Classification of States of Markov Chain]]

>[!important]
>**Harris recurrence** *strengthen* the concept of **recurrence** by requiring not only an **infinite average number** of visits to **every small set** but also an infinite number of visits for **every path** of the Markov chain.


## Equivalent Definition

>[!important] Proposition
>Let $(X_{n})$ be a Markov chain, and $\mathcal{B}(\mathcal{X})$ be the Borel $\sigma$-algebra on state space. 
>
>If for every $A\in \mathcal{B}(\mathcal{X})$, $$\mathcal{P}\left(\tau_{A} < \infty | X_{0} = x\right) = 1, \; \forall x\in A,$$ then $$\mathcal{P}\left(\eta_{A} = \infty \;|\; X_{0} = x\right) = 1, \quad x\in A,$$ and $(X_{n})$ is **Harris recurrent**.

## Discrete State Case

![[Classification of States of Markov Chain#^18549b]]

>[!info]
>The concept of Harris recurrence and Recurrence is equivalent if $\mathcal{X}$ is countable.




-----------
##  Recommended Notes and References


- [[Classification of States of Markov Chain]]

- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]
- [[Number of Passages and Probability of Finite Return]]



- [[Monte Carlo Statistical Methods by Robert]] pp 222