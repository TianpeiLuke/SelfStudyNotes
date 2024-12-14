---
tags:
  - concept
  - computer_science/np_problems
  - algorithm/set
  - optimization/theory
  - computer_science/computational_complexity_theory
keywords:
  - satisfiability_problem
  - sat_problem_np
topics:
  - computational_complexity_theory
name: Boolean Satisfiability Problem or SAT
date of note: 2024-08-26
---

## Concept Definition

>[!important]
>**Name**: Boolean Satisfiability Problem or SAT

>[!important] Definition
>The **(Boolean) Satisfiability problem** or **SAT** problem is stated as follows:
>
>Given a set of *boolean variables* $$V = \{ v_{1}\,{,}\ldots{,}\,v_{n} \}$$ where $v_{i}\in \{ 0,1 \}$, and  a set of *logic clauses* $C$ over $V$, 
>- Does there exists a *satisfying truth assignment* for $C$?
>- In other word, is there an assignment to $v_{i}\in \{ 0,1 \}, i=1\,{,}\ldots{,}\,n$ so that every clause in $C$ contains *at least one true literal*?



### 3-SAT Problem


## Explanation

>[!quote]
>For a combination of social and technical reasons, it is well accepted that **satisfiability** is a **hard** problem; one for which *no worst-case polynomial-time algorithm exists*. 
>- Literally every top-notch algorithm expert in the world (and countless lesser lights) has directly or indirectly tried to come up with a fast algorithm to test whether any given set of clauses is satisfiable. All have failed. 
>- Furthermore, many *strange* and *impossible-to-believe* things in the field of computational complexity have been shown to be true *if* there exists a fast satisfiability algorithm. 
>- **Proving** something is **as hard as satisfiability** means that it is **hard**.
>  
>-- [[Algorithm Design Manual by Skiena]] pp 367 - 369  

- [[NP Hard Complexity Class and Problems]]
- [[NP Complete Complexity Class and Problems]]


## Integer Programming

- [[Integer Linear Optimization Problem and Integer Programming]]
- [[Combinatorial Optimization Problem]]



-----------
##  Recommended Notes and References



- [[Constraint Satisfaction Problem or CSP]]
- [[Algorithm General Definition]]
- [[Computational Complexity Theory]]


- [[Bayesian Network on Directed Acyclic Graph]]
- [[Sum-Product Variable Elimination]]
- [[Sum-Product Belief Propagation Algorithm for Clique Tree]]


- [[Introduction to Algorithms by Cormen]] pp 1066, 1073–1079, 1120–1121, 1124 ex.
- [[Algorithm Design Manual by Skiena]] pp 367, 421, 480- 481,
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Probabilistic Graphical Models by Koller]]
- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Foundations of Machine Learning by Mohri]]
- [[Artificial Intelligence Modern Approach by Russell]] pp 250, 264, 277, 334, 362


- [[Algorithms to Live By Chapter 08 Relaxation]]
- Wikipedia [Boolean_satisfiability_problem](https://en.wikipedia.org/wiki/Boolean_satisfiability_problem)