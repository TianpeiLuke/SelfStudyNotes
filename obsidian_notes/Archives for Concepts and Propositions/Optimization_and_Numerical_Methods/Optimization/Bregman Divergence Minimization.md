---
tags:
  - concept
  - optimization/algorithm
  - optimization/convex_optimization
keywords:
  - bregman_divergence
  - bregman_projection
topics:
  - optimization/algorithm
name: Bregman Divergence Minimization
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Bregman Distance Minimization

![[Bregman Divergence#^b31c31]]

![[Generalized Proximal Method#^8944af]]

>[!important] Definition
>Consider **non-convex** *optimization* problem
>$$
>\min_{x \in \mathbb{R}^{n}} f(x)
>$$
>where $f: \mathbb{R}^{n} \to (-\infty, \infty].$ Let $\psi: \mathbb{R}^{n} \to \mathbb{R}$ be a **convex** function.
>
>The **Bregman divergence minimization algorithm** solves the following problem at each iteration $k$
>$$
> x_{k+1} \in \arg\min_{x\in \mathbb{R}^n}\left\{  f(x) + \frac{1}{c_{k}} \mathbb{D}_{\psi}\left( x \left\|\right. x_{k} \right)\right\}
>$$
>where $\mathbb{D}_{\psi}\left( x \left\|\right. y \right)$ is the **Bregman divergence** associated with $\psi$ between $x_{k}$ and $x$, i.e. $$\mathbb{D}_{\psi}\left( x \left\|\right. x_{k} \right) = \psi(x) - \psi(x_{k}) - \left\langle \nabla \psi(x_{k}) , x - x_{k} \right\rangle$$

^745bcc

- [[Bregman Divergence]]
- [[Generalized Proximal Method]]

## Explanation

>[!example]
>Let $$\psi(x) = \frac{1}{2}\lVert x \rVert_{2}^2$$ Then the *Bregman divergence* associated with $\ell_{2}$ norm is 
>$$
>\begin{align*}
>\mathbb{D}_{\frac{1}{2}\lVert \cdot \rVert_{2}^2}\left( x \left\|\right. x_{k} \right) &= \frac{1}{2}\lVert x \rVert_{2}^2 - \frac{1}{2}\lVert x_{k} \rVert_{2}^2 - \left\langle x_{k} , x - x_{k} \right\rangle \\[5pt]
>&= \frac{1}{2} \lVert x - x_{k} \rVert_{2}^2 
>\end{align*}
>$$
>
>Then the *Bregmann distance minimization* becomes
>$$
> x_{k+1} \in \arg\min_{x\in \mathbb{R}^n}\left\{  f(x) + \frac{1}{2c_{k}} \lVert x - x_{k} \rVert_{2}^2 \right\}
>$$
>which is the **primal proximal algorithm.**

- [[Proximal Algorithm]]

>[!example]
>Let $$\psi_{i}(x^{i}) = \left\{\begin{array}{cc} x^{i}\log x^{i}& \text{ if }x^{i} >0\\[5pt] 0 & \text{ if }x^{i} = 0\\[5pt] \infty & \text{ if }x^{i} < 0\end{array}\right.$$ be *negative entropy* and $$\psi(x) = \sum_{i=1}^{d}\psi_{i}(x^{i})$$ 
>- the gradient $$\nabla \psi_{i}(x^{i}) = \log x^{i} + 1$$
> 
>Then the *Bregman divergence* associated with the *negative entropy* is 
>$$
>\begin{align*}
>\mathbb{D}_{\psi}\left( x \left\|\right. x_{k} \right) &= \sum_{i=1}^{d}\psi_{i}(x^{i}) - \sum_{i=1}^{d}\psi_{i}(x_{k}^{i}) - \left\langle \nabla \psi(x_{k}) , x - x_{k} \right\rangle \\[5pt]
>&= \sum_{i=1}^{d}\left( x^{i}\left[ \log \left( \frac{x^{i}}{x_{k}^{i}}\right) - 1\right]  + x_{k}^{i} \right)
>\end{align*}
>$$
>which is the *Kullback-Leibler divergence*.
>
>Then the *Bregmann distance minimization* becomes
>$$
> x_{k+1} \in \arg\min_{x\in \mathbb{R}^n}\left\{  f(x) + \frac{1}{c_{k}} \sum_{i=1}^{d}\left\{ x^{i}\left[ \log \left( \frac{x^{i}}{x_{k}^{i}}\right) - 1\right]\right\} \right\}
>$$
>which is the **entropy minimization algorithm**.

- [[Kullback-Leibler Divergence]]
- [[Entropy Minimization Algorithm]]

## Majorization-Minimization

>[!important]
>The *Bregman divergence minimization* algorithm above is equivalent to approximately solve the optimization 
>$$\min_{x}\; F(x)$$ where $$F(x) = f(x) - \psi(x)$$ with $\psi$ being **convex.**
>
>The objective of each iteration in *Bregman divergence* is equivalent to a **minorizing surrogate function** 
>$$M_{k}(x, x_{k}) := f(x) - \psi(x_{k}) - \left\langle \nabla \psi(x_{k}) , x- x_{k}  \right\rangle$$
>Thus the algorithm is equivalent to a **majorization-minimizatoin algorithm.**
>$$
>\min_{x} \left\{ f(x) + \mathbb{D}_{\psi}(x \;||\; x_{k}) \right\} \; \iff \; \min_{x} \left\{ M_{k}(x, x_{k}) \right\} 
>$$

- [[Majorization-Minimization Algorithm]]




-----------
##  Recommended Notes and References


- [[Bregman Projection]]

- [[Proximal Algorithm]]



- [[Convex Optimization Algorithms by Bertsekas]] pp 388