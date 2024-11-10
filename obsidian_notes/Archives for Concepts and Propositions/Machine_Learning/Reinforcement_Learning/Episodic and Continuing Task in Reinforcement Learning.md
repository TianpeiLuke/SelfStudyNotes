---
tags:
  - concept
  - reinforcement_learning/theory
  - reinforcement_learning/algorithm
keywords:
  - episodic_task_rl
  - continuing_task_rl
topics:
  - reinforcement_learning/theory
name: Episodic and Continuing Task in Reinforcement Learning
date of note: 2024-11-10
---

## Concept Definition

>[!important]
>**Name**: Episodic and Continuing Task in Reinforcement Learning


>[!important] Definition
>The **Episodic tasks** are tasks where
>- a final state at $T$ can be *observed* 
>- and after that, the enviroment and agents will be *reset* to inital state.
>
>**Episodic tasks** can be naturally broken into *subsequences* in terms of *agent-environment interaction*,  called an **episodes**.
>- Each episode *ends* in a special state called the **terminal state**, 
>- followed by a *reset* to a standard **starting state** or to a sample from a standard distribution of starting states. 

- [[Returns and Goals of Reinforcement Learning]]
- [[Markov Decision Process]]

>[!important] Definition
>The **continuing tasks** are tasks that cannot be broken into identifiable *episodes*, but goes on *continually without limit* in terms of  the agent–environment interaction. 
>




## Explanation


- [[Episodic Semi-Gradient Multi-Step SARSA]]
- [[Episodic Semi-Gradient SARSA]]
- 


-----------
##  Recommended Notes and References



- [[Value Function and Bellman Equation for MDP]]

- [[Reinforcement Learning]]


- [[Reinforcement Learning An Introduction by Sutton]]