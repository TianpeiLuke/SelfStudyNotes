---
tags:
  - concept
  - online_learning/theory
  - online_learning/algorithms
  - machine_learning/online_learning
keywords:
  - mirror_descent_algorithm
  - exponential_weights_algorithm
topics:
  - online_learning
  - machine_learning_algorithm
name: Exponential Weights Algorithm via Mirror Descent
date of note: 2024-08-06
---

## Concept Definition

>[!important]
>**Name**: Exponential Weights Algorithm via Mirror Descent

![[Exponential Weights Algorithm for Convex Loss#^05f7e9]]

![[Mirror Descent Algorithm#^1b2c18]]


>[!important] Definition
>The **exponential weights algorithm (EWA)** is equivalent to a **mirror descent algorithm** that solves the following **online optimization problem** at each iteration $t=1\,{,}\ldots{,}\,T$
>$$
>w_{t} \in \arg\min_{w \in \Delta_{k}}\left\{ \sum_{s=1}^{t}\left\langle w , \ell_{s} \right\rangle  + \frac{1}{\eta}\,\mathbb{KL}\left( w \left\|\right. w_{1} \right) \right\}
>$$
>where 
>- $w_{t} := (w_{1}^{(t)} \,{,}\ldots{,}\,w_{k}^{(t)}) \in \Delta_{k}$ is a **normalized weight**.
>- $w_{1} := \frac{1}{k}(1 \,{,}\ldots{,}\,1)$ is the uniform distribution
>- $\ell_{t} := \left( \ell_{1,t} \,{,}\ldots{,}\, \ell_{k,t} \right)$ are losses for all $k$ *experts*.


^9a4b7d

- [[Generalized Proximal Method]]
- [[Online Mirror Descent Algorithm]]
- [[Entropy Minimization Algorithm]]
- [[Kullback-Leibler Divergence]]
- [[Incremental Algorithm]]


>[!important]
>The solution of above **online convex optimization problem** is 
>$$
>w_{i}^{(t)} = \frac{w_{i}^{(1)}\,\exp \left( -\eta \sum_{s=1}^{t-1}\,\ell_{i, s} \right)}{\sum_{i=1}^{k}w_{i}^{(1)}\,\exp \left( -\eta \sum_{s=1}^{t-1}\,\ell_{i, s} \right)}
>$$
>The **incremental update** is
>$$
>w_{i}^{(t)} = \frac{w_{i}^{(t-1)}\,\exp \left( -\eta\, \ell_{i, t-1} \right)}{\sum_{i=1}^{k}w_{i}^{(t-1)}\,\exp \left( -\eta\, \ell_{i, t-1} \right)},
>$$
>which is the **exponentially weighted update**.

- [[Generalized Proximal Method]]
- [[Convex Optimization Problem]]


## Explanation


![[Weighted Average Forecast via Potential#^668a02]]




-----------
##  Recommended Notes and References


- [[Mirror Descent Algorithm]]
- [[Online Gradient Decent Algorithm]]
- [[Exponential Weights Algorithm for Convex Loss]]
- [[Weighted Average Forecast via Potential]]
- [[Prediction with Expert Advice]]

- [[Kullback-Leibler Divergence]]

- [[Mirror Descent Algorithm]]
- [[Generalized Proximal Method]]
- [[Bregman Divergence Minimization]]


- Blog [Gradient Descent as Exponential Weights](https://blog.wouterkoolen.info/GDasEW/post.html)
- [[Online Learning and Online Convex Optimization by Shalev-Shwartz]] pp 143  - 144
- [[Introduction to Online Convex Optimization by Hazan]] pp 60