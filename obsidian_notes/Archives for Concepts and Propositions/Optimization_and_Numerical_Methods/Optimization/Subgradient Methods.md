---
tags:
  - concept
  - optimization/algorithm
keywords:
  - subgradient_methods
topics:
  - optimization/algorithm
name: Subgradient Methods
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Subgradient Methods

>[!important] Definition
>Consider the problem of minimization of a *convex nondifferentiable function* $f: \mathbb{R}^{n} \to \mathbb{R}$. 
>
>The **subgradient method** works as follows
>1. initiate at $x_{0}$
>2. for $k=0,1 \,{,}\ldots{,}\,$:
>	1. choose **sub-gradient direction** $d_{k}$ as $$d_{k} \in \arg\min_{\lVert d \rVert \le 1 }D_{d}\,f(x_{k})$$ where $D_{v}f(x)$ is the *directional derivative* of $f$ at $x$ along $v$.
>	2. choose *stepsize* $\alpha_{k}$
>	3. generate new iterate $$x_{k+1} = x_{k}+ \alpha_{k}\;d_{k}$$ 


- [[Gradient Descent Algorithm]]

## Explanation


## Perceptron

- [[Perceptron Algorithm]]



-----------
##  Recommended Notes and References

- [[Subdifferential of Convex Function]]
- [[Gradient Descent Algorithm]]
- [[Gradient Projection Method]]

- [[Convex Optimization Problem]]

- [[Convex Optimization Algorithms by Bertsekas]] pp 78, 135
- [[Nonlinear Programming by Bertsekas]] pp 620