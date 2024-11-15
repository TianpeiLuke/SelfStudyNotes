---
tags:
  - concept
  - optimization/algorithm
  - optimization/convex_optimization
keywords:
  - entropy_minimization
  - entropy_regularization
topics:
  - optimization/algorithm
name: Entropy Minimization Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Entropy Minimization Algorithm

![[Generalized Proximal Method#^8944af]]

>[!important] Definition
>Consider **non-convex** *optimization* problem
>$$
>\min_{x \in \mathbb{R}^{n}} f(x)
>$$
>where $f: \mathbb{R}^{n} \to (-\infty, \infty]$.
>
>The **entropy minimization algorithm** or **entropic regularized minimization algorithm** solves the following problem at each iteration $k$
>$$
> x_{k+1} \in \arg\min_{x\in \mathbb{R}^n}\left\{ f(x) + \frac{1}{c_{k}}D_{k}(x, x_{k}) \right\} 
>$$
>where $D_{k}$ is the **unnormalized Kullback-Leibler divergence**, i.e. $$D_{k}(x, x_{k}) := \sum_{i=1}^{n}x^{i}\left(\log \left(\frac{x^{i}}{x_{k}^{i}}\right) - 1\right) := \sum_{i=1}^{n}x_{k}^{i}\;\phi \left(\frac{x^{i}}{x_{k}^{i}}\right)$$
>- The **unnormalized entropy function** $\phi$ is defined as $$\phi(x) = \left\{\begin{array}{cl} x(\log(x) - 1) &\text{ if } x>0 \\[5pt] 0 &\text{ if }x =0\\[5pt] +\infty & \text{ if }x <0 \end{array}\right.$$

- [[f-Divergence]]
- [[Kullback-Leibler Divergence]]
- [[Generalized Proximal Method]]

## Explanation



## Bregman Divergence Minimization

![[Bregman Divergence Minimization#^745bcc]]

- [[Bregman Divergence Minimization]]
- [[Bregman Divergence]]


## Applications

### Optimal Transport

- [[Entropic Regularized Optimal Transport in Discrete Settings]]
- [[Sinkhorn Algorithm for Entropy Regularized Optimal Transport]]

### Maximum Entropy Reinforcement Learning

- [[Maximum Entropy Reinforcement Learning]]
- [[Soft Actor-Critic Algorithm]]




-----------
##  Recommended Notes and References



- [[Kullback-Leibler Divergence]]
- [[Shannon Entropy]]
- [[Phi Entropy Functional]]

- [[Entropic Regularized Optimal Transport in Discrete Settings]]



- [[Majorization-Minimization Algorithm]]
- [[Mirror Descent Algorithm]]


- [[Convex Optimization Algorithms by Bertsekas]] pp 383
- [[Nonlinear Programming by Bertsekas]] pp 553
- [[Introduction to Online Convex Optimization by Hazan]] pp 136