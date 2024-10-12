---
tags:
  - concept
  - machine_learning/algorithms
  - probabilistic_graphical_models/models
  - probabilistic_graphical_models/representation
  - probabilistic_graphical_models/algorithm
  - probabilistic_graphical_models/theory
keywords:
  - mean_field_approximation
topics:
  - probabilistic_graphical_model
name: Structured Variational Approximation
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Structured Variational Approximation

![[Log-Partition Function of Exponential Family#^88a0c0]]
![[Exponential Family and Convex Duality#^ed96df]]

- [[Log-Partition Function of Exponential Family]]
- [[Exponential Family and Convex Duality]]

>[!info] 
>There are **two fundamental difficulties** associated with the **variational principle** 
>- the nature of the *constraint set* $\mathbb{M}$
>- the lack of an explicit form for the *dual function* $A^{*}$.

>[!important]
>The **core idea** of **mean field approaches** is simple: 
>
>let us limit the optimization to a *subset of distributions* for which both $\mathbb{M}$ and $A^{*}$ are relatively easy to characterize; e.g., perhaps they correspond to a graph with small treewidth. 
>
>We refer to any such distribution as "**tractable**." 
>- The simplest choice is the family of **product distributions**, which gives rise to the **naive mean field** method.

- [[Mean Field Approximation for PGM]]
- [[Mean Field Approximation for Exponential Family]]
- [[Mean Field Approximation for Gaussian Markov Random Field]]

### Structured Variational Approach

![[Maximum Entropy Learning for Approximate Inference in PGM#^5fbd75]]

![[Marginal Polytope and Local Consistent Polytope#^161ed7]]

- [[Maximum Entropy Learning for Approximate Inference in PGM]]
- [[Marginal Polytope and Local Consistent Polytope]]




## Explanation





-----------
##  Recommended Notes and References

- [[Mean Field Approximation for PGM]]


- [[Kullback-Leibler Divergence]]
- [[Information Projection and Moment Projection]]

- [[Maximum Entropy Learning]]
- [[Evidence Lower Bound]]



- [[Probabilistic Graphical Models by Koller]]
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 125 - 147
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
