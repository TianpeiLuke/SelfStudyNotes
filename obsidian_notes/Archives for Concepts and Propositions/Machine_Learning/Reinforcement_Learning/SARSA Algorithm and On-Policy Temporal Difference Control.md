---
tags:
  - concept
  - machine_learning/algorithms
  - reinforcement_learning/algorithm
keywords:
  - on_policy_learning
  - temporal_difference_learning
  - sarsa_algorithm
topics:
  - reinforcement_learning/algorithm
name: Sarsa Algorithm and On-Policy Temporal Difference Control
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Sarsa Algorithm and On-Policy Temporal Difference Control

![[Temporal Difference Learning#^a52316]]

### SARSA Update

>[!important]
>In **SARSA update**, we need to estimate the *action-value function* $Q(X, a)$ using *TD learning*.

>[!info]
>  we recall the **Bellman equation** for *action-value function* $q$ and state-value function $v$ as below. 
> $$ 
> \begin{align}
> v_{\pi}(s) &=    \mathbb{E}_{ \pi }\left[ R_{t+1}  + \gamma\,v_{\pi}(X_{t+1}) | X_{t} = x \right] \nonumber\\
> q_{\pi}(x, a) &=  \mathbb{E}_{ \pi }\left[ R_{t+1} + \gamma q_{\pi}(X_{t+1}, A_{t+1}) | X_{t}=x, A_{t}=a \right]
> \end{align}
>$$  

>[!important] Definition
>**SARSA** update derive the TD prediction from the *equation* of **action-value function**.
>$$
> \begin{align}
> Q(X_{t}, A_{t}) &\leftarrow Q(X_{t}, A_{t}) + \alpha_{t}\left[ R_{t+1} + \gamma Q(X_{t+1}, A_{t+1})  - Q(X_{t}, A_{t}) \right] . 
> \end{align}
>$$   
>The name of **SARSA** comes from the fact that the update is controlled by the **tuple** $$(X_{t}, A_{t}, R_{t+1}, X_{t+1}, A_{t+1}).$$ 
>Unlike the TD prediction, here we need to **sample a new action** based on the new state and policy.

^cf105f

- [[Value Function and Bellman Equation for MDP]]

### SARSA for Prediction

>[!important] Definition
>The general form of the **SARSA control algorithm** or the **state-action-reward-state-action** algorithm is given in the following. Like **on-policy Monte Carlo control**, we have to *balance* the *exploration-exploitation* by choosing $\pi$ as $\epsilon$-soft.
>
>- *Require*: **$\epsilon$-soft policy** $\pi$, i.e. $$\pi(a| x) \ge \frac{\epsilon}{|\mathcal{A}(x)|},\, \forall a\in \mathcal{A}(x)$$
>- *Require*: step size $\alpha_{t} >0$ for $t=1\,{,}\ldots{,}\,$
>- *Require*: reward *discount factor* $\gamma >0$
>- *Initialize* **table for action-value function** $Q_{0}(x, a)$ for all $x\in \mathcal{X}$ and $a\in \mathcal{A}$. 
>	- Note that the **terminal state** $Q_{0}(x_{\text{terminal}}, a) = 0$ for all $a\in \mathcal{A}$
>- For **episode** $k=1,\,2\,{,}\ldots{,}\,$:
>	- Initialize state $X_{0}$
>	- For step $t=0,\,1\,{,}\ldots{,}\,T$:
>		- Choose **action** $A_{t}$ given policy $\pi$ and **current state** $X_{t}$ $$A_{t} \sim \pi(\cdot\,|\,X_{t}\,)$$
>		- Observe **reward** $R_{t+1}$ and **next state** $X_{t+1}$
>		- Generate the **next action** $A_{t+1}$ according to policy $\pi$ and *next state* $X_{t+1}$ $$A_{t+1} \sim \pi(\cdot\,|\,X_{t+1}\,)$$
>		- **SARSA update** on entry $(X_{t}, A_{t})$ as  $$Q_{t+1}(X_{t}, A_{t}) = Q_{t}(X_{t}, A_{t}) + \alpha_{t}\left[ R_{t+1} + \gamma Q_{t}(X_{t+1}, A_{t+1})  - Q_{t}(X_{t}, A_{t}) \right] $$

- [[epsilon-Greedy Algorithm]]
- [[Exploration and Exploitation Tradeoff]]
- [[Prediction and Control Problems in Reinforcement Learning]]

### SARSA for On-Policy Control

>[!important] Definition
>The general form of the **SARSA control algorithm** for **on-policy control** is described as 
>
>- *Require*: action space $\mathcal{A}(x)$
>- *Require*: step size $\alpha_{t} >0$ for $t=1\,{,}\ldots{,}\,$
>- *Require*: reward *discount factor* $\gamma >0$
>- *Require*: $\epsilon >0$ controls the exploration.
>- *Initialize* **table for action-value function** $Q_{0}(x, a)$ for all $x\in \mathcal{X}$ and $a\in \mathcal{A}$. 
>	- Note that the **terminal state** $Q_{0}(x_{\text{terminal}}, a) = 0$ for all $a\in \mathcal{A}$
>- For **episode** $k=1,\,2\,{,}\ldots{,}\,$:
>	- Initialize state $X_{0}$
>	- For step $t=0,\,1\,{,}\ldots{,}\,T$:
>		- *Randomly generate* an action $A \sim \text{Uniform}(\mathcal{A}(X_{t}))$
>		- Choose **action** $A_{t}$ given $Q_{t}$ and **current state** $X_{t}$ according to the **$\epsilon$-greedy policy** $$A_{t} = \left\{ \begin{array}{cc} A & \text{ with probability }\epsilon\\ \arg\max_{a\in \mathcal{A}(X_{t})}\,Q_{t}(X_{t}, a) &\text{ with probability }1 - \epsilon \end{array} \right.$$
>		- Observe **reward** $R_{t+1}$ and **next state** $X_{t+1}$
>		- Randomly generate an action $A' \sim \text{Uniform}(\mathcal{A})$
>		- Generate the **next action** $A_{t+1}$ according to the same **$\epsilon$-greedy policy** $$A_{t+1} = \left\{ \begin{array}{cc} A' & \text{ with probability }\epsilon\\ \arg\max_{a\in \mathcal{A}(X_{t+1})}\,Q_{t}(X_{t+1}, a) &\text{ with probability }1 - \epsilon \end{array} \right.$$
>		- **SARSA update** on entry $(X_{t}, A_{t})$ as  $$Q_{t+1}(X_{t}, A_{t}) = Q_{t}(X_{t}, A_{t}) + \alpha_{t}\left[ R_{t+1} + \gamma Q_{t}(X_{t+1}, A_{t+1})  - Q_{t}(X_{t}, A_{t}) \right] $$

- [[Prediction and Control Problems in Reinforcement Learning]]

## Explanation

>[!info]
>TD prediction methods can be used for the **control problem**. Note that in **Generalized Policy Iteration (GPI)**, the policy improvement is obtained by choosing *greedy/$\epsilon$-greedy policy* with respect to the action-value function. 
>
>**SARSA algorithm** only substitute the *TD methods* for the **evaluation** or **prediction part** in the GPI.  

>[!important]
>Sarsa algorithm is **on-policy control**, since the policy used to *generate actions* is the *same policy* that is *updated*. 
>
>As in all on-policy methods, we continually estimate $q_{\pi}$ for the **behavior policy** $\pi$, and at the same time change $\pi$ toward *greediness* with respect to $q_{\pi}$. 
>

- [[On-Policy and Off-Policy Reinforcement Learning]]
- [[Prediction and Control Problems in Reinforcement Learning]]

## Temporal Difference Learning for Action-Value Function

>[!info]
>Similar to how TD prediction is derived from the equation of **state-value function**, **SARSA** derive the TD prediction from the *equation* of **action-value function**.
>$$
> \begin{align}
> V(S_{t}) &\leftarrow V(S_{t}) + \alpha_{t}\left[ R_{t+1} + \gamma V(S_{t+1})  - V(S_{t}) \right] . &\text{ TD(0)} \nonumber\\[5pt]
> Q(S_{t}, A_{t}) &\leftarrow Q(S_{t}, A_{t}) + \alpha_{t}\left[ R_{t+1} + \gamma Q(S_{t+1}, A_{t+1})  - Q(S_{t}, A_{t}) \right] . &\text{ SARSA}
> \end{align}
>$$ 
>We see that the estimate of *state-value function* $Q$ at time $t$ depends on the state-value function estimate at $t+1$, rewards at $t+1$. 

- [[Temporal Difference Learning]]






-----------
##  Recommended Notes and References


- [[Temporal Difference Learning]]

- [[Dynamic Programming for MDP]]
- [[Value Function and Bellman Equation for MDP]]
- [[Markov Decision Process]]



- [[Reinforcement Learning An Introduction by Sutton]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1142 - 1143
- [[Foundations of Machine Learning by Mohri]] pp 334