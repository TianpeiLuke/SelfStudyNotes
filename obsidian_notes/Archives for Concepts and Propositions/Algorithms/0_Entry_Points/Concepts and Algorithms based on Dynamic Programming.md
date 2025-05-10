---
tags:
  - entry_point
  - concept
  - algorithm/dynamic_programming
  - optimization/dynamic_programming
  - deep_learning/algorithms
  - natural_language_processing/tokenization
  - probabilistic_graphical_models/algorithm
keywords: 
topics: 
name: 
date of note: 2024-09-16
---

## List of Concepts

- [[Dynamic Programming Algorithms]]

### Optimization

- [[Integer Linear Optimization Problem and Integer Programming]]
- [[Knapsack or Subset Sum Problem]]
- [[Longest Increasing Subsequence Algorithm]]


### Flow and Shortest Path

- [[Graph]]
- [[Network and Flow and Capacity and Cut]]

- [[A-star Best-First Search]]
- [[Bellman-Ford Algorithm for Single-Source Shortest Path Problem]]
- [[Dijkstra Algorithm for Single-Source Shortest Path Problem on DAG]]
- [[Ford-Fulkerson Method for Maximum Flow Problem]]

### Martingale and Optimal Stopping

- [[Martingale]]
- [[Stopping Time of Filtration]]
- [[Dynamic Programming for Optimal Stopping]]


### Markov Decision Process and Reinforcement Learning

- [[Markov Decision Process]]
- [[Dynamic Programming for MDP]]
- [[Value Function and Bellman Equation for MDP]]
- [[Bellman Optimality Equation for MDP]]
- [[Bellman Operator for Policy on Value Functions]]


### Probabilistic Graphical Model

- [[Bayesian Network on Directed Acyclic Graph]]
- [[Markov Network on Undirected Graph]]

- [[Sum-Product Variable Elimination]]
- [[Sum-Product Belief Propagation Algorithm for Clique Tree]]
- [[Sum-Product Belief-Update Message Passing Algorithm for Clique Tree]]
- [[Gaussian Belief Propagation]]
- [[Sum-Product Expectation Propagation Algorithm]]
- [[Sum-Product Belief-Update Expectation Propagation Algorithm]]


- [[Max-Product Variable Elimination]]
- [[Max-Product Belief Propagation for Clique Tree]]

- [[Hidden Markov Model]]
- [[Hidden Markov Model Inference via Forward-Backward Algorithm]]
- [[Hidden Markov Model MAP Inference via Viterbi Algorithm]]


### Automatic Differentiation

- [[Automatic Differentiation]]
- [[Back-Propagation Algorithm]]
- [[Back-Propagation Through Time]]
- [[Topological Sorting]]


### Numerical Linear Algebra

- [[Matrix-Chain Multiplication]]


### Natural Language Processing

- [[Minimum Edit Distance or Levenshtein Distance via Dynamic Programming]]
- [[CKY Parsing as Dynamic Programming Algorithm]]
- [[Longest Common Subsequence between Strings]]
- [[Substring Matching via Dynamic Programming]]
- [[Unigram Tokenization]]


### Multi-Stage Games

- [[Backward Induction and Dynamic Programming]]
- [[Sequential Game Play and Sequential Rationality]]
- [[Extensive-Form Game]]
- [[Finitely Repeated Games]]
- [[Infinitely Repeated Games]]


### Calculus of Variations

- [[Lagrangian Function in Mechanics and Variational Calculus]]
- [[Hamiltonian Function in Mechanic and Variational Calculus]]
- [[Hamilton-Jacobi-Bellman Equation]]

## Compare to Greedy Algorithm

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

- [[Dynamic Programming by Bellman]]
- [[Dynamic Programming and Optimal Control by Bertsekas]]

- [[Markov Decision Processes by Puterman]] 
- [[Reinforcement Learning An Introduction by Sutton]] 

- [[Deep Learning by Goodfellow]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] 
- [[Artificial Intelligence Modern Approach by Russell]]
- [[Probabilistic Graphical Models by Koller]] 

- Lecture
	- MIT Open Course [Dynamic Programming and Stochastic Control](https://ocw.mit.edu/courses/6-231-dynamic-programming-and-stochastic-control-fall-2015/)