---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/representation
  - math/graph_theory
keywords:
  - cluster_graph
  - family_presevation
topics:
  - probabilistic_graphical_model
  - math/graph_theory
name: Cluster Graph and Family Preservation
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Cluster Graph and Family Preservation

>[!important] Definition
>A **cluster graph** $\mathcal{U}$ for a set of factors $\Phi$ over $\mathcal{X}$ is an *undirected graph*, 
>- each of whose *nodes* $i$ is associated with a **subset** $C_{i} \subseteq \mathcal{X}$. 
>- Each edge between a *pair of clusters* $C_{i}$ and $C_{j}$ is associated with a **sepset** $$S_{i,j} \subseteq C_{i} \cap C_{j}.$$

>[!important] Definition
>A *cluster graph* must be **family-preserving**:
>
>- each *factor* $\phi\in \Phi$  must be *associated with* a *cluster* $C_{i}$, denoted $\alpha(\phi)$, such that $$\text{Scope}[\phi] \subseteq C_{i}.$$ 




## Explanation

>[!quote]
>A *cluster graph* is a **data structure** that provides a *graphical flowchart* of the **factor-manipulation process**. *Each node* in the cluster graph is a **cluster**, which is associated with a *subset* of variables; the graph contains *undirected edges* that connect clusters whose **scopes** have some **non-empty intersection.**
>
>-- [[Probabilistic Graphical Models by Koller]] pp 346

>[!quote]
>An execution of **variable elimination** defines a **cluster graph**: We have a *cluster* for each factor $\psi_{i}$ used in the *computation*, which is associated with the set of variables $C_{i} = Scope[\psi_{i}].$ We draw an *edge* between two clusters $C_i$ and $C_{j}$ if the **message** $\tau_{i}$, produced by *eliminating a variable* in $\psi_{i}$, is used in the computation of $\tau_{j}$.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 346




-----------
##  Recommended Notes and References

- [[Clique Tree and Graph and Running Intersection Property]]

- [[Chord and Chorded Graph]]
- [[Complete Graph Clique and Triangle]]
- [[Hypergraph in Graph Theory]]

- [[Tree Graph and Forest]]
- [[Graph]]


- [[Probabilistic Graphical Models by Koller]] pp 346
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
