---
tags:
  - concept
  - algorithm/search
  - machine_learning/algorithms
  - optimization/algorithm
  - algorithm/greedy_algorithm
  - algorithm/stochastic_search
keywords:
  - hill_climbing
  - stochastic_hill_climbing
  - random_restart_hill_climbing
topics:
  - optimization
  - algorithm/search
name: Random Restart Hill Climbing
date of note: 2024-08-25
---

## Concept Definition

>[!important]
>**Name**: Random Restart Hill Climbing

![[Greedy Search and Hill Climbing#^85f6f8]]

>[!important] Definition
>The **random restart hill climbing algorithm** describes as follow
>- Initialize $x_{0}$
>- Initialize $f_{max} = -\infty$, and $x^{*} = x_{0}$
>- For $t=0\,,1 \,{,}\ldots{,}\,$
>	- $$x_{t+1} = \arg\max_{x \in \mathcal{N}_{G}(x_{t})}f(x)$$ where $\mathcal{N}_{G}(x)$ is the *neighborhood* of $x$ in graph $G$, i.e. $$\mathcal{N}_{G}(x) := \{ y\in \mathcal{V}: xy\in \mathcal{E}  \}$$
>	- If $f(x_{t+1}) \le f_{max}$:
>		- **Random restart**: choose next state randomly $$x_{t+1} \in \text{Uniform}(\mathcal{V})$$
>	- else:
>		- $f_{max} = f(x_{t+1})$
>		- $x^{*} = x_{t+1}$

- [[Greedy Search and Hill Climbing]]



## Explanation





-----------
##  Recommended Notes and References



- [[Gradient Descent Algorithm]]
- [[Greedy Search and Hill Climbing]]


- [[Introduction to Algorithms by Cormen]]
- [[Algorithm Design Manual by Skiena]]
- [[Algorithms to Live By Book Summary]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 299
- [[Artificial Intelligence Modern Approach by Russell]]
- [[Probabilistic Graphical Models by Koller]] pp 1159