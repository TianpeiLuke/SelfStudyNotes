---
tags:
  - concept
  - machine_learning/algorithms
  - probabilistic_graphical_models/algorithm
keywords:
  - sum_product
  - message_passing
  - clique_tree
  - belief_propagation
  - dynamic_programming
  - rule_based_variable_elimination
topics:
  - probabilistic_graphical_model
name: Rule-based Sum-Product Belief Propagation
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Rule-based Sum-Product Belief Propagation

![[Sum-Product Belief Propagation Algorithm for Clique Tree#^c3b4f5]]

### Product for Rule-based CPD via Rule Split and Product






### Sum-Product Message Passing for Rule-based CPD


>[!important] Algorithm
>The **SP-Message** subprocedure is described as
>- *Require*: $i$, the *sending* clique index
>- *Require*: $j$, the *receiving* clique index
>- *Multiplies** all **incoming messages** from its **other neighbors** with its *initial clique potential* $$\psi(C_{i}) = \psi_{i}\,\cdot\prod_{k\in (N(i) - j)}\delta_{k\to i}$$
>- *Sum out* all variables **except** those in the **sepset** between $C_{i}$ and $C_{j}$ $$\tau(S_{i,j}) = \sum_{C_{i} \setminus S_{i,j}}\psi(C_{i})$$
>- *Return* **message** $\tau(S_{i,j})$


### Asynchronous Sum-Product Message Passing



>[!important] Algorithm
>The **(Asynchronous) Sum-Product Message Passing Algorithm** for **Clique Tree** is described as 
>- *Require*: $\Phi$, the set of *factors*
>- *Require*: $T$, the **clique tree** over $\Phi$
>- *Require*: $\alpha$, the initial *assignment* of *factors to cliques*
>- **Initialize** all the cliques:
>	- for each clique $C_{i}$:
>		- $$\psi_{i}(C_{i}) = \prod_{\alpha(\phi_{s}) = i}\phi_{s}.$$
>- While exists neighboring $i,j$ such that $C_{i}$ is **ready** to transmit to $C_{j}$.
>	- Call **Sum-Product Message Passing** subprocedure and update message from $i$ to the neighbor $j$ **sepset** $$\delta_{i \to j}(S_{i, j}) = \text{SP-Message}(i, j)$$
>- For each clique $i$:
>	- Update the **belief** $$\beta_{i} = \psi_{i}\,\cdot\prod_{k\in N(i)}\delta_{k\to i}$$ 
>- *Return*: *all beliefs* $\{ \beta_{i}, i\in V(T) \}$


## Explanation





-----------
##  Recommended Notes and References


- [[Rule-based Variable Elimination in Graphical Model]]
- [[Local Probabilistic Models]]

- [[Sum-Product Belief Propagation Algorithm for Clique Tree]]
- [[Clique Tree and Graph and Running Intersection Property]]
- [[Tree Graph and Forest]]

- [[Bayesian Network on Directed Acyclic Graph]]
- [[Markov Network on Undirected Graph]]


- [[Probabilistic Graphical Models by Koller]] pp  329 - 334, 

