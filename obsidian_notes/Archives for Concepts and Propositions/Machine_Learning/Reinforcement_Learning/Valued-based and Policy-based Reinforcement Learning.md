---
tags:
  - concept
  - machine_learning/algorithms
  - reinforcement_learning/theory
  - reinforcement_learning/algorithm
  - value_iteration
  - policy_iteration
keywords:
  - value_based_reinforcement_learning
  - policy_based_reinforcement_learning
topics:
  - reinforcement_learning/theory
name: Valued-based and Policy-based Reinforcement Learning
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Valued-based and Policy-based Reinforcement Learning

>[!important] Definition
> By far, we mainly discussed the value-based methods, this chapter, we focus on policy-based methods. 
>- **Value-based methods** (or **action-value methods**): all these methods (DP, MC, TD with **tabular** or **function approximation**) learned the *values of actions* and then *selected actions* based on their estimated action values; their policies would not even exist without the action-value estimates.
> 
>- **Policy-based methods** (or **policy gradient methods**): methods that instead learn a *parameterized policy* that can select actions *without consulting a value function*.  A value function may still be used to learn the policy parameter, but is *not required* for action selection. 

- [[Tabular Representation and Function Approximation RL]]
- [[Policy Iteration Algorithm]]
- [[Policy Gradient Algorithm]]

>[!important]
> Perhaps the simplest **advantage** that *policy parameterization* may have over *action-value parameterization* is that the policy may be a simpler function to approximate. Problems vary in the complexity of their policies and action-value functions. 
> 
> Finally, we note that the choice of policy parameterization is sometimes a good way of **injecting prior knowledge** about the desired form of the policy into the reinforcement learning system. This is often the *most important reason* for using a **policy-based learning method**.



## Explanation





-----------
##  Recommended Notes and References


- [[Actor-Critic Algorithm]]
- [[Policy Gradient Algorithm]]
- [[Markov Decision Process]]


- [[Reinforcement Learning An Introduction by Sutton]] pp 321 - 324
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1148
