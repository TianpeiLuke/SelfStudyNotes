---
tags:
  - concept
  - optimization/theory
  - evolutionary_computation
keywords:
  - evolutionary_algorithm
topics:
  - evolutionary_algorithm
name: Evolutionary Algorithms
date of note: 2024-08-24
---

## Concept Definition

>[!important]
>**Name**: Evolutionary Algorithms

>[!important] Definition
>The **evolutionary computation algorithm** solves the constrained optimization problem $$\min_{x\in \mathcal{X}} f(x)$$
>where
>-  the objective function $f: \mathcal{X} \to \mathbb{R}$ is called the **fitness function**.
>- A feasible solution  $x\in \mathcal{X}$ is called a **candidate solution**, or **phenotype**, or an **individual**
>- The space of all possible candidate solutions $\mathcal{X}$ is called the **phenotype space**.
>- The terms **genotype**, **chromosome**, and **individual** are used to denote points in the space where the evolutionary search actually take place. 
>- The space of genotype is called the **genotype space**

^ac42fa

- [[Constrained Optimization Problem]]
- [[Introduction to Evolutionary Computing by Eiben]] pp 28 - 32

>[!info]
>The evolutionary algorithm is used for **combinatorial optimization problem** when the feasible region is **discrete** (i.e. with *integer constraint*)

- [[Combinatorial Optimization Problem]]
- [[Integer Linear Optimization Problem and Integer Programming]]


>[!important] Definition
>The **evolutionary algorithm** maintains a collection of $K$ *candidate solutions* called the **population** of $K$ good candidate. A *population* is a *multiset of genotypes*.
>- Denote the population at time $t$ as $\mathcal{S}_{t}$.
>- The **diversity** of a *population* is a measure of the number of *different solutions*.
>- At each time $t$, an *individual* in *population* at $t+1$ is called a **child** or an **offspring**.
>- An *individual* in the *population* $\mathcal{S}_{t}$ that is selected at $t$ is called a **parent**.

^12072d

- [[Parent Selection for Evolutionary Computation]]

>[!important]
>The role of **variation operators** is to create new individuals from old ones. In the corresponding *phenotype space* this amounts to generating new *candidate solutions*.


>[!important] Definition
>In **evolutionary algorithms**, an offspring can be created in two ways:
>- **mutation**: where a *parent* $x\in \mathcal{S}_{t}$ is selected, and a **random mutation** is applied to it.
>	- The mutation is a **unary variation operator**. 
>	- This is like *asexual reproduction*.
>- **recombination** or **crossover**: where two parents $x,y \in \mathcal{S}_{t}$ are selected, and an offspring is created.
>	- The *recombination* is a **stochastic variation operator**
>	- It chooses *what parts* of each parent are combined, and *how* this is done, depend on *random drawings*.
>	- This is like *sexual reproduction*.

^8340f3



>[!important] Definition
>The procedure by which parents are chosen is called the **selection function**.
>
>- The role of **parent selection** or **mate selection** is to distinguish among individuals based on their quality, and, in particular, to allow the *better individuals* to become *parents* of the next generation.
>- Together with the **survivor selection** mechanism, *parent selection* is responsible for pushing *quality improvements*.

### Population Management

- [[Population Management Models for Evolutionary Computation]]



## Explanation

>[!important] Definition
>Evolutionary algorithm is a subfield of **evolutionary computation**, a generic **population-based** **meta-heuristic optimization**. 
>- They are a family of *population-based trial and error* problem solvers with a **meta-heuristic** or **stochastic optimization** character. 
>
>The other **meta-heuristic** optimization algorithms include **swam intelligence algorithms**

>[!quote]
>The principle behind **recombination** is simple – by *mating* two individuals with different but desirable features, we can produce an *offspring* that *combines both of those features*.
>
>-- Eiben, A. E., & Smith, J. E. (2015). _Introduction to evolutionary computing_. Springer-Verlag Berlin Heidelberg. pp 32

>[!info]
>*Evolutionary computation* can be seen as a *stochastic local search*, where at each iteration the algorithm produce a batch of candidate solutions (*offspring population*) that improve objective function (*fitness*) locally. 

- [[Stochastic Hill Climbing]]




-----------
##  Recommended Notes and References




- [[Population-based Incremental Learning]]
- [[Genetic Algorithms]]
- [[Random Restart Hill Climbing]]
- [[Stochastic Hill Climbing]]
- [[Greedy Search and Hill Climbing]]
- [[Derivative-Free Optimization]]

- [[Probabilistic Graphical Models]]


- [[Introduction to Evolutionary Computing by Eiben]] pp 14, 26 - 32, 120
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 298 - 307