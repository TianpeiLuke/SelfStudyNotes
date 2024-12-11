---
tags:
  - concept
  - algorithm/greedy_algorithm
  - optimization/algorithm
  - algorithm/search
keywords:
  - tabu_search
  - hill_climbing
  - local_search
topics:
  - algorithm/search
  - optimization/algorithm
name: Tabu Search
date of note: 2024-08-27
---

## Concept Definition

>[!important]
>**Name**: Tabu Search

![[Greedy Search and Hill Climbing#^85f6f8]]

>[!info]
>**Hill climbing** will stop as soon as it reaches a *local maximum* or a *plateau*.

>[!important] Definition
>The **tabu search** maintains a “*tabu*” list of *visited points*, to which the algorithm is forbidden to return. 
>- It allows moves that *decrease* (or at least do not increase) the scoring function, provided the move is to a *new state* that has not been seen before.
>- This forces the algorithm to **explore new states**, and increases the chances of escaping from local maxima.
>- We continue to do this for up to $c_{max}$ steps (known as the “**tabu tenure**”).
>

- [[Greedy Search and Hill Climbing]]
- [[Exploration and Exploitation Tradeoff]]

>[!important] Definition
>The **tabu search** algorithm finds the *optimal solution* as follow:
>- *Require*: fitness function $f$
>- *Require*: $c_{max}$, the **tabu tenure**
>- *Require*: the *length* of tabu $\tau$
>- Initialize $x_{0}$
>- Initialize $f_{max} = -\infty$, $x^{*}= x_{0}$
>- Initialize the *counter of no progress* $c = 0$
>- For $t=0,\,1\,{,}\ldots{,}\,$ until the *termination condition* is satisfied:
>	- $$x_{t+1} = \arg\max_{x \in \mathcal{N}(x_{t}) \setminus\,\left\{ x_{t-\tau} \,{,}\ldots{,}\, x_{t-1}\right\} }f(x)$$ where $\mathcal{N}(x_{t})$ is the *neighborhood* of $x_{t}$.
>	- If $f(x_{t+1}) > f_{max}$:
>		- $x^{*} = x_{t+1}$
>		- $f_{max} = f(x_{t+1})$
>		- Restart the counter $c = 0$
>	- else:
>		- Incremental update of *counter of no progress* $$c \leftarrow c+1$$
>	- If $c \ge c_{max}$, i.e. the *maximum attempt* is reached without progress
>		- Return $x^{*}$ as **local maximal solution** and $f_{max}$ as **local maximum**.


## Explanation

>[!info]
>At *local maxima* $x_{t} = x^{*}$, the *tabu search* will be forced to pick a neighboring point at the *same height* or *lower*. It continues in this way, “**circling**” the peak, possibly being *forced downhill* to a lower level-set. (an **inverse basin flooding** operation.)
>
>The algorithm will leave this neighborhood if it finds a **ridge** that leads to a **new peak**, or until it exceeds a *maximum* number of non-improving moves.




-----------
##  Recommended Notes and References


- [[Greedy Search and Hill Climbing]]
- [[Random Restart Hill Climbing]]


- [[Introduction to Algorithms by Cormen]]
- [[Algorithm Design Manual by Skiena]]
- [[Algorithms to Live By Book Summary]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 300
- [[Introduction to Evolutionary Computing by Eiben]] pp 180
- [[Artificial Intelligence Modern Approach by Russell]] pp 154, 222