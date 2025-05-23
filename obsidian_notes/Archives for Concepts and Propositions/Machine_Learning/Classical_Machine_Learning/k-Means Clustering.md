---
tags:
  - concept
  - machine_learning/models
  - machine_learning/clustering
  - k_mean_clustering
  - unsupervised_learning
keywords:
  - k_means_clustering
  - unsupervised_learning
topics:
  - machine_learning_algorithm
  - machine_learning_theory
name: k-Means Clustering
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: k-Means Clustering

>[!important] Definition
>Let $\mathcal{D} := \{ x_{1} \,{,}\ldots{,}\, x_{m}\} \in \mathbb{R}^d$ be $m$ samples. Denote $d$ as the Euclidean metric $$d(x_{i}, x_{j}) = \lVert x_{i} - x_{j} \rVert_{2}.$$  Assume that $\mathcal{D}$ is *partitioned* into $k$ *mutual exclusive clusters* $$C_{1} \,{,}\ldots{,}\,C_{k}$$ so that each sample is assigned to *one of the cluster*. That is, define the **assignment map** $$\sigma: i \mapsto s\in [k] \text{ when }x_{i} \in C_{s}$$
>
>Define the **within-point scatter** as 
>  $$
>  \begin{align*}
> W(\sigma) &= \frac{1}{2}\sum_{s=1}^{k}\sum_{\sigma(i) = s}\sum_{\sigma(j) = s}\lVert x_{i} - x_{j} \rVert_{2}^2 \\[5pt]
> &= \sum_{s=1}^{k}\,N_{s} \sum_{\sigma(i) = s} \lVert x_{i} - \mu_{s} \rVert_{2}^2 \\[5pt]
> &= \sum_{i=1}^{m} \lVert x_{i} - \mu_{\sigma(i)} \rVert_{2}^2 
>\end{align*}
>$$
>where $N_{s}$ is the number of samples assigned to $C_{s}$, and  $\mu_{s}$ is the **mean vector** associated with $s$-th cluster $C_{s}$ $$\mu_{s} = \frac{1}{N_{s}}\sum_{\sigma(i) = s}x_{i}.$$
>
>The **goal** is to find **optimal assignment** $\sigma^{*}$ that *minimize the within-point scatter*
>$$
>\min_{\sigma}\;  \frac{1}{2}\sum_{s=1}^{k}\sum_{\sigma(i) = s}\sum_{\sigma(j) = s}\lVert x_{i} - x_{j} \rVert_{2}^2
>$$



>[!important] Definition
>The **k-means clustering algorithm** is an *iterative descent algorithm* for solving
>$$
>\min_{\sigma}\;  \frac{1}{2}\sum_{s=1}^{k}\sum_{\sigma(i) = s}\sum_{\sigma(j) = s}\lVert x_{i} - x_{j} \rVert_{2}^2 = \sum_{s=1}^{k}\,N_{s} \sum_{\sigma(i) = s} \lVert x_{i} - \mu_{s} \rVert_{2}^2 
>$$
>
>The algorithm is described as follow:
>- *Require*: the number of cluster $k$
>- *Require*: a set of observations $\{ x_{1} \,{,}\ldots{,}\,x_{m} \}$
>- *Randomly* choosing $k$ *observations* with index $\{ r_{1} \,{,}\ldots{,}\, r_{k} \} \subset [m]$ 
>- *Initialize assignment as* $$\sigma^{(1)}(r_{s}) = s,\quad s=1\,{,}\ldots{,}\,k$$
>- For $t=1\,{,}\ldots{,}\,$ until convergence
>	- Solving the following optimization problem for $k$ **cluster mean vectors** $\{ \mu_{1}^{(t)} \,{,}\ldots{,}\,\mu_{k}^{(t)} \}$ given **assignment** $\sigma^{(t)}$,     $$(\mu_{1}^{(t)} \,{,}\ldots{,}\,\mu_{k}^{(t)}) = \arg\min_{\mu_{i}, i=1\,{,}\ldots{,}\,k}\sum_{s=1}^{k}\,N_{s} \sum_{\sigma^{(t)}(i) = s} \lVert x_{i} - \mu_{s} \rVert_{2}^2 $$
>		- For $s=1\,{,}\ldots{,}\,k$
>			- The *optimal mean vector* can be obtained as $$\mu_{s}^{(t)}  = \frac{1}{N_{s}}\sum_{\sigma^{(t)}(i) = s}x_{i}.$$
>	- Find the **optimal assignment** by solving the following problem given $k$ **mean vectors** $\{ \mu_{1}^{(t)} \,{,}\ldots{,}\,\mu_{k}^{(t)} \}$,  $$\sigma^{(t+1)} = \arg\min_{\sigma} \sum_{s=1}^{k}\,N_{s} \sum_{\sigma(i) = s} \lVert x_{i} - \mu_{s}^{(t)} \rVert_{2}^2 $$
>		- The optimal assignment is to assign each observation to the **closest (current) cluster mean**. That is, for each $i\in [m]$ $$\sigma^{(t+1)}(i) = s\; \text{  if  }\lVert x_{i} - \mu_{s}^{(t)}\rVert_{2} \le \lVert x_{i} - \mu_{p}^{(t)}\rVert_{2},\; \forall p \neq s$$


