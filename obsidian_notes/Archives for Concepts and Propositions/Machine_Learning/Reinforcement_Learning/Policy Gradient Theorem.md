---
tags:
  - concept
  - machine_learning/algorithms
  - reinforcement_learning/theory
  - reinforcement_learning/algorithm
keywords:
  - policy_gradient_theorem
topics:
  - reinforcement_learning/theory
  - reinforcement_learning/algorithm
name: Policy Gradient Theorem
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Policy Gradient Theorem

![[Markov Decision Process#^f5dcdf]]

![[Markov Decision Process#^f0b818]]

![[Markov Decision Process#^c86b5a]]

![[Markov Decision Process#^a1e9de]]

![[Policy Gradient Optimization#^f0d871]]

>[!important] Policy Gradient Theorem
>For both the **episodic case** and **continuing case** under *ergodic MDP*, the objective functions $\mathcal{R}(\theta)$ are defined as in 
>$$
>\begin{align}
>\mathcal{R}(\theta) &:= v_{\pi(\theta)}(s_{0})  &\\[5pt]
>&=\sum_{a}\pi(a |s_{0}, \theta)\,q_{\pi}(s_{0}, a) & \text{ episodic case }  \\[10pt]
>\mathcal{R}(\theta) &:= r(\pi(a |s, \theta))  & \\[5pt]
> &= \sum_{s}\mu_{\pi(\theta)}(s)\,\sum_{a}\pi(a |s, \theta)\,\sum_{s', r}p(s', r| s, a)\,r, & \text{ continuing case } 
>\end{align}
>$$
>respectively. 
>
>Then the **gradient of average reward** is given by 
>$$
> \begin{align}
> \nabla_{\theta}\,\mathcal{R}(\theta) &\propto \sum_{s}\mu_{\pi(\theta)}(s)\, \sum_{a} \nabla_{\theta}\pi(a \,|\,s, \theta)\,q_{\pi}(s, a) & \\[5pt]
> &=  \mathbb{E}_{ S \sim \mu_{\pi(\theta)} }\left[  \sum_{a} \nabla_{\theta}\,\pi(a \,|\,S, \theta)\,q_{\pi}(S, a)  \right]  & \\[5pt]
> &=  \mathbb{E}_{ S \sim \mu_{\pi(\theta)} }\left[\,\mathbb{E}_{ A \sim  \pi(a\,|\,s, \theta)  }\left[\, \nabla_{\theta} \log \pi(A \,|\,S\,,\,\theta)\,q_{\pi}(S, A) \right] \right], & (1)
> \end{align}
>$$  
>where 
>- $\mu_{\pi}$ is the **limiting state distribution** under $\pi$,  $$\mu_{\pi}(s) = \lim_{t\rightarrow \infty}P\{S_{t} = s| S_{0}, \pi\},$$ (or *on-policy distribution* under policy $\pi$).  
>
>In particular, the **gradient of objective** does **not depend** on the **gradient of state distribution** $\nabla \mu$.  
>
>- For *ergodic MDP* with *average reward objective*, the equation $(1)$  is **exact**. 
>- For *episodic task*, the constant of *proportionality* is the *average length* of an episode.

- [[Policy Gradient Optimization]]
- [[Markov Decision Process]]
- [[Invariant Measure and Stationary Distribution]]
- [[Classification of States of Markov Chain]]
- [[Kac Theorem on Markov Chain]]


## Explanation

>[!info]
>Parameterized policy methods have an **important theoretical advantage** over *action-value methods* in the form of the **policy gradient theorem**, which gives an exact formula for how performance is affected by the policy parameter that does **not involve derivatives** of the *state distribution*. 
>
>This theorem provides a theoretical foundation for all policy gradient methods.

- [[Policy Gradient Optimization]]



-----------
##  Recommended Notes and References



- [[Reinforcement Learning An Introduction by Sutton]] pp 324 - 326
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1147