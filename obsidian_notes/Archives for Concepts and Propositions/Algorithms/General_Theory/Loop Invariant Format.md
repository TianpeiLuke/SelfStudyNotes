---
tags:
  - concept
  - algorithm/general_theory
keywords:
  - loop_invariant
topics:
  - algorithm/general_theory
name: Loop Invariant Format
date of note: 2024-12-08
---

## Concept Definition

>[!important]
>**Name**: Loop Invariant Format

>[!important] Definition
>**Loop invariants** help us understand why an algorithm is correct. 
>
>When you’re using a loop invariant, you need to show three things:  
>- **Initialization**: It is *true prior* to the first iteration of the loop.  
>- **Maintenance**: If it is true before an iteration of the loop, it *remains true* before the next iteration.  
>- **Termination**: The loop terminates, and when it terminates, the **invariant** - usually along with the reason that the loop terminated - gives us a useful *property* that helps show that the algorithm is correct.

- [[Algorithm General Definition]]
- [[Mathematical Induction]]


## Explanation





-----------
##  Recommended Notes and References



- [[Algorithm Design Manual by Skiena]]
- [[Introduction to Algorithms by Cormen]] pp 19 - 20