---
tags:
  - concept
  - reinforcement_learning/algorithm
  - reinforcement_learning/theory
keywords:
  - linear_approximation_value_function
  - linear_td
topics:
  - reinforcement_learning/algorithm
name: Linear Temporal Difference Learning
date of note: 2024-08-09
---

## Concept Definition

>[!important]
>**Name**: Linear Temporal Difference Learning

![[Value Function Approximation as Supervised Learning#^ac5adb]]

>[!important] Definition
>One of special cases of function approximation is the **linear approximation** $$\hat{v}(x; w) = \left\langle w , f(x) \right\rangle = \sum_{i=1}^{d}\,w_{i}\,f^{i}(x)$$ where $w\in \mathbb{R}^d$ is the **weights**, and $f: \mathcal{X} \to \mathbb{R}^d$ is called a **feature vector** or **basis functions**.


- [[Value Function Approximation as Supervised Learning]]
- [[Basis of Vector Space]]


>[!important] Definition
>The **gradient** of linear approximation of value function is the *feature vector*
>$$
>\nabla_{w}\,\hat{v}(x; w) = f(x)
>$$

### SGD Update

>[!important] Definition
>The **stochastic gradient descent (SGD) update** at time $t$ is simply 
>$$
>w_{t+1} = w_{t} + \alpha \left[ U_{t} - \hat{v}(X_{t}, w_{t}) \right]\,f(X_{t}) 
>$$
>where $U_{t}$ is the *target* and $f$ is the basis function.

- [[Stochastic Gradient Descent Algorithm]]
- [[Gradient Monte Carlo Method for Value Function Approximation]]

### Semi-Gradient TD(0)

![[Semi-Gradient Temporal Difference#^5680d7]]

>[!important] Definition
>The **semi-gradient TD(0) update** at time $t$ for linear value approximation is
>$$
>\begin{align*}
>w_{t+1} &= w_{t} + \alpha\,\left[ R_{t+1} + \gamma\,\left\langle w_{t} , f_{t+1} \right\rangle - \left\langle w_{t} , f_{t} \right\rangle \right]\,f_{t} \\[10pt]
>&=  w_{t} + \alpha\,\left[ R_{t+1}\,f_{t} - \left\langle w_{t} , \left(  f_{t} - \gamma f_{t+1} \right)  \right\rangle\,f_{t} \right]
\end{align*}
>$$
>where $f_{t} := f(X_{t}) := \left( f^{1}(X_{t}) \,{,}\ldots{,}\, f^{d}(X_{t})\right)\in \mathbb{R}^d.$

- [[Semi-Gradient Temporal Difference]]

### Fixed Point for Semi-Gradient TD(0)

>[!important]
>Note that the **conditional mean estimator** of $w_{t+1}$ is
>$$
> \mathbb{E}\left[ w_{t+1}\,|\, w_{t} \right] = w_{t} + \,\alpha\,\left( b - A\,w_{t} \right)
>$$
>where $$b :=  \mathbb{E}\left[ R_{t+1}\,f_{t} \right] \in \mathbb{R}^d$$ and $$A :=  \mathbb{E}\left[f_{t}\,\left( f_{t} - \gamma\,f_{t+1}\right)^{T}   \right] \in \mathbb{R}^{d\times d}$$
>
>This is the *minimum mean squared estimator*.

- [[Minimum Mean Square Estimation]]
- [[Uniformly Minimum Variance Unbiased Estimation]]





## Explanation





-----------
##  Recommended Notes and References


- [[Value Function Approximation as Supervised Learning]]
- [[Stochastic Gradient Descent Algorithm]]
- [[Monte Carlo and Applications]]

- [[Semi-Gradient Temporal Difference]]
- [[Gradient Descent Algorithm]]


- [[Value Function and Bellman Equation for MDP]]
- [[Minimum Mean Square Estimation]]



- [[Reinforcement Learning An Introduction by Sutton]] pp 202