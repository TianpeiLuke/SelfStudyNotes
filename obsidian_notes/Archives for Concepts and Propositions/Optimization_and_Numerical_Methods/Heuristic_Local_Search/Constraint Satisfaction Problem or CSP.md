---
tags:
  - concept
  - computer_science/np_problems
  - algorithm/set
  - optimization/theory
  - algorithm/dynamic_programming
  - probabilistic_graphical_models/theory
  - computer_science/computational_complexity_theory
keywords:
  - constraint_satisfaction_problem
  - csp_problem
topics:
  - computational_complexity_theory
name: Constraint Satisfaction Problem CSP
date of note: 2024-08-26
---
 
## Concept Definition

>[!important]
>**Name**: Constraint Satisfaction Problem or CSP

>[!important] Definition
>A **Constraint Satisfaction Problem (CSP)** is a mathematical framework where the goal is to find an assignment to a set of variables that satisfies a set of constraints.
>
>- *Require*: a set of **variables** $$\mathcal{X} = \{X_1, X_2, \ldots, X_n\}$$
>- *Require*: a corresponding set of **domains** $$\mathcal{D} = \{D_1, D_2, \ldots, D_n\}$$ where each $D_i$ is the set of possible values for variable $X_i$.
>- *Require*: a set of **constraints** $\mathcal{C}$ where each constraint $C_k$ involves some subset of variables and specifies allowable combinations of values for those variables.
>
>
>The objective is to find an **assignment**:
>  $$
>  \{X_1 = v_1, X_2 = v_2, \ldots, X_n = v_n\}
>  $$
>  where $v_i \in D_i$, such that **all constraints are satisfied**:
>  $$
>  C_k(v_{i_1}, v_{i_2}, \ldots) = \text{True} \quad \text{for all } C_k \in \mathcal{C}.
>  $$


- [[Backtracking]]
- [[NP Complete Complexity Class and Problems]]

## Explanation



- [[Boolean Satisfiability Problem or SAT]]


## Examples

- [[N-Queens]]


-----------
##  Recommended Notes and References


- [[Integer Linear Optimization Problem and Integer Programming]]
- [[Combinatorial Optimization Problem]]
- [[Constrained Optimization Problem]]
- [[Algorithm General Definition]]
- [[Computational Complexity Theory]]


- [[Bayesian Network on Directed Acyclic Graph]]
- [[Sum-Product Variable Elimination]]
- [[Sum-Product Belief Propagation Algorithm for Clique Tree]]


- [[Introduction to Algorithms by Cormen]] pp 1066, 1073–1079, 1120–1121, 1124 ex.
- [[Algorithm Design Manual by Skiena]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Probabilistic Graphical Models by Koller]] pp 569
- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Foundations of Machine Learning by Mohri]]
- [[Artificial Intelligence Modern Approach by Russell]] pp 202 - 227


- [[Algorithms to Live By Chapter 08 Relaxation]]
- Wikipedia [Constraint_satisfaction_problem](https://en.wikipedia.org/wiki/Constraint_satisfaction_problem)