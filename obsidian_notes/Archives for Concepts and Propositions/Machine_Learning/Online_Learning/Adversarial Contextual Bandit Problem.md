---
tags:
  - concept
  - reinforcement_learning/bandit
  - adversarial_contextual_bandit
keywords:
  - contextual_bandit
  - multi_arm_bandit
topics:
  - bandit_problem
name: Adversarial Contextual Bandit Problem
date of note: 2024-08-08
---

## Concept Definition

>[!important]
>**Name**: Adversarial Contextual Bandit Problem

![[Contextual Bandit Problem#^af2210]]


>[!important] Definition
>Let $k > 1$ be the number of **arms**, and $\mathscr{P}_{k-1}$ be the set of all *probability distributions* over the set $[k]$.
>
>An **adversarial contextual bandit** is described as follows:
>- At each round $t = 1, 2, \ldots, T$:
>	- The *adversary* selects:
>		- A set of **context vectors** $$\{c_{t,1}, c_{t,2}, \ldots, c_{t,k}\} \subseteq \mathbb{R}^{d},$$ where $c_{t,i}$ is the context associated with arm $i$ at time $t$.
>		- A corresponding **reward vector** $$x_t = (x_{t,1}, \ldots, x_{t,k}),$$ where each $x_{t,i} = x_{t,i}(c_{t,i}) \in [0,1]$$ can depend arbitrarily on the context.
>	- The *learner* observes the context vectors $\{c_{t,1}, \ldots, c_{t,k}\}$.
>	- The *learner* selects a **distribution** $$P_{t} \in \mathscr{P}_{k-1}$$ over the arms based on the observed contexts.
>	- The *learner* **samples** an **action** $$A_{t} \sim P_{t}.$$
>	- The *learner* observes the **reward**:
>	  $$
>	  X_{t} = x_{t,A_{t}},
>	  $$
>	  but does **not** observe the rewards of the other arms.
>
>**Key Features**:
>- The adversary can **adaptively** choose contexts and rewards based on the past behavior of the learner (adaptive adversary) or fix them ahead of time (oblivious adversary).
>- The learner must design a policy that **competes** with the best possible mapping from contexts to actions in hindsight.




## Explanation





-----------
##  Recommended Notes and References


- [[Contextual Bandit Problem]]
- [[Multi-Armed Adversarial Bandit]]
- [[Stochastic Bandit Problem]]



- [[Bandit Algorithms by Lattimore]]
- [[Reinforcement Learning An Introduction by Sutton]] pp 37 - 40