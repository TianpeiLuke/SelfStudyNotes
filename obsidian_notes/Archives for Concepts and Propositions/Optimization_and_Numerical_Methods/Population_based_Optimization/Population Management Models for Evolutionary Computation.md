---
tags:
  - concept
  - evolutionary_computation
keywords:
  - population management
topics: 
name: Population Management Models for Evolutionary Computation
date of note: 2024-08-28
---

## Concept Definition

>[!important]
>**Name**: Population Management Models for Evoluationary Compuation

![[Evolutionary Computation Algorithms#^ac42fa]]

![[Evolutionary Computation Algorithms#^12072d]]

![[Evolutionary Computation Algorithms#^8340f3]]

- [[Evolutionary Computation Algorithms]]

>[!important] Definition
>Two different models of **population management** are found in the literature: 
>- the **generational model** and
>- the **steady-state model**.

### Generational Model

>[!important] Definition
>In **generational model**: 
>- In each generation we begin with a population of size $\mu$, from which a **mating pool** of parents is selected. Every member of the pool is a **copy** of something in the *population*, but the proportions will probably differ, with (usually) more copies of the ‘better’ parents. 
>- Next, $\lambda$ **offspring** are created from the *mating pool* by the application of variation operators, and evaluated. 
>- After each generation, the whole population is **replaced** by $\mu$ individuals selected from its *offspring*, which is called the **next generation**.

- [[Genetic Algorithms]]
- [[Genetic Programming]]
- [[EDA or Estimation of Distribution Algorithm]]
- [[Cross-Entropy Method for EDA]]
- [[Differentiable Cross-Entropy Method]]
- [[Particle Swarm Optimization]]

### Steady-State Model

>[!important] Definition
>In **steady-state model**: 
>- the entire population is not changed at once, but rather *a part of it*.
>- In this case, $\lambda (<\mu)$ *old* individuals are replaced by $\lambda$ *new* ones, the offspring.
>- The proportion of the population that is *replaced* is called the **generational gap**, and is equal to $\lambda/\mu$.

- [[Evolutionary Programming]]
- [[Evolutionary Strategies]]
- [[CMA-ES or Covariance Matrix Adaptation Evolution Strategy]]

### Parent Selection

- [[Parent Selection for Evolutionary Computation]]

### Survivor Selection

- [[Survivor Selection for Evolutionary Computation]]



## Explanation





-----------
##  Recommended Notes and References



- [[Survivor Selection for Evolutionary Computation]]
- [[Parent Selection for Evolutionary Computation]]
- [[Evolutionary Computation Algorithms]]
- [[Derivative-Free Optimization]]
- [[Comparison of Population-based Methods]]


- [[Introduction to Evolutionary Computing by Eiben]] pp 14, 26 - 32, 120
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 298 - 307