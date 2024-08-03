---
tags:
  - concept
  - machine_learning/algorithms
  - probabilistic_graphical_models/algorithm
keywords:
  - sum_product
  - message_passing
  - clique_tree
topics:
  - probabilistic_graphical_model
name: Sum-Product Message Passing Algorithm for Clique Tree
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Sum-Product Message Passing Algorithm Analysis for Clique Tree

![[Sum-Product Belief Propagation Algorithm for Clique Tree#^d4e300]]

![[Sum-Product Belief Propagation Algorithm for Clique Tree#^1e148a]]

### Correctness

>[!important] Proposition
>Assume that $X$ is **eliminated** when a message is sent from $C_{i}$ to $C_{j}$.
>
>Then $X$ does **not appear** anywhere in the tree on $C_{j}$ **side** of the **edge** $ij\in E(T)$.

- [[Sum-Product Belief Propagation Algorithm for Clique Tree]]
- [[Clique Tree and Graph and Running Intersection Property]]
- [[Paths in Graph and Length of Path]]

>[!important] Definition
>Let $T$ be a *rooted clique tree*, and  $ij\in E(T)$.  Denote $\le$ as a *tree-order* from *root* to *leave* i.e.
>$$
> k \leq i \iff C_{k} \in C_{r}-C_{i}\text{ path in }E(T).
>$$
>Define $\alpha(k)$ as the clique index for factor $\phi_{k}$.
>
>- Denote the set of *factors* in the *cliques* on the $C_{i}$-side of the edge as $$\Phi_{\lceil i \rceil } := \left\{ \phi_{k}: \alpha(k)\le i \right\}. $$
>- Denote the set of *variables* that appears on the $C_{i}$-side but *not in sepset* $S_{i,j}$ as $$\mathcal{V}_{\lceil i \rceil}:= \{ X_{p}: X_{p} \in \text{scope}[\phi_{m}],\; \alpha(m) \le i,\; X_{p} \not\in S_{i,j} \}$$
>  

- [[Tree-Order Relation]]

>[!info]
>Intuitively, the message $\delta_{i\to j}$ is the product of all factors in $\Phi_{\lceil i \rceil }$, and then marginalized over the variables in the *sepset* $S_{i,j}$  

>[!important] Theorem
>Let $\delta_{i\to j}$  be the **message** from $C_{i}$ to $C_{j}$.
>
>Then 
>$$
> \delta_{i\to j}(S_{i,j}) = \sum_{\mathcal{V}_{\lceil i \rceil }}\prod_{\phi \in \Phi_{\lceil i \rceil }}\phi
>$$

>[!important] Corollary
>Let $C_{r}$ be the *root clique* in a clique tree, and assume that $\beta_{r}$ is computed as in the **sum-product message passing algorithm**.
>
>Then 
>$$
>\beta_{r}(C_{r}) = \sum_{\mathcal{X} \setminus C_{r}}\,\hat{\mathcal{P}}_{\Phi}(\mathcal{X}).
>$$


>[!important] Corollary
>Assume that, for each clique $i$, $\beta_{i}$ is computed as in the **sum-product belief propagation algorithm**.
>
>Then 
>$$
>\beta_{i}(C_{i}) = \sum_{\mathcal{X} \setminus C_{i}}\,\hat{\mathcal{P}}_{\Phi}(\mathcal{X}).
>$$


## Explanation

>[!info]
>a **sepset** divides the *graph* into **conditionally independent pieces**. 
>
>It is this conditional independence property that allows the **message over the sepset** to **summarize completely** the information in *one side of the clique tree* that is necessary for the computation in the other.





-----------
##  Recommended Notes and References


- [[Clique Tree and Graph and Running Intersection Property]]
- [[Root and Rooted Tree]]
- [[Paths in Graph and Length of Path]]

- [[Tree Graph and Forest]]

- [[Bayesian Network on Directed Acyclic Graph]]
- [[Markov Network on Undirected Graph]]


- [[Probabilistic Graphical Models by Koller]] pp 353- 355
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 24
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
