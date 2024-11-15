---
tags:
  - concept
  - reinforcement_learning/theory
  - reinforcement_learning/algorithm
keywords:
  - finite_horizon_task_mdp
  - infinite_horizon_task_mdp
topics:
  - reinforcement_learning/theory
name: Finite and Infinite-Horizon Task in Markov Decision Process
date of note: 2024-11-10
---

## Concept Definition

>[!important]
>**Name**: Finite and Infinite-Horizon Task in Markov Decision Process


![[decision_epochs.png]]

>[!important] Definition
>Decisions are made at points of time referred to as **decision epochs**. 
>
>In discrete time problems, time is divided into **periods** or **stages**. 
>- A decision epoch corresponds to the *beginning of a period.*
>- The set of decision epochs is either *finite* or *infinite*.

>[!important] Definition
>A discrete time problem is called a **finite horizon problem**, if the set of decision epochs is finite.
>- It means that the interaction *terminates* after a *fixed finite* number of time steps. 
>
>A discrete time problem is called a **infinite horizon problem**, if the set of decision epochs is countably infinite.
>- It means that the interaction does *not terminate.* 
>  
>The **infinite horizon problem** refers to the problem where the interaction *terminates eventually* but not with fixed time step. 

- [[Episodic and Continuing Task in Reinforcement Learning]]
- [[Returns and Goals of Reinforcement Learning]]
- [[Markov Decision Process]]
- [[Finite Set and Cardinality]]
- [[Countable Set and Uncountable Set]]


## Explanation

>[!info]
>The term **finite-horizon** vs. **infinite-horizon** is more standard than **episodic** vs **continuing**.

- [[Episodic and Continuing Task in Reinforcement Learning]]

## Reward Definition

### Expected Total Reward for Finite-Horizon Task

>[!important] Definition
>Let $\pi$ be a randomized history-dependent policy. Assume that the task is of *finite-horizon* which terminates at $T$ epochs.
>
>Then the **expected total reward** under policy $\pi$ starting at state $x$ is defined by 
>$$
>v_{T}^{\pi}(x) = \mathbb{E}_{x}^{\pi}\left[  \sum_{t=1}^{T-1}r_{t}(X_{t}, A_{t}) + r_{T}(X_{T}) \right]
>$$
>- Under *deterministic history-dependent policy* $\pi = (d_{1}\,{,}\ldots{,}\,d_{T-1})$, the **expected total reward** is given by 
>$$
>v_{T}^{\pi}(x) = \mathbb{E}_{x}^{\pi}\left[  \sum_{t=1}^{T-1}r_{t}(X_{t}, d_{t}(X_{t})) + r_{T}(X_{T}) \right]
>$$

- [[Markov Decision Processes by Puterman]] pp 78

### Expected Total Discount Reward for Finite-Horizon Task

>[!important] Definition
>Let $\pi$ be a randomized history-dependent policy. Assume that the task is of *finite-horizon* which terminates at $T$ epochs.
>
>Then the **expected total reward** under policy $\pi$ starting at state $x$ is defined by 
>$$
>v_{T}^{\pi, \gamma}(x) = \mathbb{E}_{x}^{\pi}\left[  \sum_{t=1}^{T-1}\,\gamma^{t-1}\,r_{t}(X_{t}, A_{t}) + \gamma^{T-1}\,r_{T}(X_{T}) \right]
>$$

- [[Markov Decision Processes by Puterman]] pp 78


### Expected Total Discounted Rewards for Infinite-Horizon Task

>[!important] Definition
>Let $\pi$ be a randomized history-dependent policy. Assume that the task is of *infinite-horizon*.
>
>Then the **expected total discounted reward** under fixed policy $\pi$ starting at fixed state $x$ is defined by 
>$$
>v_{\gamma}^{\pi}(x) = \lim_{ T \to \infty }  \mathbb{E}_{ x }^{\pi}\left[  \sum_{t=1}^{T}\,\gamma^{t-1}\,r(X_{t}, A_{t}) \right]
>$$
>- the *discount factor* $\gamma \in (0,1).$

- [[Markov Decision Processes by Puterman]] pp 121

### Average Reward for Infinite-Horizon Task

>[!important] Definition
>Let $\pi$ be a randomized history-dependent policy. Assume that the task is of *infinite-horizon*.
>
>Then the **average reward** or **gain** under fixed policy $\pi$ starting at fixed state $x$ is defined by 
>$$
>g^{\pi}(x) = \lim_{ T \to \infty }  \frac{1}{T} \mathbb{E}_{ x }^{\pi}\left[  \sum_{t=1}^{T}\,r(X_{t}, A_{t}) \right] = \lim_{ T \to \infty } \frac{1}{T}v_{T}^{\pi}(x)
>$$

- [[Markov Decision Processes by Puterman]] pp 121


-----------
##  Recommended Notes and References



- [[Value Function and Bellman Equation for MDP]]

- [[Reinforcement Learning]]

- [[Markov Decision Processes by Puterman]] pp 18, 119, 125 - 128
- [[Reinforcement Learning An Introduction by Sutton]] pp 11, 54 - 57, 70, 91, 124, 249, 294