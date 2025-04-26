---
tags:
  - concept
  - reinforcement_learning/bandit
  - multi_arm_bandit
  - contextual_bandit
keywords:
  - contextual_bandit
  - multi_arm_bandit
topics:
  - bandit_problem
name: Contextual Bandit Problem
date of note: 2024-08-08
---

## Concept Definition

>[!important]
>**Name**: Contextual Bandit Problem

![[Multi-Armed Adversarial Bandit#^d92056]]

>[!important] Definition
>Let $k > 1$ be the number of **arms**, and let $\mathscr{P}_{k-1}$ be the set of all *probability distributions* over the set $[k]$.
>
>A **contextual bandit** is described as follows:
>- At each round $t = 1, 2, \ldots, T$:
>	- The *environment* reveals a **context** $$c_{t} \in \mathcal{C},$$ where $\mathcal{C}$ is the context space.
>	- The *learner* selects a **distribution** $$P_{t}(\cdot \mid c_{t}) \in \mathscr{P}_{k-1}$$ based on the observed context $c_{t}$.
>	- The *learner* **samples** an **action** $$A_{t} \sim P_{t}(\cdot \mid c_{t}).$$
>	- The *learner* observes the **reward** for the selected action:
>	  $$
>	  X_{t} = x_{t, A_{t}}(c_{t}) = \sum_{i=1}^{k}\,x_{t,i}(c_{t})\,\mathbb{1}\{A_{t} = i\},
>	  $$
>	  where $x_{t,i}(c_{t}) \in [0,1]$ is the (unknown) reward associated with arm $i$ under context $c_{t}$.
>
>**Key Difference** from multi-armed bandits:
>- In contextual bandits, the learner’s action selection depends on the observed **context** $c_t$ at each round.
>- Rewards are **context-dependent**, i.e., each arm's reward may vary based on the current context.


## Explanation





-----------
##  Recommended Notes and References

- [[Multi-Armed Adversarial Bandit]]
- [[Stochastic Bandit Problem]]



- [[Bandit Algorithms by Lattimore]]
- [[Reinforcement Learning An Introduction by Sutton]] pp 37 - 40