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
>- **HNSW** graphs are among the top-performing indexes for *vector similarity search*
>- 

- [[Similarity Search]]
- [[Approximate Nearest Neighbor Search]]

>[!info]
>We can split [ANN algorithms](https://www.pinecone.io/learn/what-is-similarity-search/) into three distinct categories; 
>- trees, 
>- hashes, 
>- and graphs. 
>
>HNSW slots into the _graph_ category. More specifically, it is a **proximity graph**, in which two vertices are linked based on their **proximity** (closer vertices are linked) — often defined in Euclidean distance.
>
>There is a significant leap in complexity from a _‘proximity’_ graph to _‘hierarchical navigable small world’_ graph. We will describe two fundamental techniques that contributed most heavily to HNSW: 
>- the **probability skip list**, 
>- and **navigable small world graphs**.

### Probability Skip Linked List

>[!important] Definition
>The **probability skip list** allows fast search like a *sorted array*, while using a *linked list* structure for easy (and fast) *insertion* of new elements (something that is not possible with sorted arrays).
>
>To search a skip list, 
>- we start at the *highest layer* with the *longest* _‘skips’_ 
>- and move along the *edges* towards the *right* (below).
>- If we find that the current node ‘key’ is _greater than_ the key we are searching for 
>	- — we know we have *overshot* our target, so we move *down* to *previous node* in the _next_ level.


![[prob_skip_list.png]]

- [[Skip Linked List and Basic Operations]]

### Navigable Small Word (NSW) Model

>[!info] 
>The idea of **Navigable Small Word (NSW) graph** is that
>- if we take a *proximity graph* but build it so that we have both **long-range** and **short-range links**, 
>	- then search times are reduced to **(poly/)logarithmic complexity**.
>	

>[!info]
>When *searching* an NSW graph, we begin at a pre-defined _entry-point_. 
>- This entry point connects to *several nearby vertices*. 
>- We identify which of these vertices is the *closest to our query vector* 
>- and *move* there.	  
>  
>We repeat the _greedy-routing search_ process of moving from vertex to vertex by identifying the nearest neighboring vertices in each friend list. 
>- Eventually, we will find *no nearer vertices* than our current vertex — this is a *local minimum* and acts as our stopping condition.  
>- The *efficiency of greedy routing* breaks down for *larger networks* (1-10K+ vertices) when a graph is *not navigable*


![[greedy_routing_nsw.png]]

- [[Navigable Small World Model and Kleinberg Variant of Watts-Strogatz Model]]
- [[Watts-Strogatz Model for Random Network]]
- [[Small World Graph]]


### Hierarchical Navigable Small World


![[hnsw.png]]



![[hnsw_search.png]]

### Greedy Search / Routing the Nearest Neighbor within Each Layer

>[!info] 
>The following algorithm describes a **greedy search algorithm** that returns the $k$ nearest neighbors to some query $q$ in layer $h$ of the **Hierarchical Navigable Small World (HNSW)**
>- This step corresponds to the *greedy routing* in **Navigable Small World (NSW)**

>[!quote]
>The _routing_ (literally the route we take through the graph) consists of *two phases*. 
>- We start with the **“zoom-out” phase** where we pass through *low-degree vertices* (degree is the number of links a vertex has)
>- and the later **“zoom-in” phase** where we pass through *higher-degree vertices*。
>  
>Our _stopping condition_ is finding **no nearer vertices** in our current vertex’s friend list. 
>- Because of this, we are more likely to hit a **local minimum** and stop too early when in the _zoom-out_ phase (fewer links, less likely to find a nearer vertex).  
>  
>To minimize the probability of stopping early (and increase recall), we can **increase the average degree** of vertices, but this *increases network complexity* (and *search time*). 
>- So we need to **balance** the average degree of vertices between recall and search speed.  
>  
>-- [Pinecone: Hierarchical Navigable Small Worlds (HNSW)](https://www.pinecone.io/learn/series/faiss/hnsw/)  

![[hnsw_high_degree_low_degree.png]]

>[!quote]
>Another approach is to start the search on high-degree vertices (**zoom-in first**). 
>- For NSW, this _does_ improve performance on low-dimensional data. We will see that this is also a significant factor in the structure of HNSW.
>
>-- [Pinecone: Hierarchical Navigable Small Worlds (HNSW)](https://www.pinecone.io/learn/series/faiss/hnsw/)  


>[!important] Definition
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
>			- There is no **nearer points** to $q$ than *current points* in $W$ 
>			- Thus $W$ is already the optimal list of nearest neighbors.
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

>[!info]
>In **search-layer**, we *traverse* through the graph by searching the *nearest neighbor* in the candidate list $C$, and then *expand* the candidate list by adding the **neighboring node** of **nearest neighbor** in the candidate list
>$$
> c=\text{NN}(C) \implies e\in \mathcal{N}(c) \stackrel{e \text{ closer}}{\implies} C \leftarrow C\cup \left\{ e \right\} \implies c=\text{NN}(C) \,{\implies}\ldots{}\,
>$$



### Heuristic Choose of M-Best Neighbors in Candidate List

>[!info] 
>The following algorithm choose the **best $M$ neighbors** from the *candidate list* to build connections.
>- Note that the **simple solution** is to select the *closest elements* to query $q$ in the candidate list.
>- A  **heuristic-based solution** is to examine the candidates starting from the *nearest* and *creates* a *connection* to a candidate only if it is *closer* to the **base element** $q$ as compared to *any other* connected elements 
>- This is used in **graph / index construction**
>  

>[!important] Definition
>**select-neighbors-simple(q, C, M)**
>- *Require*: the query $q\in \mathbb{R}^{d}$
>- *Require*: the candidate set $C$
>- *Require*: the *number of neighbors* to return as $M$
>- *Return* $$R = \left\{ x^{(1)} \,{,}\ldots{,}\, x^{(M)}\right\}, \quad x^{(i)} = \arg\min_{x \in C \setminus\, \left\{x^{(j)}, j\le i-1 \right\} }d(x, q)$$ as $M$-nearest neighbor in $C$ to $q$


>[!important] Definition
>**select-neighbors-heuristic(q, C, M, h, extCandidate, keepPruned)**
>- *Require*: the query $q\in \mathbb{R}^{d}$
>- *Require*: the candidate set $C$
>- *Require*: the *number of neighbors* to return as $M$
>- *Require*: the layer number $h$
>- *Require*: **extCandidate**, the *boolean flag*  that extends the candidate set
>	- This is useful only when we have *extremely clustered data*
>- *Require*: **keepPruned**, the *boolean flag* that  allows getting *fixed number of connections per element*
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

>[!info] Definition
>The following algorithm describes the **construction** of **Hierarchical Navigable Small World (HNSW)**
>- The goal of insert operation is to 
>	- develop multiple layers of nodes 
>	- add $M$ *direct connections* between inserted node and existing node at each layer 
>	- the *direct link* is added according the *nearest neighbor candidate* to *inserted node*.
>- For each new element to be *inserted*, an integer $h$ is  *randomly selected* with **exponentially decaying probability** $$h \sim \lfloor - \log \left(\mathcal{U}(0,1)\right) \rfloor $$
>- The creators of HNSW found that the **best performance** is achieved when we **minimize the overlap** of *shared neighbors* across layers. 
>	- _Decreasing m_L_ can help *minimize overlap* (pushing more vectors to _layer 0_), 
>	- but this *increases the average number* of traversals during search. 
>	- So, we use an _m_L_ value which *balances* both.
>	- _A rule of thumb_ for this _optimal value_ is `1/ln(M)`.

>[!info]
>- The **first phase** starts from the *top layer* to the bottom layer:
>	- At *each layer* $l\le h$, it **greedily** traverses the graph to *find the $1$-nearest neighbor* $W_{l}$
>- The **second phase** starts when the search phase *reaches* to or *less than* $h$,  
>	- We increase the number of retrieved element from $1$ to `efConstruct` to controls the *recall*
>	- Collect the found `efConstruct`-nearest neighbor to $q$ at *each layer* to form a *candidate list* to **build directional connection** to $q$
>	- Retrieve the *best* $M$ neighbors to $q$ in the candidate list as $R$

>[!info]
>- The *maximum number of connections* that an element can have per layer is defined by the parameter $M_{max}$
>- If a node is already full at the moment of making of *a new connection*, then its *extended connection list* gets **shrunk** by the same algorithm that used for the selection of neighbors


>[!important] Definition
>**insert(G, q, M, M_max, efConstruct, m_L)**
>- *Require*: $G$, the **HNSW** graph
>- *Require*: $q\in \mathbb{R}^{d}$ the *new element* to be inserted
>- *Require*: $M$  the *number of best neighbors* to return from candidate list
>- *Require*: $M_{max}$, *maximum number of connections* that an element can have *per layer* (i.e. the max degree)
>- *Require*: $\text{efConstruct}$, the size of *dynamic candidata list*
>-  *Require*: $m_{L}$, the *normalization factor* for *level generation*
>- Initialize the set of *current found nearest elements* $$W = \emptyset$$ 
>- Retrieve the *entry point* in HNSW as $ep$ at top layer
>- Retrieve the **top layer number** of HNSW as $L$, which also the level for $ep$
>- Randomly **generate level number** to insert the new element $q$, $$h\sim \lfloor - \log(\mathcal{U}(0,1)) \cdot m_{L} \rfloor $$
>- *(Phase 1)* For $l=L,\,(L-1) \,{,}\ldots{,}\, (h+1)$:
>	- **Greedy search** the **nearest elements** to $q$ at layer $l$ $$W \leftarrow \text{search-layer}(q, ep, 1, l)$$
>	- Find **nearest neighbor** to $q$ in $W$ as the **entry point** for **next layer** $$ep = \arg\min_{x\in W}d(x, q)$$
>- *(Phase 2)* For $l = \min\left\{ L, h \right\}\,{,}\ldots{,}\,0$:
>	- **Greedy search** the `efConstruct`-**nearest elements** to $q$ at layer $l$ $$W \leftarrow \text{search-layer}(q, ep, \text{efConstruct}, l)$$
>	- Retrieve the **best $M$ neighbors** to $q$ within retrieved list $W$, $$R \leftarrow \text{select-neighbors}(q, W, M, l)$$
>		- We can call the function **select-neighbors-heuristic** or **select-neighbors-simple**
>	- Add **birectional connection** from points in $R$ to $q$ at *layer* $l$
>		- Build a *proximity graph* at layer $l$
>	- The following steps **shrink connections** if needed
>	- For each $e\in R$:
>		- Retrieve all neighboring points to $e$ at layer $l$ $$\text{eConn} = \mathcal{N}_{l}(e)$$
>		- If $|\text{eConn}| > M_{max}$
>			- Then **shrink connections** by selecting *best $M_{max}$ neighbors* $$\text{eNewConn} \leftarrow \text{select-neighbors}(q, \text{eConn}, M_{max}, l)$$
>				- We can call **select-neighbors-heuristic** or **select-neighbors-simple**
>			- Set the *new neighborhood* of $e$ $$\mathcal{N}(e) \leftarrow \text{eNewConn}$$
>				- Prune directional links from $(\text{eConn} \setminus\, \text{eNewConn})$ to $q$
>	- Set the list of *entry point* for *next layer* as the `efConstruct`-*nearest element* $$ep \leftarrow W$$
>- If $h > L$
>	- Set the *entry point* of the *HNSW* as the new element $q$.
>		- New element is inserted in a new top layer.




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
>	- Equivalently, call the **select-neighbors-simple** function $$R \leftarrow \text{select-neighbors-simple}(q, W, k)$$
>- *Return*
>	- $R$



## Explanation

>[!info]
>**HNSW** is a key method for *approximate nearest neighbor search* in **high-dimensional vector databases**, for example in the context of embeddings from neural networks in large language models.

- [[Retrieval Augmented Generation]]
- [[Information Retrieval with Encoder Language Models]]

### Time Complexity

>[!quote]
>The **complexity scaling** of a single search can be strictly analyzed under the assumption that we build the exact **Delaunay graphs** instead of the approximate ones. 
>- Suppose we have found the closest element on some layer (this is guaranteed by having the Delaunay graph) and then descended to the next layer. 
>- One can show that the **average number of steps** before we find the closest element in the layer is *bounded by a constant*. 
>
>Indeed, the element levels are drawn randomly, so when traversing the graph there is a fixed **probability** $$p = \exp(m_{L})$$ that the *next node belongs to the upper layer*.
>- However, the search on the layer always *terminates before* it reaches the element which belongs to the *higher layer* (otherwise the search on the upper layer would have stopped on a different element), 
>- so the **probability** of *not reaching the target* on $s$-th step is *bounded* by $$\exp(-s\,m_{L})$$
>- Thus the **expected number of steps** in a layer is *bounded* by a sum of *geometric progression* $$S = \frac{1}{1 - \exp(-m_{l})},$$ independent of the dataset size. 
>
>If we assume that in the limit of the infinite dataset size $N\to \infty$ the **average degree** of a node in the **Delaunay graph** is capped by a constant $C$ (this is the case for random Euclid data [48], but can be in principle violated in exotic spaces), 
>- then the **overall average number of distance** evaluations in a layer is *bounded* by a constant $$C\cdot S,$$ independent of the dataset size. 
>- And since the **expectation of the maximum layer index** by the construction scales as $$O(\log(N)),$$ 
>	- the **overall complexity scaling** is $$O(\log(N)),$$ in agreement with the simulations on low dimensional datasets.
>
>--  Malkov, Y. A., & Yashunin, D. A. (2018). Efficient and robust approximate nearest neighbor search using hierarchical navigable small world graphs. _IEEE transactions on pattern analysis and machine intelligence_, _42_(4), 824-836. [[malkovEfficientRobustApproximate2020]]

### Memory Cost

>[!quote]
>HNSW is not the best index in terms of memory utilization. However, if this is important and using [another index](https://www.pinecone.io/learn/series/faiss/vector-indexes/) isn’t an option, we can improve it by compressing our vectors using [product quantization (PQ)](https://www.pinecone.io/learn/series/faiss/product-quantization/). Using PQ will reduce recall and increase search time — but as always, much of ANN is a case of balancing these three factors.
>
>If, instead, we’d like to improve our search speeds — we can do that too! All we do is add an IVF component to our index. There is plenty to discuss when adding **IVF** or **PQ** to our index, so we wrote an [entire article on mixing-and-matching of indexes](https://www.pinecone.io/learn/series/faiss/composite-indexes/).
>
>-- [Pinecone: Hierarchical Navigable Small Worlds (HNSW)](https://www.pinecone.io/learn/series/faiss/hnsw/)

![[hnsw_memory.png]]





-----------
##  Recommended Notes and References




- [[FAISS - Facebook AI Similarity Search Tutorial]]
- [[Similarity Search]]
- [[Approximate Nearest Neighbor Search]]
- [[Indexing or Index Construction for Information Retrieval]]
- [[Information Retrieval]]
- [[Graph]]

- [[Networks by Newman]] pp 723

- Blog
	- [Pinecone: Hierarchical Navigable Small Worlds (HNSW)](https://www.pinecone.io/learn/series/faiss/hnsw/)
	- [Pinecone: vector similarity search](https://www.pinecone.io/learn/what-is-similarity-search/)
- Youtube
	- [HNSW for Vector Search Explained and Implemented with Faiss](https://www.youtube.com/watch?v=QvKMwLjdK-s)
	- [Graph-Based Approximate Nearest Neighbors (ANN) and HNSW](https://www.youtube.com/watch?v=4PsyNdFlxmk)
	- [Vector Database Search - Hierarchical Navigable Small Worlds (HNSW) Explained](https://www.youtube.com/watch?v=77QH0Y2PYKg&t=96s)
- Malkov, Y. A., & Yashunin, D. A. (2018). Efficient and robust approximate nearest neighbor search using hierarchical navigable small world graphs. _IEEE transactions on pattern analysis and machine intelligence_, _42_(4), 824-836. [[malkovEfficientRobustApproximate2020]]