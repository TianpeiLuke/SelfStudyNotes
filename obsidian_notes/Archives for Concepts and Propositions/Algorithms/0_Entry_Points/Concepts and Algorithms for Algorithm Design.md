---
tags:
  - entry_point
  - concept
  - algorithm/analysis
  - algorithm/design_paradigm
  - algorithm/data_structure
keywords: 
topics: 
name: 
date of note: 2024-09-16
---

## General Theory of Algorithm, Data Structure and Analysis

- [[Algorithm General Definition]]
- [[Data Structure General Definition]]
- [[Loop Invariant Format]]
- [[Algorithm RAM Model and Running-Time Complexity Analysis]]
- [[Algorithm Big-O Notations and Dominance Relation]]
- [[Algorithm Best-Case Running Time Analysis]]
- [[Algorithm Worst-Case Running Time Analysis]]
- [[Algorithm Average-Case Running Time Analysis]]
- [[Probabilistic Analysis of Randomized Algorithm]]
- [[Algorithm Big-O Notations in Probability]]

### Recursion

- [[Recursion Algorithm]]
- [[Loop Invariant Format]]
- [[Recurrence and Algorithmic Recurrence]]

### Amortized Analysis

- [[Algorithm Amortized Analysis]]

### Computational Complexity Theory

- [[Computational Complexity Theory]]
- [[P Complexity Class and Problems]]
- [[NP Complexity Class and Problems]]
- [[NP Hard Complexity Class and Problems]]
- [[NP Complete Complexity Class and Problems]]


### NP Complete Problems

- [[3-Dimensional Matching]]
- [[Boolean Satisfiability Problem SAT]]
- [[Knapsack or Subset Sum Problem]]
- [[Traveling Salesman Problem]]
- [[Hamiltonian Cycle Problem]]
- [[Subgraph Isomorphism Problem]]
- [[Set Cover Problem]]
- [[Vertex Cover Problem]]
- [[Graph Partition Problem]]
- [[Maximum Clique Problem]]
- [[Minimum k-Cut Problem]]
- [[Minimum k-Spanning Tree]]
- [[Subset Sum Problem]]
- [[Independent Set Problem]]
- [[Graph Coloring Problem]]
- [[Feedback Arc and Vertex Set Problem]]
- [[Optimal Job Scheduling]]
- [[Optimal Assignment Problem and Monge Problem]]
- [[Conjunctive Normal Form or CNF Formula]]


## Algorithm Design Paradigms 



