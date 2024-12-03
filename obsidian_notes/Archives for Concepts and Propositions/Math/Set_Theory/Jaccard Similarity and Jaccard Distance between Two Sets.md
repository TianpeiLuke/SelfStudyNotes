---
tags:
  - concept
  - math/set_theory
  - machine_learning/kernel_methods
  - information_retrieval/similarity_metric
keywords:
  - jaccard_distance
  - jaccard_similarity
topics:
  - information_retrieval/metrics
  - machine_learning/kernel_methods
  - set_theory
name: Jaccard Similarity and Jaccard Distance between Two Sets
date of note: 2024-11-13
---

## Concept Definition

>[!important]
>**Name**: Jaccard Similarity and Jaccard Distance between Two Sets

>[!important] Definition
>Let $A,B$ be two sets, and assume that $$A \cup B \neq \emptyset. $$
>
>The **Jaccard similarity** or **Jaccard index** or **Jaccard coefficient** between $A$ and $B$ is defined as
>$$J(A, B) := \frac{\lvert A \cap B \rvert }{\lvert A \cup B \rvert }$$
>- The **Jaccard similarity** is bounded as $$0 \le J(A, B) \le 1.$$
>- $$J(A, B) = 0\, \iff A \cap B = \emptyset$$

^584d86

- [[Set Operations]]
- [[Finite Set and Cardinality]]

>[!important] Definition
>The **Jaccard distance** between two finite sets $A$ and $B$ is defined as
>$$d_{J}(A, B) = 1 - J(A,B) := 1- \frac{\lvert A \cap B \rvert }{\lvert A \cup B \rvert } = \frac{\lvert A \,\Delta\, B \rvert }{\lvert A \cup B \rvert }$$
>where 
>$$A \,\Delta\, B = A \cup B  - A \cap B$$ is the **symmetric difference** between $A$ and $B$.



### Measure

>[!important] Definition
>Let $(\Omega, \mathscr{F}, \mu)$ be a measure space. 
>
>Let $A,B\in \mathscr{F}$ be *$\mu$-measurable sets* and assume that 
>$$\mu(A \cup B) \neq 0.$$
>
>The **Jaccard similarity** or **Jaccard index** *with respect to* $\mu$ between $A$ and $B$ is defined as
>$$J_{\mu}(A, B) := \frac{\mu \left(A \cap B\right) }{\mu \left(A \cup B \right) }$$
>- The **Jaccard similarity** is bounded as $$0 \le J(A, B) \le 1.$$
>- The **Jaccard distance** *with respect to* $\mu$ is defined as $$d_{\mu}(A, B) = 1 - J_{\mu}(A, B) := \frac{\mu\left(A \,\Delta\, B \right) }{\mu \left(A \cup B\right)  }.$$

- [[Measure Space and Countably Additive Measure]]


## Explanation






-----------
##  Recommended Notes and References



- [[Positive Definite Kernel Examples]]
- [[Positive Definite Kernel]]


- [[Introduction to Information Retrieval by Manning]]
- 
- [[Networks by Newman]] pp 197, 299
- Wikipedia [Jaccard_index](https://en.wikipedia.org/wiki/Jaccard_index)
