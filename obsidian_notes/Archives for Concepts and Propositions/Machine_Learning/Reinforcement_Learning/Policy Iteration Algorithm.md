---
tags:
  - concept
  - machine_learning/algorithms
  - reinforcement_learning/algorithm
keywords:
  - policy_iteration
topics:
  - reinforcement_learning/algorithm
name: Policy Iteration Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Policy Iteration Algorithm

>[!important] Definition
>The **policy iteration** finds the *optimal policy* $\pi^{*}$ by iteratively running the following two tasks
>- **policy evaluation** task: *estimating* the value function $v_{\pi}$ or $q_{\pi}$ given policy $\pi$
>- **policy improvement** task: find the *optimal policy* $\pi$ given estimated value functions $v_{\pi}$ or $q_{\pi}$.

![[Dynamic Programming for MDP#^d0f53b]]

>[!important] Definition
>The **policy iteration** estimates the *optimal policy* $\pi^{*}$ by the followings steps:
>- *Require*: action space $\mathcal{A}(x)$
>- *Require*: the *state-value functions* $V(x)$ for all $x\in \mathcal{X}$
>- *Require*: the **policy** $\pi(a|x)$ for all $a\in \mathcal{A}(x)$ and $x\in \mathcal{X}$
>- *Require*: the **Markov transition function** $p(x'| x, a)$
>- *Require*: the **reward function** $r(x, a)$
>- *Require*: $\delta >0$
>- *Initialize* the value function $V_{0}(x)$ for all $x\in \mathcal{X}$
>- *Initialize* the policy function $\pi_{0}(a|x)$ for all $a\in \mathcal{A}(x)$ and $x\in \mathcal{X}$
>- **Policy Evaluation (Prediction)**, i.e. estimate $V(x)$
>	- While $\Delta \ge \delta$:
>		- $\Delta = 0$
>		- For each state $x\in \mathcal{X}$:
>			- $v_{cur} = V(x)$
>			- Update **value function** via **Bellman equation** $$V(x) \leftarrow \sum_{a \in \mathcal{A}}\pi(a | x) \sum_{u \in \mathcal{X}}\,p(u | x, a)\,\left[r(x, a) + \gamma\,V(u)  \right]$$
>			- Find the total variation $$\Delta \leftarrow \max\left( \Delta, \lvert v_{cur} - V(x) \rvert  \right)$$
>- **Policy Improvement**, i.e. estimate $\pi(a|x)$ based on $V$
>	- Set *policy stable flag* $f_{stable} = True$
>	- For each state $x\in \mathcal{X}$:
>		- Obtain the probability of each actions under given policy and state $$\pi_{cur} = \pi(\cdot|x)$$
>		- Update the **policy** via **greedy algorithm (deterministic)**. That is, for all $a\in \mathcal{A}(x)$ $$\pi(a|x) = \mathbb{1}\left\{ a\in \arg\max_{a\in \mathcal{A}(x)}\sum_{u\in \mathcal{X}}p(u|x, a)\left[ r(x, a) + \gamma\,V(u) \right] \right\}$$
>		- If $\pi_{cur} \neq  \pi(\cdot|x)$:
>			- $f_{stable} = False$
>- If $f_{stable} = True$
>	- *Return* **optimal policy** $\pi \approx \pi^{*}$ and **optimal value** $V \approx v^{*}$
>- Else
>	- Repeat the **Policy Evaluation (Prediction)** and **Policy Improvement** steps.





- [[Dynamic Programming for MDP]]
- [[Value Function and Bellman Equation for MDP]]
- [[Markov Decision Process]]

## Explanation





-----------
##  Recommended Notes and References


- [[Dynamic Programming for MDP]]
- [[Prediction and Control Problems in Reinforcement Learning]]


- [[Reinforcement Learning An Introduction by Sutton]] pp 80 
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1124
- [[Foundations of Machine Learning by Mohri]] pp 322
