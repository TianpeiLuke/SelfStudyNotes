---
tags:
  - concept
  - optimization/theory
  - evolutionary_algorithm
  - evolutionary_computation
keywords:
  - natural_gradient_descent
  - natural_evolutionary_strategies
  - evolutionary_strategy
topics:
  - optimization/algorithm
  - evolutionary_algorithm
name: Natural Evolutionary Strategies
date of note: 2024-08-24
---

## Concept Definition

>[!important]
>**Name**: Natural Evolutionary Strategies

![[Evolutionary Strategies#^54d190]]


>[!important] Definition
>The **canonical natural evolutionary strategy** is described as below:
>- *Require*: *objective (fitness) function* $f$
>- *Require*: $\theta_{1}$
>- *Require*: learning rate $\alpha >0$
>- For $t=1\,{,}\ldots{,}\,$ until termination condition is met:
>	- *Generate* a batch of $\lambda$ samples $$X_{t}^{1} \,{,}\ldots{,}\,X_{t}^{\lambda} \sim p(\cdot|\theta_{t})$$
>	- *Evaluate* the **fitness** of *parent population* $$f(X_{t}^{i}), \quad i=1\,{,}\ldots{,}\,\lambda$$
>	- Compute the **score functions** of population $$\nabla_{\theta}\, \log p(X_{t}^{i}\,|\,\theta_{t}), \quad i=1\,{,}\ldots{,}\,\lambda$$
>	- Compute the **search gradient** via *Monte Carlo method* on parent population $$d_{t} := \nabla_{\theta}\mathcal{L} = \frac{1}{\lambda}  \sum_{i=1}^{\lambda}f(X_{t}^{i})\,\nabla_{\theta}\log p(X_{t}^{i}\,|\,\theta_{t})$$
>	- Estimate **Fisher Information matrix** of $\theta$ via *Monte Carlo method*  on  parent population $$I_{t} = \frac{1}{\lambda}\,\sum_{i=1}^{\lambda} \left[\nabla_{\theta}\log p(X_{t}^{i}\,|\,\theta_{t})\right]\left[\nabla_{\theta}\log p(X_{t}^{i}\,|\,\theta_{t})\right]^{T} $$
>	- Update the **search distribution** with *natural gradient ascent* $$\theta_{t+1} = \theta_{t} + \alpha\,I_{t}^{-1}\,d_{t} $$

- [[Evolutionary Strategies]]
- [[Fisher Information for Exponential Family]]


## Explanation

>[!info]
>We can see natural gradient descent as **Newton's method** where the *Hessian* is replaced by the *Fisher information matrix*.

- [[Newton Method]]

## Natural Parameters in Exponential Family

- [[Exponential Family of Distributions]]
- [[Log-Partition Function of Exponential Family]]
- [[Gaussian Graphical Model]]


## Natural Gradient in Information Geometry


- [[Gradient Descent Algorithm#Riemannian Manifold]]
- [[Fisher Information Metric of Statistical Manifold]]
- [[Divergence Function on Manifold]]




-----------
##  Recommended Notes and References

- [[Parent Selection for Evolutionary Computation]]
- [[Survivor Selection for Evolutionary Computation]]

- [[Gradient Descent Algorithm#Riemannian Manifold]]
- [[Fisher Information Metric of Statistical Manifold]]
- [[Geodesic on Manifolds]]

- [[Fisher Information for Exponential Family]]

- [[Exponential Family of Distributions]]
- [[Log-Partition Function of Exponential Family]]

- [[Evolutionary Strategies]]
- [[CMA-ES or Covariance Matrix Adaptation Evolution Strategy]]
- [[Evolutionary Computation Algorithms]]
- [[Derivative-Free Optimization]]


- [[Introduction to Evolutionary Computing by Eiben]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 306 - 307
- Wierstra, D., Schaul, T., Glasmachers, T., Sun, Y., Peters, J., & Schmidhuber, J. (2014). Natural Evolution Strategies. _Journal of Machine Learning Research_, _15_(27), 949–980.