---
tags:
  - concept
  - machine_learning/models
  - machine_learning/theory
  - machine_learning/classification
keywords:
  - k_nearest_neighbor
  - k_nearest_neighbor_classification
topics:
  - machine_learning_models
  - machine_learning_theory
name: k Nearest Neighbor Classification
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: k Nearest Neighbor Classification

![[Empirical Risk Minimization#^a84128]]


>[!important] Definition
>Let $\mathcal{D} := \left\{ (X_{i}, Y_{i}) \right\}_{i=1\,{,}\ldots{,}\,n}$ be a set of $n$ training samples, where 
>- $Y_{i}\in \{ 0,1 \}$
>- $X_{i} \in \mathcal{X}$ with metric $d: \mathcal{X} \times \mathcal{X} \to [0, \infty)$.
>
>**The $k$-Nearest Neighbor Rule** for $k \in [n]$ is defined by
>$$
> \begin{align*}
> h_n(x) &= \left\{\begin{array}{cl}
> 1 & \sum_{i=1}^{n}w_{n,i}\mathbb{1}\{Y_i = 1\} > \sum_{i=1}^{n}w_{n,i}\mathbb{1}\{Y_i = 0\}\\[5pt]
> 0 & \text{otherwise}
> \end{array}
> \right.
> \end{align*}
>$$ 
>where 
>$$
>w_{n,i} = \left\{\begin{array}{cl} \dfrac{1}{k} & \text{ if } d(x, X_{i}) \le d(x, X^{(k)}) \\[5pt] 0 & \text{ otherwise} \end{array}\right.
>$$
> 
>- $X_i$ is said to be **the $k$-th nearest neighbor** $X^{(k)}$ of $x$ if the distance $d(x,X_i)$ is the *$k$-th smallest* among $d(x,X_1) \,{,}\ldots{,}\, d(x,X_n)$  
>- In case of a *distance tie*, the candidate with the smaller index is said to be closer to $x$. 
>- The decision is based upon a **majority vote**. 
>- It is convenient to let $k$ be *odd*, to avoid voting ties. 

- [[Order Statistics]]
- [[Metric Space]]
- [[Empirical Risk Minimization]]
- [[Characteristic Function of Set]]



## Explanation


## Theory


## Implementation via Approximate Nearest Neighbor Search

- [[Approximate Nearest Neighbor Search]]
- [[k-d Tree Structure for Approximate Nearest Neighbor Search]]
- [[Locality-Sensitive Hashing or LSH for Approximate Nearest Neighbor Search]]

- [[Navigable Small World Model and Kleinberg Variant of Watts-Strogatz Model]]
- [[Hierarchical Navigable Small Worlds or HNSW for Graph-based ANN Search]]




-----------
##  Recommended Notes and References


- [[Empirical Risk Minimization]]
- [[Statistical Decision Problem]]
- [[PAC Learnable and Agnostic PAC Learnable]]
- [[Classification Problem]]


- [[Elements of Statistical Learning by Hastie]] pp 463
- [[Understanding Machine Learning by Shalev-Shwartz]] pp 219- 220
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1008
- [[Probabilistic Theory of Pattern Recognition by Devroye]] pp 61 - 83
