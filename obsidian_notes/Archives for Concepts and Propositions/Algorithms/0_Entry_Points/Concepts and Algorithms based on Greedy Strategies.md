---
tags:
  - entry_point
  - concept
  - algorithm/greedy_algorithm
  - optimization/algorithm
  - machine_learning/algorithms
  - natural_language_processing/large_language_models
keywords: 
topics: 
name: 
date of note: 2024-12-10
---

## List of Concepts

- [[Greedy Heuristic Algorithms]]

### Greedy Search Algorithms

- [[Greedy Search and Hill Climbing]]
- [[Random Restart Hill Climbing]]
- [[Tabu Search]]
- [[Nelder-Mead Simplex Method]]

### Greedy Decoding 

- [[Greedy Decoding for Causal Language Model Generation]]
- [[Beam Search for Causal Decoding of Language Model]]

### Minimum Spanning Tree

- [[Prim Algorithm to Prune Minimum Spanning Tree]]
- [[Kruskal Algorithm to Prune Minimum Spanning Tree]]

### Evolutionary Computation Algorithms

- [[Comparison of Population-based Methods]]
- [[Parent Selection for Evolutionary Computation]]
- [[Survivor Selection for Evolutionary Computation]]
- [[Population Management Models for Evolutionary Computation]]
- [[Particle Swarm Optimization]]

### Iterative and Proximal Algorithms in Optimization

#### Iterative Algorithms

- [[Iterative Descent]] and [[Approximation Method for Optimization]]
- [[Gradient Descent Algorithm]]
- [[Newton Method]]
- [[Subgradient Methods]]

#### Proximal Algorithms

- [[Proximal Algorithm]]
- [[Dual Proximal Algorithm]]
- [[Augmented Lagrangian Function]]
- [[Augmented Lagrangian Algorithm]]
- [[Alternating Direction Method of Multipliers Algorithm]]

- [[Proximal Gradient Algorithm]]
- [[Dual Proximal Gradient Algorithm]]

- [[Proximal Cutting-Plane Algorithm]]
- [[Bundle Methods]]

### Classification

- [[k Nearest Neighbor Classification]]
- [[k Nearest Neighbor Density Estimation]]
- [[Approximate Nearest Neighbor Search]]


### Submodular Optimization

- [[Theory and Algorithms for Submodular Optimization]]
- [[Submodular Function as Convex Equivalence of Set Function]]
- [[Base Polyhedron]]
- [[Submodualar Polyhedron]]
- [[Positive Submodular Polyhedron]]
- [[Symmetric Submodular Polyhedron]]
- [[Greedy Algorithm for Submodular and Base Polyhedron]]
- [[Greedy Algorithm for Positive Submodular Polyhedron]]
- [[Greedy Algorithm for Symmetric Submodular Polyhedron]]


### EM Algorithm

- [[Expectation-Maximization Algorithm]]
- [[Majorization-Minimization Algorithm]]

### Clustering

- [[k-Means Clustering]]

### Online Learning and Online Convex Optimization

- [[Online Convex Optimization]]
- [[Follow-The-Leader Algorithm]]
- [[Follow-The-Regularized-Leader Algorithm]]
- [[Mirror Descent Algorithm]]
- [[Online Mirror Descent Algorithm]]

### Bandit Problem

- [[Explore-Then-Commit Bandit Algorithm]]
- [[epsilon-Greedy Algorithm]]

### Reinforcement Learning

- [[Policy Iteration Algorithm]]
- [[Value Iteration Algorithm]]
- [[SARSA Algorithm and On-Policy Temporal Difference Control]]
- [[Q Learning Algorithm and Off-Policy Temporal Difference Control]]
- [[Expected SARSA Algorithm]]
- [[Policy Gradient Algorithm]]
- [[Actor-Critic Algorithm]]

### Submodular Methods for Combinational Optimization


## Compared to Dynamic Programming

>[!quote]
>Here is where **greedy algorithms** *differ* from **dynamic programming**. 
>- In **dynamic programming**, you make a choice at each step, but the *choice* usually depends on the *solutions to subproblems*. 
>	- Consequently, you typically solve dynamic programming problems in a **bottom-up manner**, progressing from *smaller* subproblems to *larger* subproblems. 
>	- (Alternatively, you can solve them top down, but memoizing. Of course, even though the code works top down, you still must solve the subproblems before making a choice.) 
>- In a **greedy algorithm**, you make whatever choice seems *best at the moment* and then solve the subproblem that remains. 
>	- The *choice* made by a greedy algorithm may depend on choices so far, but it *cannot* depend on any *future choices* or on the *solutions to subproblems*. 
>- Thus, 
>	- unlike **dynamic programming**, which *solves the subproblems before* making the *first choice*,  a **greedy algorithm** makes its *first choice before* solving any *subproblems*.  $$\begin{align*}\text{dynamic programming:}& \quad \text{ solving subproblem }\to \text{ choice} \\[5pt] \text{greedy algorithm:}& \quad \text{ choice }\to \text{ solving subproblem}\end{align*}$$
>	- A dynamic-programming algorithm proceeds **bottom up**, whereas a greedy strategy usually progresses **top down**, making one greedy choice after another, reducing each given problem instance to a smaller one.
>	  
>-- [[Introduction to Algorithms by Cormen]] pp 427	  



## Coding Exercise








-----------
##  Recommended Notes and References



- [[Introduction to Algorithms by Cormen]]
- [[Algorithm Design Manual by Skiena]]
- [[Algorithms to Live By Book Summary]]

- [[Game Theory An Introduction by Tadelis]] 


- [[Markov Decision Processes by Puterman]] 
- [[Reinforcement Learning An Introduction by Sutton]] 


- [[Convex Optimization Algorithms by Bertsekas]]
- [[Nonlinear Programming by Bertsekas]]
- [[Numerical Optimization by Nocedal]]
- [[Prediction Learning and Games by Cesa-Bianchi]]
- [[Bandit Algorithms by Lattimore]]


- [[Elements of Statistical Learning by Hastie]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] 
- [[Artificial Intelligence Modern Approach by Russell]]