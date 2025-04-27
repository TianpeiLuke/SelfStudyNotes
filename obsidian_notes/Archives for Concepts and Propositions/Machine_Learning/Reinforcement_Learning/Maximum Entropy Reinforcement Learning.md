---
tags:
  - concept
  - reinforcement_learning/theory
  - reinforcement_learning/algorithm
  - maximum_entropy_learning
  - maximum_entropy_reinforcement_learning
keywords:
  - maximum_entropy_learning_reinforcement_learning
topics:
  - reinforcement_learning
name: Maximum Entropy Reinforcement Learning
date of note: 2024-07-13
---

## Concept Definition

>[!important]
>**Name**:  Maximum Entropy Reinforcement Learning

![[Policy Gradient Algorithm#^f0d871]]

>[!important] Definition
>Given 
>- a *Markov decision process* $$\{T, \mathcal{X}, \mathcal{B}(\mathcal{X}), \mathcal{A}, \mathscr{F}_{\mathcal{A}}\,,\, p_{t}(\cdot|x, a)\,,\, r_{t}(x, a)\},$$
>- and a *Markov policy* $\pi = (\delta_{1}, \delta_{2} \,{,}\ldots{,}\,)$ where each $\delta_{t}$ is *randomized Markov decision rule* $$\delta_{t}: x \mapsto q_{\delta_{t}(x)}(\cdot) \in \mathscr{P}_{\mathcal{A}},$$
>
>the **maximum entropy reinforcement learning** find optimal Markov policy $$\pi: \mathcal{X}\to \mathscr{P}(\mathcal{A})$$ that *maximizes* the expected reward with additional *entropy regularization* on $\pi$
>$$
>\begin{align*}
>\min_{\pi} \;&\; \sum_{t=0}^{T} \mathbb{E}^{ \pi }\left[\; r(X_{t}, A_{t}) + \lambda\,H(\pi(\cdot\,|\,X_{t})) \;\right]
>\end{align*}
>$$
>where
>- the **temperature parameter** $\lambda >0$ determines the relative importance of the entropy term against the reward.
>	- It controls the *stochasticity* of the optimal policy. 

- [[Policy Gradient Algorithm]]
- [[Entropy Minimization Algorithm]]
- [[Kullback-Leibler Divergence]]
- [[Conditional Probability]]


## Explanation

>[!quote]
>This objective has a number of conceptual and practical **advantages**. 
>- First, the policy is incentivized to **explore** more widely, while **giving up** on clearly *unpromising avenues*. 
>- Second, the policy can capture **multiple modes** of *near-optimal behavior*. In problem settings where multiple actions seem equally attractive, the policy will **commit equal probability** mass to those actions. 
>- Lastly, prior work has observed **improved exploration** with this objective (Haarnoja et al., 2017; Schulman et al., 2017a), and in our experiments, we observe that it considerably improves learning speed over state-of-art methods that optimize the conventional RL objective function. 
>- We can extend the objective to **infinite horizon** problems by introducing a discount factor γ to ensure that the sum of expected rewards and entropies is finite.


## Soft Actor Critic

- [[Soft Actor-Critic Algorithm]]


-----------
##  Recommended Notes and References


- [[Reinforcement Learning]]
- [[Maximum Entropy Learning]]
- [[Kullback-Leibler Divergence]]
- [[Markov Decision Process]]
- [[Exponential Family of Distributions]]


- [[Reinforcement Learning An Introduction by Sutton]]
- [[Markov Decision Processes by Puterman]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1171

- Medium [Maximum Entropy Policies in Reinforcement Learning & Everyday Life](https://awjuliani.medium.com/maximum-entropy-policies-in-reinforcement-learning-everyday-life-f5a1cc18d32d)
- Youtube [CS885 Module 2: Maximum Entropy Reinforcement Learning](https://www.youtube.com/watch?v=ZsW0LCPPWHU)
- Ziebart, B. D., Maas, A. L., Bagnell, J. A., & Dey, A. K. (2008, July). Maximum entropy inverse reinforcement learning. In _Aaai_ (Vol. 8, pp. 1433-1438).
- Haarnoja, T., Zhou, A., Abbeel, P., & Levine, S. (2018, July). Soft actor-critic: Off-policy maximum entropy deep reinforcement learning with a stochastic actor. In _International conference on machine learning_ (pp. 1861-1870). PMLR.