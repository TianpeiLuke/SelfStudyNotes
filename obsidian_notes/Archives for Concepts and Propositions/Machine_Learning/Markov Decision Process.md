---
tags:
  - concept
  - machine_learning/theory
  - reinforcement_learning/theory
  - statistics/decision_theory
  - math/stochastic_process
keywords:
  - markov_decision_process
  - stochastic_process
  - statistical_decision_theory
topics:
  - machine_learning_theory
name: Markov Decision Process
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Markov Decision Process

![[Statistical Decision Problem#^1e4cc1]]

![[Sequential Decision Process#^827f09]]


- [[Sequential Decision Process]]
- [[Stochastic Process]]
- [[Statistical Decision Problem]]
- [[Parametric Models]]
- [[Statistical Decision Theory by Berger]] pp 282

### Reward

>[!important] Definition
>At each epoch $t\in T$, the **reward function** is defined as  
>$$
>r_{t}: \mathcal{X}_{t} \times \mathcal{A}_{t}  \to [0, \infty)
>$$
>where at the *decision epoch* $t\in T$, the **reward** received by *taking action* $a \in \mathcal{A}_{t}$ *in state* $x \in \mathcal{X}$ is denoted as 
>$$
>r_{t}(x, a)
>$$
>
>Sometimes, the reward function also depends on *the next state*, which is defined as
>$$
>r_{t}: \mathcal{X}_{t} \times \mathcal{A}_{t} \times \mathcal{X}_{t+1} \to [0, \infty)
>$$ 
>and the **reward** received at epoch $t$  by *taking action* $a \in \mathcal{A}_{t}$ *in state* $x \in \mathcal{X}_{t}$ at epoch $t$ and the system reaching to state $u\in \mathcal{X}_{t+1}$ is denoted as 
>$$
>r_{t}(x, a, u)
>$$

### Transition Probability

>[!important] Definition
>At each epoch $t\in T$, a **transition probability function** (or **transition kernel**) is a function $K_{t}$ defined on $\mathcal{X}_{t} \times \mathcal{A}_{t}\times \mathcal{B}(\mathcal{X}_{t+1})$ such that 
> 1. $\forall (x,a) \in \mathcal{X}_{t} \times \mathcal{A}_{t}$,    $K_{t}(x, a, \cdot)$  is a **probability measure** on $\mathcal{B}(\mathcal{X}_{t+1})$;
> 2. $\forall A \in \mathcal{B}(\mathcal{X}_{t+1})$,    $K_{t}(\cdot, \cdot, A)$ is a **measurable** function on $\mathcal{X}_{t} \times \mathcal{A}_{t}$.
>    
>Denote the transition probability at epoch $t$ as 
>$$
>p_{t}(A | x, a) := K_{t}(x, a, A)
>$$    
>
>The transition function can be extended to represents the probability of *next state* $X_{t+1}\in A_{X}$ and *next reward* $R_{t}\in B_{\mathcal{A}}$ given *current state* $X_{t} =x$ and *current action* $a$. In particular, $$K_{t}: \mathcal{X} \times \mathcal{A}\times \mathcal{B}(\mathcal{X}) \times \mathscr{F}_{\mathcal{A}} \to[0, \infty)$$ where $$p_{t}(A_{X}, B_{\mathcal{A}} | x, a) := K_{t}(x. a, A_{X}, B_{\mathcal{A}}).$$

- [[Markov Transition Kernel and Transition Function]]


### Markov Decision Process

![[Markov Chain and Markov Process#^793949]]


>[!important] Definition
>Let $(X_{t}, t\in T)$ be a *discrete-time stochastic process* where $T \subset \mathbb{N}$ is the index set, and $X_{t}\in \mathcal{X}$, 
>
>A **Markov decision process** is a collection $\{T, \mathcal{X}, \mathcal{B}(\mathcal{X}), \mathcal{A}, \mathscr{F}_{\mathcal{A}}, K_{t}, r_{t}\}$ where
>- $\mathcal{X}$ is the *state space* of the stochastic process $(X_{t}, t\in T)$
>	- We can generalize to allow $\mathcal{X}_{t}$ to depend on $t$. $$\mathcal{X} = \bigcup_{t\in T}\mathcal{X}_{t}$$
>- $\mathcal{B}(\mathcal{X})$ is the *Borel $\sigma$-algebra* on $\mathcal{X}$
>- $\mathcal{A}$ is the set of all *allowable actions* and $\mathscr{F}_{\mathcal{A}}$ is the *$\sigma$-algebra* on $\mathcal{A}.$
>	- We can also generalize to allow $\mathcal{A}_{t}$ to depend on $t$ and state $x$. $$\mathcal{A}_{x} = \bigcup_{t\in T}\mathcal{A}_{x, t}.$$ 
>- $K_{t}:\mathcal{X} \times \mathcal{A}\times \mathcal{B}(\mathcal{X}) \to[0, \infty)$ is the *transition functions* where $$p_{t}(A | x, a) := K_{t}(x, a, A)$$ represents the probability of state $X_{t+1}\in A$ given previous state $X_{t}=x$ and previous action $A_{t} = a$
>	- The transition function can be extended to represents the probability of *next state* and *next reward* given *current state* and *current action*. In particular, $$K_{t}: \mathcal{X} \times \mathcal{A}\times \mathcal{B}(\mathcal{X}) \times \mathscr{F}_{\mathcal{A}} \to[0, \infty)$$ where $$p_{t}(A_{X}, B_{\mathcal{A}} | x, a) := K_{t}(x. a, A_{X}, B_{\mathcal{A}})$$
>- $r_{t}: \mathcal{X} \times \mathcal{A} \to [0, \infty)$ is the *immediate reward* where $r_{t}(x, a)$ represents the *immediate rewards* received after transitioning from state $X_{t} = x$ due to action $a\in \mathcal{A}.$
>	- The reward may *depend on the next state*. In this case, let $$r_{t}: \mathcal{X} \times \mathcal{A} \times \mathcal{X} \to [0, \infty),$$   where $r_{t}(x, a, u)$ is the reward received *after* transitioning from state $X_{t} = x$ to  $X_{t+1} = u$, *due to action* $a.$

- [[Markov Chain and Markov Process]]
- [[Markov Decision Processes by Puterman]] pp 19 - 20

### Decision Rule and Decision Policy

>[!important] Definition
>A **Markov decision rule** is a *measurable function* (a *statistic*) $$d_{t}: (\mathcal{X}, \mathcal{B}(\mathcal{X})) \to (\mathcal{A}, \mathscr{F}_{\mathcal{A}})$$ 
>That is, the decision for current action **only depends** on the **current state** $x_{t}$, **not history** $$h_{t} := (x_{1}, a_{1} \,{,}\ldots{,}\, x_{t-1}, a_{t-1}, x_{t})$$





## Explanation

>[!quote]
>The qualifier "**Markov**" is used because the *transition probability* and *reward functions* depend on the **past only** through the **current state** of the system and the **action selected** by the decision maker in that state. Under certain policies, the induced *stochastic process need not be Markov*. Some authors refer to the above collection of objects as a Markov decision problem; here that expression is reserved for a Markov decision process together with an *optimality criterion*.
>
>-- [[Markov Decision Processes by Puterman]] pp 20



-----------
##  Recommended Notes and References

- [[Policy Iteration Algorithm]]
- [[Value Iteration]]
- [[Temporal Difference Learning]]
- [[Q Learning Algorithm]]

- [[Statistical Decision Problem]]




- [[Sequential Importance Sampling]]

- [[sigma Algebra]]
- [[Stochastic Process]]

- [[Reinforcement Learning An Introduction by Sutton]]
- [[Markov Decision Processes by Puterman]] pp 36
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Statistical Decision Theory by Berger]] pp 282



- [[Probability and Measure by Billingsley]]
