---
tags:
  - concept
  - optimization/theory
  - evolutionary_algorithm
  - evolutionary_computation
keywords:
  - cross_entropy_method
  - eda_algorithm
  - estimation_of_distribution_algorithm
topics:
  - evolutionary_algorithm
name: Cross-Entropy Method for EDA
date of note: 2024-08-24
---

## Concept Definition

>[!important]
>**Name**: Cross-Entropy Method for EDA

![[EDA or Estimation of Distribution Algorithm#^ad5721]]

>[!important] Definition
>The **cross-entropy method (CEM)** is a special case of **EDA** where the population is represented by a *multivariate Gaussian*. 
>
>- In particular, we estimate $\mu_{t+1}, \Sigma_{t+1}$ bases on *selected top $K$ fittest samples* $\mathcal{S}_{t}^{(s)}$
>- This is closely related to **sequential monte carlo (SMC)** methods [[Sequential Importance Sampling]]

- [[Cross-Entropy Loss Function]]
- [[EDA or Estimation of Distribution Algorithm]]



>[!important] Definition
>The **cross entropy method (CME)** generate *offsprings* based on the following steps:
>- *Initialize* population $\mathcal{S}_{0}$ with $K$ random *candidate solutions*;
>- For $t= 0,\,1\,{,}\ldots{,}\,$ until the *termination condition* is satisfied:
>	- **Compute** the **fitness** for each candidate $X_{t}^{i}$ in $\mathcal{S}_{t}$, $$f(X_{t}^{i})$$
>	- **Select** a *subpopulation* $\mathcal{S}_{t}^{(s)}$ of $m$ **elites**  based on the *fittest* subset of  population. $$\mathcal{S}_{t}^{(s)} = \left\{ X_{t}^{i} \in \mathcal{S}_{t}: f(X_{t}^{i}) \ge f(X_{t}^{(m)}) \right\}$$ where $X_{t}^{(j)}$ is the *j*-th fittest samples.
>	- **Model Fitting**: estimate the *mean* and *covariance* of the Gaussian distribution
>		- $$\mu_{t+1} = \frac{1}{m}\sum_{X_{t}^{i} \in \mathcal{S}_{t}^{(s)}}X_{t}^{i}$$
>		- $$\Sigma_{t+1} = \frac{1}{m}\sum_{X_{t}^{i} \in \mathcal{S}_{t}^{(s)}}\left( X_{t}^{i} - \mu_{t+1}\right)\left( X_{t}^{i} - \mu_{t+1}\right)^{T}$$
>	- **Model Sampling**:
>		- **Generate** a set of $K$ candidates according to the *learned Gaussian distribution* $$X_{t+1}^{i} \sim \mathcal{N}(\mu_{t+1}, \Sigma_{t+1}), \quad i=1\,{,}\ldots{,}\,K$$
>	- Choose the *offspring population* as the generated candidates $$\mathcal{S}_{t+1} = \left\{ X_{t+1}^{i}, \; i=1\,{,}\ldots{,}\,K \right\}.$$

- [[Gaussian Random Vector]]
- [[Gaussian Graphical Model]]
- [[Gaussian Bayesian Network]]
- [[Expectation-Maximization Algorithm]]


## Explanation

>[!quote]
>The *CEM* is sometimes used for **model-based RL** (Section 35.4), since it is simple and can find reasonably good optima of multimodal objectives. It is also sometimes used inside of **Bayesian optimization** (Section 6.6), to optimize the multi-modal acquisition function.
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 306

- [[Model-based Reinforcement Learning]]



-----------
##  Recommended Notes and References


- [[Differentiable Cross-Entropy Method]]
- [[Cross-Entropy Loss Function]]
- [[EDA or Estimation of Distribution Algorithm]]

- [[Natural Evolutionary Strategies]]
- [[Evolutionary Algorithms]]
- [[Derivative-Free Optimization]]

- [[REINFORCE Algorithm with Baseline]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 298 - 307
- [[Introduction to Evolutionary Computing by Eiben]]