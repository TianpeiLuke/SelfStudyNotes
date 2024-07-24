---
tags:
  - concept
  - machine_learning/algorithms
  - probabilistic_graphical_models/theory
  - probabilistic_graphical_models/algorithm
  - probabilistic_graphical_models/inference
keywords:
  - probabilistic_graphical_model
  - clique_tree
  - marginal_polytope
  - local_consistent_polytope
topics:
  - probabilistic_graphical_model
name: Marginal Polytope and Local Consistent Polytope
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: *Marginal Polytope* and *Local Consistent Polytope*

>[!important] Definition
>Let $\mathcal{G}$ be a *cluster graph* corresponding to some distribution $\mathcal{P}$. Define a set of *beliefs* $$(\{ \beta_{i},\; i\in V(\mathcal{G}) \}\,\cup\, \{ \mu_{i,j},\; ij\in E(\mathcal{G}) \}) := (\beta, \mu).$$
>
>The **marginal polytope** of $\mathcal{G}$ is defined as
>$$
>\mathbb{M}(\mathcal{G}) := \left\{(\beta, \mu):\;\exists \mathcal{P}\; \text{ such that } \beta_{i} = \mathcal{P}(C_{i}),\; i\in V(\mathcal{G}),\;\; \mu_{i,j} = \mathcal{P}(S_{i,j}),\; ij\in E(\mathcal{G}) \right\} 
>$$


- [[Polyhedron and Polytope]]
- [[Cluster Graph and Family Preservation]]
- [[Probabilistic Graphical Models by Koller]] pp 411
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 57 


>[!important] Definition
>We call the constraint set as the **locally consistent polytope**
>$$
>\mathbb{L}(\mathcal{G}) := \left\{(\beta, \mu):\, \sum_{c_{i}}\beta_{i}(c_{i}) = 1,\,  \beta_{i}(c_{i}) \ge 0,\;\; \forall i \in V(\mathcal{G}),\,\forall c_{i};\;\;  \mu_{i,j}(s_{i,j}) = \sum_{C_{i} \setminus S_{i,j}}\beta_{i}(c_{i}),\;\; \forall ij\in E(\mathcal{G}),\,\forall s_{i,j}\right\} 
>$$  

^c31624

- [[Probabilistic Graphical Models by Koller]] pp 412
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 76


>[!important] Proposition
>For **any graph** $\mathcal{G}$,  the *locally consistent polytope* is a *relaxation* of the *marginal polytope*.
>$$
>\mathbb{M}(\mathcal{G}) \subseteq \mathbb{L}(\mathcal{G}).
>$$
>For **tree-structured graph** $T$,  the **equality** holds, i.e.
>$$
>\mathbb{M}(T) = \mathbb{L}(T).
>$$

- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 76

>[!important] Definition
>The beliefs $\{\mu_{i,j}, \;ij\in E(\mathcal{G})\}$ and $\{\beta_{i},\; i\in V(\mathcal{G})\}$ in $\mathbb{L}(\mathcal{G})$ is called the **pseudomarginals**.


## Explanation







-----------
##  Recommended Notes and References

- [[Maximum Entropy Learning of Clique Tree PGM]]
- [[Variational Inference for Clique Tree]]

- [[Evidence Lower Bound]]



- [[Bayesian Network on Directed Acyclic Graph]]
- [[Markov Network Distribution to Graph]]

- [[Exponential Family and Convex Duality]]
- [[Maximum Entropy Learning of Exponential Family]]
- [[Exponential Family of Distributions]]

- [[Clique Tree and Graph and Running Intersection Property]]
- [[Cluster Graph and Family Preservation]]
- [[Graph]]
- [[Polyhedron and Polytope]]

- [[Probabilistic Graphical Models by Koller]] pp 411
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 57, 76
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
