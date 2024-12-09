---
tags:
  - concept
  - machine_learning/algorithms
  - probabilistic_graphical_models/models
  - probabilistic_graphical_models/algorithm
  - probabilistic_graphical_models/inference
keywords:
  - max_product
  - message_passing
  - clique_tree
topics:
  - probabilistic_graphical_model
name: Max-Product Message Passing for Clique Tree
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Max-Product Message Passing for Clique Tree

### Computing the Max-Marginals

>[!important]
>In the same way that we used **dynamic programming** to modify the sum-product variable elimination algorithm to the case of clique trees, we can also modify the **max-product algorithm** to define a **max-product belief propagation algorithm** in clique trees.

- [[Sum-Product Belief Propagation Algorithm for Clique Tree]]

>[!important] Algorithm
>The **MP-Message** subprocedure is described as
>- *Require*: $i$, the *sending* clique index
>- *Require*: $j$, the *receiving* clique index
>- *Multiplies** all **incoming messages** from its **other neighbors** with its *initial clique potential* $$\psi(C_{i}) = \psi_{i}\,\cdot\prod_{k\in (N(i) - j)}\delta_{k\to i}$$
>- *Sum out* all variables **except** those in the **sepset** between $C_{i}$ and $C_{j}$ $$\tau(S_{i,j}) = \max_{C_{i} \setminus S_{i,j}}\psi(C_{i})$$
>- *Return* **message** $\tau(S_{i,j})$

>[!important] Algorithm
>The **Max-Product Belief Propagation Algorithm** for **Clique Tree** is described as 
>- *Require*: $\Phi$, the set of *factors*
>- *Require*: $T$, the **clique tree** over $\Phi$
>- *Require*: $\alpha$, the initial *assignment* of *factors to cliques*
>- **Initialize** all the cliques:
>	- for each clique $C_{i}$:
>		- $$\psi_{i}(C_{i}) = \prod_{\alpha(\phi_{s}) = i}\phi_{s}.$$
>- While exists neighboring $i,j$ such that $C_{i}$ is **ready** to transmit to $C_{j}$.
>	- Call **Sum-Product Message Passing** subprocedure and update message from $i$ to the neighbor $j$ **sepset** $$\delta_{i \to j}(S_{i, j}) = \text{MP-Message}(i, j)$$
>- For each clique $i$:
>	- Update the **belief** $$\beta_{i} = \psi_{i}\,\cdot\prod_{k\in N(i)}\delta_{k\to i}$$ 
>- *Return*: *all beliefs* $\{ \beta_{i}, i\in V(T) \}$

- [[Topological Sorting]]

>[!info]
>As for sum-product message passing, the algorithm will **converge** after a single **upward and downward pass**. After those steps, the resulting clique tree $T$ will contain the appropriate **max-marginal** in every *clique*.

>[!important] Proposition
>Consider a run of the **max-product clique tree algorithm**, where we initialize with a set of factors $\Phi$. Let $\beta_{i}$ be a set of beliefs arising from the **upward** and **downward pass** of this algorithm.
>
>Then for each clique $C_{i}$, and each assignment $c_{i}$ to $C_{i}$, we have that $$\beta_{i}(c_{i}) = \text{MaxMarg}_{\hat{\mathcal{P}}_{\Phi}}(c_{i})$$
>That is, the **clique belief** contains, for *each assignment* $c_{i}$ to the clique variables, the *(unnormalized) measure*  $\hat{P}_{\Phi}$ of the **most likely assignment** $\xi$ **consistent** with $c_{i}$.

>[!important] Definition
>Because max-product message passing over a clique tree produces **max-marginals** in *every clique*, and because **max-marginals must agree**, it follows that any two adjacent cliques must **agree on their sepset**:
>$$
> \max_{C_{i} \setminus S_{i,j}}\beta_{i} = \max_{C_{j} \setminus S_{i,j}}\beta_{j} = \mu_{i,j}(S_{i,j})
>$$
>In this case, the clusters are said to be **max-calibrated**.

- [[Clique Tree Calibration]]

>[!important] Corollary
>The beliefs in a clique tree resulting from an upward and downward pass of the **max-product clique tree algorithm** are **max-calibrated.**


## Explanation

- [[Dynamic Programming Algorithms]]



-----------
##  Recommended Notes and References

- [[Max-Product Variable Elimination]]
- [[Max-Product Belief Update for Clique Tree]]

- [[Clique Tree and Graph and Running Intersection Property]]
- [[Tree-Order Relation]]
- [[Root and Rooted Tree]]
- [[Tree Graph and Forest]]


- [[Probabilistic Graphical Models by Koller]] pp 562
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 409
