---
tags:
  - concept
  - algorithm/analysis
keywords:
  - ram_model_algorithm_analysis
  - running_time_analysis
topics:
  - algorithm/analysis
name: Algorithm RAM Model and Running-Time Complexity Analysis
date of note: 2024-12-08
---

## Concept Definition

>[!important]
>**Name**: Algorithm RAM Model and Running-Time Complexity Analysis

### RAM Model

>[!important] Definition
>The **Random Access Machine (RAM)** is a hypothetical computer model for *machine independent algorithm design*.
>
>Under this model, we assumes that
>- Each **simple operation** takes *exactly one time step*
>	- such as 
>		- $+$, *addition*;
>		- $*$, *multiplication*;
>		- $-$, *subtraction*;
>		- $=$, *assignment*; 
>		- $\text{if}$, *condition check* 
>		- $\text{call}$, *sub-routine call * 
>- **Loops** and **subroutines** are *not* considered simple operations.
>	- Instead, they are the *composition* of many single-step operations.
>	- The time it takes to run through a loop or execute a *sub-routine* depends on the number of loop iterations, or the specific characteristic of the program.
>- Each **memory access** takes exactly *one time step.*

^76c416

>[!quote]
>Under the RAM model, we measure **run time** by counting the *number of steps* an algorithm takes on a given problem instance. If we assume that our RAM executes a *given number of steps per second*, this operation count converts naturally to the *actual running time*.
>
>-- [[Algorithm Design Manual by Skiena]] pp 32

>[!important] Definition
>The **running time** of an algorithm on a particular input is the *number of instructions* and *data accesses* executed.

### Worst-Case Complexity Analysis

- [[Algorithm Worst-Case Running Time Analysis]]

### Average-Case Complexity Analysis

- [[Algorithm Average-Case Running Time Analysis]]
- [[Probabilistic Analysis of Randomized Algorithm]]

### Best-Case Complexity Analysis

- [[Algorithm Best-Case Running Time Analysis]]

### Growth Rate

- [[Algorithm Big-O Notations and Dominance Relation]]

## Explanation

>[!quote]
>Take-Home Lesson: 
>- Algorithms can be understood and studied in a **language and machine-independent manner**.
>  
>-- [[Algorithm Design Manual by Skiena]] pp 32  




-----------
##  Recommended Notes and References

- [[Loop Invariant Format]]
- [[Algorithm General Definition]]

- [[Introduction to Algorithms by Cormen]] pp  25 - 31, 49 - 76
- [[Algorithm Design Manual by Skiena]] pp 31
- [[Matrix Computations by Golub]] pp 12
- [[Numerical Linear Algebra by Trefethen]]