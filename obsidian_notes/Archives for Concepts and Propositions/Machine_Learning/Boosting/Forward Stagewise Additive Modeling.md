---
tags:
  - concept
  - machine_learning/boosting
  - machine_learning/models
  - machine_learning/algorithms
  - statistics/estimation
keywords:
  - additive_modeling
  - greedy_algorithm
topics: 
name: Forward Stagewise Additive Modeling
date of note: 2024-08-01
---

## Concept Definition

>[!important]
>**Name**: Forward Stagewise Additive Modeling

>[!important] Definition
>Consider the problem of estimation of an **additive model**
>$$
>f(x) = \sum_{t=1}^{T}\beta_{t}\,b(x; \gamma_{t})
>$$
>where $\beta_{t}, t=1 \,{,}\ldots{,}\,T$ are the *expansion coefficients*, and $b(x; \gamma_{t})\in \mathcal{Y}$. 
>
>Given data $\left\{(x_{i}, y_{i}), \; i=1 \,{,}\ldots{,}\,m\right\}$ in domain $\mathcal{X}\times \mathcal{Y}$, the **estimation** problem can be formulated as the *loss minimization problem* 
>$$
>\min_{\left\{ \beta_{t}, \gamma_{t} \right\}_{1}^{T}}\;\sum_{i=1}^{m}L\left( y_{i},\, \sum_{t=1}^{T}\,\beta_{t}\,b(x_{i}; \gamma_{t}) \right)
>$$
>where $L: \mathcal{Y} \times \mathcal{Y} \to \mathbb{R}_{+}$

### Forward Stagewise Additive Modeling

>[!info] Definition
>**Forward stagewise modeling** approximates the solution by **sequentially** adding new basis functions to the expansion *without adjusting* the parameters and coefficients of those that have already been added.
>
>At each iteration $t$, one solves for the *optimal basis function* $b(x; \gamma_{t})$, and corresponding *coefficient* $\beta_{t}$ to add to the current expansion $f_{t-1}(x)$.


>[!important] Definition
>The **Forward stagewise additive modeling** solves the optimization problem
>$$
>\min_{\left\{ \beta_{t}, \gamma_{t} \right\}_{1}^{T}}\;\sum_{i=1}^{m}L\left( y_{i},\, \sum_{t=1}^{T}\,\beta_{t}\,b(x_{i}; \gamma_{t}) \right)
>$$
>via the following **greedy algorithm**:
>- *Require*: a collection of **labeled data** $\left\{ (x_{i}, y_{i}), \; i=1 \,{,}\ldots{,}\, m\right\}$ where $x_{i}\in \mathcal{X}$ and $y_{i}\in \mathcal{Y}$
>- *Initialize*: $f_{0} = 0$.
>- For $t= 1 \,{,}\ldots{,}\,T:$
>	- $$(\beta_{t}, \gamma_{t}) \in \arg\min_{(\beta, \gamma)}\left\{ \sum_{i=1}^{m}L\left( y_{i},\, f_{t-1}(x_{i}) +\, \beta\,b(x_{i};\, \gamma) \right)\right\} $$
>	- Update $$f_{t}(x) = f_{t-1}(x) + \beta_{t}\,b(x;\,\gamma_{t})$$
>- *Output*: $F_{T}.$

## Explanation

>[!info]
>The additive model $$f(x) = \sum_{t=1}^{T}\beta_{t}\,b(x; \gamma_{t})$$ can be seen as an expansion of $f$ by basis $\left\{ b(\cdot; \gamma):  \gamma \in \Gamma \right\}$



## AdaBoost

>[!info]
>When the loss function is the **exponential loss**, we have AdaBoost algorithm.


![[Exponential Loss Minimization for AdaBoost#^8d14db]]

- [[Exponential Loss Minimization for AdaBoost]]
- [[AdaBoost Algorithm]]



-----------
##  Recommended Notes and References



- [[Exponential Loss Minimization for AdaBoost]]
- [[AdaBoost Algorithm]]

- [[Statistical Estimation Problem]]

- [[Incremental Algorithm]]
- [[Incremental Gradient Algorithm]]
- [[Incremental Aggregated Gradient Algorithm]]


- [[Elements of Statistical Learning by Hastie]] pp 342 - 343
- [[Boosting Foundations and Algorithms by Schapire]]