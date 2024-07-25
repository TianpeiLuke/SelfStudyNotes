---
tags:
  - concept
  - machine_learning/algorithms
  - probabilistic_graphical_models/theory
keywords:
  - clique_tree_measure
  - max_product
topics:
  - probabilistic_graphical_model
name: Clique Tree Measure for Max-Product and Reparameterization
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Clique Tree Measure for Max-Product and Reparameterization

### Clique Tree Invariant and Reparameterization

![[Clique Tree Invariant of Sum Product and Reparameterization of PGM#^d162e9]]

>[!important] 
>For the **max-product clique tree**, the **reparameterization** holds as well. 


### Max Product Message Passing Preserve the Clique Tree Invariant

![[Belief Propagation and Belief Update Equivalence for Clique Tree#^64f40c]]

>[!important] Proposition
>In an execution of **max-product message passing** (whether *belief propagation* or *belief update*) in a **clique tree**, equation $$\mathcal{Q}_{T}(\mathcal{X}) = \frac{\prod_{i\in V(T)}\,\beta_{i}(C_{i})}{\prod_{ij \in E(T)}\,\mu_{i,j}(S_{i,j})},$$  holds throughout the algorithm.


>[!important] Theorem
>Let $\{ \beta_{i} \}$ and $\{\mu_{i,j}\}$ be the **max-calibrated** set of *beliefs* obtained from executing **max-product message passing**, and let $\mathcal{Q}_{T}$ be the distribution *induced* by these beliefs. 
>
>Then $\mathcal{Q}_{T}$ is a **representation** of the distribution  $\hat{\mathcal{P}}_{\Phi}$ that also satisfies the **max-product calibration** constraints of equation $$\mu_{i,j}(S_{i,j}) = \max_{C_{i} \setminus S_{i,j}}\beta_{i}(C_{i}) = \max_{C_{j} \setminus S_{i,j}}\beta_{j}(C_{j}).$$

- [[Clique Tree Calibration]]

## Explanation

>[!quote]
>Comparing this computation to example 10.6, we see that the sum-product clique tree and the max-product clique tree **both induce reparameterizations** of the original measure  $\hat{\mathcal{P}}_{\Phi}$, but these two reparameterizations are **different**, since they must satisfy different constraints.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 565



-----------
##  Recommended Notes and References

- [[Clique Tree Invariant of Sum Product and Reparameterization of PGM]]

- [[Clique Tree Calibration]]
- [[Clique Tree and Graph and Running Intersection Property]]

- [[Tree-Order Relation]]
- [[Root and Rooted Tree]]
- [[Tree Graph and Forest]]


- [[Probabilistic Graphical Models by Koller]] pp 564
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
