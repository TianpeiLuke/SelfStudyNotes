---
tags:
  - concept
  - optimization/algorithm
  - deep_learning/algorithms
  - optimization/convex_optimization
keywords:
  - stochastic_gradient_descent
  - momentum_algorithm
  - nesterov_momentum
topics:
  - optimization/algorithm
  - deep_learning/algorithm
name: Stochastic Gradient Descent with Nesterov Momentum
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Stochastic Gradient Descent with Nesterov Momentum

![[Stochastic Gradient Descent Algorithm#^c471ba]]


>[!important] Definition
>Let  $f: \mathcal{X} \times \Theta \to \mathbb{R}$ be *continuous differentiable* in $\theta\in \Theta$. Let $X \in \mathcal{X}$ be a random variable in $\mathcal{X}$ and the p.d.f. of $X$ with respect to a dominating measure $\nu$ is $p(x)$.
>
>Consider the *unconstrained stochastic minimization problem*
>$$
>\begin{align*}
> \min_{\theta \in \Theta} \,&\,\mathbb{E}_{p}\left[  f(X; \theta) \right]
>\end{align*}
>$$
>
>The **stochastic gradient descent (SGD) algorithm with Nesterov momentum** works as follows
>- *Require*: **learning rate** $\alpha$, momentum parameter $\beta$
>- *Require*: Initial parameter $\theta_{0}$, initial *momentum* $m_{0}$
>- While the *convergence criteria* not met:
>	- **Sample** a *mini-batch* of $m$ samples $(X_{1}^{(k)} \,{,}\ldots{,}\,X_{m}^{(k)} )$ from distribution $p(x)$
>	- **Interim update** on *parameter* $$\hat{\theta}_{k} = \theta_{k} + \alpha\,m_{k}$$ 
>	- **Estimate** the **negative gradient** at *interim point* via *Monte Carlo method*: $$\hat{d}_{k} := -\frac{1}{m}\sum_{i=1}^{m} \nabla_{\theta} f(X_{i}^{(k)}, \hat{\theta}_{k})$$
>	- Update **momentum** along the *estimated gradient direction*:  $$m_{k+1} =  \alpha\;m_{k} + \beta\;\hat{d}_{k}$$ 
>	- Update **parameter** along the *momentum* $$\theta_{k+1} = \theta_{k} + m_{k+1}$$ 
>	- $k \leftarrow k+1$





## Explanation





-----------
##  Recommended Notes and References

- [[Stochastic Gradient Descent with Momentum]]
- [[Stochastic Gradient Descent Algorithm]]
- [[Gradient Descent Algorithm]]


- [[Deep Learning by Goodfellow]] pp 291
- [[Convex Optimization Algorithms by Bertsekas]] pp 63
- [[Deep Learning Foundations and Concepts by Bishop]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]