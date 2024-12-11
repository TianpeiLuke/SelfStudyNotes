---
tags:
  - concept
  - algorithm/greedy_algorithm
  - algorithm/search
  - algorithm/recursion
  - algorithm/design_paradigm
keywords:
  - greedy_algorithm
topics:
  - algorithm/greedy_algorithm
name: Greedy Heuristic Algorithms
date of note: 2024-11-24
---

## Concept Definition

>[!important]
>**Name**: Greedy Heuristic Algorithms

>[!important] Definition
>A **greedy algorithm** solves an *optimization problem* by making a *sequence of choices*. 
>- At *each* decision point, the algorithm makes the choice that seems *best at the moment*.
>- Note that this is a *heuristic strategy*, which does not always produces the optimal solution.

- [[Constrained Optimization Problem]]
- [[Unconstrained Local Minimization]]

>[!important] Definition
>The process that develops a **greedy algorithm** consists of the following step
>- Determine the **optimal substructure** of the problem.
>- Develop a *recursive solution*.
>	- Formulate the *recurrence*.
>- Show that if we make a **greedy choice**, then **only one subproblem** remains.
>- Prove that it is always *safe* to make a *greedy choice*
>	- Show that there always exists an *optimal solution* that makes the greedy choice
>- Develop a *recursive* algorithm that implements the greedy strategy.
>- Convert the recursive algorithm to an *iterative* algorithm.

- [[Recursion Algorithm]]
- [[Recurrence and Algorithmic Recurrence]]

### Greedy Choice Property

>[!important] Definition
>One of the *key* ingredient of *greedy algorithm* is the **greedy choice property**
>- A *global solution* can be collected by making *locally optimal choices*
>- We need to prove that 
>	- a *greedy choice* at each step yields a **globally optimal solution**. 
>- Typically, 
>	- the proof examines a *globally* optimal solution to some *subproblem*. 
>	- It then shows how to *modify* the solution to *substitute* the greedy choice for some other choice, resulting in one *similar*, but *smaller*, *subproblem*.

- [[Unconstrained Global Minimization]]
- [[Unconstrained Local Minimization]]

### Optimal Substructure

>[!important] Definition
>A problem exhibits **optimal substructure** if an *optimal* solution to the *problem* contains within it *optimal* solutions to *subproblems*.
>$$
> S \subset A \implies  \arg\min_{x\in S} F(x) \supset \arg\min_{x\in A} F(x)
>$$
>- The existence of *optimal substructure* is the *key* ingredient of both *dynamic programming* and *greedy algorithm.*

>[!important] Definition
>The *structure* of optimal solution obtained by *greedy algorithm* is 
>$$
>\begin{align*}
> &S^{(0)} = A\\[5pt]
> &x^{(t)} = \arg\min_{x\in S^{(t)}} F(x) \\[5pt]
> &S^{(t+1)} = G(S^{(t)} ; x^{(t)}) \subseteq S^{(t)} \\[7pt]
> \implies &\ldots \subseteq S^{(t+1)} \subseteq S^{(t)} \,{\subseteq}\ldots{\subseteq}\, S^{(0)} := A\\[7pt]
> \implies & x^{(t)} \to x^{*} = \arg\min_{x\in A} F(x)
>\end{align*}
>$$



## Explanation

>[!info]
>In greedy algorithm, we cast the optimization problem as one in which 
>- we **make a choice** 
>- and are left with **only one problem to solve**.

>[!info]
>To demonstrate the **optimal substructure** after made the greedy choice, we need to show that what *remains* is a subproblem with the *property* that 
>- if you *combine* an *optimal solution* to the *subproblem* with the *greedy choice* you have made, you arrive at an optimal solution to the *original problem*.

### Greedy vs. Dynamic Programming

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

>[!quote]
>Because both the **greedy** and **dynamic-programming strategies** exploit *optimal substructure*, you might be tempted to 
>- generate a dynamic-programming solution to a problem when a *greedy solution* *suffices*,
>- or, conversely, you might *mistakenly* think that a greedy solution works when in fact a *dynamic-programming* solution is *required*.
>  
>-- [[Introduction to Algorithms by Cormen]] pp 428	  

- [[Dynamic Programming Algorithms]]

## Applications

### Greedy Search Algorithms

- [[Greedy Search and Hill Climbing]]
- [[Random Restart Hill Climbing]]
- [[Tabu Search]]
- [[Nelder–Mead Simplex Method]]

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

### Iterative and Proximal Algorithms in Optimization

- [[Iterative Descent]] and [[Approximation Method for Optimization]]
- [[Subgradient Methods]]
- [[Proximal Algorithm]]

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

- [[SARSA Algorithm and On-Policy Temporal Difference Control]]
- [[Q Learning Algorithm and Off-Policy Temporal Difference Control]]
- [[Expected SARSA Algorithm]]




-----------
##  Recommended Notes and References


- [[Algorithm General Definition]]

- [[Introduction to Algorithms by Cormen]] pp 417 - 441
- [[Algorithms to Live By Book Summary]]
- [[Algorithm Design Manual by Skiena]] pp 91, 245, 343, 499, 590, 680, 683