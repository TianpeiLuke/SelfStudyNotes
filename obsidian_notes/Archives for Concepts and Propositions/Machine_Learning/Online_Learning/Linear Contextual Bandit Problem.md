---
tags:
  - concept
  - reinforcement_learning/bandit
  - linear_contextual_bandit
keywords:
  - contextual_bandit
  - multi_arm_bandit
topics:
  - bandit_problem
name: Linear Contextual Bandit Problem
date of note: 2024-08-08
---

## Concept Definition

>[!important]
>**Name**: Linear Contextual Bandit Problem

![[Contextual Bandit Problem#^af2210]]


>[!important] Definition
>Let $k > 1$ be the number of **arms**, and $\mathscr{P}_{k-1}$ be the set of all *probability distributions* over the set $[k]$.
>
>A **linear contextual bandit** is described as follows:
>- Each arm $i \in [k]$ is associated with an **unknown parameter vector** $$\theta_{i}^{\star} \in \mathbb{R}^{d}.$$
>- At each round $t = 1, 2, \ldots, T$:
>	- The *environment* reveals a set of **context vectors** $$\{c_{t,1}, c_{t,2}, \ldots, c_{t,k}\} \subseteq \mathbb{R}^{d},$$ where $c_{t,i}$ is the context associated with arm $i$ at time $t$.
>	- The *learner* selects a **distribution** $$P_{t} \in \mathscr{P}_{k-1}$$ over the arms based on the observed context vectors.
>	- The *learner* **samples** an **action** $$A_{t} \sim P_{t}.$$
>	- The *learner* observes the **reward** for the chosen action:
>	  $$
>	  X_{t} = c_{t,A_{t}}^{\top} \theta_{A_{t}}^{\star} + \eta_{t},
>	  $$
>	  where $\eta_{t}$ is a zero-mean noise term (typically assumed to be sub-Gaussian).
>
>**Key Features**:
>- The expected reward of arm $i$ given its context $c_{t,i}$ is **linear** in the context:
>  $$
>  \mathbb{E}[X_{t} \mid A_{t} = i] = c_{t,i}^{\top} \theta_{i}^{\star}.
>  $$
>- The learner must **explore** the arms to estimate the unknown parameters $\{\theta_{i}^{\star}\}$ while **exploiting** the best arms based on observed contexts.



## Explanation





-----------
##  Recommended Notes and References


- [[Contextual Bandit Problem]]
- [[Multi-Armed Adversarial Bandit]]
- [[Stochastic Bandit Problem]]



- [[Bandit Algorithms by Lattimore]]
- [[Reinforcement Learning An Introduction by Sutton]] pp 37 - 40