---
tags:
  - concept
  - machine_learning/algorithms
  - reinforcement_learning/book
  - reinforcement_learning/theory
  - reinforcement_learning/algorithm
keywords:
  - reinforce_algorithm
topics:
  - reinforcement_learning/algorithm
name: REINFORCE Algorithm for Monte Carlo Policy Gradient
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: REINFORCE Algorithm for Monte Carlo Policy Gradient

![[Value Function and Bellman Equation for MDP#^e3c917]]

![[Value Function and Bellman Equation for MDP#^f9fda7]]

>[!important] Definition
>Let  $\{T, \mathcal{X}, \mathcal{B}(\mathcal{X}), \mathcal{A}, \mathscr{F}_{\mathcal{A}}\,,\, p_{t}(\cdot|x, a)\,,\, r_{t}(x, a)\}$ be a *Markov decision process* and $v_{\pi}(x)$ is the *state-value function* under policy $\pi_{\theta}$, which is parameterized by $\theta$.
>
>Define the **loss function** as $$J(\theta) := v_{\pi_{\theta}}(x_{0})$$ which is the the *true value* under $\pi_{\theta}$.
>- Note that the *state-value function* can be obtained via the *action-value function* $$v_{\pi_{\theta}}(x) = \sum_{a\in \mathcal{A}(x)}\,\pi(a\,|\,x, \theta)\,q_{\pi_{\theta}}(x, a)$$
>- The policy is given by an *exponential soft-max function* $$\pi(a\,|\,x, \theta) := \text{softmax}(h(x, a, \theta)) := \frac{\exp(h(x, a, \theta))}{\sum_{b\in \mathcal{A}(x)}\exp(h(x, b, \theta))}$$ where the *preference function* can be defined as a linear function of some *feature vectors* $$h(x, a, \theta) = \left\langle  \theta\,,\,f(x, a)    \right\rangle$$
>  
>The principle of **REINFORCE** when computing the *gradient of expected value function* with respect to parameters 
>$$
>\begin{align*}
>\nabla_{\theta}\;\mathbb{E}_{ \mu }\left[  v_{\pi}(X) \right]
>\end{align*}
>$$  

- [[Value Function and Bellman Equation for MDP]]
- [[Markov Decision Process]]
- [[Policy Gradient Optimization]]
- [[Softmax Function and Log-Sum-Exp Function]]
- [[Linear Temporal Difference Learning]]


## Explanation





-----------
##  Recommended Notes and References



- [[Returns and Goals of Reinforcement Learning]]


- [[Reinforcement Learning An Introduction by Sutton]] pp 326 - 329
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 265, 1137, 1148
