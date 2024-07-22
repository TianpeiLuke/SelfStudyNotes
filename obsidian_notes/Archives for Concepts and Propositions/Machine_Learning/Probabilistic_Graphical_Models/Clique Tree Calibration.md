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

^d56b22

- [[Clique Tree and Running Intersection Property]]

>[!important] Definition
>A clique tree $T$ is said to be **calibrated** if 
>- all pairs of *adjacent cliques* $C_{i}$ and $C_{j}$ are *calibrated*.

^ec693c

>[!important] Definition
>For a **calibrated** *clique tree* $T$,  the  **clique belief** for $\beta_{i}(C_{i})$ and the **sepset belief** satisfies the equation $$\mu_{i,j}(S_{i,j}) = \sum_{C_{i} \setminus S_{i,j}}\beta_{i}(C_{i}) = \sum_{C_{j} \setminus S_{i,j}}\beta_{j}(C_{j}).$$

### Max Calibration

>[!important] Definition
>For a **calibrated** *clique tree* $T$,  the  **clique max-marginal** for $\beta_{i}(C_{i})$ and the **sepset max-marginal** satisfies the equation $$\mu_{i,j}(S_{i,j}) = \max_{C_{i} \setminus S_{i,j}}\beta_{i}(C_{i}) = \max_{C_{j} \setminus S_{i,j}}\beta_{j}(C_{j}).$$


## Explanation

>[!quote]
>A **calibrated clique tree** is more than simply a **data structure** that stores the results of probabilistic inference for all of the cliques in the tree. As we now show, it can also be viewed as an **alternative representation** of the measure $\hat{\mathcal{P}}_{\Phi}(\mathcal{X})$.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 361




-----------
##  Recommended Notes and References


- [[Sum-Product Message Passing Algorithm for Clique Tree]]
- [[Clique Tree Invariant of Sum Product and Reparameterization of PGM]]
- [[Clique Tree and Running Intersection Property]]

- [[Tree-Order Relation]]
- [[Root and Rooted Tree]]
- [[Tree Graph and Forest]]


- [[Probabilistic Graphical Models by Koller]] pp 355 - 358
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
