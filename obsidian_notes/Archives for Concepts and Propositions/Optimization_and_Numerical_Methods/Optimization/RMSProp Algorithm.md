---
tags:
  - concept
  - optimization/algorithm
  - deep_learning/algorithms
  - optimization/convex_optimization
keywords:
  - rmsprop_algorithm
  - stochastic_gradient_descent
topics:
  - optimization
  - deep_learning/algorithm
name: RMSProp Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: RMSProp Algorithm

![[AdaGrad Algorithm#^d7cf1b]]

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
>The **AdaGrad algorithm** works as follows
>- *Require*: *learning rate* $\alpha$, **decay rate** $\rho$
>- *Require*: Initialize parameter $\theta_{0}$
>- *Require*: small constant $\delta$ for numerical stability
>- Initialize **gradient accumulation variable** $r_{0}=0$
>- While the *convergence criteria* not met:
>	- **Sample** a *mini-batch* of $m$ samples $(X_{1}^{(k)} \,{,}\ldots{,}\,X_{m}^{(k)} )$ from distribution $p(x)$
>	- *Estimate* the *gradient* via *Monte Carlo method*: $$\hat{g}_{k} := \frac{1}{m}\sum_{i=1}^{m} \nabla_{\theta} f(X_{i}^{(k)}, \theta_{k})$$
>	- **Accumulate squared gradient** $$r_{k+1} = \rho\,r_{k} + (1 - \rho)\,\hat{g}_{k}\, \odot \hat{g}_{k}$$
>	- Compute *update direction* $$\hat{d}_{k+1} = - \frac{\alpha}{\sqrt{\delta + r_{k+1}}} \odot \hat{g}_{k}$$
>	- Update parameter along the direction $\hat{d}_{k}$ $$\theta_{k+1} = \theta_{k} + \hat{d}_{k+1}$$ 
>	- $k \leftarrow k+1$

^7c751d



## Explanation

>[!quote]
>The **RMSProp algorithm** (Hinton, 2012) modifies **AdaGrad** to perform better in the *nonconvex* setting by changing the *gradient accumulation* into an **exponentially weighted moving average.** AdaGrad is designed to converge rapidly when applied to a *convex function*. When applied to a nonconvex function to train a neural network, the learning trajectory may pass through many different structures and eventually arrive at a region that is a locally convex bowl. AdaGrad **shrinks the learning rate** according to the *entire history of the squared gradient* and may have made the learning rate *too small* before arriving at such a convex structure. RMSProp uses an **exponentially decaying average** to discard history from the *extreme past* so that it can converge rapidly after finding a convex bowl, as if it were an instance of the AdaGrad algorithm initialized within that bowl.
>
>
>-- [[Deep Learning by Goodfellow]] pp 299



-----------
##  Recommended Notes and References

- [[AdaGrad Algorithm]]
- [[Adam Algorithm]]


- [[Stochastic Gradient Descent Algorithm]]
- [[Stochastic Gradient Descent with Momentum]]


- [[Deep Learning by Goodfellow]] pp 299
- [[Deep Learning Foundations and Concepts by Bishop]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]