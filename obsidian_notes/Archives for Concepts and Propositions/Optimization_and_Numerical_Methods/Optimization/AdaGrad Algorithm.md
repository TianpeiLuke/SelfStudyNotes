---
tags:
  - concept
  - optimization/algorithm
  - deep_learning/algorithms
keywords:
  - adagrad_algorithm
  - stochastic_gradient_descent
topics:
  - optimization
  - deep_learning/algorithm
name: AdaGrad Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: AdaGrad Algorithm

![[Stochastic Gradient Descent Algorithm#^c471ba]]


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
>- *Require*: **learning rate** $\alpha$
>- *Require*: Initialize parameter $\theta_{0}$
>- *Require*: small constant $\delta$ for numerical stability
>- Initialize **gradient accumulation variable** $r_{0}=0$
>- While the *convergence criteria* not met:
>	- **Sample** a *mini-batch* of $m$ samples $(X_{1}^{(k)} \,{,}\ldots{,}\,X_{m}^{(k)} )$ from distribution $p(x)$
>	- *Estimate* the *gradient* via *Monte Carlo method*: $$\hat{g}_{k} := \frac{1}{m}\sum_{i=1}^{m} \nabla_{\theta} f(X_{i}^{(k)}, \theta_{k})$$
>	- **Accumulate squared gradient** $$r_{k+1} = r_{k} + \hat{g}_{k}\, \odot \hat{g}_{k}$$
>	- Compute *update direction* $$\hat{d}_{k+1} = - \frac{\alpha}{\delta + \sqrt{r_{k+1}}} \odot \hat{g}_{k}$$
>	- Update parameter along the direction $\hat{d}_{k+1}$ $$\theta_{k+1} = \theta_{k} + \hat{d}_{k+1}$$ 
>	- $k \leftarrow k+1$

^d7cf1b




## Explanation

>[!quote]
>The **AdaGrad algorithm**, shown in algorithm 8.4, individually *adapts the learning rates* of all model parameters by scaling them **inversely proportional** to the **square root** of the **sum** of **all the historical squared values** of *the gradient* (Duchi et al., 2011). The parameters with the largest partial derivative of the loss have a correspondingly rapid decrease in their learning rate, while parameters with small partial derivatives have a relatively small decrease in their learning rate. The net effect is greater progress in the more gently sloped directions of parameter space
>
>-- [[Deep Learning by Goodfellow]] pp 297



-----------
##  Recommended Notes and References


- [[RMSProp Algorithm]]
- [[Adam Algorithm]]

- [[Stochastic Gradient Descent Algorithm]]
- [[Stochastic Gradient Descent with Momentum]]


- [[Deep Learning by Goodfellow]]
- [[Deep Learning Foundations and Concepts by Bishop]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]