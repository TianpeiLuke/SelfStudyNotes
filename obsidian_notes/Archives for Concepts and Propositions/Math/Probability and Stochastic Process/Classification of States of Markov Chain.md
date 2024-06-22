---
tags:
  - concept
  - math/stochastic_process
keywords:
  - classification_state
  - recurrent_state
  - positive_recurrent_state
topics:
  - stochastic_process
name: Classification of States of Markov Chain
date of note: 2024-06-19
---

## Concept Definition

>[!important]
>**Name**: Classification of States of Markov Chain

### Discrete State Markov Chain

>[!important] Definition
>Let $(X_{n})$ be a *discrete-time discrete-state Markov chain* on $\mathcal{X}$.
>
>A state $x \in \mathcal{X}$ is called  **recurrent** if $$\mathcal{P}( \tau_{x} < \infty | X_{0} = x) = 1,$$ i.e. the *first hitting time*  at initial state $x$ is finite.

- [[Stopping Time of Markov Chain]]
- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]

>[!important] Definition
>Let $(X_{n})$ be a *discrete-time discrete-state Markov chain* on $\mathcal{X}$.
>
>A state $x \in \mathcal{X}$ is called  **transient** if $$\mathcal{P}( \tau_{x} < \infty | X_{0} = x) < 1.$$



>[!important] Definition
>A **recurrent state** $x\in \mathcal{X}$ is 
>- **positive recurrent** if the *expected returning time* $$\mathbb{E}\left[  \tau_{x} | X_0 = x \right] < \infty;$$
>
>- otherwise we say it is **null recurrent**.

### Uncountable State Markov Chain



- [[Small Set of Markov Chain]]

## Explanation

>[!info]
>A state is **recurrent** if the Markov Chain will *return to* the state $x$ after stating from $x$.

## Characterization of Recurrent State

>[!important] Proposition
>Let $(X_{n})$ be a *discrete-time discrete-state Markov chain* on $\mathcal{X}$.
>
>The following conditions are **equivalent**:
>
>-  state $x\in \mathcal{X}$ is **recurrent state**;
>- The **ever returning probability** $$\mathcal{P}\left(\tau_{x} < \infty | X_{0}= x\right) = 1;$$
>- The **probability of total number of visiting** is $$P(\eta_{x} = \infty |\, X_{0} = y) = \mathcal{P}\left(\tau_{x} < \infty | X_{0}= y\right)$$ and $$P(\eta_{x} = \infty |\, X_{0} = x) = 1;$$ where $$\eta_{x} := \sum_{n=1}^{\infty}\mathbb{1}\left(X_{n} \in x\right).$$
>- The **expected total number of returning** is *infinite* $$\mathbb{E}\left[\eta_{x} | X_{0}= x\right] = \infty;$$ 
>- The *sum* of all **$n$-step return probabilities** $$\sum_{n=0}^{\infty}K^{n}(x, x) = \infty.$$
>

- [[Number of Passages and Probability of Finite Return]]

## Classification of States

>[!important] Proposition
>If $i$ is **recurrent**, and $i \rightarrow j$, then also $j \rightarrow i$.

- [[Communicate as Equivalence State Relation for Markov Chain]]

>[!important] Proposition
>If $i$ is **positive recurrent**, and $i \leftrightarrow j$, then $j$ is also **positive recurrent**.

>[!info]
>Positive recurrency is a property *closed* under $\leftrightarrow$ *equivalence relation*.

>[!important] Theorem
>If $i$ is **recurrent**, and $i \rightarrow j$, then $j$ is also **recurrent**. 
>
>Therefore, in any **equivalent class** under $\leftrightarrow$,  either 
>- **all states are recurrent** or 
>- **all are transient**. 
>  
>In particular, if the chain is **irreducible**, then either *all states are recurrent* or *all are transient.*

- [[Irreducibility of Markov Chain]]

## Finite Discrete State Markov Chain

>[!important] Theorem
>If a *closed subset* $S_0 \subset \mathcal{X}$ only has **finitely many states**, then there must be **at least one recurrent state**. 
>
>In particular any **finite Markov chain** must contain **at least one positive recurrent state**. 

## Uncountable State Markov Chain





-----------
##  Recommended Notes and References

- [[Harris Recurrent State of Markov Process]]
- [[Irreducibility of Markov Chain]]

- [[Communicate as Equivalence State Relation for Markov Chain]]
- [[Markov Chain and Markov Process]]

- [[Monte Carlo Statistical Methods by Robert]] pp 213