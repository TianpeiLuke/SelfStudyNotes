---
tags:
  - concept
  - algorithm/search
  - algorithm/graph
  - a_star_search
  - best_first_search
keywords:
  - local_search
  - a_star_search
topics:
  - algorithm/search
  - heuristic_search
name: A-star Best-First Search
date of note: 2024-08-08
---

## Concept Definition

>[!important]
>**Name**: A-star Best-First Search

### Algorithm

>[!important] Definition
>The **A\*-search algorithm** is a best-first search algorithm that finds the lowest-cost path from a start node to a goal node using both actual cost and heuristic estimates.
>
>- *Require*: a set of **nodes** representing the search space.
>- *Require*: a **start node** $s_{\text{start}}$ and a **goal node** $s_{\text{goal}}$.
>- *Require*: a **cost function** $g(s)$ that represents the actual cost from $s_{\text{start}}$ to a node $s$.
>- *Require*: a **heuristic function** $h(s)$ estimating the cost from $s$ to $s_{\text{goal}}$.
>
>- **Initialize**:
>    - Set $g(s_{\text{start}}) = 0$.
>    - Initialize an empty *priority queue* (often called the **open set**) and insert $s_{\text{start}}$ with priority $$f(s_{\text{start}}) = g(s_{\text{start}}) + h(s_{\text{start}}).$$
>    - Initialize an empty **closed set** to track explored nodes.
>
>- While the open set is not empty:
>    - **Remove** the node $s$ with the *lowest* $f(s) = g(s) + h(s)$ from the open set.
>    - If $s = s_{\text{goal}}$, then **return** the path from $s_{\text{start}}$ to $s_{\text{goal}}$ by **tracing back** parent pointers.
>    - *Add* $s$ to the closed set.
>    - For each **neighbor** $s'$ of $s$:
>        - If $s'$ is in the closed set, **continue** to the next neighbor.
>        - Compute **tentative cost**:
>          $$
>          g_{\text{tentative}}(s') = g(s) + \text{Cost}(s, s')
>          $$
>        - If $s'$ is not in the open set or $g_{\text{tentative}}(s') < g(s')$:
>            - Set/update $$g(s') = g_{\text{tentative}}(s').$$
>            - Set the parent of $s'$ to $s$.
>            - Update the priority of $s'$ in the open set to:
>              $$
>              f(s') = g(s') + h(s').
>              $$
>
>- *Return*: failure if the open set is empty and no path is found.

- [[Beam Search for Causal Decoding of Language Model]]
- [[Best-First Search]]

## Explanation




-----------
##  Recommended Notes and References


- [[Breadth-First Search]]
- [[Depth-First Search]]
- [[Graph]]

- [[Artificial Intelligence Modern Approach by Russell]] pp 93 - 99
- [[Algorithm Design Manual by Skiena]] pp 300
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1154