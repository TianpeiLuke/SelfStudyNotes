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
>let us limit the optimization to a *subset of distributions* for which both $\mathbb{M}$ and $A^{*}$ are relatively easy to characterize; e.g., perhaps they correspond to a graph with *small treewidth*. 
>
>We refer to any such distribution as "**tractable**." 
>- The simplest choice is the family of **product distributions**, which gives rise to the **naive mean field** method.

- [[Mean Field Approximation for PGM]]
- [[Mean Field Approximation for Exponential Family]]
- [[Mean Field Approximation for Gaussian Markov Random Field]]

### Tractable Family of Distributions

>[!important] Definition
>Consider an *exponential family* $P_{\phi}$ with a collection $\phi = (\phi_{\alpha}, \alpha \in I)$ of *sufficient statistics* associated with the *cliques* of $\mathcal{G} = (\mathcal{V}, \mathcal{E})$.  That is, $$\mathscr{P} := \left\{P_{\phi} \in \mathcal{M}:  P_{\phi} \vDash \mathcal{I}(\mathcal{G}) \right\}$$
>Given a *subgraph* $\mathcal{F} \subset \mathcal{G}$, let $$\mathcal{I}(\mathcal{F}) \subseteq \mathcal{I}(\mathcal{G})$$ be the subset of independence assertions associated with the subgraph. 
>- The corresponding sufficient statistics are associated with the cliques in the sub-graph, which is indexed by $I_{\mathcal{F}} \subset I.$
>
>The **tractable family** is a *set of all distributions* that are *Markov* with respect to $\mathcal{F}$ is a *sub-family* of the full $\phi$-exponential family; $$\mathscr{P}_{\mathcal{F}} := \{ P_{\phi}\in \mathscr{P}: P_{\phi} \vDash \mathcal{I}(\mathcal{F})  \} \subset \mathscr{P}$$
>- it is parameterized by the *subspace of canonical parameters*
>$$
> \begin{align}
> \Omega(\mathcal{F}) := \{\eta \in \Omega: \eta_{\alpha} = 0, \; \forall\, \alpha \in I \setminus I_{\mathcal{F}}\}. 
> \end{align}
>$$  
>- By definition, the exponential family in **tractable family** has some of cliques removed. 

- [[Exponential Family of Distributions]]
- [[Markov Network on Undirected Graph]]
- [[Bayesian Network on Directed Acyclic Graph]]
- [[I-Map and Independence Assertion]]
- [[Cluster Graph and Family Preservation]]

### Mean-Field Approximation of Mean Parameter Space

![[Marginal Polytope and Local Consistent Polytope#^161ed7]]

- [[Maximum Entropy Learning of Exponential Family]]
- [[Marginal Polytope and Local Consistent Polytope]]

>[!important] Definition
>Denote the **maginal polytope** of $\mathcal{G}$ $$\mathbb{M}(\mathcal{G}) := \mathbb{M}(\mathcal{G}; \phi)$$ as the *mean parameter space* for $\phi$-exponential family $P_{\phi}$ on graph $\mathcal{G} = (\mathcal{V}, \mathcal{E})$. 
>
>Given the tractable sub-graph $\mathcal{F}$, these **mean field methods** are based on optimizing over   the *subset of mean parameters* that can be obtained by the *subset of exponential family densities*
>$$
> \begin{align}
> \mathbb{M}_{\mathcal{F}}(\mathcal{G}):= \mathbb{M}_{\mathcal{F}}(\mathcal{G}; \phi) &:= \{\mu \in \mathbb{R}^{d}, \;\; \mathbb{E}_{ \eta }\left[  \phi(X) \right] =  \mu, \;\; \text{ for some }\eta \in \Omega(\mathcal{F}) \} \\[5pt]
> &=  \nabla A_{\Omega_{\mathcal{F}}} 
> \end{align}
>$$  
>- The **interior** of $\mathbb{M}_{\mathcal{F}}(\mathcal{G}; \phi)$ is a *subset of interior* of $\mathbb{M}(\mathcal{G}; \phi)$:
>$$  
> \begin{align*}
> \mathbb{M}_{\mathcal{F}}(\mathcal{G}; \phi)^{\circ}  &\subseteq  \mathbb{M}(\mathcal{G}; \phi)^{\circ}, \quad \forall \mathcal{F} \subseteq \mathcal{G}.
> \end{align*}
>$$  
>- $\mathbb{M}_{\mathcal{F}}$ is an **inner approximation** to the set $\mathbb{M}$ of *realizable mean parameters*. 

### Structured Variational Approach

![[Maximum Entropy Learning for Approximate Inference in PGM#^5fbd75]]



## Explanation


## Examples

>[!info]
>Given the $\phi$-exponential family on graph $\mathcal{G} = (\mathcal{V}, \mathcal{E})$, we can find some of examples of **tractable families**:

>[!example]
>  The **fully factorized** or **product form distributions** on the sub-graph $$\mathcal{F}_{0} = (\mathcal{V}, \emptyset)$$ with all nodes but **no edges**.
>$$ 
> \begin{align}
> P_{\mathcal{F}_{0}}(x; \eta) &= \prod_{s\in \mathcal{V}}P(x_s; \eta_s). 
> \end{align}
>$$ 
>- The *parameter space* of this family of distributions is
>$$
> \begin{align}
> \Omega(\mathcal{F}_{0}) := \{\eta \in \Omega: \eta_{s, t} = 0, \; \forall\, (s, t) \in \mathcal{E} \}, 
> \end{align}
>$$  
>This model is the basis for **naive mean field algorithm**.

- [[Mean Field Approximation for Exponential Family]]
- [[Product Measure]]


>[!example]
> The **tree-structured distributions** on **spanning tree** of $$\mathcal{T}(\mathcal{G}) = (\mathcal{V}, \mathcal{E}(\mathcal{T}))$$
>$$ 
> \begin{align}
> P_{\mathcal{T}}(x; \eta) &= \prod_{s\in \mathcal{V}}P(x_s; \eta_s)\prod_{(s,t)\in \mathcal{E}(\mathcal{T})}P(x_s, x_t; \eta_{s, t}). 
> \end{align}
>$$
> 
>-  The *parameter space* of this family of distributions is
>$$  
> \begin{align}
> \Omega(\mathcal{T}(\mathcal{G})) := \{\eta \in \Omega: \eta_{s, t} = 0, \; \forall\, (s, t) \in \mathcal{E} \setminus \mathcal{E}(\mathcal{T})\},
> \end{align}
>$$  
>which set the *canonical parameters to be zero* for any edge **not in the tree**.

- [[Clique Tree and Graph and Running Intersection Property]]
- [[Spanning Tree and Chord]]


-----------
##  Recommended Notes and References

- [[Mean Field Approximation for PGM]]


- [[Kullback-Leibler Divergence]]
- [[Kullback-Leibler Divergence for Exponential Family]]
- [[Information Projection and Moment Projection]]

- [[Maximum Entropy Learning]]
- [[Evidence Lower Bound]]

- [[Probabilistic Graphical Models]]
- [[Induced Subgraph]]
- [[Graph]]


- [[Probabilistic Graphical Models by Koller]]
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 125 - 147
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
