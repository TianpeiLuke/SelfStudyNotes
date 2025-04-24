---
tags:
  - concept
  - machine_learning/algorithms
  - reinforcement_learning/algorithm
  - actor_critic_algorithm
keywords:
  - advantage_actor_critic_algorithm
  - actor_critic_algorithm
  - reinforce_algorithm_baseline
  - a2c
topics:
  - reinforcement_learning/algorithm
name: Advantage and Advantage Actor Critic or A2C Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Advantage Actor Critic or A2C and A3C Algorithm

### Advantage Function

>[!important] Definition
>The **advantage function** is defined as 
>$$
>A(x_{t}, a_{t}) = Q(x_{t}, a_{t}) - V(x_{t})
>$$
>where 
>- $(x_{t}, a_{t})$ are state and action at $t$ 
>- $Q(\cdot, \cdot)$ and $V(\cdot)$ are action-state and value-state functions.

^c94fbd


- [[Value Function and Bellman Equation for MDP]]

### Sample Approximation of Advantage Function

>[!important] 
>Assume that the value-state function is given by the value network $$V_{\theta}(x_{t})$$
>
>Then the **sample approximation of advantage function** is given by the *TD error* $$\hat{A}(x_{t}, a_{t}) := \delta_{t} := r_{t} + \gamma\,V_{\theta}(x_{t+1}) - V_{\theta}(x_{t})$$

^69485c


- [[Generalized Advantage Estimation or GAE in PPO]]
- [[Temporal Difference Learning]]

### Actor-Critic Algorithm

![[Actor-Critic Algorithm#^5ba730]]

- [[Actor-Critic Algorithm]]
- [[REINFORCE Algorithm with Baseline]]
- [[REINFORCE Algorithm for Monte Carlo Policy Gradient]]

### Advantage Actor-Critic or A2C Algorithm 





## Explanation





-----------
##  Recommended Notes and References


- [[Proximal Policy Optimization or PPO Algorithm]]
- [[Policy Gradient Algorithm]]
- [[Markov Decision Process]]


- [[Reinforcement Learning An Introduction by Sutton]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1149
- Medium [blog](https://towardsdatascience.com/understanding-actor-critic-methods-931b97b6df3f)
