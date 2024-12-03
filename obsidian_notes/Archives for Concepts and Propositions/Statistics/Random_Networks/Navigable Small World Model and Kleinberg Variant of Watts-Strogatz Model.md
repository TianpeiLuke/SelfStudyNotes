---
tags:
  - concept
  - algorithm/search
  - information_retrieval/search
  - statistics/network_analysis
  - information_retrieval/link_analysis
keywords:
  - navigable_small_world_model
  - nsw_model_search
  - kleinberg_variant
  - watts_strogatz_model
  - small_world_model
topics:
  - algorithm/search
  - network_analysis
  - information_retrieval/search
  - information_retrieval/link_analysis
name: Navigable Small World Model and Kleinberg Variant of Watts-Strogatz Model
date of note: 2024-11-30
---

## Concept Definition

>[!important]
>**Name**: Navigable Small World Model and Kleinberg Variant of Watts-Strogatz Model

### Degree Distribution 

>[!important] Definition
>Let $\mathcal{V}$ be a set of $n$ nodes. 
>
>A *tree* $\mathcal{T}$ is defined as follows:
>- each level of the tree $\mathcal{T}$ has $b > 2$ *branches*
>- and the tree has $n$ *leaves (terminal nodes)* which corresponds to the nodes.
>- Thus $$b^{h(\mathcal{T})} = n \implies h(\mathcal{T}) = \log_{b}(n)$$ where $h(\mathcal{T})$ is the *depth (height)* of the tree $\mathcal{T}$.
>  
>The **primary distance metric** $D_{\mathcal{T}}: \mathcal{V}\times \mathcal{V} \to \mathbb{R}_{+}$ between nodes $i$ and $j$ is defined as 
>- the *depth (height)* of *smallest subtree* that *contains* $i$ and $j$  $$D_{\mathcal{T}}(i,j) := \min\left\{h(\mathcal{T}_{\alpha}): \mathcal{T}_{\alpha} \subset \mathcal{T},\; i\in V(\mathcal{T}_{\alpha}),\, j\in V(\mathcal{T}_{\alpha})  \right\} $$  
>- or, equivalently, the **half** of the **distance** between $i,j\in \mathcal{T}$  $$D_{\mathcal{T}}(i,j) = \frac{1}{2}D(i,j; \mathcal{T})$$ where $D$ is the *shortest path distance* on $\mathcal{T}$. 

- [[k-d Tree Structure for Approximate Nearest Neighbor Search]]
- [[Paths in Graph and Length of Path]]
- [[Trails in Directed Graph]]


>[!important] Definition
>An algorithm for searching to find a *directed path* from node $i$ to node $j$ is **decentralized** if 
>- it only uses information about the *identities of the neighbors* of $i$ 
>- and their *location* as *leaves in the tree*, 
>- and the *location* of node $j$ as a *leaf in the tree*.

>[!important] Definition
>The *search time* is called **poly-logarithmic** if 
>- there exists $\gamma >0$ for which any two randomly selected nodes $s, t\in \mathcal{X}$ are *connected* by a *directed path* of *length* *at most* $O([\log(n)]^{\gamma})$ with a probability at least $1 - \epsilon$.
>
>There exists $\gamma >0$ such that for any $\epsilon >0$, and any *uniformly selected* $s,t\in \mathcal{X}$, 
>$$
>\mathcal{P}\left\{d(s,t) > C\,\left[ \log(n) \right]^{\gamma}  \right\} \le \epsilon
>$$
>- We say the *outdegree* $d$ of a sequence of random networks indexed by $n$ is **poly-logarithmic** if there exists $\gamma$ such that the degree $$d \propto  (\log(n))^{\gamma}$$

- [[Basic Inequalities and Cramér–Chernoff Method]]

>[!important] Theorem (by Kleinberg)
>Let $\mathcal{V}$ be a set of $n$ nodes. A *tree* $\mathcal{T}$ is defined as follows:
>- each level of the tree $\mathcal{T}$ has $b > 2$ **branches**
>- and the tree has $n$ *leaves (terminal nodes)* which corresponds to the nodes, i.e. $$h(\mathcal{T}) = \log_{b}(n)$$
>
>- Denote the **primary distance metric** between two nodes $i$ and $j$ in $\mathcal{V}$ via the tree $\mathcal{T}$ as $D_{\mathcal{T}}(i,j)$
>
>
>Consider a sequence, indexed by $n$, of *random networks* $G_{n}$ formed on $n$ nodes $$V(G_{n}) = \mathcal{V}$$  based on a group structure as described below:
>- Each node $i\in V(G_{n})$ forms $d$ **directed links**, $$\{ (i,j_{1}) \,{,}\ldots{,}\, (i,j_{d}) \}$$
>	- where the other end $j_{s}$ is chosen *independently at random* with probability $$p(j_{s}) = b^{-\alpha\,D_{\mathcal{T}}(i,j)}, \quad \forall j_{s}\in \mathcal{V}$$
>
>Then
>- If $$\alpha = 1,$$ and $$d \ge c\left(\log_{b}(n)\right)^2$$ for some $c >0$, then there *exists* a **decentralized algorithm** for which the *search time* is **poly-logarithmic** with exponent $1$
>- If $$\alpha \neq 1,$$  then there is **no poly-logarithmic degree** for which there exists a *decentralized algorithm* with a *search time* that is *poly-logarithmic.*

- [[Tree Graph and Forest]]
- [[Social Economic Networks by Jackson]] pp 279


### Kleinberg Variant of Small World Model


- [[Watts-Strogatz Model for Random Network]]
- [[Greedy Search and Hill Climbing]]




## Explanation


>[!important] 
>The **time complexity** of searching $k$ nearest neighbor in the graph of $n$ nodes is $$O(\log^k(n))$$

## Extension

- [[Hierarchical Navigable Small Worlds or HNSW for Graph-based ANN Search]]


-----------
##  Recommended Notes and References


- [[Approximate Nearest Neighbor Search]]

- [[FAISS - Facebook AI Similarity Search Tutorial]]

- [[Similarity Search]]
- [[Information Retrieval]]
- [[Random Graph]]
- [[Graph]]

- [[Sum-Product Belief Propagation Algorithm for Clique Tree]]
- [[Sum-Product Belief-Update Message Passing Algorithm for Clique Tree]]
- [[Neural Message Passing Algorithm for Graph Neural Network]]

- [[Networks by Newman]] pp 64, 718 -723
- [[Social Economic Networks by Jackson]] pp 268 - 283


- Malkov, Y., Ponomarenko, A., Logvinov, A., & Krylov, V. (2012). Scalable distributed algorithm for approximate nearest neighbor search problem in high dimensional general metric spaces. In _Similarity Search and Applications: 5th International Conference, SISAP 2012, Toronto, ON, Canada, August 9-10, 2012. Proceedings 5_ (pp. 132-147). Springer Berlin Heidelberg.
- Malkov, Y., Ponomarenko, A., Logvinov, A., & Krylov, V. (2014). Approximate nearest neighbor algorithm based on navigable small world graphs. _Information Systems_, _45_, 61-68.
- Boguna, M., Krioukov, D., & Claffy, K. C. (2009). Navigability of complex networks. _Nature Physics_, _5_(1), 74-80.
- Kleinberg, J. M. (2000). Navigation in a small world. _Nature_, _406_(6798), 845-845.
