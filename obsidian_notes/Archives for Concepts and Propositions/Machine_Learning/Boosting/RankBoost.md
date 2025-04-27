---
tags:
  - concept
  - machine_learning/boosting
  - rank_boost
  - learning_to_rank
  - RankBoost
keywords:
  - rank_boost
  - learning_to_rank
topics:
  - machine_learning_models
  - machine_learning_algorithm
  - machine_learning/boosting
name: RankBoost
date of note: 2024-07-30
---

## Concept Definition

>[!important]
>**Name**: RankBoost

>[!important] Definition
>The **RankBoost** algorithm is described as the following:
>- *Require*: a collection of **preference-labeled pairs** $$\left\{ (x_{i}, x_{j}), \; (i,j) \in P \right\}$$ where $x_{i}, x_{j} \in \mathcal{X}$ and $P$ is the set of index pairs with preference relation $x_{i} \succ x_{j}$.
>- **Initialize** with uniform weight distribution over pairs: 
>  $$
>  D_{1}(i,j) = \frac{1}{|P|} \quad \forall (i,j) \in P
>  $$
>- For $t = 1 \,{,}\ldots{,}\,T$:
>	- Train a **weak ranker** using distribution $D_{t}$
>	- Get **weak hypothesis** $$h_{t}: \mathcal{X} \to \mathbb{R}$$ where higher scores indicate preference
>	- Select $h_{t}$ to **minimize the weighted ranking error**
>	  $$
>	  \epsilon_{t} := \sum_{(i,j)\in P} D_{t}(i,j) \, \mathbb{1}\left\{ h_{t}(x_{i}) \leq h_{t}(x_{j}) \right\}
>	  $$
>	- Choose **rate** 
>	  $$
>	  \alpha_{t} = \frac{1}{2}\log\left( \frac{1 - \epsilon_{t}}{\epsilon_{t}} \right)
>	  $$
>	- **Update weights** based on rate $\alpha_{t}$: for all $(i,j) \in P$:
>		- $$
>		\begin{align*}
>		D_{t+1}(i,j) &= \frac{D_{t}(i,j)}{Z_{t}} \times \exp\left( -\alpha_{t}\left( h_{t}(x_{i}) - h_{t}(x_{j}) \right) \right)
>		\end{align*}
>		$$
>		where $Z_{t}$ is the **partition function** (normalization factor) ensuring $\sum_{(i,j)\in P} D_{t+1}(i,j) = 1$.
>
>- *Output* the final **ranking function** as a weighted sum of the weak rankers:
>  $$
>  H(x) = \sum_{t=1}^{T} \alpha_{t} \, h_{t}(x).
>  $$
>- *Prediction*: Given two examples $x_i$ and $x_j$, predict $x_i \succ x_j$ if $H(x_i) > H(x_j)$.


## Explanation





-----------
##  Recommended Notes and References


- [[AdaBoost Algorithm]]



- [[Foundations of Machine Learning by Mohri]] pp 214
- [[Boosting Foundations and Algorithms by Schapire]]  pp 345