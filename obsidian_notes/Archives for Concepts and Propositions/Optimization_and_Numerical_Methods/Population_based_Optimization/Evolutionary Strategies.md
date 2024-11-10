---
tags:
  - concept
  - optimization/theory
  - evolutionary_algorithm
  - evolutionary_computation
keywords:
  - covariance_matrix_adaptation_evolutionary_strategy
  - evolutionary_strategy
topics:
  - optimization
  - evolutionary_algorithm
name: Evolutionary Strategies
date of note: 2024-08-24
---

## Concept Definition

>[!important]
>**Name**: Evolutionary Strategies

>[!important] Definition
>**Evolution strategies** are a form of *distribution-based optimization* in which the distribution over the population is represented by a *Gaussian*, $\mathcal{N}(\mu, \Sigma)$. 
>
>Unlike *CEM*, the parameters are updated using **gradient ascent** applied to the *expected value of the objective*, rather than using *MLE* on a set of elite samples. 
>
>More precisely, consider the optimization problem via **smoothed objective** $$\max_{\theta\in \Theta} \mathcal{L}(\theta) =  \max_{\theta\in \Theta}\mathbb{E}_{ p(x|\theta) }\left[ f(X) \right].$$ 
>
>- We can use the *REINFORCE estimator* to compute the *gradient of this objective* as follows: 
>  $$
> \begin{align*}
> \nabla_{\theta}\,\mathcal{L}(\theta) &= \nabla_{\theta}\,\mathbb{E}_{ p(x|\theta) }\left[ f(X) \right] \\[5pt]
> &= \int_{\mathcal{X}} \nabla_{\theta}\, p(x|\theta)\,f(x)\,d\mu(x)\\[5pt]
> &= \int_{\mathcal{X}} [p(x|\theta)\, \nabla_{\theta}\,\log p(x|\theta)]\,f(x)\,d\mu(x) \\[5pt]
> &= \mathbb{E}_{ p(x|\theta) }\left[ f(X)\, \nabla_{\theta}\,\log p(X|\theta) \right] 
> \end{align*}
> $$
>- This can be approximated by drawing **Monte Carlo samples**.

- [[REINFORCE Algorithm for Monte Carlo Policy Gradient]]
- [[EDA or Estimation of Distribution Algorithm]]

>[!important] Definition
>The **canonical search gradient evolutionary strategy** is described as below:
>- *Require*: *objective (fitness) function* $f$
>- *Require*: $\theta_{1}$
>- *Require*: learning rate $\alpha >0$
>- For $t=1\,{,}\ldots{,}\,$ until termination condition is met:
>	- *Generate* a batch of $\lambda$ samples $$X_{t}^{1} \,{,}\ldots{,}\,X_{t}^{\lambda} \sim p(\cdot|\theta_{t})$$
>	- *Evaluate* the **fitness** of *parent population* $$f(X_{t}^{i}), \quad i=1\,{,}\ldots{,}\,\lambda$$
>	- Compute the **score functions** of population $$\nabla_{\theta}\, \log p(X_{t}^{i}\,|\,\theta_{t}), \quad i=1\,{,}\ldots{,}\,\lambda$$
>	- Compute the **search gradient** via **Monte Carlo estimation** $$d_{t} := \nabla_{\theta}\mathcal{L} = \frac{1}{\lambda}  \sum_{i=1}^{\lambda}f(X_{t}^{i})\,\nabla_{\theta}\, \log p(X_{t}^{i}\,|\,\theta_{t})$$
>	- Update the **search distribution** with *gradient ascent* $$\theta_{t+1} = \theta_{t} + \alpha\,d_{t} $$

^54d190

- [[Gradient Descent Algorithm]]
- [[Log-Likelihood Score Function]]
- [[REINFORCE Algorithm for Monte Carlo Policy Gradient]]


## Explanation


>[!info]
>The following is called the "**log-likelihood trick**".
> $$
> \begin{align*}
> \nabla_{\theta}\,\mathcal{L}(\theta) &= \nabla_{\theta}\,\mathbb{E}_{ p(x|\theta) }\left[ f(X) \right] \\[5pt]
> &= \int_{\mathcal{X}} \nabla_{\theta}\, p(x|\theta)\,f(x)\,d\mu(x)\\[5pt]
> &= \int_{\mathcal{X}} [p(x|\theta)\, \nabla_{\theta}\,\log p(x|\theta)]\,f(x)\,d\mu(x) \\[5pt]
> &= \mathbb{E}_{ p(x|\theta) }\left[ f(X)\, \nabla_{\theta}\,\log p(X|\theta) \right] 
> \end{align*}
> $$
>








-----------
##  Recommended Notes and References

- [[Parent Selection for Evolutionary Computation]]
- [[Survivor Selection for Evolutionary Computation]]



- [[CMA-ES or Covariance Matrix Adaptation Evolution Strategy]]
- [[Natural Evolutionary Strategies]]

- [[Evolutionary Computation Algorithms]]
- [[Combinatorial Optimization Problem]]
- [[Derivative-Free Optimization]]

- [[Policy Gradient Algorithm]]
- [[Markov Decision Process]]
- [[Sequential Decision Process]]


- [[Introduction to Evolutionary Computing by Eiben]] pp 14, 101
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 306 - 307
- Wierstra, D., Schaul, T., Glasmachers, T., Sun, Y., Peters, J., & Schmidhuber, J. (2014). Natural Evolution Strategies. _Journal of Machine Learning Research_, _15_(27), 949–980.