## Explanation

>[!quote]
>The K-means algorithm is one of the most popular **iterative descent clustering** methods.
>
>--  [[Elements of Statistical Learning by Hastie]] pp 509

>[!info]
>The assignment map $\sigma$ can be characterized by a **many-to-one mapping**, or **encoder** $$k = \sigma(i),$$ that assigns the $i$th observation to the $k$th cluster.
>
>The Euclidean metric characterizes the **dissimilarity** between observations.

>[!info]
>*k-means* algorithm is an **approximation algorithm** to solve the NP-hard optimal assignment problem.

- [[NP Hard Complexity Class and Problems]]
- [[Greedy Heuristic Algorithms]]


## Variants





## Applications

### Vector Quantization


### Information Retrieval and Index Compression

- [[Inverted File Index for ANN Search]]
- [[Product Quantization for ANN Search and Index Compression]]




## Optimal Assignment Problem and Wasserstein Distance

>[!quote]
>The $k$-means objective function is quite popular in practical applications of clustering. However, it turns out that finding the **optimal k-means solution** is often computationally infeasible (the problem is **NP-hard**, and even **NP-hard** to *approximate to within some constant*). As an alternative, the following simple iterative algorithm is often used, so often that, in many cases, the term **k-means Clustering** refers to the *outcome* of this algorithm rather than to the clustering that *minimizes the $k$-means objective cost*.
>
>-- [[Understanding Machine Learning by Shalev-Shwartz]] pp 270

>[!important]
>The k-mean problem is a **special case** of the optimal assignment problem when the **cost** is defined as the **squared Euclidean distance**
>$$
>\min_{\sigma}\;  \sum_{i} d^2(x_{i}, \mu_{\sigma(i)})
>$$
>
>The optimal value of the k-mean objective is close related to **the $2$-Wasserstein distance** $$\mathcal{W}_{2}^2(\alpha_{x}, \beta_{\mu})$$ where two discrete measures $$\alpha_{x} = \sum_{i=1}^{m}\delta_{x_{i}},\;\; \beta_{\mu} = \sum_{s=1}^{k}\,N_{s}\,\delta_{\mu_{s}}$$

^5944a3

- [[Optimal Assignment Problem and Monge Problem]]
- [[Wasserstein Distance]]
- [[Discrete Measure]]





-----------
##  Recommended Notes and References



- [[Elements of Statistical Learning by Hastie]] pp 460, 509–514
- [[Understanding Machine Learning by Shalev-Shwartz]] pp 268 - 271
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 922