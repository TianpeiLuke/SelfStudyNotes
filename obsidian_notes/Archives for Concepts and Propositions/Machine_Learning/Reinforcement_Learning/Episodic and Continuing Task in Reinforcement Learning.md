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

### Expected Returns and Average Rewards

>[!important] Definition
> For **episodic task**, the objective function is the **expected returns** i.e. the value function under policy $\pi$ of the start state of the episode:
>$$ 
> \begin{align}
> \mathcal{R}(\pi) &:= v_{\pi}(s_{0}) =\sum_{a}\pi(a \,|\, s_{0})\,q_{\pi}(s_{0}, a)  
> \end{align}
>$$ 

- [[Value Function and Bellman Equation for MDP]]

>[!important] Definition
> For **continuing task**, the objective function is the **average rewards**
>$$ 
> \begin{align}
> \mathcal{R}(\pi) &:= r(\pi(a |s ))  \nonumber \\[8pt]
> &= \sum_{s}\mu_{\pi}(s)\,\sum_{a}\pi(a |s) \sum_{s', r}p(s', r| s, a)r. 
> \end{align}
>$$  
>where $\mu$ is the **steady-state distribution**. 
>- It is the **invariant distribution** under $\pi$, $$\mu(s) = \lim_{t\rightarrow \infty}P\{S_{t} = s| S_{0}, \pi\},$$ or **on-policy distribution** under policy $\pi$.





## Explanation


- [[Episodic Semi-Gradient Multi-Step SARSA]]
- [[Episodic Semi-Gradient SARSA]]
- 


-----------
##  Recommended Notes and References



- [[Value Function and Bellman Equation for MDP]]

- [[Reinforcement Learning]]


- [[Reinforcement Learning An Introduction by Sutton]] pp 11, 54 - 57, 70, 91, 124, 249, 294