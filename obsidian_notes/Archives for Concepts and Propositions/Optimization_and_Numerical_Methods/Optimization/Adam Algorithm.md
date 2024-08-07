---
tags:
  - concept
  - optimization/algorithm
  - deep_learning/algorithms
keywords:
  - adam_algorithm
  - stochastic_gradient_descent
  - momentum_algorithm
  - rmsprop_algorithm
topics:
  - optimization
  - deep_learning/algorithm
name: Adam Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Adam Algorithm

![[Stochastic Gradient Descent with Momentum#^2c265d]]

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
>The **Adam algorithm** works as follows
>- *Require*: *learning rate* $\alpha$, 
>- *Require*: **exponential decay rate for moment estimate** $\rho_{1} \in [0,1)$ and $\rho_{2} \in [0,1)$
>- *Require*: Initialize parameter $\theta_{0}$
>- *Require*: small constant $\delta$ for numerical stability
>- Initialize **1st moment (i.e. momentum) variable** $m_{0}=0$, 
>- Initialize **2nd moment variable** $r_{0}=0$
>- Initialize **time step** $k=0$
>- While the *convergence criteria* not met:
>	- *Sample* a *mini-batch* of $m$ samples $(X_{1}^{(k)} \,{,}\ldots{,}\,X_{m}^{(k)} )$ from distribution $p(x)$
>	- *Estimate* the *gradient* via *Monte Carlo method*: $$\hat{g}_{k} := \frac{1}{m}\sum_{i=1}^{m} \nabla_{\theta} f(X_{i}^{(k)}, \theta_{k})$$
>	- Update **biased first-order moment estimate of gradient** $$m_{k+1} = \rho_{1}\,m_{k} + (1 - \rho_{1})\,\hat{g}_{k}$$
>	- Update **biased second-order moment estimate of gradient** $$r_{k+1} = \rho_{2}\,r_{k} + (1 - \rho_{2})\,\hat{g}_{k}\, \odot \hat{g}_{k}$$
>	- **Correct bias** in *first-order moment estimate* $$\hat{m}_{k+1} = \frac{m_{k+1}}{1 - \rho_{1}^{k+1}}$$
>	- **Correct bias** in *second-order moment estimate* $$\hat{r}_{k+1} = \frac{r_{k+1}}{1 - \rho_{2}^{k+1}}$$
>	- Compute *update direction* $$\hat{d}_{k+1} = - \frac{\alpha}{\delta + \sqrt{\hat{r}_{k+1}}} \odot \hat{m}_{k+1}$$
>	- Update parameter along the direction $\hat{d}_{k+1}$ $$\theta_{k+1} = \theta_{k} + \hat{d}_{k+1}$$ 
>	- $k \leftarrow k+1$



## Explanation

>[!quote]
>**Adam** (Kingma and Ba, 2014) is yet another adaptive learning rate optimization algorithm and is presented in algorithm 8.7. The name “Adam” derives from the phrase “**adaptive moments.**” In the context of the earlier algorithms, it is perhaps best seen as a variant on **the combination** of **RMSProp** and **momentum** with a few important distinctions. First, in Adam, momentum is incorporated directly as an estimate of the *first-order moment* (with exponential weighting) of the *gradient*. The most straightforward way to add momentum to RMSProp is to apply momentum to the **rescaled gradients**. The use of momentum in combination with rescaling does not have a clear theoretical motivation. Second, Adam includes **bias corrections** to the estimates of both the first-order moments (the momentum term) and the **(uncentered) second-order moments** to account for their initialization at the origin (see algorithm 8.7). RMSProp also incorporates an estimate of the (uncentered) second-order moment; however, it lacks the correction factor. Thus, unlike in Adam, the RMSProp second-order moment estimate may have high bias early in training. Adam is generally regarded as being **fairly robust to the choice of hyperparameters**, though the learning rate sometimes needs to be changed from the suggested default.
>
>-- [[Deep Learning by Goodfellow]] pp 301



## Comparison







-----------
##  Recommended Notes and References

- [[AdaGrad Algorithm]]
- [[RMSProp Algorithm]]


- [[Stochastic Gradient Descent Algorithm]]
- [[Stochastic Gradient Descent with Momentum]]


- [[Deep Learning by Goodfellow]] pp 301
- [[Deep Learning Foundations and Concepts by Bishop]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]