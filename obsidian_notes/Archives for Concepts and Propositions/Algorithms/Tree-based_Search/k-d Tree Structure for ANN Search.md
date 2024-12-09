---
tags:
  - concept
  - information_retrieval/index
  - information_retrieval/search
  - algorithm/search
  - algorithm/tree_based_search
  - algorithm/tree
keywords:
  - kd_tree_search
topics:
  - information_retrieval/search
  - algorithmt/tree_based_search
name: k-d Tree Structure for Approximate Nearest Neighbor Search
date of note: 2024-11-29
---

## Concept Definition

>[!important]
>**Name**: k-d Tree Structure for Approximate Nearest Neighbor Search

![[Approximate Nearest Neighbor Search#^fb4fa7]]

- [[Approximate Nearest Neighbor Search]]

>[!important] Definition
>The **$k$-$d$ tree** is a data structure used for *multi-dimensional space partitioning.*
>- It creates a *binary tree* with each node representing a part of the space by *iteratively* dividing the space *along predefined dimensions*.
>	- *Each node* in the binary tree compares points in *one specific dimension*
>- k-d tree *parition* the space into a small number of *box-shaped* cells $C$ as $$\mathcal{X} = \bigcup_{i\in I}C_{i} \subset \mathbb{R}^{k}, \quad C_{i}\cap C_{j} = \emptyset, \quad \forall i,j\in I,$$ each containing only a few representatives from an input set of points.
>	- Each cell $C_{i}$ is defined by $2k$ *half-spaces* where $k$ is the *dimension* of the space $\mathcal{X}$. 
>	- These cells are identified via the *path* from *root* to the corresponding *nodes*, with each half-space defined via the coordinate value of the node along the predefined dimension.
>	- "*$k$-$d$ tree*" means *k-dimensional tree.*
>

- [[Partition of Set]]
- [[Binary Tree Order and Traversal]]

![[kd_tree_partition.png]]



### Construction of k-d Tree

>[!quote]
>Typical algorithms construct **kd-trees** by partitioning point sets. 
>- Each node in the tree is defined by a **plane** cutting through *one of the dimensions*. 
>	- Ideally, this plane partitions the subset of points into *equal-sized left/right* (or up/down) subsets. 
>- These children are again partitioned into *equal halves*, using planes through a *different dimension*. 
>- Partitioning *stops* after $\log(n)$ *levels*, with every point in its own leaf cell. 
>
>The cutting planes along any path from the root to another node defines a **unique box-shaped region** of space. 
>- Each subsequent plane cuts this box into two boxes. 
>- Each box-shaped region is defined by $2k$ planes, where k is the number of dimensions. 
>- Indeed, the “**kd**” in *kd-tree* is short for “**k-dimensional**.” 
>- We maintain the region of interest defined by the intersection of these half-spaces as we move down the tree.
>  
>-- [[Algorithm Design Manual by Skiena]] pp 460  

>[!info]
>Building k-d tree
>- pick random dimension
>- find median
>- split data
>- repeat


>[!important] Definition
>The *recursive* algorithm for **construction of $k$-$d$ tree** is described as follows:
>
 >**kdtree** ($\mathcal{D}$, $h$):
>- *Require*: data set $\mathcal{D} := \{ x_{1} \,{,}\ldots{,}\,x_{n} \} \subset \mathbb{R}^{k}$
>	- Denote each point as $$x_{i} := (x_{i}^{1}\,{,}\ldots{,}\,x_{i}^{k}).$$
>- *Require*: **depth** of **current layer** $h$
>- If $\mathcal{D} = \emptyset$:
>	- Return  `None`
>- Determine the **current dimension** of interest from the *layer depth* as $$d \equiv h \mod k$$
>- **Sort** $\mathcal{D}$ in ascending order according to $d$-th *coordinate value* i.e. for any $i \le j$, $$x_{(i)} \le x_{(j)}\; \iff \; x_{(i)}^{d} \le x_{(j)}^{d}$$
>	- Denote $\mathcal{D}^{(d)}$ as the sorted list via $d$-th *coordinate*
>- *Create* **node** at level $h$
>	- $$\text{node.value}= x_{(i)} \;\;\text{ if }\;\;x_{(i)}^{(d)} = \text{median}(x_{1}^{d} \,{,}\ldots{,}\,x_{n}^{d})$$
>	- Denote $$\mathcal{D}_{\leq}^{(d)} := \left\{ x_{i_{1}} \,{,}\ldots{,}\,x_{i_{m}}\;:\, x_{i_{1}}^{d} \,{\le}\ldots{\le}\, x_{i_{m}}^{d} \le \text{median} \right\} $$ and  $$\mathcal{D}_{>}^{(d)} := \left\{ x_{j_{1}} \,{,}\ldots{,}\,x_{j_{n-m}}\;:\, \text{median} < x_{j_{1}}^{d} \,{\le}\ldots{\le}\, x_{j_{n-m}}^{d}  \right\} $$
>- Construct the **left subtree** by calling the  **kdtree** function via **recursion**
>	- $$\text{node.left}= \text{kdtree}(\mathcal{D}_{\leq}^{(d)}, h+1)$$
>- Construct the **right subtree** by calling the  **kdtree** function via **recursion**
>	- $$\text{node.right}= \text{kdtree}(\mathcal{D}_{>}^{(d)}, h+1)$$
>- Return
>	- $\text{node}$, the reference to the root

- [[Binary Tree Order and Traversal]]
- [[Recursion Algorithm]]

![[kd_tree_example.png]]

### Approximate Nearest Neighbor Search in k-d Tree

>[!important] Definition
>Given a query $q$ and a k-d tree that partitioned the data set $\mathcal{D}$  into cells $$\mathcal{X} = \bigcup_{i\in I}C_{i}, \quad C_{i}\cap C_{j} = \emptyset, \quad \forall i,j\in I,$$ 
>
>The **approximate nearest neighbor search** in **$k$-$d$ tree** can be down by traversing down the hierarchy to find the *smallest cell* containing $q$, and then scan through the objects *in this cell* until we find what we want.
>$$
>x^{(1)} = \arg\min_{x\in \mathcal{D}} d(q, x) \implies  \hat{x}^{(1)} = \arg\min_{x \in C_{i(q)}}\; d(q, x)
>$$
>where $q \in C_{i(q)}.$

>[!important] Definition
>The **approximate nearest neighbor search** via **$k$-$d$ tree** can be seen as a **recursive algorithm** that finds the *smallest cell that contains* $q$ and compares with the minimal distance of points in cell with $q$.
>
>**search(q, node, h, best, min_dist)**:
>- *Require*: the query $q$ $$q := (q^1 \,{,}\ldots{,}\,q^{k})$$
>- *Require*: the *reference* to the *node* of a $k$-$d$ (sub-)tree, $\text{node}$
>- *Require*: the depth of the node
>- *Require*: the *best candidate point* $$\text{best} = x^{*}\in \mathcal{D}$$
>- *Require*: the *minimum distance* $\text{min\_dist}$
>- Determine the *coordinate dimension* for comparison $$d \equiv h \mod k$$
>- If $\text{node}$ is `None`
>	- *Return*
>		- $\text{best}$
>		- $\text{min\_dist}$
>- Compute **distance** from *query* to the node value $$d_{q,n} := d(q\,,\, \text{node.value})$$ 
>	- If $d_{q,n} \le \text{min\_dist}$
>		- *Update* the minimum distance $$\text{min\_dist} \leftarrow d_{q,n}$$
>		- *Update* the best candidate as the node $$\text{best} \leftarrow \text{node.value}$$
>- Compare the *$d$-th coordinate* of the *query* with the corresponding *node value*:
>	- If $q^{d} \le \text{node.value}^{d}$
>		- Search the **left sub-tree** via **recursion** $$(\text{best},\, \text{min\_dist}) \leftarrow \text{search}(q, \text{node.left}, h+1, \text{best}, \text{min\_dist})$$
>		- Compare the **distance** from *query* to **cutting plane** at node along the coordinate $d$, $$r := \text{node.value}^{d} - q^{d}$$
>		- If $r \le \text{min\_dist}$:
>			- *Explore* **right sub-tree** and update the *best solutions* and *minimal distance* $$(\text{best},\, \text{min\_dist}) \leftarrow \text{search}(q, \text{node.right}, h+1, \text{best}, \text{min\_dist})$$
>	- Else, i.e. $q^{d} > \text{node.value}^{d}$
>		-  Search the **right sub-tree** via **recursion** $$(\text{best},\, \text{min\_dist}) \leftarrow \text{search}(q, \text{node.right}, h+1, \text{best}, \text{min\_dist})$$
>		- Find the **distance** from *query* to **cutting plane** at node along the coordinate $d$, $$r := q^{d} - \text{node.value}^{d}$$
>		- If $r \le \text{min\_dist}$:
>			- *Explore* **left sub-tree** and update the *best solutions* and *minimal distance*  $$(\text{best},\, \text{min\_dist}) \leftarrow \text{search}(q, \text{node.left}, h+1, \text{best}, \text{min\_dist})$$
>- *Return* 
>	- $\text{best}$
>	- $\text{min\_dist}$


- [[Greedy Search and Hill Climbing]]

### Insert Operation

>[!important] Definition
>The **insert** operation of k-d tree is described as the **recursion** below
>
>**insert(x, node, h)**
>- *Require*: the value $x\in \mathbb{R}^{k}$ to be inserted to the tree
>- *Require*: node, as the *reference* to the current node
>- *Require*: the current *depth* $h$ of the node
>- Determine the *coordinate dimension* for comparison $$d \equiv h \mod k$$
>- If $\text{node} =$ `None`:
>	- *create* a new node with $$\text{node.value} = x,$$ $$\text{node.left} = \text{node.right}= \text{None}$$
>- Elif $\text{node.value} = x$:
>	- *Return* with duplication warning
>- Elif $x^{d} \le \text{node.value}^{d}$:
>	- Add node to the **left sub-tree** $$\text{node.left} = \text{insert}(x, \text{node.left}, h+1)$$
>- Else i.e. $x^{d} > \text{node.value}^{d}$:
>	- Add node to the **right sub-tree** $$\text{node.right} = \text{insert}(x, \text{node.right}, h+1)$$
>- *Return*: node

### FindMin Operation

>[!important] Definition
>**find_min(d)** function find the point with the *smallest value* in the *$d$-th dimension*.
>
>The **find_min(node, h, cd)** function can be described as follows:
>- *Require*: node, as the reference to current node in the tree
>- *Require*: the current depth $h$
>- *Require*: the current search dimension $cd$
>- If $\text{node}=$`None`: i.e. the sub-tree is empty
>	- Return `None`
>- Determine the *coordinate dimension* for comparison $$d \equiv h \mod k$$
>- If $d = cd$:
>	- Then the **minimum** *cannot be in the* **right subtree**, so search the **left subtree**
>	- If $\text{node.left}=$`None`:
>		- *Return*: node.value.
>	- Else:
>		- *Return*: $$\text{find\_min}(\text{node.left}, h+1, cd)$$
>- Elif $d \neq cd$:
>	- Then the **minimum** can be in **either** subtrees.
>	-  *Return*: $$\min\{\text{node.value},\; \text{find\_min}(\text{node.left}, h+1, cd), \; \text{find\_min}(\text{node.right}, h+1, cd)\}$$



### Deletion Operation


>[!important] 
>In order to **delete** a *node* with corresponding *dimension* $d$ in the tree, we have to find the *node* with **minimal value** *along the dimension* $d$ in the **right subtree**.  $$\text{node-next} = \text{find\_min}(\text{node.right}, h+1, d)$$ This node is the *immediate neighbor* of the deleted node in the tree.
>- We need to **replace** the deleted node with the *immediate next node*.
>- And then *delete* that value in the right sub-tree via **recursive call** of **delete** operation on the right sub-tree.
>
>If the *right subtree is empty*, we find the *minimal value along* $d$ in the **left subtree** $$\text{node-min-left} = \text{find\_min}(\text{node.right}, h+1, d)$$
>- Then *replace* the deleted node with the left minimum
>- And call the deletion process to delete the remaining minimum node in the *left subtree*

>[!important]
>The *recursive* **deletion** operation for k-d tree is described as below
>
>**delete(x, node, h)**
>- *Require*: the value $x\in \mathcal{D}$ to be deleted
>- *Require*: the reference to the current node
>- *Require*: the *current depth*  $h$ of node
>- If $\text{node}=$`None`:
>	- *Return* with error message
>- Determine the *coordinate dimension* for comparison $$d \equiv h \mod k$$
>- If $\text{node.value} = x$, i.e. the node contains value to be deleted
>	- If $\text{node.right}\neq$`None`, i.e the **right subtree nonempty**
>		- *Replace* the value of node to be deleted by the **minimum value** in the **right subtree**. The new node is the *minimum-value in the right tree*. $$\text{node.value} = \text{find\_min}(\text{node.right}, h+1, d)$$
>		- *Recursive* call **delete operation** on the *right sub-tree* $$\text{node.right} = \text{delete}(\text{node.value},\, \text{node.right}, h+1)$$
>	- Elif $\text{node.left}\neq$`None`, i.e the **left subtree nonempty**
>		- *Replace* the value of node to be deleted by the **minimum value** in the **left subtree**; effectively, this **swap** *left subtree* with the *right subtree* $$\text{node.value} = \text{find\_min}(\text{node.left}, h+1, d)$$
>		- *Recursive* call **delete operation** on the *new right sub-tree* $$\text{node.right} = \text{delete}(\text{node.value},\, \text{node.left}, h+1)$$
>	- Else, i.e. no subtrees then delete directly
>		- $$\text{node} = None$$
>- Else, if current node value does **not match deleted value**
>	- If $x^{d} \le \text{node.value}^{d}$
>		- Search node to be deleted to the *left subtree* and *delete* it $$\text{node.left} = \text{delete}(x, \text{node.left},\, h+1)$$
>	- Else
>		- Search node to be deleted to the *right subtree* and *delete* it  $$\text{node.right} = \text{delete}(x, \text{node.right},\, h+1)$$
>- *Return*
>	- node.
 



## Explanation

>[!important]
>The search complexity is the equivalent to the **height** of the search tree
>- In the **worst-case** the tree would essentally be a linked list and the height would be $$O(n).$$
>- In the **best case** it would be *well-balanced* and the height would be $$O(\log n)$$
>  
>For $d$-dimensional space, the complexity is $$O(d \log(n))$$  

- [[Algorithm Big-O Notations and Rate of Growth]]

>[!info]
>The **$k$-$d$ tree** can be seen as a variant of **coordinate descent algorithm** which minimize the distance between candidate and query by looping over the *coordinate dimensions.*

- [[Block Coordinate Descent Algorithm]]


## Variants of k-d Tree

- [[Ball Tree Structure for ANN Search]]


## Other ANN Search 

- [[Locality-Sensitive Hashing or LSH for ANN Search]]
- [[Hierarchical Navigable Small Worlds or HNSW for Graph-based ANN Search]]




-----------
##  Recommended Notes and References


- [[Binary Tree Order and Traversal]]
- [[Information Retrieval]]
- [[Similarity Search]]
- [[Tree Graph and Forest]]
- [[k Nearest Neighbor Classification]]
- [[k Nearest Neighbor Density Estimation]]



- [[Introduction to Algorithms by Cormen]]
- [[Algorithm Design Manual by Skiena]] pp 460 - 463, 638 - 647


- Notes
	- [UMD course note on SG-KD-Tree](https://www.cs.umd.edu/class/fall2019/cmsc420-0201/Handouts/sg-kd-tree.pdf)
	- [UMD Matth kd-trees](https://www.math.umd.edu/~immortal/CMSC420/notes/kdtrees.pdf)
	- [CMU Course note kdtrees](https://www.cs.cmu.edu/~ckingsf/bioinfo-lectures/kdtrees.pdf)
- Wikipedia [K-d_tree](https://en.wikipedia.org/wiki/K-d_tree)
- Youtube 
	- [KD-Tree Nearest Neighbor Data Structure](https://www.youtube.com/watch?v=Glp7THUpGow)
	- [KD tree algorithm: how it works](https://www.youtube.com/watch?v=TLxWtXEbtFE)
	- [Tutorial 5: K-NN Part 7 KD-Trees](https://www.youtube.com/watch?v=oQQrxiJvnhw)
	- [kNN.15 K-d tree algorithm](https://www.youtube.com/watch?v=Y4ZgLlDfKDg)
- Medium
	- [Ball tree and KD Tree Algorithms](https://medium.com/@geethasreemattaparthi/ball-tree-and-kd-tree-algorithms-a03cdc9f0af9)
	- [A look into K-Dimensional Trees](https://medium.com/smucs/a-look-into-k-dimensional-trees-290ec69dffe9)