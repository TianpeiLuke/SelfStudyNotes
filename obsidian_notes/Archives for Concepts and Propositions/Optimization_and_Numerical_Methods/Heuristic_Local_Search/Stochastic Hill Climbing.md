---
tags:
  - concept
  - algorithm/search
  - machine_learning/algorithms
  - optimization/algorithm
  - algorithm/greedy_algorithm
  - algorithm/stochastic_search
keywords:
  - stochastic_local_search
  - hill_climbing
  - stochastic_hill_climbing
topics:
  - algorithm/search
  - optimization
name: Stochastic Hill Climbing
date of note: 2024-08-25
---

## Concept Definition

>[!important]
>**Name**: Stochastic Hill Climbing

![[Greedy Search and Hill Climbing#^85f6f8]]

>[!important] Definition
>Hill climbing is *greedy*, since it picks the best point in its local neighborhood, by solving $$\arg\max_{x\in \mathcal{N}(x_{t})} f(x)$$  exactly. One way to reduce the chance of getting stuck in *local maxima* is to *approximately maximize* this objective at each step. 
>
>For example, we can define a *probability distribution* over the **uphill neighbors**,  *proportional* to how much they improve, and then *sample* one at random. This is called **stochastic hill climbing**.


>[!important] Definition
>The **stochastic hill climbing** is described as 
>- Initialize $x_{0}$
>- Initialize $f_{max} = -\infty$, $x^{*}= x_{0}$
>- For $t=0,\,1\,{,}\ldots{,}\,$ until the *termination condition* is satisfied:
>	- Generate a random sample from some **search distribution** $p(\cdot|\theta_{t})$ $$X_{t+1} \sim p_{f,t}(x)$$ where the density $p_{f,t}(x)$ is proportional to how much $f(x)$ can improve. 
>		- For instance, $$p_{t}(x) \propto \exp \left( \Delta f_{t} \right)$$
>	- If $f(X_{t+1}) > f_{max}$:
>		- $x^{*} = X_{t+1}$
>		- $f_{max} = f(X_{t+1})$
>	- else:
>		- Return $x^{*}$ as **local maximal solution** and $f_{max}$ as **local maximum**.

- [[Greedy Search and Hill Climbing]]
- [[EDA or Estimation of Distribution Algorithm]]
- [[Evolutionary Strategies]]



## Explanation

>[!info]
>The *neighborhood* associated with the stochastic hill climbing is defined based on the *concentration of probability measure* around its mean

- [[Concentration of Measure in Metric Space]]
- [[Sub-Gaussian Random Variable]]





-----------
##  Recommended Notes and References


- [[Simulated Annealing]]
- [[Stochastic Gradient Descent Algorithm]]
- [[Gradient Descent Algorithm]]
- [[Greedy Search and Hill Climbing]]

- [[Evolutionary Computation Algorithms]]


- [[Introduction to Algorithms by Cormen]]
- [[Algorithm Design Manual by Skiena]]
- [[Algorithms to Live By Book Summary]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 299
- [[Introduction to Evolutionary Computing by Eiben]] pp 47
- [[Artificial Intelligence Modern Approach by Russell]]
- Wikipedia [Stochastic_hill_climbing](https://en.wikipedia.org/wiki/Stochastic_hill_climbing)