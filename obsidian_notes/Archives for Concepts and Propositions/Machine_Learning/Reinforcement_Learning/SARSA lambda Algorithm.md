---
tags:
  - concept
  - reinforcement_learning/algorithm
  - reinforcement_learning/theory
keywords:
  - sarsa_lambda_algorithm
  - eligibility_traces
topics:
  - reinforcement_learning/algorithm
name: SARSA lambda Algorithm
date of note: 2024-08-09
---

## Concept Definition

>[!important]
>**Name**: SARSA($\lambda$) Algorithm

![[Temporal Difference lambda Algorithm#^cba720]]

- [[Temporal Difference lambda Algorithm]]

>[!important] Definition
>In *SARSA($\lambda$)*, define the **eligibility trace** as a real-valued function for each state-action pair. That is,
>$$
>(x, a) \to e(x, a) \in \mathbb{R}
>$$
>
>Given state $X_{t}$ at time $t$, assume that $A_{t}$ is chosen, the **update rule** for *eligibility trace*  is
>$$
>\begin{align*}
> e_{t}(X_{t}, A_{t}) &= e_{t-1}(X_{t}, A_{t}) + 1 \\[5pt]
> e_{t}(x, a) &= \lambda\,e_{t-1}(x, a) \quad \forall (x, a) \neq (X_{t}, A_{t})
>\end{align*}
>$$

>[!important] Definition
>The **SARSA($\lambda$) update rule** for *state-value function* given **eligibility trace** $e(x, a)$ is defined as
>$$
> \begin{align}
> Q_{t+1}(X_{t}, A_{t}) &\leftarrow Q_{t}(X_{t}, A_{t}) + \alpha_{t}\left(R_{t+1} + \gamma Q_{t}(X_{t+1}, A_{t+1})  - Q_{t}(X_{t}, A_{t})\right)\;e_{t}(X_{t}, A_{t}) \\[5pt]
>&=   Q_{t}(X_{t}, A_{t}) + \alpha_{t}\,\delta_{t}\,e_{t}(X_{t}, A_{t})
> \end{align} 
>$$
>where $\delta_{t}$ is the **TD error** $$\delta_{t} := R_{t+1} + \gamma V_{t}(X_{t+1})  - V_{t}(X_{t}).$$


###  SARSA($\lambda$) Algorithm for Tabular Value Function Representation

>[!important] Definition
>The **tabular-based SARSA($\lambda$) algorithm** is described as below:
>- *Require*:  *policy* $\pi$,
>- *Require*: step size $\alpha_{t} >0$ for $t=1\,{,}\ldots{,}\,$
>- *Require*: reward *discount factor* $\gamma \in (0,1)$
>- *Require*: decay factor $\lambda\in [0,1]$
>- *Initialize* **table for action-value function** $Q_{0}(x, a)$ for all $x\in \mathcal{X}$ and $a\in \mathcal{A}$. 
>	- Note that the **terminal state** $Q_{0}(x_{\text{terminal}}, a) = 0$ for all $a\in \mathcal{A}$
>- For **episode** $k=1,\,2\,{,}\ldots{,}\,$:
>	- Initialize state $X_{0}$, and 
>	- Choose an *action* $A_{0}$ from $X_{0}$ based on policy derived from $Q_{0}$, $$A_{0} \sim \pi(\cdot\,|\,X_{0}\,)$$ 
>	- Initialize *eligibility trace* $e(x, a) =0$ for all $x\in \mathcal{X}$ and $a\in \mathcal{A}$
>	- For step $t=0,\,1\,{,}\ldots{,}\,T$:
>		- Take Action $A_{t}$
>		- Observe **reward** $R_{t+1}$ and **next state** $X_{t+1}$
>		- Generate the **next action** $A_{t+1}$ from *next state* $X_{t+1}$  based on policy $\pi$ derived from $Q_{t}$ $$A_{t+1} \sim \pi(\cdot\,|\,X_{t+1}\,)$$
>		- Compute the **temporal difference error** $$\delta_{t} = R_{t+1} + \gamma Q_{t}(X_{t+1}, A_{t+1})  - Q_{t}(X_{t}, A_{t}) $$
>		- Update **eligibility trace** for *all state-action pairs* 
>			- For observed state-action pair, $$e_{t}(X_{t}, A_{t}) = e_{t-1}(X_{t}, A_{t}) + 1$$ 
>			- For *unobserved state-action pair*, $$e_{t}(x, a) = e_{t-1}(x,a), \quad (x, a)\neq (X_{t}, A_{t})$$
>		- For *all state-action pair* $(x,a) \in \mathcal{X}\times \mathcal{A}$
>			- Update *action-value function* for **all state-action pair** (not just observed one) using **TD error** with **eligibility trace** $$Q_{t+1}(x, a) = Q_{t}(x, a) + \alpha\,\delta_{t}\, e_{t}(x, a)$$
>			- Update the *eligibility trace* with **$\lambda$-decay** $$e_{t}(x, a) \leftarrow  \gamma\,\lambda\,e_{t}(x, a)$$

- [[SARSA Algorithm and On-Policy Temporal Difference Control]]
- [[Temporal Difference lambda Algorithm]]





## Explanation





-----------
##  Recommended Notes and References


- [[Temporal Difference lambda Algorithm]]
- [[Eligibility Traces]]



- [[Multi-Step SARSA Algorithm Off-Policy]]
- [[Multi-Step Return and Multi-Step Temporal Difference Learning]]

- [[SARSA Algorithm and On-Policy Temporal Difference Control]]
- [[Temporal Difference Learning]]

- [[Prediction and Control Problems in Reinforcement Learning]]
- [[Value Function and Bellman Equation for MDP]]
- [[Monte Carlo and Applications]]

- [[Reinforcement Learning An Introduction by Sutton]] pp 303 - 307