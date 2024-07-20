---
tags:
  - concept
  - machine_learning/algorithms
  - probabilistic_graphical_models/theory
  - probabilistic_graphical_models/algorithm
keywords:
  - clique_tree
  - clique_tree_calibration
topics:
  - probabilistic_graphical_model
name: Clique Tree Calibration and Induced Distribution
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Clique Tree Calibration and Induced Distribution

>[!important] Definition
>Let $T$ be a *clique tree* with cliques $C_{i}, i\in V(T)$.
>
>Two adjacent cliques $C_{i}$ and $C_{j}$ are said to be **calibrated** if 
>$$
>\sum_{C_{i} \setminus S_{i,j}}\beta_{i}(C_{i}) = \sum_{C_{j} \setminus S_{i,j}}\beta_{j}(C_{j})
>$$
>

- [[Clique Tree and Running Intersection Property]]

>[!important] Definition
>A clique tree $T$ is said to be **calibrated** if 
>- all pairs of *adjacent cliques* $C_{i}$ and $C_{j}$ are *calibrated*.

>[!important] Definition
>For a **calibrated** *clique tree* $T$,  the  **clique belief** for $\beta_{i}(C_{i})$ and the **sepset belief** satisfies the equation $$\mu_{i,j}(S_{i,j}) = \sum_{C_{i} \setminus S_{i,j}}\beta_{i}(C_{i}) = \sum_{C_{j} \setminus S_{i,j}}\beta_{j}(C_{j}).$$


## Explanation





-----------
##  Recommended Notes and References


- [[Sum-Product Message Passing Algorithm for Clique Tree]]
- [[Clique Tree Measure for Sum-Product and Reparameterization]]
- [[Clique Tree and Running Intersection Property]]

- [[Tree-Order Relation]]
- [[Root and Rooted Tree]]
- [[Tree Graph and Forest]]


- [[Probabilistic Graphical Models by Koller]] pp 355 - 358
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
