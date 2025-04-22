---
tags:
  - concept
  - machine_learning/algorithms
  - proximal_policy_gradient
  - ppo
  - reinforcement_learning/algorithm
  - deep_learning/large_language_models
keywords:
  - reinforcement_learning
  - proximal_gradient_algorithm
topics:
  - reinforcement_learning/algorithm
  - deep_learning/large_language_models
name: Proximal Policy Gradient Optimization Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Proximal Policy Gradient Optimization Algorithm


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

- [[Generalized Advantage Estimation or GAE in PPO]]

>[!important] Definition
>Then the **total loss** combines *policy*, *value*, and *entropy bonus*:
>$$
>\mathcal{L}(\theta) = − \mathcal{L}^{\text{CLIP}}(\theta) + c_{v}\, \mathbb{E}_{ t }\left[ \left(V_{\theta}(s_{t}) - R_{t}\right)^2 \right] ​- c_{H}\, \mathbb{E}_{ t }\left[  \mathcal{H}\left(\pi_{\theta}\left(\cdot\,|\,s_{t}\right)\right) \right] .
>$$ 	  


## Explanation

>[!info]
>- **Vanilla policy gradients** can take steps that change the policy too much, destabilising learning.
>     
> - **Trust‑Region Policy Optimization** (TRPO) fixes this with a hard KL‐divergence constraint but needs second‑order methods.
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


- [[Reinforcement Learning An Introduction by Sutton]]

- [[Preference Alignment for LLM]]
- [[Supervised Fine-Tuning or Instruction Fine-Tuning of LLM]]
- [[Supervised Fine-Tuning and Preference Alignment for LLM]]

- **“Proximal Policy Optimization Algorithms.”** J. Schulman et al., arXiv 1707.06347 (2017).
- **“Trust Region Policy Optimization.”** J. Schulman et al., ICML 2015.
