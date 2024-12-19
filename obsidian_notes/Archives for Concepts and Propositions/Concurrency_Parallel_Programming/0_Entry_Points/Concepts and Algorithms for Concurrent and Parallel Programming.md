---
tags:
  - entry_point
  - concept
  - parallel_computing
  - concurrent_computing
keywords: 
topics: 
name: 
date of note: 2024-12-18
---

## List of Concepts and Principles

### Basic Problems in Concurrent and Parallel Computing

#### Concurrent Programming

- [[Concurrent Programming]]
- [[Shared-Memory Multi-Processors or Multi-Cores]]
- [[Concurrent Coordination Problem]]
- [[Safety Property of Computer Program]]
- [[Liveness Property of Computer Program]]
- [[Producer-Consumer Problem for Concurrent Programming]]
- [[Reader-Writer Problem for Concurrent Programming]]

#### Parallel Programming

- [[Speedup of Parallelism]]
- [[Amdahl Law to Analyze Speedup of Parallelism]]
- [[Parallel Programming]]


### Mutual Exclusion in Concurrent Computing

- [[Mutual Exclusion Problem in Concurrent Programming]]
- [[Critical Section for Concurrent Programming]]
- [[Deadlock in Concurrent Programming]]
- [[Starvation in Concurrent Programming]]
- [[Two-Thread Solution for Mutual Exclusion Problem]]
- [[Peterson Lock Algorithm for Mutual Exclusion Problem]]
- [[Filter Lock Algorithm for Mutual Exclusion Problem]]
- [[Fairness in Concurrent Programming]]
- [[Bounded Wait-Free Property]]
- [[Lamport Bakery Algorithm]]


### Concurrent Object

- [[Sequential Object]]
- [[Sequential Consistency in Programming]]
- [[Linearizability of Object]]
- [[Concurrent Object]]
- [[Concurrent Correctness]]
- [[Progress Conditions of Concurrent Object]]
- [[Wait-Freedom as Progress Conditions]]
- [[Lock-Freedom as Progress Conditions]]
- [[Obstruction-Freedom as Progress Conditions]]


### Foundations of Shared Memory 

- [[Space of Registers for Shared-Memory Multi-Processors]]
- [[MRSW Registers]]
- [[Atomic SRSW Registers]]
- [[Atomic MRSW Registers]]
- [[Atomic MRMW Registers]]
- [[Atomic Snapshots]]



### Power of Primitive Synchoronization

- [[Consensus Numbers for Synchronization Operations]]
- [[Atomic Registers]]
- [[Consensus Protocols for Synchronization Operations]]
- [[FIFO Queue for Synchronization Operations]]
- [[Multiple Assignment Object]]
- [[Read-Modify-Write Operations]]
- [[Common2 RMW Operation]]
- 


### Universality of Consensus

- [[Universality of Consensus]]
- [[Lock-Free Universal Construction]]
- [[Wait-Free Universal Construction]]



## Data Structure and Algorithms

### Spin Locks and Contention

- [[Atomic Objects]]
- [[Test-and-Set Locks]]
- [[Exponential Back-off]]
- [[Queue Locks]]
- [[CLH Queue Lock]]
- [[MCS Queue Lock]]
- [[Hierarchical Locks]]


### Monitors and Blocking Synchronization

- [[Monitor Locks]]
- [[Lost-Wakeup Problem]]
- [[Readers-Writers Locks]]


### Linked List and Locking

- [[Linked List Data Structure]]
- [[Concurrent Reasoning]]
- [[Coarse-Grained Synchronization]]
- [[Fine-Grained Synchronization]]
- [[Optimistic Synchronization]]
- [[Lazy Synchronization]]
- [[Nonblocking Synchronization]]


### Queue and Memory Management and ABA Problem

- [[Queue as FIFO Data Structure for Exploration]]
- [[Bounded Partial Queue]]
- [[Unbounded Total Queue]]
- [[Lock-Free Unbounded Queue]]
- [[ABA Problem and Memory Reclamation]]
- [[Dual Data Structure for Synchronous Queue]]


### Stacks and Elimination

- [[Stack as FILO Data Structure for Backtrack]]
- [[Unbounded Lock-Free Stack]]
- [[Elimination in Concurrent Programming]]
- [[Elimination Back-off Stack]]

### Counting and Sorting and Distributed Coordination

- [[Shared Counting in Concurrent Programming]]
- [[Quiescently Consistent Pool]]
- [[Counting Networks]]
- [[Diffracting Trees]]
- [[Parallel Sorting]]
- [[Sorting Network]]
- [[Distributed Coordination]]


### Concurrent Hashing and Natural Parallelism

- [[Hash Table for Efficient Retrieval and Inverse Map]]
- [[Closed-Address Hash Sets]]
- [[Lock-Free Hash Sets]]
- [[Open-Address Hash Sets]]


### Skiplists and Balanced Search

- [[Skip Linked List Data Structure]]
- [[Lock-based Concurrent Skip-List]]
- [[Lock-Free Concurrent Skip-List]]
- [[Concurrent Skip-List]]


### Priority Queues

- [[Priority Queue as Partially Ordered Data Structure]]
- [[Bounded Array-based Priority Queue]]
- [[Bounded Tree-based Priority Queue]]
- [[Unbounded Heap-based Priority Queue]]
- [[Unbounded Skiplist-based Priority Queue]]


### Scheduling and Work Distribution

- [[Parallel Program Analysis]]
- [[Work Distribution for Parallel Programming]]
- [[Multi-Programming]]
- [[Work Stealing in Parallel Programming]]
- [[Work Stealing Deques]]
- [[Optimal Job Scheduling]]



### Data Parallelism

- [[Data Parallelism]]
- [[MapReduce Architecture for Data Parallelism]]
- [[Stream Computing]]
- [[Model Parallelism]]

### Barriers

- [[Barriers in Parallel Programming]]
- [[Barriers in Parallel Programming Implementation]]
- [[Sense Reversing Barrier]]
- [[Combining Tree Barrier]]
- [[Static Tree Barrier]]
- [[Termination Detection Barrier]]

### Optimism and Manual Memory Management



### Transactional Programming

- [[Transactional Programming]]



## Explanation





-----------
##  Recommended Notes and References

- [[Concepts and Algorithms for Algorithm Design]]

- [[The Art of Multiprocessor Programming by Herlihy]]
- [[Introduction to Algorithms by Cormen]]
- [[Algorithm Design Manual by Skiena]]
- [[Matrix Computations by Golub]]