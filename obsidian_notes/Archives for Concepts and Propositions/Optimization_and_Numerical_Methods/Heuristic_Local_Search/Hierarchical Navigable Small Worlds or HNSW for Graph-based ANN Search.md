---
tags:
  - concept
  - algorithm/search
  - information_retrieval/search
  - information_retrieval/link_analysis
  - statistics/network_analysis
keywords:
  - hnsw_model_graph_ann_search
  - approximate_nearest_neightbor_search
  - graph_based_approximate_nearest_neighbor_search
topics:
  - network_analysis
  - information_retrieval/link_analysis
  - information_retrieval/search
name: 
date of note: 2024-11-30
---

## Concept Definition

>[!important]
>**Name**: Hierarchical Navigable Small Worlds or HNSW for Graph-based ANN Search

>[!important] Definition
>The **Hierarchical Navigable Small Worlds** or **HNSW** is a graph-based *approximate nearest neighbor search algorithm*.

- [[Approximate Nearest Neighbor Search]]

### Navigable Small Word (NSW) Model


- [[Navigable Small World Model and Kleinberg Variant of Watts-Strogatz Model]]
- [[Watts-Strogatz Model for Random Network]]
- [[Small World Graph]]

### Probability Skip Linked List


- [[Skip Linked List and Basic Operations]]



### Hierarchical Navigable Small World



![[hnsm.png]]

### Greedy Search the Nearest Neighbor within Each Layer

>[!important] Definition
>The following algorithm describes a **greedy search algorithm** that returns the $k$ nearest neighbors to some query $q$ in layer $h$ of the **Hierarchical Navigable Small World (HNSW)**
>
>**search-layer(q, ep, k, h)**
>- *Require*: $q\in \mathbb{R}^{d}$ query
>- *Require*: $ep\in \mathbb{R}^{d}$ is the *entry point*
>- *Require*: $k$, number of nearest to $q$ elements to return
>- *Require*: layer number $h$
>- Initialize the set of *visited* element $$V \leftarrow ep$$
>- Initialize the set of *candidates* $$C \leftarrow ep$$
>- Initialize the set of *found nearest neighbors* $$W \leftarrow ep$$
>- While $|C| > 0$:
>	- Retrieve the **nearest element** to $q$ in $C$ $$c = \arg\min_{x\in C}d(x, q)$$
>	- Find the **furthest element** to $q$ in $W$  $$f = \arg\max_{w\in W}d(w, q)$$
>	- If $d(c,q) > d(f,q)$: 
>		- Then $$C \succ W$$ according to distance to $q$, 
>			- $W$ is already the optimal list of nearest neighbors.
>		- *Break*
>	- For each $e\in \mathcal{N}(c)$ in the *direct neighborhood* of $c$ at layer $h$:
>		- if $e\not\in V$ **not visited**:
>			- $$V \leftarrow V \cup \{ e \}$$
>			- Find the **furthest element** to $q$ in $W$, $$f = \arg\max_{w\in W}d(w, q)$$
>			- If $d(e,q) < d(f,q)$ or $|W| < k$:
>				- **Insert** $e$ to $W$ and $C$
>					- $$W \leftarrow W \cup \{ e \}$$
>					- $$C \leftarrow C \cup \{ e \}$$
>				- If $|W| > k$:
>					- **remove furthest element** to $q$ in $W$, $$W \leftarrow W \setminus \{ f \}$$ for $$f = \arg\max_{w\in W}d(w, q)$$
>- *Return*
>	- the $k$-nearest neighbor $W$ in layer $h$,

- [[Greedy Search and Hill Climbing]]
- [[Strict Partial Order Relation]]

### Heuristic Choose of M-Best Neighbors in Candidate List