|                                 | **divide-and-conquer**                                                                                                    | **greedy algorithm**                                                                                                                                                                      | **dynamic programming**                                                                                                                                                                                                                                                                                    |
| ------------------------------- | ------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| objective                       | $$x^{*} = \arg\min_{x\in \mathcal{X}}V(x)$$                                                                               | $$x^{*} = \arg\min_{x\in \mathcal{X}}V(x)$$                                                                                                                                               | $$x^{*} = \arg\min_{x\in \mathcal{X}}V(x)$$                                                                                                                                                                                                                                                                |
| subproblem domain               | $$\mathcal{X} = \bigcup_{i\in I}S_{i}$$ and $$S_{i} \cap S_{j} = \emptyset$$                                              | $$ S_{t+1} \subseteq  S_{t} \,{ \subseteq}\ldots{ \subseteq}\, S_{0} := \mathcal{X} $$                                                                                                    | $$S_{t+1}\leftarrow x_{t} \leftarrow S_{t} \,{\leftarrow}\ldots{\leftarrow}\,S_{0} := \mathcal{X}$$                                                                                                                                                                                                        |
| optimal solution of subproblem  | optimal solutions of *subproblems* are *independent* $$x^{(i)} := \arg\min_{x\in S_{i}}V(x)$$                             | optimal solution depends *only* on the *greedy choice* $$x_{t} := \arg\min_{x\in S_{t}}V(x)$$                                                                                             | **Bellman optimality equation**: optimal solution depends on the *choice* which is function of optimal solution of *next iteration* $$V(x_{t}) = \min_{a_{t}\in \mathcal{A}(x_{t})} \{R(x_{t}, a_{t}) + \beta V(x_{t+1})\}$$                                                                               |
| new subproblem domain           | *Independent from choice*, obtained from partitioning                                                                     | Depending on the *greedy choice* $S_{t}$,  $$S_{t+1}= T(S_{t})$$each choice would generate *only one* subproblem                                                                          | Depending on the *current choice* and the *solution* of subproblem in *next iteration*  $$S_{t+1}^{(i)} = T(x_{t} = i)$$ each choice would generate *multiple* new subproblems                                                                                                                             |
| relationship of subproblems     | **independent** $$S_{i} \cap S_{j} = \emptyset$$                                                                          | **overlapping**                                                                                                                                                                           | **overlapping** $$S_{t_{1}} \cap S_{t_{2}} \neq \emptyset$$                                                                                                                                                                                                                                                |
| **optimal substructure**        | the optimal solution is from a *combination* of the optimal solution of *each sub-problem* $$x^{*} = f(x^{(i)}, i\in I)$$ | the optimal solution is contained in each subproblem domain $$x^{*}\in S_{t}$$ and can be obtained by combining *subproblem solution* with *greedy choice*<br>$$x^{*} = g(x_{t}, a_{t})$$ | the optimal solution is obtained by the **Bellman equation**  *after* the optimal solution of *subproblem* in *next iteration* is obtained.  The optimal solution is the **fixed point** to the Bellman equation $$x_{t} \to x^{*}$$ the optimal solution is the result of an **optimal policy** $\pi^{*}$ |
| **ordering of problem solving** | **parallel, top-down**                                                                                                    | **sequential, top-down**                                                                                                                                                                  | **sequential, bottom up**                                                                                                                                                                                                                                                                                  |
| pass                            | forward pass only                                                                                                         | forward pass only                                                                                                                                                                         | **forward-backward pass**                                                                                                                                                                                                                                                                                  |
| **computation graph**           | a *multi-layer* **rooted tree**                                                                                           | a *multi-step* **trail**                                                                                                                                                                  | a *multi-layer* **network**                                                                                                                                                                                                                                                                                |

^b8bfb7






### Divide and Conquer

- [[Divide-and-Conquer Algorithms]]
- [[Divide-and-Conquer Analysis Substitution Method]]
- [[Divide-and-Conquer Analysis Recursion-Tree Method]]
- [[Divide-and-Conquer Analysis Master Method]]

### Greedy Algorithm

- [[Concepts and Algorithms based on Dynamic Programming]]
- [[Greedy Heuristic Algorithms]]

### Dynamic Programming

- [[Concepts and Algorithms based on Dynamic Programming]]
- [[Dynamic Programming Algorithms]]
- [[Value Function and Bellman Equation for MDP]]
- [[Bellman Optimality Equation for MDP]]


## Data Structure

- [[Data Structure General Definition]]

### Linked List

- [[Linked List Data Structure]]
- [[Skip Linked List Data Structure]]

### Stack

- [[Stack as FILO Data Structure for Backtrack]]

### Queue

- [[Queue as FIFO Data Structure for Exploration]]

### Priority Queue and Heap

- [[Priority Queue as Partially Ordered Data Structure]]
- [[Heap as Partially Ordered Data Structure]]
- [[Min-Heap Data Structure]]
- [[Fibonacci-Heap Data Structure]]

### Hash Table

- [[Hash Table for Efficient Retrieval and Inverse Map]]


### Rooted Tree

- [[Root and Rooted Tree]]
- [[Binary Search Tree Data Structure]]
- [[k-d Tree Structure for ANN Search]]
- [[Ball Tree Structure for ANN Search]]
- [[Red-Black Tree as Balanced Binary Search Tree]]

- [[Suffix Tree for Fast Query]]
- [[Order-Statistic Tree]]
- [[Interval Tree]]

### Disjoint-Set Data Structure

