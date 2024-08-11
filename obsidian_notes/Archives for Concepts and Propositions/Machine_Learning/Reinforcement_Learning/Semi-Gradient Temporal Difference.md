---
tags:
  - concept
  - reinforcement_learning/algorithm
  - reinforcement_learning/theory
keywords:
  - semi_gradient_temporal_difference
  - gradient_descent_algorithm
  - stochastic_gradient_descent
  - temporal_difference_learning
topics:
  - reinforcement_learning/theory
  - reinforcement_learning/algorithm
name: Semi-Gradient Temporal Difference
date of note: 2024-08-09
---

## Concept Definition

>[!important]
>**Name**: Semi-Gradient Temporal Difference

![[Value Function Approximation as Supervised Learning#^ac5adb]]

![[Gradient Monte Carlo Method for Value Function Approximation#^00a8b6]]

- [[Gradient Monte Carlo Method for Value Function Approximation]]

>[!important] Definition
>Similar to *temporal difference learning*, we replace **target** from the *Monte Carlo estimate of return* to the **temporal difference estimate** $$\hat{G}_{t} := R_{t+1} + \gamma \hat{v}(X_{t+1}, w_{t}),$$
>

^5680d7


### Semi-Gradient Temporal Difference

>[!important] Definition
>The **Semi-Gradient Temporal Difference TD(0)** algorithm is described as the followings:
>- *Require*: the *policy* $\pi$ in evaluation
>- *Require*: approximate value function $\hat{v}(\cdot; w): \mathcal{X} \to \mathbb{R}$ parameterized by $w\in \mathbb{R}^d$ and is *differentiable* in $w$
>- *Require*: step size $\alpha >0$
>- *Initialize* $w_{0}\in \mathbb{R}^d$
>- For *episode* $k=1 \,{,}\ldots{,}\,$
>	- Initialize state $X_{0}$
>	- For $t=0\,{,}\ldots{,}\,T-1$
>		- Choose and take *action* $$A_{t} \sim \pi(\cdot\,|\,X_{t})$$
>		- Observe *reward* $R_{t+1}$ and *next state* $X_{t+1}$
>		- Compute the **temporal difference estimate** of return $$\hat{G}_{t} := R_{t+1} + \gamma\,  \hat{v}(X_{t+1}, w_{t})$$
>		- Update **parameter** for value function using **SGD** on **TD error** $$\begin{align*}w_{t+1} &= w_{t} + \alpha\,\left[ \hat{G}_{t}  - \hat{v}(X_{t}, w_{t}) \right]\;  \nabla_{w}\hat{v}(X_{t}, w_{t})\\[5pt]&=  w_{t} + \alpha\,\left[ R_{t+1} + \gamma\,  \hat{v}(X_{t+1}, w_{t})  - \hat{v}(X_{t}, w_{t}) \right]\;  \nabla_{w}\hat{v}(X_{t}, w_{t})\end{align*}$$

- [[Temporal Difference Learning]]


## Explanation

>[!quote]
>Note that *bootstrapping methods* are **not** in fact instances of **true gradient descent**.
>- They take into account the *effect* of *changing the weight vector* $w_{t}$ on the estimate, but **ignore its effect** on the **target**.
>  
>They include only *a part of the gradient* and, accordingly, we call them **semi-gradient methods**. 
>
>-- [[Reinforcement Learning An Introduction by Sutton]] pp 202 





-----------
##  Recommended Notes and References


- [[Gradient Monte Carlo Method for Value Function Approximation]]
- [[Monte Carlo and Applications]]
- [[Stochastic Gradient Descent Algorithm]]
- [[Gradient Descent Algorithm]]
- [[Gradient of Smooth Map]]

- [[Value Function Approximation as Supervised Learning]]
- [[Value Function and Bellman Equation for MDP]]
- [[Minimum Mean Square Estimation]]



- [[Reinforcement Learning An Introduction by Sutton]] pp 203