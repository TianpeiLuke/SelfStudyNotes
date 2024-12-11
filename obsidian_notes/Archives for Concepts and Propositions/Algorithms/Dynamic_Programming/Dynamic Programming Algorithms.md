---
tags:
  - concept
  - algorithm/dynamic_programming
  - reinforcement_learning/algorithm
  - natural_language_processing
  - optimization/dynamic_programming
  - optimization/algorithm
  - optimization/theory
  - algorithm/design_paradigm
  - algorithm/recursion
keywords:
  - dynamic_programming
topics:
  - algorithm/design_paradigm
  - algorithm/dynamic_programming
  - optimization/algorithm
  - reinforcement_learning/algorithm
  - machine_learning_algorithm
name: Dynamic Programming Algorithms
date of note: 2024-11-19
---

## Concept Definition

>[!important]
>**Name**: Dynamic Programming Algorithms

>[!important] Definition
>The **dynamic programming (DP)** is an *multi-stage optimization strategy*.


>[!important] Definition
>To develop a dynamic programming algorithm, we follow a sequence of *four steps*:
>- Characterize the **structure** of the an *optimal solution*
>- *Recursively* define the **value** of an *optimal solution*
>- Compute the value of an optimal solution
>	- This is typically done in **bottom-up** fashion
>- *Construct* an optimal solution from computed information.	 


- [[Constrained Optimization Problem]]
- [[Backward Induction and Dynamic Programming]]
- [[Recursion Algorithm]]


### Optimal Substructure

>[!important] Definition
>A problem exhibits **optimal substructure** if an *optimal* solution to the *problem* contains within it *optimal* solutions to *subproblems*.
>$$
> S \subset A \implies  \arg\min_{x\in S} F(x) \supset \arg\min_{x\in A} F(x)
>$$
>- The existence of *optimal substructure* is the *key* ingredient of both *dynamic programming* and *greedy algorithm.*
>- Dynamic programming builds an optimal solution to the problem *from* optimal solutions to *subproblems*

>[!important] Definition
>The following patterns can be used to identify the **optimal substructure**:
>- Show a solution to the problem consists of **making a choice**.
>	- Making this choice leaves *one or more subproblems solved*
>- Assume that for given problem, we **are given the choice** that *leads to optimal solution*
>	- Not concerning on *how to determine this choice*.
>- *Given this choice*, determine which *subproblem* appears, and how to best *characterize* the resulting space of subproblems
>- Show that the *solutions* to the *subproblems* used within an *optimal solution* to the problem must themselves be *optimal* 
>	- Find the **Bellman equation** $$V(x^{*}) = \min_{x\in A}F(x, V(z^{*}))$$
>	- **Proof by contradition**: 
>		- supposing that each of the subproblem solutions is not optimal and then deriving a contradiction.
>		- Show that *substituting* *non-optimal* solution from subproblem with *optimal solution* would result in an *improvement* in the *original problem* $$g(x, V(z^{*})) \le g(x, V(z)),\quad \forall z\in S,\; z^{*} = \arg\min_{z\in S} V(z)$$


### Bellman Equations

>[!important] Definition
>The *structure* of the *optimal solution* obtained by *dynamic programming* is characterized by the **Bellman equation**.
>$$
>\begin{align*}
>&S \subset A\\[5pt]
>&x^{*} \in \arg\min_{x \in A}V(x)\\[5pt]
>\implies& V(x) = g(x, V(z),\, z\in S)\\[5pt]
>\implies & V(x^{*}) = \min_{x\in A} g(x, V(z^{*})) := \min_{x\in A} g\left(x,\;  \min_{z\in S}V(z) \right)
>\end{align*}
>$$
>- Note that the optimal solution $x^{*}$ can *only* be obtained *after* the optimal solution of *subproblem* $z^{*}$ is *obtained*. $$z^{*} = \arg\min_{z\in S}V(z) \to x^{*} \in \arg\min_{x \in A}V(x) $$

