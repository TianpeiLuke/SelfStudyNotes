---
tags:
  - concept
  - optimization/algorithm
  - online_learning/algorithms
  - optimization/convex_optimization
keywords:
  - incremental_algorithm
topics:
  - optimization
  - online_convex_optimization
name: Incremental Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Incremental Algorithm

>[!important] Definition
>The **Incremental methods** solves the following optimization problem
>$$
> \min_{x\in \mathcal{X}} \sum_{t=1}^{T}f_{t}(x)
>$$
>where 
>- $\mathcal{X} \subseteq \mathbb{R}^{d}$ is a *closed convex set*,
>- $f_{t}: \mathbb{R}^{d} \to \mathbb{R}$ is either *differentiable* or *convex*.
>- $T$ is very large so that a full sub-gradient / gradient step is expensive

^b32a9f

- [[Online Convex Optimization]]

>[!important] 
>The main update for the **Incremental methods** can be described as the following
>- For $k=1,\,2 \,{,}\ldots{,}\,$
>	- *Initialize* $\psi_{0,k} = x_{k}$
>	- For $t=1 \,{,}\ldots{,}\,T$
>		- $$\psi_{t,k} = P_{\mathcal{X}}\left( \psi_{t-1, k} - \alpha_{k}\,g_{t,k} \right)$$ where 
>			- $g_{t,k}\in \partial f_{t}(\psi_{t-1, k})$ is the **sub-gradient** of $f_{t}$ at $\psi_{t-1,k}$ and 
>			- $P_{\mathcal{X}}$ is the **projection operator**
>	- Update $$x_{k+1} = \psi_{T, k}$$

- [[Subgradient Methods]]
- [[Subdifferential of Convex Function]]
- [[Gradient Projection Method]]


## Explanation

>[!info]
>A key characteristic of the incremental algorithm is that the *objective function* is **additive** with a large number of *component functions* $$f(x):=\sum_{t=1}^{T}f_{t}(x).$$
>
>The **idea** of incremental algorithm is to update $x$ *using one component function* $f_{t}$ *at a time*.


## Examples

### Maximum Likelihood Estimation

>[!example]
>Assume $X_{1} \,{,}\ldots{,}\,X_{n}$ are i.i.d. with distribution $p(x; \theta)$. The **maximum likelihood estimation** of parameter $\theta \in\Theta$ can be found by solving the following optimization problem
>$$
> \min_{\theta \in \Theta} \;-\sum_{i=1}^{n}\log p(x_{i}; \theta) := \sum_{i=1}^{n}f_{i}(\theta)
>$$
>where $f_{i}(\theta) := -\log p(x_{i}; \theta)$

- [[Maximum Likelihood Estimation]]


### Stochastic Optimization and Sampling Approach

>[!example]
>Another example is the **stochastic optimization**, when the objective function can be seen as the expectation 
>$$
>\min_{\theta \in \Theta}  \mathbb{E}_{ P }\left[ f(X; \theta) \right]
>$$ 
>Solving the above optimization problem requires us to estimate the expectation, which can be approximated using **sampling-methods** such as **Markov Chain Monte Carlo**.
>
>- The **sampling-based** gradient decent algorithm can be viewed as an incremental algorithm, since for each update, the algorithm need to generate a sequence of samples and to update based on generated samples.

- [[Simulated Annealing]]
- [[Markov Chain Monte Carlo Methods]]

### Incremental Gradient Methods

- [[Incremental Gradient Algorithm]]

- [[Alternating Direction Method of Multipliers Algorithm]]





-----------
##  Recommended Notes and References

- [[Gradient Descent Algorithm]]
- [[Incremental Gradient Algorithm]]
- [[Incremental Aggregated Gradient Algorithm]]

- [[Online Convex Optimization]]
- [[Regret for Online Learning]]


- [[Convex Set]]
- [[Convex Optimization Problem]]

- [[Convex Optimization Algorithms by Bertsekas]] pp 83