>[!important] Definition
>The following algorithm choose the **best $M$ neighbors** from the *candidate list*
>- Note that the **simple solution** is to select the *closest elements* to query $q$ in the candidate list.
>- A  **heuristic-based solution** is to examine the candidates *starting from* the *nearest* and *creates* a *connection* to a candidate only if it is closer to the **base element** $q$ as compared to any other *connected elements* 
>  
>  
>**select-neighbors-heuristic(q, C, M, h, extCandidate, keepPruned)**
>- *Require*: the query $q\in \mathbb{R}^{d}$
>- *Require*: the candidate set $C$
>- *Require*: the *number of neighbors* to return as $M$
>- *Require*: the layer number $h$
>- *Require*: the *boolean flag*  **extCandidate** which extends the candidate set
>	- This is useful only when we have *extremely clustered data*
>- *Require*: the *boolean flag* **keepPruned** allows getting *fixed number of connections per element*
>- Initialize the set of *best neighbors* $$R = \emptyset$$
>- Initialize the *queue* of *candidates* $$W = C$$
>- If $\text{extCandidate}=$True
>	- *extend candidate list* by neighbors
>	- for each $e\in C$
>		- for each adjacent node $e_{adj}\in \mathcal{N}(e)$ in layer $h$
>			- if $e_{adj} \not\in W$
>				- $$W \leftarrow W \cup \{ e_{adj} \}$$
>- Set up a *queue* of *discarded candidates* $$W_{d} = \emptyset$$
>- While $|W| > 0$ and $|R| < M$:
>	- Extract the **nearest element** to $q$ in $W$  $$e = \arg\min_{x\in W}d(x, q)$$
>	- If $d(e, q) < \min_{x\in R}(x, q)$, i.e. $e$ is **closer** to $q$ compared to **all of elements** in $R$
>		- Insert $e$ to set $R$, $$R \leftarrow R \cup \{ e \}$$
>	- Else
>		- *Discard* $e$, $$W_{d} \leftarrow W_{d} \cup \{ e \}$$
>- If $\text{keepPruned}=$True:
>	- Add some of *discarded connections*
>	- While $|W_{d}| > 0$ and $|R| < M$:
>		- $$R \leftarrow R \cup \{ e' \}$$ where $$e' = \arg\min_{x\in W_{d}}d(x, q)$$
>- *Return*:
>	- $R$, the set of $M$ best neighbors.

>[!info]
>This is a sub-routine in the *phase 2* of **network construction.**

### Insert Operation

>[!important] Definition
>The following algorithm describes the **construction** of **Hierarchical Navigable Small World (HNSW)**
>- The goal of insert operation is to 
>	- develop multiple layers of nodes 
>	- add $M$ *direct connections* between inserted node and existing node at each layer 
>	- the *direct link* is added according the *nearest neighbor candidate* to *inserted node*.
>- For each new element to be *inserted*, an integer $h$ is  *randomly selected* with **exponentially decaying probability** $$h \sim \lfloor - \log \left(\mathcal{U}(0,1)\right) \rfloor $$
>- The **first phase** starts from the *top layer* to the bottom layer:
>	- At *each layer* $l\le h$, it **greedily** traverses the graph to *find the $k$-nearest neighbor* $W_{l}$
>- When the search phase *reaches* to or *less than* $h$, the **second phase** starts
>	- We increase the number of retrieved element from $1$ to $kConstruct$ to controls the *recall*
>	- Collect the found $k$-nearest neighbor at *each layer* to form a *candidate list* $$C := \bigcup_{l}W_{l}$$
>	- Retrieve the *best* $M$ neighbors to $q$ in the candidate list as $R$
>- The *maximum number of connections* that an element can have per layer is defined by the parameter $M_{max}$
>- If a node is already full at the moment of making of a new connection, then its extended connection list gets *shrunk* by the same algorithm that used for the selection of neighbors



### K-Nearest Neighbor Search

>[!important] Definition
>The **$k$-nearest neighbor search** via **HNSW** is similar to **insert** operation, except for that the terminate layer $h=0$
>- The difference is that the *closest neighbors* found at the **ground layer** which are used as *candidates* for the connections are now **returned** as the search result. 
>- The quality of the search is controlled by the parameter $k$
>  
>  
>**k-nn-search(G, q, k,  dk)**
>- *Require*: $G$ the  **HNSW** graph
>- *Require*: $q\in \mathbb{R}^{d}$ the *query*
>- *Require*: $k$ *nearest neighbors* to $q$ to return
>- *Require*: $dk$, the *size of dynamic candidate list*
>- Initialize current nearest element set $$W = \emptyset$$
>- Retrieve the *entry point* in HNSW as $ep$ at top layer
>- Retrieve the **top layer number** of HNSW as $L$, which also the level for $ep$
>- For $l= L,\, L-1\,{,}\ldots{,}\,1$:
>	- Set dynamic list size as $1$, 
>	- Find **list of nearest neighbor** to $q$ at each layer $$W \leftarrow \text{search-layer}(q, ep, 1, l)$$
>	- Find **nearest neighbor** to $q$ in $W$ as the **entry point** for **next layer** $$ep = \arg\min_{x\in W}d(x, q)$$
>- Search for **$dk$-nearest neighbor** in **bottom layer** $$W \leftarrow \text{search-layer}(q, ep, dk, 0)$$
>- Find the **$k$-nearest neighbor** to $q$ in candidate list $W$ $$R := \text{kNN}(W, q)$$
>- *Return*
>	- $R$



## Explanation

>[!info]
>**HNSW** is a key method for *approximate nearest neighbor search* in **high-dimensional vector databases**, for example in the context of embeddings from neural networks in large language models.

- [[Retrieval Augmented Generation]]
- [[Information Retrieval with Encoder Language Models]]



-----------
##  Recommended Notes and References




- [[FAISS - Facebook AI Similarity Search Tutorial]]
- [[Similarity Search]]
- [[Approximate Nearest Neighbor Search]]
- [[Information Retrieval]]
- [[Graph]]

- [[Networks by Newman]] pp 723

- Youtube
	- [HNSW for Vector Search Explained and Implemented with Faiss](https://www.youtube.com/watch?v=QvKMwLjdK-s)
	- [Graph-Based Approximate Nearest Neighbors (ANN) and HNSW](https://www.youtube.com/watch?v=4PsyNdFlxmk)
	- [Vector Database Search - Hierarchical Navigable Small Worlds (HNSW) Explained](https://www.youtube.com/watch?v=77QH0Y2PYKg&t=96s)
- Malkov, Y. A., & Yashunin, D. A. (2018). Efficient and robust approximate nearest neighbor search using hierarchical navigable small world graphs. _IEEE transactions on pattern analysis and machine intelligence_, _42_(4), 824-836. [[malkovEfficientRobustApproximate2020]]