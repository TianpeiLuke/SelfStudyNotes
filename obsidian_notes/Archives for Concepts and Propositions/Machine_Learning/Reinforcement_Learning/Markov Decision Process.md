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
  - reinforcement_learning/theory
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

^f5dcdf

>[!important] Definition
>When the reward depends on both current state and action and next state, the **expected rewards** at epoch $t$ is evaluated by computing
>$$
> r_{t}(x, a)= \sum_{u\in \mathcal{X}}\,r_{t}(x, a, u)\,p_{t}(u | x, a)
>$$

^f0b818

- [[Expected Payoff in Statistical Decision Problem]]


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

^c86b5a

- [[Markov Transition Kernel and Transition Function]]


### Markov Decision Process

![[Markov Chain and Markov Process#^793949]]


>[!important] Definition
>Let $(X_{t}, t\in T)$ be a *discrete-time stochastic process* where $T \subset \mathbb{N}$ is the index set, and $X_{t}\in \mathcal{X}$, 
>
>A **Markov decision process (MDP)** is a collection $\{T, \mathcal{X}, \mathcal{B}(\mathcal{X}), \mathcal{A}, \mathscr{F}_{\mathcal{A}}, K_{t}, r_{t}\}$ where
>- $\mathcal{X}$ is the *state space* of the stochastic process $(X_{t}, t\in T)$
>	- We can generalize to allow $\mathcal{X}_{t}$ to depend on $t$. $$\mathcal{X} = \bigcup_{t\in T}\mathcal{X}_{t}$$
>- $\mathcal{B}(\mathcal{X})$ is the *Borel $\sigma$-algebra* on $\mathcal{X}$
>- $\mathcal{A}$ is the set of all *allowable actions* and $\mathscr{F}_{\mathcal{A}}$ is the *$\sigma$-algebra* on $\mathcal{A}.$
>	- We can also generalize to allow $\mathcal{A}_{t}$ to depend on $t$ and state $x$. $$\mathcal{A}_{x} = \bigcup_{t\in T}\mathcal{A}_{x, t}.$$ 
>- $K_{t}:\mathcal{X} \times \mathcal{A}\times \mathcal{B}(\mathcal{X}) \to[0, \infty)$ is the *transition kernel* where $$p_{t}(A | x, a) := K_{t}(x, a, A)$$ represents the probability of state $X_{t+1}\in A$ given previous state $X_{t}=x$ and previous action $A_{t} = a$
>	- The transition function can be extended to represents the probability of *next state* and *next reward* given *current state* and *current action*. In particular, $$K_{t}: \mathcal{X} \times \mathcal{A}\times \mathcal{B}(\mathcal{X}) \times \mathscr{F}_{\mathcal{A}} \to[0, \infty)$$ where $$p_{t}(A_{X}, B_{\mathcal{A}} | x, a) := K_{t}(x. a, A_{X}, B_{\mathcal{A}})$$
>- $r_{t}: \mathcal{X} \times \mathcal{A} \to [0, \infty)$ is the *immediate reward* where $r_{t}(x, a)$ represents the *immediate rewards* received after transitioning from state $X_{t} = x$ due to action $a\in \mathcal{A}.$
>	- The reward may *depend on the next state*. In this case, let $$r_{t}: \mathcal{X} \times \mathcal{A} \times \mathcal{X} \to [0, \infty),$$   where $r_{t}(x, a, u)$ is the reward received *after* transitioning from state $X_{t} = x$ to  $X_{t+1} = u$, *due to action* $a.$

^a1e9de

- [[Markov Chain and Markov Process]]
- [[Markov Decision Processes by Puterman]] pp 19 - 20

### Decision Rule

>[!important] Definition
>A **Markov decision rule** is a *measurable function*  $$\delta_{t}: (\mathcal{X}, \mathcal{B}(\mathcal{X})) \to (\mathcal{A}_{x}, \mathscr{F}_{\mathcal{A}_{x}})$$ which specify at epoch $t$ the action choice when the system is *at state* $x \in \mathcal{X}$.
>
>- It is called **Markovian** since the decision for current action **only depends** on the *current state* $x_{t}$, *not history*.
>- It is **deterministic** since it choose an action without uncertainty. 

^63a761

>[!important] Definition
>For each $s\in T$, a *deterministic decision rule* is said to be **history dependent** if it is a *measurable function* (a *statistic*) $$\delta_{s}: (\mathcal{H}^{s}, \mathscr{F}_{\mathcal{H}}^{s}) \to (\mathcal{A}_{x}, \mathscr{F}_{\mathcal{A}_{x}})$$  
>where 
>$$
>\mathcal{H}^s = \prod_{i=1}^{s}\mathcal{X}_{i}\;\times \prod_{i=1}^{s-1}\mathcal{A}_{i},\quad h_{s} := \left(x_{1}, a_{1} \,{,}\ldots{,}\,x_{s-1}, a_{s-1}, x_{s}\right) \in \mathcal{H}^s.
>$$
>Moreover, the history can be defined *recursively*
>$$
>\mathcal{H}^s = \mathcal{H}^{s-1} \times \mathcal{A} \times \mathcal{X}, \quad h_{s} = (h_{s-1}, a_{s-1}, x_{s})
>$$

- [[Multi-Step Return and Multi-Step Temporal Difference Learning]]
- [[Multi-Step SARSA Algorithm On-Policy]]


>[!important] Definition
>For each $s\in T$,  a **randomized** *decision rule* $\delta_{t}$ specify a *probability distribution* $q_{\delta_{t}}$ on $\mathcal{A}$ based on history or current state, i.e.
>$$
>q_{\delta_{t}(\cdot)}(\cdot)  \in \mathscr{P}_{\mathcal{A}}
>$$
>where $\mathscr{P}_{\mathcal{A}}$ is the *space of all probability measures* on $(\mathcal{A}, \mathscr{F}_{\mathcal{A}})$.
>
>- A *randomized decision rule* is said to be **Markov** if it is a *measurable function* $$\delta_{t}: (\mathcal{X}, \mathcal{B}(\mathcal{X})) \to (\mathscr{P}_{\mathcal{A}}, \mathscr{F}_{\mathscr{P}_{\mathcal{A}}})$$
>- A *randomized decision rule* is said to be **history dependent** if it is a *measurable function*  $$\delta_{s}: (\mathcal{H}^{s}, \mathscr{F}_{\mathcal{H}}^{s}) \to (\mathscr{P}_{\mathcal{A}}, \mathscr{F}_{\mathscr{P}_{\mathcal{A}}})$$  

^1d9419

- [[Space of Bounded Signed Measures]]

>[!info]
>In the literature of reinforcement learning, we denote the **stationary randomized Markov decision rule** using conditional probability 
>$$
>\pi(a | x) = q_{\delta_{t}(x)}(a)
>$$
>Note that from definition of [[Conditional Probability]], for each $x\in \mathcal{X}$, $$\pi(\cdot | x) \in \mathscr{P}_{\mathcal{A}}$$

^56b9a5



### Returns and Expected Rewards

- [[Returns and Goals of Reinforcement Learning]]

>[!important] Definition
>When a decision rule is given, the *rewards* and *transition functions* become functions on current state $x$ or histories $h_{t}$.
>
>- For **Markov deterministic rule**, $$r_{t}(x, a) = r_{t}(x, \delta^{MD}_{t}(x)), \quad p_{t}(A| x, a) = p_{t}(A | x, \delta^{MD}_{t}(x))$$
>- For **History dependent rule**,  $$r_{t}(x, a) = r_{t}(x, \delta^{HD}_{t}(h_{t})), \quad p_{t}(A| x, a) = p_{t}(A | x, \delta^{HD}_{t}(h_{t}))$$

### Decision Policy

>[!important] Definition
>A **policy**, or **contingency plan**, or **plan**, or **strategy** specifies the *decision rule* to be used at *all decision epoch*. It provides the decision maker with a *prescription for action selection* under any possible future system state or history.
>
>A **policy** $\pi$ is a *sequence of decision rules*, i.e. $$\pi := \left(\delta_{1}, \delta_{2} \,{,}\ldots{,}\,\right)$$ where $\delta_{t}$ can be *deterministic* or *random*, *Markov* or *history dependent*.

^67062c


- [[Markov Decision Processes by Puterman]] pp 22

>[!important] Definition
>A *policy* is called **stationary** if $$\delta_{t} = \delta, \quad \forall t\in T.$$
>
>A *stationary policy* has the form $$\pi = \left(\delta, \delta \,{,}\ldots{,}\,\right).$$


## Explanation

>[!quote]
>The qualifier "**Markov**" is used because the *transition probability* and *reward functions* depend on the **past only** through the **current state** of the system and the **action selected** by the decision maker in that state. Under certain policies, the induced *stochastic process need not be Markov*. Some authors refer to the above collection of objects as a Markov decision problem; here that expression is reserved for a Markov decision process together with an *optimality criterion*.
>
>-- [[Markov Decision Processes by Puterman]] pp 20

>[!quote]
>A **fundamental question** in Markov decision problem theory is:
>
> For a given *optimality criterion*, **under what conditions** is it **optimal** to use a **deterministic Markovian decision rule** at each stage?
> 
>-- [[Markov Decision Processes by Puterman]] pp 21 


## Stochastic Process induced by MDP

>[!important] Definition
>The **stochastic process** behind the *Markov decision process* $$\{T, \mathcal{X}, \mathcal{B}(\mathcal{X}), \mathcal{A}, \mathscr{F}_{\mathcal{A}}, \,p_{t}(\cdot|x,a), \, r_{t}(x,a)\}$$ can be described as below:
>- Let $(\Omega, \mathcal{B}(\Omega))$ be measurable space 
>- The *sample space* $\Omega$ is defined as $$\Omega = \mathcal{X} \times \mathcal{A} \times \mathcal{X} \times \mathcal{A} \,{\times}\ldots{\times}\,$$
>	- If the MDP is **finite-horizon**, then $$\Omega = \{ \mathcal{X} \times \mathcal{A} \}^{T-1} \times \mathcal{X}$$
>	- If the MDP is **infinite-horizon**, then $$\Omega = \{ \mathcal{X} \times \mathcal{A} \}^{\infty} \times \mathcal{X}$$
>	- each element is called a **sample path** $$\omega = (x_{1}, a_{1}, x_{2}, a_{2} \,{,}\ldots{,}\,)$$
>- $\mathcal{B}(\Omega)$ is the *Borel $\sigma$-algebra* on $\Omega$
>- For $t\in T$, define *random variables* $X_{t}\in \mathcal{X}$ and $A_{t}\in \mathcal{A}$ such that $$X_{t}(\omega) = x_{t}, \quad A_{t}(\omega) = a_{t}$$
>- Define the **history process** $H_{t}$ by $$H_{1}(\omega) := x_{1}, \quad H_{t}(\omega) := (x_{1}, a_{1} \,{,}\ldots{,}\,x_{t})$$
>- Let the *probability distribution* $\mathcal{P}_{1}$ denote the **initial distribution** of system state $X_{1}$
>	- Assume **degenerate** $\mathcal{P}_{1}$, i.e. there exists some $x_{1}\in \mathcal{X}$ $$\mathcal{P}_{1}(X_{1} = x_{1}) = 1.$$
>- A **randomized history dependent policy** $\pi := (\delta_{1}, \delta_{2} \,{,}\ldots{,}\,)$  induces a probability measure $\mathcal{P}^{\pi}$ on $(\Omega, \mathcal{B}(\Omega))$ through $$\begin{align*}
> \mathcal{P}^{\pi}\left(X_{1} = x\right) &= \mathcal{P}_{1}(x) \\[5pt]
> \mathcal{P}^{\pi}\left(A_{t} = a | H_{t} = h_{t}\right) &= q(a \,;\, d_{t}(h_{t})) \\[5pt]
> \mathcal{P}^{\pi}\left(X_{t+1} = u \,|\, H_{t} = (h_{t-1}, a_{t-1}, x_{t})\,,\, A_{t} = a_{t}\right) &= p_{t}(u \,|\, x_{t}\,,\, a_{t})
>\end{align*}$$
>- The probability of any *finite-horizon sample path* $\omega = (x_{1}, a_{1}, x_{2}, a_{2} \,{,}\ldots{,}\,x_{T})$ is given by $$\mathcal{P}^{\pi}(x_{1}, a_{1}, x_{2}, a_{2} \,{,}\ldots{,}\,x_{T}) = \mathcal{P}_{1}(x_{1})\,q_{\delta_{t}(x_{1})}(a_{1})\,p_{1}(x_{2}|x_{1}\,,\,a_{1}) \,{}\ldots{}\,q_{\delta_{T-1}(h_{T-1})}(a_{T-1})\,p_{T-1}(x_{T}|x_{T-1}\,,\,a_{T-1})$$	
>- A **policy** $\pi$ is said to be **Markov**, if $\delta_{t}$ depends on the history only through the current state, i.e. $$\mathcal{P}^{\pi}\left(A_{t} = a | H_{t} = (h_{t-1}, a_{t-1}, x_{t})\right) =  \mathcal{P}\left(A_{t} = a| X_{t} = x_{t}\right) = q(a \,;\, d_{t}(x_{t}))$$
>	- In this case, the induced stochastic process $$\left(X_{t}, t\in T\right)$$ is a **discrete-time Markov process**.
>	- For **Markov policy**, the bivariate stochastic process $$\left((X_{t})\,, \,r_{t}\left(X_{t}, A_{t}\right),\, t\in T\right)$$ is called a **Markov reward process**.


- [[Stochastic Process]]
- [[Markov Chain and Markov Process]]
- [[Markov Decision Processes by Puterman]] pp 23

## Value Function and Bellman Equation

- [[Value Function and Bellman Equation for MDP]]
- [[Bellman Optimality Equation for MDP]]




-----------
##  Recommended Notes and References




- [[Policy Iteration Algorithm]]
- [[Value Iteration Algorithm]]
- [[Temporal Difference Learning]]
- [[Q Learning Algorithm and Off-Policy Temporal Difference Control]]

- [[Regret for Online Learning]]
- [[No-Regret Learning]]

- [[Sequential Decision Process]]
- [[Statistical Decision Problem]]




- [[Sequential Importance Sampling]]

- [[sigma Algebra]]
- [[Stochastic Process]]

- [[Reinforcement Learning An Introduction by Sutton]] pp 47- 71
- [[Distributional Reinforcement Learning by Bellemare]] pp 15, 42
- [[Markov Decision Processes by Puterman]] pp 36
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1118 - 1120
- [[Statistical Decision Theory by Berger]] pp 282
- [[Foundations of Machine Learning by Mohri]] pp 314
- [[Artificial Intelligence Modern Approach by Russell]] pp 647 - 686


- [[Probability and Measure by Billingsley]]
