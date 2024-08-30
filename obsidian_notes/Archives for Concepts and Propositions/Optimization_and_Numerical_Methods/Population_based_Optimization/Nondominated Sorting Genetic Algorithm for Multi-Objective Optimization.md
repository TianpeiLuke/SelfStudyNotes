---
tags:
  - concept
  - genetic_algorithm
  - optimization/multi-objective
keywords:
  - nsga_algorithm
  - multi_objective_optimization
  - genetic_algorithm
topics:
  - optimization/algorithm
  - multi-objective_optimization
name: Nondominated Sorting Genetic Algorithm for Multi-Objective Optimization
date of note: 2024-08-28
---

## Concept Definition

>[!important]
>**Name**: Nondominated Sorting Genetic Algorithm for Multi-Objective Optimization

![[Multi-Objective Optimization Problem#^c437bf]]

![[Multi-Objective Optimization Problem#^9b6787]]

>[!important] Defintion
>The **nondominated sorting genetic algorithm (NSGA)**
>- assigns *fitness* based on dividing the population into a number of *fronts of equal domination*.
>	- The algorithm iteratively seeks all the *nondominated points* in the population that have *not been labelled* as belonging to a previous front.
>	- It then *labels* the new set as belonging to the *current front*, and 
>	- *increments the front count*, 
>	- repeating until all solutions have been labelled.
>- Each point in a given front gets as its **raw fitness** the **count** of all solutions in **inferior fronts**. $$f(x) = \sum_{x_{j} \in \mathcal{S}} \mathbb{1}\left\{ x_{j}: \,L(x_{j}) <  L(x) \right\}$$ where $L(x): \mathcal{X} \to \mathbb{N}$ is the *Pareto front assignment*  and $$L(x_{i}) < L(x_{j}) \;\iff\; x_{i} \preceq x_{j}$$
>- *fitness sharing* is implemented to promote diversity, but this time it is calculated considering only members from that *individual’s front*

- [[Genetic Algorithms]]

>[!important] Defintion
>The **nondominated sorting genetic II algorithm (NSGA-II)** improves over *NSGA* in the following ways:
>- A **crowding distance metric** for each solution $x$ is defined as the **Manhatten distance (Hamming distance)** between $x$ and its *nearest neighbor* $x_{\text{NN}}$, i.e. $$d(x, x_{\text{NN}}) := \sum_{i=1}^{d}\lvert x^{i} - x_{\text{NN}}^{i} \rvert $$
> 	- For each point, the crowding distance metric is the *average side length* of the cuboid defined by its *nearest neighbours* in the same front. 
>	- The larger this value, the fewer solutions reside in the vicinity of the point. 
>- A $(\mu + \lambda)$ **survivor selection strategy** is used (with $\mu = \lambda$). 
>	- The two populations are merged and *fronts assigned*. 
>	- The new population is obtained by accepting individuals from *progressively inferior fronts* until it is full. 
>	- If not all of the individuals in the last front considered can be accepted, they are chosen on the basis of their *crowding distance*.
>- **Parent selection** uses a *modified tournament operator* that considers 
>	- first *dominance rank* $L(x)$
>	- then *crowding distance* $d(x, x_{\text{NN}})$.

- [[Weighted Hamming Distance]]
- [[Survivor Selection for Evolutionary Computation]]
- [[Parent Selection for Evolutionary Computation]]
- [[Diversity Maintenance for Evolutionary Computation]]

>[!quote]
>this (NSGA-II) achieves **elitism** (via the plus strategy) and an **explicit diversity maintenance scheme**, as well as *reduced dependence* on parameters.
>
>-- [[Introduction to Evolutionary Computing by Eiben]] pp 199

![[nsga2_survival_white.png]]


## Explanation







-----------
##  Recommended Notes and References


- [[Genetic Algorithms]]
- [[Population Management Models for Evolutionary Computation]]
- [[Parent Selection for Evolutionary Computation]]



- [[Multi-Objective Optimization Problem]]
- [[Pareto Optimality and Pareto Dominate for Game Strategy]]
- [[Constrained Optimization Problem]]


- [[Introduction to Evolutionary Computing by Eiben]] pp 198 - 199
- Blog [NSGA-II: Non-dominated Sorting Genetic Algorithm](https://pymoo.org/algorithms/moo/nsga2.html#NSGA-II:-Non-dominated-Sorting-Genetic-Algorithm "Permalink to this headline")
- Github [pymoo](https://github.com/anyoptimization/pymoo)