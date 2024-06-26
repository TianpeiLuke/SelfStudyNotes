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
>Let $(X_{n})$ be a *discrete-state Markov chain* on $\mathcal{X}$.
>
>A state $x \in \mathcal{X}$ is called  **recurrent** if $$\mathcal{P}( \tau_{x} < \infty | X_{0} = x) = 1,$$ i.e. the *first hitting time*  at initial state $x$ is finite.

^8a85fa

- [[Stopping Time of Markov Chain]]
- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]

>[!important] Definition
>Let $(X_{n})$ be a *discrete-time discrete-state Markov chain* on $\mathcal{X}$.
>
>A state $x \in \mathcal{X}$ is called  **transient** if $$\mathcal{P}( \tau_{x} < \infty | X_{0} = x) < 1.$$


 ![[Positive Recurrent Markov Chain#^de7c69]]

- [[Positive Recurrent Markov Chain]]

### Harris Chain

>[!important] Definition
>Let $(X_{n})$ be a Markov chain with *possibly uncountable-state  (i.e. Harris chain)* on $\mathcal{X}$.
>
>A set $A \subset \mathcal{X}$ is called  **recurrent** if $$\mathbb{E}\left[\eta_{A} \;|\;X_{0} = x \right] = +\infty, \; \forall x\in A,$$  i.e. the *expected total number of returning* to $A$ is infinity.

^4e0184

- [[Number of Passages and Probability of Finite Return]]

>[!important] Definition
>Let $(X_{n})$ be a Markov chain with *possibly uncountable-state  (i.e. Harris chain)* on $\mathcal{X}$.
>
>A set $A \subset \mathcal{X}$ is called  **uniformly transient** if there exists some constant $M >0$ such that $$\mathbb{E}\left[\eta_{A} \;|\;X_{0} = x \right] < M, \; \forall x\in A,$$  i.e.  the *expected total number of returning* to $A$ is *finite*.

>[!important] Definition
>Let $(X_{n})$ be a Markov chain with *possibly uncountable-state  (i.e. Harris chain)* on $\mathcal{X}$.
>
>A set $A \subset \mathcal{X}$ is called  **transient** if there exists a **countable covering** of $A$ by *uniformly transient sets*; that is, there exists a *countable collection* of *uniformly transient sets* $B_{i}$ such that $$A := \bigcup_{i}B_{i}$$

- [[Covering of Set and Open Covering of Topological Set]]

![[Positive Recurrent Markov Chain#^17e86b]]

![[Positive Recurrent Markov Chain#^4850a2]]

- [[Positive Recurrent Markov Chain]]
- [[Invariant Measure and Stationary Distribution]]

### Harris Recurrence

![[Harris Recurrent Set and Harris Recurrent Markov Chain#^f40444]]

- [[Harris Recurrent Set and Harris Recurrent Markov Chain]]


## Explanation

>[!info]
>A state is **recurrent** if the Markov Chain will *return to* the state $x$ after stating from $x$.

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

## Criterion of Recurrence

### Discrete State Markov Chain

>[!important] Proposition
>Let $(X_{n})$ be a *discrete-state Markov chain* on $\mathcal{X}$.
>
>The following conditions are **equivalent**:
>
>-  state $x\in \mathcal{X}$ is **recurrent state**;
>- The **ever returning probability** $$\mathcal{P}\left(\tau_{x} < \infty | X_{0}= x\right) = 1;$$
>- The **probability of infinite total number of visiting** is $$P(\eta_{x} = \infty |\, X_{0} = y) = \mathcal{P}\left(\tau_{x} < \infty | X_{0}= y\right)$$ and $$P(\eta_{x} = \infty |\, X_{0} = x) = 1;$$ where $$\eta_{x} := \sum_{n=1}^{\infty}\mathbb{1}\left(X_{n} \in x\right).$$
>- The **expected total number of returning** is *infinite* $$\mathbb{E}\left[\eta_{x} | X_{0}= x\right] = \infty;$$ 
>- The *sum* of all **$n$-step return probabilities** $$\sum_{n=0}^{\infty}K^{n}(x, x) = \infty.$$
>

^18549b

- [[Stopping Time of Markov Chain]]
- [[Number of Passages and Probability of Finite Return]]
- [[Recursion Formulas for Discrete State Markov Chain]]


>[!info]
>For **discrete-state Markov chain**, **recurrent** set and **Harris recurrent** set are the same.


### Harris Chain

>[!important] 
>For a Harris chain $(X_{n})$, the followings are **equivalent**:
>-  set $A \in \mathcal{B}(\mathcal{X})$ is **Harris recurrent**;
>- The **ever returning probability** $$\mathcal{P}\left(\tau_{A} < \infty | X_{0}= x\right) = 1;\quad \forall x\in A$$
>- The **probability of infinite total number of visiting** is $$P(\eta_{A} = \infty |\, X_{0} = x) = 1;\quad \forall x\in A$$ 

- [[Harris Recurrent Set and Harris Recurrent Markov Chain]]


>[!info]
>Note that the definition of **recurrent** is **weaker** than **Harris recurrent** if the state space is **uncountable**
>  
>In other word, for any $x\in A$,
>$$
>P(\eta_{A} = \infty |\, X_{0} = x) \neq 0 \implies \mathbb{E}\left[\eta_{A} | X_{0}= x\right] = \infty
>$$
>But there exists example such that 
>$$
>P(\eta_{A} = \infty |\, X_{0} = x) = 0 \quad\text{ but }\quad \mathbb{E}\left[\eta_{A} | X_{0}= x\right] = \infty
>$$




## Classification of States

### Discrete-State Case

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

^89b449

- [[Recurrent Markov Chain]]
- [[Irreducibility of Markov Chain]]

>[!important]
>Based above proposition, we can **classify** each class, and an **irreducible Markov Chain** as **recurrent** or **transient**. 



### Uncountable-State Case

>[!important] Theorem 
>Let $(X_{n})$ be **$\mu$-irreducible** Markov chain with **accessible atom** $\alpha$.
>
>- If $\alpha$ is **recurrent**, every set $A\in \mathcal{B}(\mathcal{X})$ such that $\mu(A) > 0$ is **recurrent**;
>- If $\alpha$ is **transient**, the entire state space $\mathcal{X}$ is **transient**.

^50067d

- [[Recurrent Markov Chain]]
- [[Atom of Markov Chain]]
- [[Irreducibility of Markov Chain]]

>[!important] Theorem
>A **$\mu$-irreducible** chain is either **recurrent** or **transient**.


## Finite Discrete State Markov Chain

>[!important] Theorem
>If a *closed subset* $S_0 \subset \mathcal{X}$ only has **finitely many states**, then there must be **at least one recurrent state**. 
>
>In particular any **finite Markov chain** must contain **at least one positive recurrent state**. 

- [[Positive Recurrent Markov Chain]]






-----------
##  Recommended Notes and References

- [[Harris Recurrent Set and Harris Recurrent Markov Chain]]
- [[Irreducibility of Markov Chain]]

- [[Communicate as Equivalence State Relation for Markov Chain]]
- [[Markov Chain and Markov Process]]

- [[Monte Carlo Statistical Methods by Robert]] pp 213, pp 220