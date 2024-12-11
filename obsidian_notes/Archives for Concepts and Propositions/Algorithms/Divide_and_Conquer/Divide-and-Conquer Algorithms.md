---
tags:
  - concept
  - algorithm/analysis
  - algorithm/divide_and_conquer
  - algorithm/design_paradigm
keywords:
  - divide_and_conquer_algorithm
topics:
  - algorithm/design_paradigm
  - algorithm/analysis
  - algorithm/divide_and_conquer
name: Divide-and-Conquer Algorithms
date of note: 2024-12-08
---

## Concept Definition

>[!important]
>**Name**: Divide-and-Conquer Algorithms

>[!important] Definition
>The **divide-and-conquer algorithm** is an *recursive algorithm design paradigm*, which is described in the following steps
>- **Base case**: solve the problem directly
>- **Recursive case**: performs the following *three characteristic steps*
>	- **Divide** the problem into *one or more* subproblems that are *smaller instances* of the *same* problem.
>	- **Conquer** the subproblems by solving them *recursively*.
>	- **Combine** the *subproblem solutions* to form a solution to the *original problem*.

- [[Recursion Algorithm]]
- [[Algorithm General Definition]]

### Algorithmic Recurrence 



### Structure of Optimal Solution

>[!important] Definition
>The **divide-and-conquer** algorithm *partition* the space into subspaces and then the optimal solution can be obtained by *combining the subproblem solution*
>$$
>\begin{align*}
>&A = \bigcup_{i\in I}C_{i}\\[5pt]
>&x^{(i)} = \arg\min_{x\in C_{i}}F(x) \\[5pt]
>\implies &x^{*} := \arg\min_{x\in A}F(x) = g(x^{(i)},\; i\in I)
\end{align*}
>$$


### Divide and Conquer Algorithm Analysis

- [[Divide-and-Conquer Analysis Substitution Method]]
- [[Divide-and-Conquer Analysis Recursion-Tree Method]]
- [[Divide-and-Conquer Analysis Master Method]]

- [[Algorithm RAM Model and Running-Time Complexity Analysis]]
- [[Algorithm Big-O Notations and Dominance Relation]]



## Explanation

>[!quote]
>A **divide-and-conquer algorithm** *breaks down* a large problem into *smaller* subproblems, which themselves may be broken down into even smaller subproblems, and so forth. 
>- The recursion **bottoms out** when it reaches a *base case* and the subproblem is *small enough* to solve directly without further recursing.
>  
>-- [[Introduction to Algorithms by Cormen]] pp 76  


>[!quote]
>One of the **most powerful techniques** for solving problems is to *break them down* into *smaller*, more *easily solved pieces*. 
>- Smaller problems are *less overwhelming*, and they permit us to **focus on details** that are lost when we are studying the whole thing. 
>- A **recursive algorithm** starts to become apparent whenever we can break the problem into smaller instances of the same type of problem. 
>- Multicore processors now sit in almost every computer, but effective *parallel processing* requires decomposing jobs into at least as many tasks as the number of processors.
>  
>-- [[Algorithm Design Manual by Skiena]] pp 147  

- [[Recursion Algorithm]]

>[!quote]
>Two important **algorithm design paradigms** are based on breaking problems down into smaller problems. 
>- In Chapter 10, we will see **dynamic programming**, which typically *removes* one element from the problem, solves the smaller problem, and then *adds back* the element to the solution of this smaller problem in the proper way. 
>- **Divide and conquer** instead *splits* the problem into (say) halves, solves *each* half, then *stitches* the pieces back together to form a full solution.
>  
>-- [[Algorithm Design Manual by Skiena]]  pp 147

- [[Dynamic Programming Algorithms]]



## Examples

### Sort Algorithms

- [[QuickSort Algorithm]]

### Median and Order-Statistics

- [[Order Statistics]]

### FFT

- [[Fast Fourier Transform]]


### Numerical Linear Algebra

- [[Strassen Matrix Multiplication Algorithm]]
- [[LU Factorization of Matrix]]
- [[Lanczos Iteration Practical with Reorthogonalization]]
- [[Arnoldi Iteration for Hessenberg Reduction of Large Matrix]]


### Binary Search Tree

- [[Binary Search Tree Data Structure]]
- [[Binary Tree Order and Traversal]]
- [[k-d Tree Structure for ANN Search]]

### Parallel Processing



### Map-Reduce







-----------
##  Recommended Notes and References


- [[Algorithm Design Manual by Skiena]] pp 147 - 166
- [[Introduction to Algorithms by Cormen]] pp 76 - 125