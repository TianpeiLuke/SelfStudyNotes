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


>[!important] Definition
>The **Bellman equations** provide the basics for dynamic programming. 
>
>We summarize **Bellman equations** for *state-value* and *action-value functions* as below:
>$$
>\begin{align*}
>v_{\pi}(x) &= \sum_{a \in \mathcal{A}}\pi(a | x) \sum_{u \in \mathcal{X}}\,p(u | x, a)\,\left[r(x, a) + \gamma\,v_{\pi}(u)  \right], \quad \forall x \in \mathcal{X} \\[5pt]
> q_{\pi}(x, a) &=  \sum_{u \in \mathcal{X}}\,p(u | x, a)\,\left[\,r(x, a) + \gamma\,\sum_{a' \in \mathcal{A}}\pi(a' | u)\,q_{\pi}(u, a')  \right], \quad \forall x \in \mathcal{X}, \; a \in \mathcal{A}
>\end{align*}
>$$

^d0f53b

- [[Value Function and Bellman Equation for MDP]]

>[!important] Definition
 >The **Bellman optimality equation**  for *state-value* and *action-value functions* as below:
>$$
>\begin{align*}
>v_{*}(x) &= \max_{a \in \mathcal{A}_{x}}\,\sum_{u \in \mathcal{X}}p(u | x, a)\left[\, r(x, a) + \gamma v_{*}(u) \,\right], \quad \forall x\in \mathcal{X} \\[5pt]
>q_{*}(x, a) &= \sum_{u \in \mathcal{X}}p(u | x, a)\,\left[ r(x, a) + \gamma\,\max_{a' \in \mathcal{A}}q_{*}(u, a') \right], \quad \forall x\in \mathcal{X}, \,a\in \mathcal{A}
>\end{align*}
>$$

- [[Bellman Optimality Equation for MDP]]
- [[Bootstrap Method]]

### Policy Iteration

- [[Policy Iteration Algorithm]]
- [[Value Iteration Algorithm]]
- [[Backward Induction and Dynamic Programming]]


## Explanation





## Online Update for Model-Free Approach

- [[SARSA Algorithm and On-Policy Temporal Difference Control]]
- [[Q Learning Algorithm and Off-Policy Temporal Difference Control]]
- [[Expected SARSA Algorithm]]





-----------
##  Recommended Notes and References

- [[Dynamic Programming for Optimal Stopping]]
- [[Value Function and Bellman Equation for MDP]]
- [[Markov Decision Process]]
- [[Dynamic Programming Algorithms]]


- [[Reinforcement Learning An Introduction by Sutton]] pp 62 - 67, 73 - 90
- [[Distributional Reinforcement Learning by Bellemare]] pp 116, 266, 135
- [[Markov Decision Processes by Puterman]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1135
- [[Foundations of Machine Learning by Mohri]] pp 315
