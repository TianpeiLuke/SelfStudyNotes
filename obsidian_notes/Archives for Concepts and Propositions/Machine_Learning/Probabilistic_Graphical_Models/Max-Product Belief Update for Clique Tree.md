---
tags:
  - concept
  - machine_learning/algorithms
  - probabilistic_graphical_models/models
  - probabilistic_graphical_models/algorithm
  - probabilistic_graphical_models/theory
keywords:
  - max_product
  - belief_update
  - clique_tree
topics:
  - probabilistic_graphical_model
name: Max-Product Belief Propagation for Clique Tree
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Max-Product Belief Update for Clique Tree

### Belief Update Algorithm


>[!important] Algorithm
>The **Max-Product Belief-Update Message Passing Algorithm** for **Clique Tree** is described as 
>- *Require*: $\Phi$, the set of *factors*
>- *Require*: $T$, the **clique tree** over $\Phi$
>- *Require*: $\alpha$, the initial *assignment* of *factors to cliques*
>- **Initialize** all the clique tree beliefs:
>	- for each clique $C_{i}$:
>		- initialize the **clique belief** $$\beta_{i} = \prod_{\alpha(\phi_{s}) = i}\phi_{s}.$$
>	- for each edge $ij\in E(T)$
>		- initialize the **sepset belief** $$\mu_{i,j} = 1$$
>- While exists an *uninformed* clique in $T$
>	- Select an edge $ij\in E(T)$
>	- Call **Max-Product Belief-Update Message Passing** subprocedure to update *clique belief* $\beta_{j}$ in receiving clique and *sepset belief* $\mu_{i,j}$ $$\text{MP-BU-Message}(i, j)$$
>- *Return*: *all clique beliefs* $\{ \beta_{i}, i\in V(T) \}$

>[!important] Algorithm
>The **MP-BU-Message** subprocedure is described as
>- *Require*: $i$, the *sending* clique index
>- *Require*: $j$, the *receiving* clique index
>- *Marginalize* the clique over the **sepset** between $C_{i}$ and $C_{j}$ $$\sigma_{i\to j} = \max_{C_{i} \setminus S_{i,j}}\beta_{i}$$
>- *Update* the **clique belief** using Bayes rule $$\beta_{j} \leftarrow \beta_{j} \cdot \frac{\sigma_{i\to j}}{\mu_{i,j}}$$
>- *Update* the **sepset belief** $$\mu_{i,j} = \sigma_{i\to j}$$ 

- [[Topological Sorting]]

## Explanation

>[!quote]
>As in the sum-product case, the *max-product belief propagation algorithm* and the *max-product belief update algorithm* are exactly **equivalent**. Thus, we can show that the analogue to equation (10.9) holds also for max-product:
>$$
>\mu_{i,j}(S_{i,j}) = \delta_{j\to i}(S_{i,j}) \cdot \delta_{i\to j}(S_{i,j})
>$$
>-- [[Probabilistic Graphical Models by Koller]] pp 563



-----------
##  Recommended Notes and References

- [[Sum-Product Belief-Update Message Passing Algorithm for Clique Tree]]

- [[Max-Product Belief Propagation for Clique Tree]]
- [[Max-Product Variable Elimination]]


- [[Clique Tree and Graph and Running Intersection Property]]
- [[Tree-Order Relation]]
- [[Root and Rooted Tree]]
- [[Tree Graph and Forest]]


- [[Probabilistic Graphical Models by Koller]] pp 563
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
