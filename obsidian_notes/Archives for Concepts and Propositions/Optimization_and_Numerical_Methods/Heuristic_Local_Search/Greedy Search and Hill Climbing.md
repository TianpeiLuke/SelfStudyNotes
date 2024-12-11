---
tags:
  - concept
  - algorithm/search
  - machine_learning/algorithms
  - optimization/algorithm
  - algorithm/greedy_algorithm
keywords:
  - greedy_algorithm
  - hill_climbing
  - gradient_free_optimization
  - local_search
topics:
  - optimization
  - algorithm/search
name: Greedy Search and Hill Climbing
date of note: 2024-08-25
---

## Concept Definition

>[!important]
>**Name**: Greedy Search and Hill Climbing

![[Gradient Descent Algorithm#^613ed7]]

- [[Gradient Descent Algorithm]]

>[!important] Definition
>Consider a **combinatorial optimization problem**
>$$
>\begin{align*}
> \max_{x} &\; f(x)\\
> \text{ s.t. }&\; x \in \mathcal{X}
>\end{align*} 
>$$
>where $\mathcal{X}$ is a *(finite) discrete set* and $f: \mathcal{X} \to \mathbb{R}$ is a real-value function. 
>
>The **hill climbing** or **steapest ascent** or **greedy search** algorithm finds the *optimal solution* as follow:
>- Initialize $x_{0}$
>- Initialize $f_{max} = -\infty$, $x^{*}= x_{0}$
>- For $t=0,\,1\,{,}\ldots{,}\,$ until the *termination condition* is satisfied:
>	- $$x_{t+1} = \arg\max_{x \in \mathcal{N}(x_{t})}f(x)$$ where $\mathcal{N}(x)$ is the *neighborhood* of $x$ in (*discrete topology* of) $\mathcal{X}$.
>	- If $f(x_{t+1}) > f_{max}$:
>		- $x^{*} = x_{t+1}$
>		- $f_{max} = f(x_{t+1})$
>	- else:
>		- Return $x^{*}$ as **local maximal solution** and $f_{max}$ as **local maximum**.
>	



^85f6f8

- [[Greedy Heuristic Algorithms]]
- [[Combinatorial Optimization Problem]]
- [[Unconstrained Local Minimization]]
- [[Topology of Set]]


## Explanation

>[!info]
>The *hill-climbing* algorithm is a **greedy algorithm**. 
>
>It is a discrete (gradient-free) version of *gradient descent algorithm*.

- [[Gradient Descent Algorithm]]


## Beam Search as Greedy Decoding

- [[Beam Search for Causal Decoding of Language Model]]


-----------
##  Recommended Notes and References


- [[Random Restart Hill Climbing]]
- [[Gradient Descent Algorithm]]

- [[Tabu Search]]
- [[Nelder–Mead Simplex Method]]

- [[Introduction to Algorithms by Cormen]]
- [[Algorithm Design Manual by Skiena]]
- [[Algorithms to Live By Book Summary]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 299
- [[Introduction to Evolutionary Computing by Eiben]] pp 47
- [[Artificial Intelligence Modern Approach by Russell]]