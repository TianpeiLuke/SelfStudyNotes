---
tags:
  - concept
  - reinforcement_learning/bandit
  - stochastic_bandit
keywords:
  - stochastic_bandit_problem
topics:
  - bandit_problem
name: Stochastic Bandit Problem
date of note: 2024-08-08
---

## Concept Definition

>[!important]
>**Name**: Stochastic Bandit Problem

![[Multi-Armed Adversarial Bandit#^d92056]]

>[!important] Definition
>Let $k > 1$ be the number of **arms**, and let $\mathscr{P}_{k-1}$ be the set of all *probability distributions* over the set $[k]$.
>
>A **stochastic $k$-armed bandit** is described as follows:
>- Each arm $i \in [k]$ is associated with a **fixed but unknown reward distribution** $\nu_i$ supported on $[0,1]$.
>- At each round $t = 1, 2, \ldots, T$:
>	- The *learner* selects a **distribution** $$P_{t} \in \mathscr{P}_{k-1}.$$
>	- The *learner* **samples** an **action** $$A_{t} \sim P_{t}.$$
>	- The *learner* observes the **reward**:
>	  $$
>	  X_{t} \sim \nu_{A_{t}},
>	  $$
>	  i.e., the reward is drawn independently from the unknown distribution $\nu_{A_t}$ associated with the selected arm.
>
>**Key Features**:
>- The reward distributions $\{\nu_i\}_{i=1}^{k}$ are **stationary** and **independent across arms**.
>- The learner must balance **exploration** (trying different arms to estimate their means) and **exploitation** (selecting the best-known arm) to maximize cumulative reward.



## Explanation





-----------
##  Recommended Notes and References

- [[Multi-Armed Adversarial Bandit]]
- [[Contextual Bandit Problem]]



- [[Markov Chain and Markov Process]]
- [[Martingale]]

- [[Sub-Gaussian Process]]
- [[Sub-Gaussian Norm]]
- [[Hoeffding Inequality]]


- [[Bandit Algorithms by Lattimore]]
- [[Reinforcement Learning An Introduction by Sutton]] pp 37 - 40