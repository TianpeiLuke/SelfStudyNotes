---
tags:
  - concept
  - optimization/algorithm
  - deep_learning/algorithms
  - optimization/convex_optimization
keywords:
  - stochastic_gradient_descent
  - gradient_descent_algorithm
topics:
  - optimization/algorithm
  - deep_learning/algorithm
name: Stochastic Gradient Descent Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Stochastic Gradient Descent Algorithm

>[!important] Definition
>Let  $f: \mathcal{X} \times \Theta \to \mathbb{R}$ be *continuous differentiable* in $\theta\in \Theta$. Let $X \in \mathcal{X}$ be a random variable in $\mathcal{X}$ and the p.d.f. of $X$ with respect to a dominating measure $\nu$ is $p(x)$.
>
>Consider the *unconstrained* **stochastic minimization problem** 
>$$
>\begin{align*}
> \min_{\theta \in \Theta} \,&\,\mathbb{E}_{p}\left[  f(X; \theta) \right]
>\end{align*}
>$$
>
>The **stochastic gradient descent (SGD) algorithm** works as follows
>- *Require*: **learning rate** $\alpha_{k}$
>- *Require*: Initialize parameter $\theta_{0}$
>- While the *convergence criteria* not met:
>	- **Sample** a *mini-batch* of $m$ samples $(X_{1}^{(k)} \,{,}\ldots{,}\,X_{m}^{(k)} )$ from distribution $p(x)$
>	- **Estimate** the **negative gradient** via *Monte Carlo method*: $$\hat{d}_{k} := -\frac{1}{m}\sum_{i=1}^{m} \nabla_{\theta} f(X_{i}^{(k)}, \theta_{k})$$
>	- Choose learning rate $\alpha_{k} >0$
>	- Update parameter along the *estimated gradient direction* $$\theta_{k+1} = \theta_{k} + \alpha_{k}\;\hat{d}_{k}$$ 
>	- $k \leftarrow k+1$

^c471ba

- [[Gradient Descent Algorithm]]
- [[Monte Carlo and Applications]]

### Choice of Learning Rate

>[!important] Proposition
>The condition for $\alpha_{k}$ to guarantee **convergence** of SGD is that 
>$$
>\sum_{k=1}^{\infty}\alpha_{k} = \infty, \quad \text{ and } \quad \sum_{k=1}^{\infty}\alpha_{k}^2 < \infty.
>$$

>[!important]
>In practice, it is common to **delay** learning rate **linearly** until iteration $\tau$
>$$
>\alpha_{k} = (1- \epsilon)\,\alpha_{0} + \epsilon\,\alpha_{\tau},
>$$ 
>with $$\epsilon := \frac{k}{\tau}.$$


## Explanation

>[!info]
>[[Gradient Descent Algorithm]] updates of parameter 
>$$
>\theta_{k+1} = \theta_{k} - \alpha_{k}\, \nabla_{\theta} \mathbb{E}_{ p }\left[  f(X; \theta) \right]
>$$
>If $\nabla_{\theta}f(x; \theta) \in L^1(\mathcal{X}, \mathscr{F},p)$, then 
>$$
>\theta_{k+1} = \theta_{k} - \alpha_{k}\, \mathbb{E}_{ p }\left[  \nabla_{\theta} f(X; \theta) \right]
>$$
>
>In *SGD*, we approximate the gradient via *Monte Carlo estimate*
>$$
>\nabla_{\theta} \mathbb{E}_{ p }\left[  f(X; \theta) \right] \approx \nabla_{\theta}\left(\frac{1}{m}\sum_{i=1}^{m}f(X_{i}; \theta) \right)
>$$



## SGD with Adaptive Learning Rate

- [[Adam Algorithm]]
- [[Stochastic Gradient Descent with Momentum]]
- [[RMSProp Algorithm]]
- [[AdaGrad Algorithm]]
- [[Adam Algorithm]]


## Online Convex Optimization and Online Gradient Descent

- [[Online Gradient Decent Algorithm]]
- [[Online Convex Optimization]]





-----------
##  Recommended Notes and References



- [[Numerical Optimization by Nocedal]]
- [[Nonlinear Programming by Bertsekas]]
- [[Deep Learning by Goodfellow]] pp 147, 286
- [[Deep Learning Foundations and Concepts by Bishop]] pp 214
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 265 - 267
- [[Monte Carlo Statistical Methods by Robert]] pp 162
- [[Reinforcement Learning An Introduction by Sutton]] pp 200 - 203