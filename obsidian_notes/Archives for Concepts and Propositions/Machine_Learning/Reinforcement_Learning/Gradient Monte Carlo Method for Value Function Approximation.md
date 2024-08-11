---
tags:
  - concept
  - reinforcement_learning/algorithm
  - reinforcement_learning/theory
keywords:
  - gradient_descent_algorithm
  - stochastic_gradient_descent
  - value_function_approximation
topics:
  - reinforcement_learning/algorithm
name: Gradient Monte Carlo Method for Value Function Approximation
date of note: 2024-08-09
---

## Concept Definition

>[!important]
>**Name**: Gradient Monte Carlo Method for Value Function Approximation

![[Value Function Approximation#^ac5adb]]

![[Value Function Approximation#^08c9a9]]

![[Stochastic Gradient Descent Algorithm#^c471ba]]


>[!important] Definition
>The goal of **value function approximation** is to minimize the *mean squared error* 
>$$
> \min_{w} \frac{1}{2} \sum_{x\in \mathcal{X}}\left[ v_{\pi}(x) - \hat{v}(x, w) \right]^2 
>$$
>where $\mathcal{X}$ is the *state-space*.
>
>Using the **stochastic gradient descent (SGD)**, at each iteration $t$, the weight update is
>$$
>\begin{align*}
> w_{t+1} &= w_{t} - \alpha\, \nabla_{w}\left\{ \frac{1}{2}\left[ v_{\pi}(X_{t}) - \hat{v}(X_{t}, w_{t}) \right]^2\right\} \\[5pt]
> &= w_{t} + \alpha\,\left[ v_{\pi}(X_{t}) - \hat{v}(X_{t}, w_{t}) \right]\;  \nabla_{w}\hat{v}(X_{t}, w_{t}) 
>\end{align*}
>$$

- [[Value Function Approximation]]
- [[Stochastic Gradient Descent Algorithm]]
- [[Minimum Mean Square Estimation]]

### SGD with Approximate Target

>[!important] Definition
>Assume that $U_{t}$ is a possible random **approximate target function** corresponding to state $X_{t}$
>$$
>U_{t} \approx v_{\pi}(X_{t})
>$$
>Usually assume that $U_{t}$ is **unbiased**, i.e. $$\mathbb{E}\left[ U_{t} | X_{t} =x \right] = v_{\pi}(x)$$
>
>Then the corresponding **SGD update** at time $t$ is 
>$$
>\begin{align*}
> w_{t+1} &= w_{t} + \alpha\,\left[ U_{t} - \hat{v}(X_{t}, w_{t}) \right]\;  \nabla_{w}\hat{v}(X_{t}, w_{t}) 
>\end{align*}
>$$

- [[Bias of Point Estimator and Unbiasedness]]


### Gradient Monte Carlo Algorithm

>[!important] Definition
>The **Gradient Monte Carlo** algorithm based on *stochastic gradient descent* is described as followings:
>- *Require*: the *policy* $\pi$ in evaluation
>- *Require*: approximate value function $\hat{v}(\cdot; w): \mathcal{X} \to \mathbb{R}$ parameterized by $w\in \mathbb{R}^d$ and is *differentiable* in $w$
>- *Require*: step size $\alpha >0$
>- *Initialize* $w_{0}\in \mathbb{R}^d$
>- For *episode* $k=1 \,{,}\ldots{,}\,$
>	- **Sample Phase**:
>		- Initialize state $X_{0}$
>		- For $s=0,\,1 \,{,}\ldots{,}\,T-1$:
>			- Choose *action* $A_{s} \sim \pi(\cdot|X_{s})$
>			- Observe *reward* $R_{s+1}$ and *next state* $X_{s+1}$
>	- **Estimation (Prediction) Phase**
>		- For $t=0\,{,}\ldots{,}\,T-1$
>			- Estimate **return** using **Monte Carlo method** $$G_{t} = \sum_{s=1}^{T-t}\gamma^{s-1}R_{t+s}$$
>			- Update **parameter** for approximate value function using **SGD** $$ w_{t+1} = w_{t} + \alpha\,\left[ G_{t} - \hat{v}(X_{t}, w_{t}) \right]\;  \nabla_{w}\hat{v}(X_{t}, w_{t})$$

- [[Monte Carlo Prediction for Value Estimation]]


## Explanation





-----------
##  Recommended Notes and References


- [[Stochastic Gradient Descent Algorithm]]
- [[Monte Carlo and Applications]]

- [[Semi-Gradient Temporal Difference]]
- [[Gradient Descent Algorithm]]


- [[Value Function and Bellman Equation for MDP]]
- [[Prediction and Control Problems in Reinforcement Learning]]

- [[Minimum Mean Square Estimation]]



- [[Reinforcement Learning An Introduction by Sutton]] pp 202