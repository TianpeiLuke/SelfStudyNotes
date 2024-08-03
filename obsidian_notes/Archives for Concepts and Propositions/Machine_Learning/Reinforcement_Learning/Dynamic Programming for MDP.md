---
tags:
  - concept
  - machine_learning/algorithms
  - reinforcement_learning/theory
  - reinforcement_learning/algorithm
  - algorithm/dynamic_programming
keywords:
  - dynamic_programming
  - markov_decision_process
  - reinforcement_learning
  - bellman_equation
  - bellman_optimality_equation
topics:
  - reinforcement_learning
  - algorithm
name: Dynamic Programming for MDP
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Dynamic Programming on Markov Decision Process

![[Value Function and Bellman Equation for MDP#^e3c917]]


>[!info]
>The *Bellman equations provide* the basics for dynamic programming. 
>
>We summarize them as below:
>$$
>\begin{align*}
>v_{\pi}(x) &= \sum_{a \in \mathcal{A}}\pi(a | x) \sum_{u \in \mathcal{X}}\,p(u | x, a)\,\left[r(x, a) + \gamma\,v_{\pi}(u)  \right], \quad \forall x \in \mathcal{X} \\
> q_{\pi}(x, a) &=  \sum_{u \in \mathcal{X}}\,p(u | x, a)\,\left[\,r(x, a) + \gamma\,\sum_{a' \in \mathcal{A}}\pi(a' | u)\,q_{\pi}(u, a')  \right], \quad \forall x \in \mathcal{X}, \; a \in \mathcal{A}
>\end{align*}
>$$
>and the *Bellman optimality equation*
>$$
>\begin{align*}
>v_{*}(x) &= \max_{a \in \mathcal{A}_{x}}\,\sum_{u \in \mathcal{X}}p(u | x, a)\left[\, r(x, a) + \gamma v_{*}(u) \,\right], \quad \forall x\in \mathcal{X} \\
>q_{*}(x, a) &= \sum_{u \in \mathcal{X}}p(u | x, a)\,\left[ r(x, a) + \gamma\,\max_{a' \in \mathcal{A}}q_{*}(u, a') \right], \quad \forall x\in \mathcal{X}, \,a\in \mathcal{A}
>\end{align*}
>$$


- [[Value Function and Bellman Equation for MDP]]
- [[Bellman Optimality Equation for MDP]]


## Explanation






-----------
##  Recommended Notes and References

- [[Dynamic Programming for Optimal Stopping]]
- [[Value Function and Bellman Equation for MDP]]
- [[Markov Decision Process]]


- [[Reinforcement Learning An Introduction by Sutton]] pp 62 - 67
- [[Markov Decision Processes by Puterman]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1135
- [[Foundations of Machine Learning by Mohri]] pp 315
