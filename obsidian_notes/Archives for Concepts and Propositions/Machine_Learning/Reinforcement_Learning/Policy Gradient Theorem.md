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
>For both the **episodic case** and **continuing case** under *ergodic MDP*, the objective functions $\mathcal{R}(\theta)$ are defined as in \eqref{eqn: obj_policy_grad_episodic} and \eqref{eqn: obj_policy_grad_continuing} respectively. 
>
>Then 
>$$
> \begin{align}
> \grad{\mb{\theta}}{\cR(\mb{\theta})} &\propto \sum_{s}\mu_{\pi(\mb{\theta})}(s)\sum_{a}\grad{\mb{\theta}}{\pi(a |\mb{s}, \mb{\theta})}q_{\pi}(\mb{s}, a) \label{eqn: policy_grad_theorem}\\
> &= \E{\mb{s} \sim \mb{\mu}_{\pi(\mb{\theta})}}{\sum_{a}\grad{\mb{\theta}}{\pi(a |\mb{s}, \mb{\theta})}q_{\pi}(\mb{s}, a) } \label{eqn: policy_grad_theorem2} \\
> &= \E{\mb{s} \sim \mb{\mu}_{\pi(\mb{\theta})}}{\E{a \sim \pi(a|\mb{s}, \mb{\theta})}{\grad{\mb{\theta}}{\log \pi(a |\mb{s}, \mb{\theta})}q_{\pi}(\mb{s}, a) }},\label{eqn: policy_grad_theorem3}
> \end{align}
>$$  
>where $\mb{\mu}_{\pi}$ is the limiting state distribution under $\pi$, $\mu(s) = \lim_{t\rightarrow \infty}Pr\{S_{t} = s| S_{0}, \pi\}$, (or on-policy distribution under policy $\pi$).  In particular, the gradient of objective does not depend on the gradient of state distribution $\grad{}{\mb{\mu}}$.  For ergodic MDP with average reward objective, the equation \eqref{eqn: policy_grad_theorem} is exact. For episodic task, the constant of proportionality is the average length of an episode.



- [[Policy Gradient Optimization]]
- [[Markov Decision Process]]

## Explanation





-----------
##  Recommended Notes and References



- [[Reinforcement Learning An Introduction by Sutton]] pp 324 - 326
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1147
