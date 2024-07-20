---
tags:
  - concept
  - machine_learning/algorithms
  - probabilistic_graphical_models/algorithm
keywords:
  - belief_propagation
  - belief_update
topics:
  - probabilistic_graphical_model
name: Belief Propagation and Belief Update Equivalence for Clique Tree
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Belief Propagation and Belief Update Equivalence for Clique Tree

![[Sum-Product Message Passing Algorithm for Clique Tree#^d4e300]]

![[Belief-Update Message Passing Algorithm for Clique Tree#^73ff45]]

>[!important] Theorem (Equivalence of Sum-Product and Belief Update Algorithms)
>Let $T$ be a clique tree.
>
>Consider 
>- a set of **sum-product initial potentials** $\{ \psi_{i}, \;i\in V(T) \}$, and
>- **messages** $\{ \delta_{i\to j},\, \delta_{j\to i},\; ij\in E(T) \}$, 
>
>and
>- a set of **belief-update beliefs** $\{ \beta_{i}, \; i\in V(T) \}$, and
>- **messages** $\{ \mu_{i,j},\; ij\in E(T) \}$,
>
>for which the following equations hold:
>$$
>\begin{align*}
> \beta_{i} &= \psi_{i}\,\prod_{k\in N(i)}\delta_{k\to i} \\[5pt]
> \mu_{i,j} &= \delta_{j\to i}\;\delta_{i\to j}.
>\end{align*}
>$$
>
>For any pair of **neighboring cliques** $C_{i}$ and $C_{j}$ in $T$, 
>- let $\{ \delta_{i\to j}',\, \delta_{j\to i}',\; ij\in E(T) \}$ be the set of *sum-product messages* following an application of **SP-Message$(i,j)$**
>- and $\{  \beta_{i}', \; i\in V(T)\}$,  $\{ \mu_{i,j}',\; ij\in E(T) \}$,  be the set of *belief-update beliefs* following an application of **BU-Message$(i,j)$**.
>  
>Then the above equations also **hold** for *new beliefs* $\delta_{i\to j}'$, $\beta_{i}'$ and $\mu_{i,j}'$. That is,
>$$
>\begin{align*}
> \beta_{i}' &= \psi_{i}\,\prod_{k\in N(i)}\delta_{k\to i}' \\[5pt]
> \mu_{i,j}' &= \delta_{j\to i}'\;\delta_{i\to j}'.
>\end{align*}
>$$

>[!important] Corollary
>In an execution of **belief-update message passing**, the **clique tree invariant equation** $$\hat{\mathcal{P}}_{\Phi}(\mathcal{X}) = \frac{\prod_{i\in V(T)}\,\beta_{i}(C_{i})}{\prod_{ij \in E(T)}\,\mu_{i,j}(S_{i,j})},$$ holds **initially** and **after** every message passing step.

^64f40c

- [[Clique Tree Invariant of Sum Product and Reparameterization of PGM]]



## Explanation





-----------
##  Recommended Notes and References

- [[Sum-Product Message Passing Algorithm for Clique Tree]]
- [[Belief-Update Message Passing Algorithm for Clique Tree]]

- [[Clique Tree and Running Intersection Property]]

- [[Tree-Order Relation]]
- [[Root and Rooted Tree]]
- [[Tree Graph and Forest]]


- [[Probabilistic Graphical Models by Koller]] pp 368
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