- [[Union-Find and Disjoint-Set Data Structure]]

### Graph

- [[Concepts and Theorems in Graph Theory]]
- [[Graph]]
- [[Directed Graph]]
- [[Directed Acyclic Graph]]
- [[Adjacency Matrix of Graph]]
- [[Adjacency List for Sparse Representation of Graph]]
- [[Incidence Matrix for Graph and Hypergraph]]


- [[Navigable Small World Model and Kleinberg Variant of Watts-Strogatz Model]]
- [[Hierarchical Navigable Small Worlds or HNSW for Graph-based ANN Search]]


## List of Algorithms

### Sorting

- [[MergeSort Algorithm]]
- [[QuickSort Algorithm]]
- [[BucketSort or Distribution Sort Algorithm]]
- [[HeapSort Algorithm]]

### Median and Order Statistics

- [[Order Statistics]]

### Hashing and Randomized Algorithm

- [[MinHash Algorithm for ANN Search]]


### Greedy Search

- [[Greedy Search and Hill Climbing]]
- [[Tabu Search]]
- [[Random Restart Hill Climbing]]
- [[Stochastic Hill Climbing]]
- [[Greedy Decoding for Causal Language Model Generation]]
- [[Beam Search]]
- [[Beam Search for Causal Decoding of Language Model]]


### Tree-based Search and Operation

- [[Binary Tree Order and Traversal]]
- [[Backtracking]]
- [[Red-Black Tree as Balanced Binary Search Tree]]


### Graph-based Search and Traversal

- [[Backtracking]]
- [[Breadth-First Search]]
- [[Depth-First Search]]
- [[Best-First Search]]
- [[A-star Heuristic Search]]
- [[Topological Sorting]]

### Graph Algorithms

#### Minimum Spanning Tree

- [[Minimum Spanning Tree Problem]]
- [[Prim Algorithm to Prune Minimum Spanning Tree]]
- [[Kruskal Algorithm to Prune Minimum Spanning Tree]]

#### Connected Components

- [[Union-Find and Disjoint-Set Data Structure]]
- [[Strongly Connected Components Identification in Graph]]
- [[Lowest Common Ancestor in Rooted Tree]]

#### Graph Matching

- [[Bipartite Graph]]
- [[Matching in Vertex and Edge of Graph]]
- [[Maximum Bipartite Matching]]


### Network Algorithms

- [[Network and Flow and Capacity and Cut]]

#### Shortest Path

- [[Single-Source Shortest Path Problem on Network]]
- [[Bellman-Ford Algorithm for Single-Source Shortest Path Problem]]
- [[Dijkstra Algorithm for Single-Source Shortest Path Problem on DAG]]
- [[All-Pairs Shortest Path Problem on Network]]
- [[Floyd-Warshall Algorithm for All-Pairs Shortest Path Problem]]

#### Maximum Flow

- [[Max-Flow Min-Cut Theorem]]
- [[Ford-Fulkerson Method for Maximum Flow Problem]]

### Numerical Computation

- [[Theory and Algorithms for Numerical Linear Algebra]]
- [[Matrix-Chain Multiplication]]
- [[Strassen Matrix Multiplication Algorithm]]


### String Related Algorithm

#### Special String



#### String Comparison and Similarity

- [[Minimum Edit Distance or Levenshtein Distance via Dynamic Programming]]
- [[Longest Common Subsequence between Strings]]

#### String Matching

- [[String Matching Problem]]
- [[Rabin-Karp Algorithm for String Matching Problem]]
- [[Knuth-Morris-Pratt Algorithm for String Matching Problem]]

#### Natural Language Processing

- [[Context-Free Grammars]]
- [[CKY Parsing as Dynamic Programming Algorithm]]





-----------
##  Recommended Notes and References



- [[Introduction to Algorithms by Cormen]]
- [[Algorithm Design Manual by Skiena]]
- [[Algorithms to Live By Book Summary]]
- [[Artificial Intelligence Modern Approach by Russell]]