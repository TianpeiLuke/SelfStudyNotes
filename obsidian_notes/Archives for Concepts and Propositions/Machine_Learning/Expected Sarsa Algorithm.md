---
tags:
  - concept
  - machine_learning/algorithms
keywords: 
topics: 
name: 
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: 

>[!info]
>One of the early breakthroughs in reinforcement learning was the development of an off-policy TD control algorithm known as **Q-learning**.
>
>Instead of Bellman equation for $q$, we now consider the *Bellman optimality equation* for $q_{*}$

![[Bellman Optimality Equation for MDP#^469b99]]

![[Bellman Optimality Equation for MDP#^2ff71a]]

>[!important] Definition
>The update rule for **Q-learning** is defined by
>$$
> \begin{align}
> Q(X_{t}, A_{t}) &\leftarrow Q(X_{t}, A_{t}) + \alpha_{t}\left[ R_{t+1} + \gamma \max_{a'\in \mathcal{A}(X_{t+1})}Q(X_{t+1}, a')  - Q(X_{t}, A_{t}) \right]. 
> \end{align}
>$$ 


## Explanation





-----------
##  Recommended Notes and References

- [[Q Learning Algorithm and Off-Policy Temporal Difference Control]]
- [[Sarsa Algorithm and On-Policy Temporal Difference Control]]
- [[Temporal Difference Learning]]

- [[Approximate Dynamic Programming for MDP]]
- [[Bellman Optimality Equation for MDP]]
- [[Value Function and Bellman Equation for MDP]]
- [[Markov Decision Process]]



- [[Reinforcement Learning An Introduction by Sutton]]