- [[Fixed Point of Bellman Operator]]
- [[Value Function and Bellman Equation for MDP]]
- [[Bellman Optimality Equation for MDP]]

### Subproblem Graphs




## Explanation


>[!info]
>"Programming" in this context refers to a **tabular method**, not to writing computer code.

>[!info]
>To characterize the space of subproblems, a good **rule of thumb** says to try to 
>- keep the space **as simple as possible** 
>- and then *expand* it as necessary.

>[!quote]
>Dynamic programming often uses optimal substructure in a **bottom-up fashion**. 
>- That is, you first find *optimal solutions* to **subproblems** 
>- and, having *solved the subproblems*, you find an *optimal solution* to the **problem**. 
>
>Finding an optimal solution to the problem entails **making a choice** among *subproblems* as to which you will use in solving the problem. 
>- The **cost** of the problem solution is usually the **subproblem costs** plus a **cost** that is directly attributable to the **choice** itself.
>  
>-- [[Introduction to Algorithms by Cormen]] pp 384  


### Compared with Divide-and-Conquer

>[!quote]
>Dynamic programming, like the *divide-and-conquer method*, solves problems by *combining* the solutions to *subproblems*.
>
>The **divide-and-conquer** algorithms 
>- *partition* the problem into **disjoint** *subproblems*, 
>- solve the subproblems *recursively*, 
>- and then *combine* their solutions to solve the original problem. 
>
>In contrast, **dynamic programming** applies when the *subproblems overlap*, that is, when *subproblems share subsubproblems*. 
>- In this context, a divide-and-conquer algorithm does *more work than necessary*, repeatedly solving the common subsubproblems.
>  
>-- [[Introduction to Algorithms by Cormen]] pp 362  

- [[Divide-and-Conquer Algorithms]]


### Compared with Greedy Algorithms

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

- [[Greedy Heuristic Algorithms]]


![[Concepts and Algorithms for Algorithm Design#^b8bfb7]]

## Applications


### Optimization

- [[Integer Linear Optimization Problem and Integer Programming]]
- [[Knapscak Problem]]


### Flow and Shortest Path

- [[Graph]]
- [[Network and Flow and Capacity and Cut]]
- [[Minimum Spanning Tree Problem]]
- [[Bellman-Ford Algorithm for Single-Source Shortest Path Problem]]
- [[Dijkstra Algorithm for Single-Source Shortest Path Problem on DAG]]
- [[A-star Heuristic Search]]


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

### Natural Language Processing

- [[Minimum Edit Distance or Levenshtein Distance via Dynamic Programming]]
- [[CKY Parsing as Dynamic Programming Algorithm]]
- [[Unigram Tokenization]]
- [[Longest Common Subsequence between Strings]]

### Numerical Linear Algorithm

- [[Matrix-Chain Multiplication]]


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



-----------
##  Recommended Notes and References


- [[Constrained Optimization Problem]]
- [[Algorithm General Definition]]

- [[Game Theory An Introduction by Tadelis]] pp 26

- [[Dynamic Programming by Bellman]]
- [[Algorithm Design Manual by Skiena]] pp 307, 474, 498, 556, 599, 633, 706
- [[Introduction to Algorithms by Cormen]] pp 362–413
- [[Dynamic Programming and Optimal Control by Bertsekas]]

- [[Markov Decision Processes by Puterman]] pp 82, 92-99, 158
- [[Reinforcement Learning An Introduction by Sutton]] pp 62 - 67, 73 - 90

- [[Deep Learning by Goodfellow]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 428


- Open Course [Dynamic Programming and Stochastic Control](https://ocw.mit.edu/courses/6-231-dynamic-programming-and-stochastic-control-fall-2015/)
- UIUC  [Algorithms](http://jeffe.cs.illinois.edu/teaching/algorithms/book/Algorithms-JeffE.pdf)

