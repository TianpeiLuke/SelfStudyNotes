---
tags:
  - concept
  - machine_learning/algorithms
  - reinforcement_learning/theory
  - reinforcement_learning/algorithm
  - algorithm/dynamic_programming
keywords:
  - dynamic_programming
  - markov_decision_process
  - reinforcement_learning
  - bellman_equation
  - bellman_optimality_equation
topics:
  - reinforcement_learning
  - algorithm
name: Bellman Optimality Equation on Markov Decision Process
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Bellman Optimality Equation on Markov Decision Process

![[Value Function and Bellman Equation for MDP#^e3c917]]

>[!important] Definition
>Value functions define a *partial ordering* over *policies*. 
>
>A *policy* $\pi$ is defined to be **better than** or **equal to** a *policy* $\pi^{'}$ if its *expected return* is greater than or equal to that of $\pi^{'}$ for all states. 
>
>In other words, $$\pi \ge \pi^{'} \iff v_{\pi}(x) \ge v_{\pi^{'}}(x), \quad \forall x \in \mathcal{X}.$$ 
>
>There is *always* **at least one policy** that is *better than or equal to all other policies*. This is an **optimal policy**. We denote all optimal policies by $\pi_{*}$.

- [[Value Function and Bellman Equation for MDP]]
- [[Simple Order Relation]]

### Optimal Policy

>[!important] Definition
>Given all *state-value functions* $v_{\pi}(x), \; x\in \mathcal{X}$, the **optimal state-value function**, denoted by $v_{*}$, is defined as
>$$
>v_{*}(x) := \max_{\pi} v_{\pi}(x), \quad \forall x\in \mathcal{X}.
>$$

>[!important] Definition
>Given all *action-value functions* $q_{\pi}(x, a), \; x\in \mathcal{X}, a\in \mathcal{A}_{x}$, the **optimal action-value function**, denoted by $q_{*}$, is defined as
>$$
>q_{*}(x, a) := \max_{\pi} q_{\pi}(x, a), \quad \forall x\in \mathcal{X}, \, a\in \mathcal{A}_{x}.
>$$

>[!important]
>The following **equations** describe the relation between the **optimal state-value function** and the **optimal action-value function**
>$$
>q_{*}(x, a) = \mathbb{E}^{\pi}\left[  R_{t+1} + \gamma\,v_{*}(X_{t+1}) \,|\,X_{t} =x, \, A_{t} = a  \right], \quad \forall x\in \mathcal{X}, \, a\in \mathcal{A}_{x}.
>$$
>and
>$$
>v_{*}(x) = \max_{a \in \mathcal{A}_{x}}q_{*}(x, a)
>$$

>[!info]
>$$
>\begin{align*}
> q_{\pi}(x, a) &= \mathbb{E}^{ \pi }\left[  R_{t+1} + \gamma\,G_{t+1}\,|\,X_{t} = x,\,A_{t} = a \right] \\[5pt]
> &=  \mathbb{E}^{ \pi }\left[  R_{t+1} + \gamma\, \mathbb{E}^{ \pi }\left[  G_{t+1} \,|\,X_{t+1}  \right]\,|\,X_{t} = x,\,A_{t} = a \right] \\[5pt]
> &:= \mathbb{E}^{ \pi }\left[  R_{t+1} + \gamma\, v_{\pi}(X_{t+1})\,|\,X_{t} = x,\,A_{t} = a \right]
>\end{align*}
>$$


### Bellman Optimality Equation

![[Value Function and Bellman Equation for MDP#^8c1d01]]

![[Value Function and Bellman Equation for MDP#^f9fda7]]


>[!important] Definition
>Given 
>- a *stationary Markov decision process* $$\{T, \mathcal{X}, \mathcal{B}(\mathcal{X}), \mathcal{A}, \mathscr{F}_{\mathcal{A}}\,,\, p(\cdot|x, a)\,,\, r(x, a)\},$$
>- and a *stationary Markov policy* $\pi = (\delta_{1}, \delta_{2} \,{,}\ldots{,}\,)$ where each $\delta_{t} = \delta$ is *randomized Markov decision rule* $$\delta: x \mapsto q_{\delta(x)}(\cdot) := \pi(\cdot | x) \in \mathscr{P}_{\mathcal{A}},$$
>- the *reward* at $t$ is denoted as $$R_{t+1} := r(X_{t}, A_{t}), \quad A_{t} \sim q_{\delta_{t}(x)}$$ 
>- $\gamma_{t} \in [0,1]$ is the *discount factor*,
>
>the **Bellman equation** *for* $v_{*}$, or the **Bellman optimality equation** for *state-value function* is obtained as
>$$
>\begin{align*}
> v_{*}(x) &= \max_{a \in \mathcal{A}_{x}}\,q_{*}(x, a)\\[5pt]
> &= \max_{a \in \mathcal{A}_{x}}\, \mathbb{E}^{\pi^{*}}\left[  R_{t+1} + \gamma\,v_{*}(X_{t+1}) \,|\,X_{t} =x, \, A_{t} = a  \right] \\[5pt]
> &= \max_{a \in \mathcal{A}_{x}}\,\sum_{u \in \mathcal{X}}p(u | x, a)\left[\, r(x, a) + \gamma v_{*}(u) \,\right], \quad \forall x\in \mathcal{X}
>\end{align*}
>$$

>[!important]
>For the *four argument transition function*, the **Bellman optimality equation** for *state-value function*
>$$
>v_{*}(x)  = \max_{a \in \mathcal{A}_{x}}\,\sum_{u \in \mathcal{X}}\sum_{r \in \mathcal{R}}p(u, r | x, a)\left[\, r + \gamma v_{*}(u) \,\right] , \quad \forall x \in \mathcal{X}
>$$

>[!important] Definition
>Given 
>- a *stationary Markov decision process* $$\{T, \mathcal{X}, \mathcal{B}(\mathcal{X}), \mathcal{A}, \mathscr{F}_{\mathcal{A}}\,,\, p(\cdot|x, a)\,,\, r(x, a)\},$$
>- and a *stationary Markov policy* $\pi = (\delta_{1}, \delta_{2} \,{,}\ldots{,}\,)$ where each $\delta_{t} = \delta$ is *randomized Markov decision rule* $$\delta: x \mapsto q_{\delta(x)}(\cdot) := \pi(\cdot | x) \in \mathscr{P}_{\mathcal{A}},$$
>- the *reward* at $t$ is denoted as $$R_{t+1} := r(X_{t}, A_{t}), \quad A_{t} \sim q_{\delta_{t}(x)}$$ 
>- $\gamma_{t} \in [0,1]$ is the *discount factor*,
>
>the **Bellman equation** *for* $q_{*}$, or the **Bellman optimality equation** for *action-value function* is obtained as
>$$
>\begin{align*}
> q_{*}(x, a) &= \mathbb{E}^{\pi}\left[  R_{t+1} + \gamma\,v_{*}(X_{t+1}) \,|\,X_{t} =x, \, A_{t} = a  \right]\\[5pt]
> &= \mathbb{E}^{\pi}\left[  R_{t+1} + \gamma\,\max_{a' \in \mathcal{A}}q_{*}(X_{t+1}, a') \,|\,X_{t} =x, \, A_{t} = a  \right]\\[5pt]
> &= \sum_{u \in \mathcal{X}}p(u | x, a)\,\left[ r(x, a) + \gamma\,\max_{a' \in \mathcal{A}}q_{*}(u, a') \right], \quad \forall x\in \mathcal{X}, a\in \mathcal{A}
>\end{align*}
>$$


>[!important]
>For the *four argument transition function*, the **Bellman optimality equation** for *action-value function*
>$$
>q_{*}(x, a)  = \sum_{u \in \mathcal{X}}\sum_{r\in \mathcal{R}}\,p(u, r | x, a)\,\left[ r + \gamma\,\max_{a' \in \mathcal{A}}q_{*}(u, a') \right]  , \quad \forall x \in \mathcal{X}, a\in \mathcal{A}
>$$

## Explanation

>[!important]
>For **discrete-state** $\mathcal{X}$ MDP,  
>- the Bellman equation for $v_{*}$ is a **system of $|\mathcal{X}|$ equations.**
>- the Bellman equation for $q_{*}$ is a **system of $|\mathcal{X}| \times|\mathcal{A}|$ equations.**






-----------
##  Recommended Notes and References

- [[Dynamic Programming for Optimal Stopping]]
- [[Value Function and Bellman Equation for MDP]]
- [[Markov Decision Process]]


- [[Reinforcement Learning An Introduction by Sutton]] pp 62 - 67
- [[Markov Decision Processes by Puterman]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1135

