---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/representation
  - probabilistic_graphical_models/algorithm
  - math/graph_theory
keywords:
  - clique_tree
  - running_intersection_property
  - junction_tree
  - clique_graph
topics:
  - probabilistic_graphical_model
  - math/graph_theory
name: Clique Tree and Running Intersection Property
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Clique Tree (Junction Tree) and Running Intersection Property

>[!important] Definition
>A **clique graph** of a graph $G$ is another graph $K(G)$ that represents the *structure of cliques* in $\mathcal{G}$.
>
>In particular, for $G =(V,E)$, and a set of *maximal cliques* $\mathscr{C} := \left\{ C_{1}, C_{2} \,{,}\ldots{,}\, \right\}$ in the graph,  the **clique graph**  $K(G)$ is a graph such that 
>- each node $v\in V\left( K(G) \right)$ represents a *maximal clique* $C_{v}$
>- each edge $vw \in E\left( K(G) \right)$ indicates that there is an *nonempty intersections* between two maximal cliques $C_{v}$ and $C_{w}$, i.e. $$S_{vw} := C_{v}\cap C_{w} \neq \emptyset.$$
>  
>That is, a *clique graph* $K(G)$ is an **intersection graph** of *maximal cliques* of graph $G$.

- [[Complete Graph Clique and Triangle]]
- [[Minimal and Maximal Property of Graph]]
- [[Set Operations]]

### Clique Tree

>[!important] Definition
>Let $H$ be an undirected graph, and let $C_{1}, C_{2} \,{,}\ldots{,}\,$ be the set of *maximal cliques* in $H.$
>
>The **sepset** between two cliques $C_{i}$ and $C_{j}$ is defined as $$S_{i,j} = C_{i}\cap C_{j}.$$
>
>Let $W_{< (ij)}$ be the set of all *vertices* in $H$ that are on *$C_{i}$ side* of the edge. 


>[!important] Definition
>If the structure of a clique graph $K(G)$ is a *tree*, we called it a **clique tree**, or a **junction tree**.

- [[Tree Graph and Forest]]

>[!important] Definition
>A *tree* $T$ is said to be a **clique tree** (or **junction tree**) for a graph $H$ if
>- each node $v\in V\left( T\right)$ represents a *clique* in $H$, and *each maximal clique* in $H$ is a *node* in $T$.
>- each **sepset** $$S_{i,j} = C_{i} \cap C_{j}$$ **separates** $W_{< (i,j)}$ and $W_{< (j,i)}$,
>	- where $W_{< (i,j)}$  is the set of all variables in the scope of *clusters* in the **$C_{i}$ side** of the tree and 
>	- $W_{< (j,i)}$ is the set of all variables in the scope of clusters in the **$C_j$ side** of the tree.

>[!info]
>If $H$ is a Markov network structure, then each **sepset** in clique tree $S_{i,j}$ renders its *two sides* **conditionally independent**.

### Running Intersection Property

>[!important] Definition
>Let $T$ be a *cluster tree* over a set of factors $\Phi$. We denote by $V(T)$ the vertices of $T$ and $E(T)$ its edges.
>
>We say that $T$ has **running intersection property** if, 
>- whenever there is a variable $X$ such that $X\in C_{i}$, and $X\in C_{j}$, then $X$ is also in *every cluster* in the *unique path* in $T$ between $C_{i}$ and $C_{j}$.  
>  
>  $$X\in C_{i}\cap C_{j} \implies X \in C_{k},\;\; \forall k\in iTj$$

- [[Cluster Graph and Family Preservation]]
- [[Tree-Order Relation]]
- [[Paths in Graph and Length of Path]]


>[!info]
>The running intersection implies that $$S_{i,j} = C_{i} \cap C_{j}$$ is the **unique separation set** between $W_{\lceil i \rceil} - S_{i,j}$ and $W_{\lfloor j \rfloor} - S_{i,j}$ for the underlying Markov network.

- [[Separation in Markov Network]]
- [[Separation of Graph]]

### Clique Tree as Cluster Tree with Running Intersection Property

>[!important] Definition
>Let $\Phi$ be a set of *factors* over $\mathcal{X}$. 
>
>A *cluster tree* over $\Phi$ that satisfies the *running intersection property* is called a **clique tree** (sometimes also called a **junction tree** or a **join tree**). 
>
>In the case of a *clique tree*, the *clusters* are also called **cliques**.

- [[Cluster Graph and Family Preservation]]

## Explanation


## Variable Elimination and Running Intersection Property

>[!important] Theorem
>Let $T$ be a **cluster tree** induced by a **variable elimination algorithm** over some set of factors $\Phi$. 
>
>Then $T$ satisfies the **running intersection property**.

- [[Cluster Graph and Family Preservation]]
- [[Sum-Product Variable Elimination]]
- [[Max-Product Variable Elimination]]

>[!important] Proposition
>Let $T$ be a **cluster tree** induced by a **variable elimination algorithm** over some set of factors $\Phi$. Let $C_{i}$ and $C_{j}$ be two neighboring clusters, such that
>- $C_{i}$ **passes the message** $\tau_{i}$ to $C_{j}$.
>
>Then the **scope** of the message $\tau_{i}$ is precisely $C_{i} \cap C_{j}$, i.e. $$\text{scope}[\tau_{i}] = S_{i,j} = C_{i} \cap C_{j}.$$



>[!important] Theorem
>A *cluster tree* $T$ associated with factors $\Phi$ satisfies the **running intersection property** *if and only if* for every **sepset** $S_{i,j}$, we have that $W_{< (i,j)}$ and $W_{< (j,i)}$ are **separated** in $H_{\Phi}$ given $S_{i,j}$
>  
>- Here $W_{< (i,j)}$  is the set of all variables in the scope of *clusters* in the **$C_{i}$ side** of the tree and 
>- $W_{< (j,i)}$ is the set of all variables in the scope of clusters in the **$C_j$ side** of the tree.






-----------
##  Recommended Notes and References


- [[Chord and Chorded Graph]]
- [[Complete Graph Clique and Triangle]]

- [[Tree Graph and Forest]]
- [[Graph]]

- [[Probabilistic Graphical Models by Koller]] pp 140, 347-348
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 28- 31
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- Wikipedia [Clique_graph](https://en.wikipedia.org/wiki/Clique_graph)
