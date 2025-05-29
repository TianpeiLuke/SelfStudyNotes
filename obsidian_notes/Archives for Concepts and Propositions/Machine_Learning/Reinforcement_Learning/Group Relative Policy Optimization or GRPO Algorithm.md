---
tags:
  - concept
  - machine_learning/algorithms
  - ppo
  - reinforcement_learning/algorithm
  - deep_learning/large_language_models
  - group_relative_policy_optimization
  - grpo
keywords:
  - reinforcement_learning
  - group_relative_policy_optimization
  - grpo
topics:
  - reinforcement_learning/algorithm
  - deep_learning/large_language_models
name: Group Relative Policy Optimization or GRPO Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Group Relative Policy Optimization or GRPO Algorithm

>[!important] Definition
>The **Group Relative Policy Optimization (GRPO)** algorithm is a reinforcement learning framework that 
>- extends traditional policy optimization 
>- by leveraging *groupwise feedback* to guide learning, improving stability and sample efficiency.



>[!important] Definition
>The **Group Relative Policy Optimization (GRPO)** algorithm is described as below:
>- *Require*: a set of **agents** or **decision groups** operating in an environment.
>- *Require*: a **policy network** $\pi_{\theta}(a|s)$ parameterized by $\theta$ that maps states $s$ to action distributions.
>- *Require*: a **grouping mechanism** that partitions episodes or trajectories into groups based on similarity, context, or task.
>
>- **Initialize** policy parameters $\theta$ randomly.
>
>- While not *convergence*:
>    - **Collect** a batch of trajectories $\mathcal{D}$ by running the current policy $\pi_{\theta}$ in the environment.
>    - **Group** the collected trajectories into subsets $\mathcal{G}_1, \ldots, \mathcal{G}_M$ according to the predefined grouping strategy.
>    - For each group $\mathcal{G}_m$:
>        - Compute **relative rewards** or **rankings** among trajectories within the group.
>        - Define a **group-relative advantage function** $\hat{A}_{\mathcal{G}_m}(s,a)$ based on relative performance rather than absolute returns.
>    - **Optimize** the policy by maximizing the expected advantage over all groups, e.g.,
>      $$
>      \max_{\theta} \mathbb{E}_{(s,a)\sim \mathcal{D}} \left[ \frac{\pi_{\theta}(a|s)}{\pi_{\theta_{\text{old}}}(a|s)} \hat{A}_{\mathcal{G}_m}(s,a) \right]
>      $$
>      subject to a **trust-region constraint** or **clipped surrogate objective** similar to PPO.
>    - Update the policy parameters $\theta$ via gradient ascent using the group-relative advantage.
>
>- *Return*: optimized policy parameters $\theta$.


- [[Proximal Policy Optimization or PPO Algorithm]]
- [[Generalized Advantage Estimation or GAE in PPO]]
- [[Advantage and Advantage Actor Critic or A2C Algorithm]]
- [[Actor-Critic Algorithm]]

>[!info]
>- *Sharing* parameters ($\theta = \theta_v$) or using separate networks both fit this template.
>- $c_v$ and $c_H$ are *scalar coefficients* (value loss and entropy bonus, e.g.\ 0.5 and 0.01).


### Clipped Surrogate Objective

>[!important]  Definition
> For a trajectory $\tau$ and time-step $t$:
> - the **probability ratio** $$r_t(\theta) ~=~ \dfrac{\pi_\theta(a_t\mid s_t)}{\pi_{\theta_{\text{old}}}(a_t\mid s_t)}$$
> - the **clipped surrogate loss** $$\mathcal L^{\text{CLIP}}(\theta) ~=~ \mathbb E_t\Bigl[ \min\bigl( r_t(\theta)\,\hat A_t,\; \operatorname{clip}(r_t(\theta),1-\epsilon,1+\epsilon)\,\hat A_t \bigr) \Bigr]$$
>where 
> 
> - $\hat A_t =$​ *advantage estimate* (usually **GAE**).
>     
> - $\epsilon\in[0.1,0.3] =$ *clip parameter*.
>     
> - When $r_t$​ stays in $[1-\epsilon,1+\epsilon]$ the gradient is the same as *vanilla PG*; 
> 	- outside, the term is *clipped*, preventing large updates.


>[!important] Definition
>Then the **total loss** combines *policy*, *value*, and *entropy bonus*:
>$$
>\mathcal{L}(\theta) = − \mathcal{L}^{\text{CLIP}}(\theta) + c_{v}\, \mathbb{E}_{ t }\left[ \left(V_{\theta}(s_{t}) - R_{t}\right)^2 \right] ​- c_{H}\, \mathbb{E}_{ t }\left[  \mathcal{H}\left(\pi_{\theta}\left(\cdot\,|\,s_{t}\right)\right) \right].
>$$

- [[Maximum Entropy Reinforcement Learning]]
- [[Soft Actor-Critic Algorithm]]

## Explanation

>[!info]
>PPO is an **actor-critic algorithm**.
>- it update both value function and policy function 

- [[Actor-Critic Algorithm]]

### Motivations

>[!important]
>- **Vanilla policy gradients** can take steps that change the policy too much, destabilising learning.
>     
> - **Trust‑Region Policy Optimization** (TRPO) fixes this with a hard KL‐divergence constraint but needs *second‑order* methods.
>     
> - **PPO** keeps the “small‑step” idea but uses _only first‑order gradients_ by **penalising or clipping** the policy update.

- [[Policy Gradient Algorithm]]
- [[Policy Gradient Theorem]]


>[!important]
>The **clipping (or KL‑penalty)** keeps the updated policy inside a _trust region_ without expensive second‑order optimisation, giving PPO a good balance of **simplicity, stability, and empirical performance** across Atari, MuJoCo, robotics, and many LLM fine‑tuning setups.

### Practical notes

> [!info]
>- **Multiple actors** (vectorised envs) improve sample throughput.
>     
> - **Shared vs. separate networks**: sharing base layers saves compute; separate heads can reduce interference.
>     
> - **Adaptive KL penalty** variant: replace clipping with a penalty term and adjust coefficient to maintain target KL.
>     
> - **Observation/return normalisation** helps with stability.
>     
> - **Reward scaling** or clipping often necessary in continuous‑control tasks.



-----------
##  Recommended Notes and References


- [[Generalized Advantage Estimation or GAE in PPO]]
- [[Advantage and Advantage Actor Critic or A2C Algorithm]]
- [[Actor-Critic Algorithm]]
- [[Actor-Critic Algorithm with Eligibility Traces]]

- [[Reinforcement Learning An Introduction by Sutton]]

- [[Preference Alignment for LLM]]
- [[Supervised Fine-Tuning or Instruction Fine-Tuning of LLM]]
- [[Supervised Fine-Tuning and Preference Alignment for LLM]]

- **“Proximal Policy Optimization Algorithms.”** J. Schulman et al., arXiv 1707.06347 (2017).
- **“Trust Region Policy Optimization.”** J. Schulman et al., ICML 2015.
