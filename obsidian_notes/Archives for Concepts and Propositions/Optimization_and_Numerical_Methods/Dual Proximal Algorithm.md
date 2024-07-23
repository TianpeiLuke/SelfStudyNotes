---
tags:
  - concept
  - optimization/algorithm
keywords:
  - dual_proximal_algorithm
topics:
  - optimization/algorithm
name: Dual Proximal Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Proximal Algorithm

![[Approximation Method for Optimization#^9a898b]]

![[Proximal Algorithm#^258191]]

- [[Proximal Algorithm]]

![[Fenchel Duality Theorem#^0a9d58]]


>[!important] Definition
>Let $f: \mathbb{R}^{n} \to (-\infty, \infty]$ be a **closed convex function**.
>
>In the *proximal algorithm*, at each iteration $k$, $x_{k+1}$ solve the following optimization problem
>$$
>x_{k+1} \in \arg\min_{x\in \mathbb{R}^n}\left\{ f(x) + \frac{1}{2c_{k}}\;\lVert x - x_{k} \rVert^2 \right\}. 
>$$
>Denote $f_{1}(x) = f(x)$ and $f_{2}(x) = \frac{1}{2c_{k}}\;\lVert x - x_{k} \rVert^2$.
>
>**The dual problem** can be written as
>$$
>\begin{align*}
>  \min \;& f_{1}^{*}(\lambda) + f_{2}^{*}(-\lambda) \\
>  \text{s.t. }& \lambda \in \mathbb{R}^{n}
>\end{align*}
>$$
>where $f_{1}^{*}$ and $f_{2}^{*}$ are *Legendre transform* of $f_{1}$ and $f_{2},$ respectively. 
>- We can compute the **convex conjugate** of $f_{2}$ explicitly
>   $$
>  \begin{align*} f_{2}^{*}(\lambda) &= \sup_{x \in \mathbb{R}^n}\left\{ \left\langle  \lambda\,,\, x \right\rangle - f_{2}(x) \right\} \\
>  &=  \sup_{x \in \mathbb{R}^n}\left\{ \left\langle  \lambda\,,\, x \right\rangle - \frac{1}{2c_{k}}\;\lVert x - x_{k} \rVert^2 \right\} \\
>  &= \left\langle  \lambda\,,\, x_{k} \right\rangle + \frac{c_{k}}{2}\lVert \lambda \rVert^2 
>  \end{align*}
>$$
>
>Thus at iteration $k$, the **dual proximal problem** can be written as
>$$
>\begin{align*}
>  \min \;& f^{*}(\lambda) - \left\langle  \lambda\,,\, x_{k} \right\rangle + \frac{c_{k}}{2}\lVert \lambda \rVert^2 \\
>  \text{s.t. }& \lambda \in \mathbb{R}^{n}.
>\end{align*}
>$$

- [[Strongly Convex Function]]
- [[Legendre Transform]]
- [[Fenchel Duality Theorem]]
- [[Lagrange Dual Problem]]
- [[Convex Optimization Problem]]

>[!info]
>Let $\lambda_{k+1}$ be the dual optimal solution. Then by KKT theorem, the **necessary and sufficient conditions** for $(x_{k+1}, \lambda_{k+1})$ are
>- $$\lambda_{k+1} \in \partial f_{1}(x_{k+1})$$
>- $$-\lambda_{k+1} \in \partial f_{2}(x_{k+1})$$ which is equal to $$\lambda_{k+1} = \frac{x_{k} - x_{k+1}}{c_{k}}.$$ This equation can be used for updating the primal solution $$x_{k+1} = x_{k} - c_{k}\;\lambda_{k+1}$$

- [[Karush-Kuhn-Tucker Optimality Condition]]


>[!important] Definition
>Let $f: \mathbb{R}^{n} \to (-\infty, \infty]$ be a **closed convex function**.
>
>The **dual proximal algorithm** solves the *dual proximal problem*. In particular, at each iteration $k$, 
>
>- The **dual variable** $\lambda_{k+1}$ solve the following optimization problem
>$$
>\lambda_{k+1} \in \arg\min_{\lambda \in \mathbb{R}^n}\left\{ f^{*}(\lambda) - \left\langle  \lambda\,,\, x_{k} \right\rangle + \frac{c_{k}}{2}\lVert \lambda \rVert^2 \right\} 
>$$
>where $f^{*}$ is the **convex conjugate** of $f$.
>- Set new update $$x_{k+1} = x_{k} - c_{k}\;\lambda_{k+1}.$$

## Explanation

>[!important]
>The *dual proximal algorithm* solves the **dual problem** of the **proximal optimization**. 
>
>- It first updates *dual variable* $\lambda_{k+1}$ not the primal variable $x_{k+1}$ 
>- It updates the *primal variable* $x_{k+1}$ based on the equation from *KKT optimality condition* $$\lambda_{k+1} \in \partial f_{1}(x_{k+1})$$

>[!info]
>- **Proximal algorithm**: $$x_{k+1} = \text{Prox}(x_{k}) \implies x_{k+1} \in \arg\min_{x\in \mathbb{R}^n}\left\{ f(x) + \frac{1}{2c_{k}}\;\lVert x - x_{k} \rVert^2 \right\}.$$
>- **Dual Proximal algorithm**: $$x_{k+1} = \text{Dual-Prox}(x_{k}) \implies x_{k+1} = x_{k} - c_{k}\;\lambda_{k+1},$$ where $$\lambda_{k+1} \in \arg\min_{\lambda \in \mathbb{R}^n}\left\{ f^{*}(\lambda) - \left\langle  \lambda\,,\, x_{k} \right\rangle + \frac{c_{k}}{2}\lVert \lambda \rVert^2 \right\}$$
>


>[!info]
>$$
>\text{proximal operation }(\text{primal problem}) \iff  \text{dual proximal operation }(\text{primal problem})
>$$



-----------
##  Recommended Notes and References


- [[Approximation Method for Optimization]]
- [[Fenchel Duality Theorem]]

- [[Augmented Lagrangian Algorithm]]
- [[Augmented Lagrangian Function]]
- [[Alternating Direction Method of Multipliers Algorithm]]

- [[Proximal Algorithm]]

- [[Convex Optimization Algorithms by Bertsekas]] pp 234