---
tags:
  - concept
  - optimization/algorithm
  - optimization/theory
  - online_learning/theory
  - online_learning/algorithms
  - optimization/convex_optimization
keywords:
  - online_convex_optimization
topics:
  - convex_analysis
  - online_learning
name: Online Convex Optimization
date of note: 2024-08-07
---

## Concept Definition

>[!important]
>**Name**: Online Convex Optimization

>[!important] Definition
>- Let the *feasible region* $\mathcal{D}$ be a **convex set**, and $\mathcal{Z}$ be a domain set.
>- Define loss function $$\ell: \mathcal{D} \times \mathcal{Z} \to \mathbb{R}$$
>- Assume that $\ell(\cdot, z)$ is a **convex function** for each $z\in \mathcal{Z}$
>
>The general **online convex optimization problem** is described as below:
>- For $t=1 \,{,}\ldots{,}\,T$:
>	- the *optimizer* provides a feasible solution $w_{t}\in \mathcal{D}$
>	- the environment **responds** with $z_{t}\in \mathcal{Z}$
>	- the *optimizer* suffers a **loss** $\ell(w_{t}, z_{t})$
>	  
>	  
>The **goal** of online convex optimization is to **minimize the regret** with respect to a *competing solution* $w^{*}\in \mathcal{D}$. 
>- The **regret** with respect to $w^{*}\in \mathcal{D}$ is defined as $$R_{T}(w^{*}) := \sum_{t=1}^{T}\ell(w_{t}, z_{t}) - \sum_{t=1}^{T}\ell(w^{*}, z_{t})$$
>- The **regret** with respect to the region $\mathcal{D}$ is defined as $$R_{T}(\mathcal{D}) = \sup_{w^{*}\in \mathcal{D}}R_{T}(w^{*})$$

^93e327

- [[Regret for Online Learning]]
- [[No-Regret Learning]]
- [[Incremental Algorithm]]


## Explanation

>[!important]
>Since the regret is **incremental over time**, the solution of online convex optimization is based on **incremental algorithm**.

- [[Incremental Algorithm]]


## Online Gradient Descent

- [[Online Gradient Decent Algorithm]]
- [[Incremental Algorithm]]
- [[Incremental Gradient Algorithm]]
- [[Stochastic Gradient Descent Algorithm]]






-----------
##  Recommended Notes and References


- [[Convex Optimization Problem]]
- [[Convex Set]]
- [[Convex Function]]

- [[Online Learning Perspective for AdaBoost]]

- [[Understanding Machine Learning by Shalev-Shwartz]] pp 257
- [[Online Learning and Online Convex Optimization by Shalev-Shwartz]] pp 120
- [[Introduction to Online Convex Optimization by Hazan]] pp 41


- [[Convex Optimization Algorithms by Bertsekas]]
- [[Convex Optimization by Boyd]]
- [[Numerical Optimization by Nocedal]]
- [[Nonlinear Programming by Bertsekas]]