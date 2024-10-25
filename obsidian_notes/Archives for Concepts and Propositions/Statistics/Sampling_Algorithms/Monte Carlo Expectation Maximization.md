---
tags:
  - concept
  - statistics/monte_carlo_simulation
  - statistics/inference
keywords:
  - expectation_maximization
  - monte_carlo_expectation_maximization
topics:
  - statistics/monte_carlo
  - statistics/inference
name: Monte Carlo Expectation Maximization
date of note: 2024-08-27
---

## Concept Definition

>[!important]
>**Name**: Monte Carlo Expectation Maximization

![[Expectation-Maximization Algorithm#^0c7718]]

>[!important] Definition
>A difficulty with the implementation of the EM algorithm is that each "**E-step**" requires the computation of the **expected log likelihood** 
>$$
>Q(\theta; \hat{\theta}_{k}) := \mathbb{E}_{ p }\left[  \log p(x, Z; \theta) \;|\; x, \hat{\theta}_{k} \right].
>$$
>
>The **Monte Carlo expectation maximization (MCEM)** overcome this difficulty by simulating $$Z_{1} \,{,}\ldots{,}\, Z_{m} \sim p(z\,|\,x, \, \hat{\theta}_{k})$$ and *approximating* the *complete-data log-likelihood* based on generated population 
>$$
>\hat{Q}(\theta; \hat{\theta}_{k}) = \frac{1}{m}\sum_{j=1}^{m}\log p(x, Z_{j}\,;\, \theta). 
>$$
>- for each $x$, as $m\to \infty$,  $$\hat{Q}(\theta; \hat{\theta}_{k}) \to Q(\theta; \hat{\theta}_{k}).$$


>[!important] Definition
>The **Monte Carlo expectation-maximization (MCEM) algorithm** works as below:
>- Repeat the following steps until convergence:
>	- **Monte Carlo E-Step**: 
>		- **Monte Carlo Sampling**: Generate a batch of $m$ samples on latent variable $Z$ given observed data $x$ and previous *estimated parameters* $\hat{\theta}_{k}$, i.e. $$Z_{1} \,{,}\ldots{,}\, Z_{m} \sim p(z\,|\,x, \, \hat{\theta}_{k})$$ where $p(z\,|\,x, \, \hat{\theta}_{k})$ is the conditional density. 
>		- **Monte Carlo Estimation**: Estimate the expectation of **complete log-likelihood function** based on generated samples $$\hat{Q}(\theta; \hat{\theta}_{k}) := \frac{1}{m}\sum_{j=1}^{m}\log p(x, Z_{j} ; \theta)$$
>	- **M-Step**: Estimate $\hat{\theta}_{k+1}$ by **maximizing** the *estimated* proposed log-likelihood function $$\hat{\theta}_{k+1} \in \arg\max_{\theta \in \Theta}\,\hat{Q}(\theta; \hat{\theta}_{k})$$
>	- $k \leftarrow k+1$.

## Explanation

>[!info]
>The Monte Carlo sampling can be achieved via **MCMC algorithms**

- [[Markov Chain Monte Carlo Methods]]
- [[Metropolis-Hastings Algorithm]]
- [[Gibbs Sampling]]
- [[Hamiltonian Monte Carlo]]


## Evolutionary Computation

>[!info]
>Note that the **majorization function** is proportional to the **cross entropy term**
>$$
>- Q(\theta; \hat{\theta}_{k}) \propto  \mathbb{E}_{ Z \sim p(z|x,\, \hat{\theta}_{k}) }\left[ -\log p(Z\,|\,x, \theta)  \right] := H_{ce}(p(\cdot|x,\, \hat{\theta}_{k})\,,\, p(\cdot\,|\,x, \theta))
>$$

- [[Cross-Entropy Loss Function]]
- [[Majorization-Minimization Algorithm]]
- Brookes, D., Busia, A., Fannjiang, C., Murphy, K., & Listgarten, J. (2020). A view of estimation of distribution algorithms through the lens of expectation-maximization. _Proceedings of the 2020 Genetic and Evolutionary Computation Conference Companion_, 189–190. [https://doi.org/10.1145/3377929.3389938](https://doi.org/10.1145/3377929.3389938)


![[EDA or Estimation of Distribution Algorithm#^6ffc51]]

![[EDA or Estimation of Distribution Algorithm#^6d994f]]


- [[EDA or Estimation of Distribution Algorithm]]








-----------
##  Recommended Notes and References


- [[Expectation-Maximization Algorithm]]
- [[Evidence Lower Bound]]
- [[Monte Carlo and Applications]]
- [[Markov Chain Monte Carlo Methods]]


- [[Monte Carlo Statistical Methods by Robert]] pp 183 - 184
