---
tags:
  - concept
  - optimization/algorithm
keywords:
  - augmented_lagrangian_algorithm
topics:
  - optimization/algorithm
name: Augmented Lagrangian Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Augmented Lagrangian Algorithm

>[!important] Definition
>Consider the *convex optimization problem* with *equality constraint*
>$$
>\begin{align*}
>  \min_{x \in \mathcal{X}}\;& f(x) \\
>  \text{s.t. }& Ax = b
>\end{align*}
>$$
>where $f: \mathbb{R}^n \to \mathbb{R}$ is a *proper convex function*, $\mathcal{X}$ is a *convex set*, and $A\in \mathbb{R}^{m \times n}$, $b\in \mathbb{R}^{m}.$
>
>The **augmented Lagrangian function** is defined as
>$$
>L_{c}(x, \lambda) = f(x) + \left\langle  \lambda\,,\, Ax - b \right\rangle + \frac{c}{2}\lVert Ax - b \rVert^2 
>$$
>for $x\in \mathbb{R}^{n}$ and $\lambda \in \mathbb{R}^{m}$
>
>The major steps of the **augmented Lagrangian method** or **augmented Lagrangian method of multipliers** are as follows:
>- at iteration $k$, 
>	- update the *primal variables* by solving $$x_{k+1} \in \arg\min_{x \in \mathcal{X}}L_{c_{k}}(x, \lambda_{k})$$
>	- update the *dual variables* $$\lambda_{k+1} = \lambda_{k} + c_{k}\left(Ax_{k+1} - b\right)$$

- [[Augmented Lagrangian Function]]
- [[Convex Optimization Problem]]
- [[Legendre Transform]]
- [[Lagrangian Dual Function]]


## Explanation


>[!info]
>For the convex program with **inequality constraint**
>$$
>\begin{align*}
>  \min_{x \in \mathcal{X}}\;& f(x) \\
>  \text{s.t. }& Ax \preceq b
>\end{align*}
>$$
>we can define a slack variable $u \in \mathbb{R}^{m}$ and convert the *inequality constraint* into *equality constraint*
>$$
>\begin{align*}
>  \min_{x \in \mathcal{X},\, \epsilon \in \mathbb{R}^{m}}\;& f(x) \\
>  \text{s.t. }& Ax - u = b
>\end{align*}
>$$

## Dual Proximal Algorithm of Dual Problem

>[!info]
>$$
>\begin{align*}
>\text{Augmented Lagrangian algorithm } &= \text{ proximal algorithm}\left(\text{ dual problem }\right) \\
>&=  \text{ dual proximal algorithm}\left(\text{ dual problem }\right)
>\end{align*}
>$$

>[!important]
>Define 
>- the **primal function** $$p(u) := \inf\left\{ f(x): x\in \mathcal{X}, Ax - b = u \right\} $$ 
>- and the **dual function** $$q(\lambda) := \inf\left\{ f(x) + \left\langle  \lambda\,,\, Ax - b    \right\rangle: x\in \mathcal{X}  \right\} $$ 
>
>Assume that 
>- $p(u)$ is *closed* and *proper*.
>- the optimal value of primal problem $p(0) = p^{*}$ is *finite*.
>  
>Note that $p$ and $q$ are convex conjugate to each other and $$\left(p(u)\right)^{*} = -q(-\lambda)$$

>[!important] Primal Proximal of Dual Problem
>The **augmented Lagrangian method** can be seen as solving the *dual problem* using **primal proximal algorithm**, i.e. at iteration $k$, the new dual variables solves 
>$$
>\lambda_{k+1} \in \arg\min\left\{ q(\lambda) - \frac{1}{2c_{k}}\lVert \lambda - \lambda_{k} \rVert^2   \right\} 
>$$

- [[Lagrange Dual Problem]]
- [[Proximal Algorithm]]

>[!important] Dual Proximal of Dual Problem
>Using conjugacy between $p$ and $q$, we see that this is equivalent to the **dual proximal algorithm** on the *dual problem*, i.e. at iteration $k$, 
> - *Bidual variable iteration* $$u_{k+1} \in \arg\min_{u \in \mathbb{R}^{m}}\left\{ p(u) + \left\langle  \lambda_{k}\,,\,u \right\rangle + \frac{c_{k}}{2}\lVert u \rVert^2 \right\}$$
> - *Dual variable iteration* $$\lambda_{k+1} = \lambda_{k} + c_{k}\,u_{k+1}.$$ where $$u_{k+1} = Ax_{k+1} - b$$

- [[Dual Proximal Algorithm]]

>[!info]
>We see that *the bidual update* in the above **dual proximal algorithm** is equivalent as minimizing the *augmented Lagrangian*
>$$
>\begin{align*}
> \inf_{x\in \mathcal{X}} L_{c}(x, \lambda) &= \inf_{x\in \mathcal{X}} \left\{  f(x) + \left\langle  \lambda\,,\, Ax - b \right\rangle + \frac{c}{2}\lVert Ax - b \rVert^2  \right\}  \\
> &= \inf_{u \in \mathbb{R}^{m}} \inf \left\{  f(x) + \left\langle  \lambda\,,\, u\right\rangle + \frac{c}{2}\lVert u\rVert^2: x\in \mathcal{X},\; Ax - b = u  \right\}\\
> &= \inf_{u \in \mathbb{R}^{m}}\left\{ \inf \left\{  f(x): x\in \mathcal{X},\; Ax - b = u  \right\} + \left\langle  \lambda\,,\, u\right\rangle + \frac{c}{2}\lVert u\rVert^2 \right\}\\
> &= \inf_{u \in \mathbb{R}^{m}}\left\{ p(u) + \left\langle  \lambda\,,\, u\right\rangle + \frac{c}{2}\lVert u\rVert^2 \right\}\\
>\end{align*}
>$$

>[!info]
>We see that variable change
>$$
>\text{ primal variables }(x_{k}) \implies \text{ dual variables }(\lambda_{k}) \implies \text{ bidual variables }(u_{k})
>$$

>[!info]
>- **Proximal algorithm**: $$x_{k+1} = \text{Prox}(x_{k}) \implies x_{k+1} \in \arg\min_{x\in \mathbb{R}^n}\left\{ f(x) + \frac{1}{2c_{k}}\;\lVert x - x_{k} \rVert^2 \right\}.$$
>- **Dual Proximal algorithm**: $$x_{k+1} = \text{Dual-Prox}(x_{k}) \implies x_{k+1} = x_{k} - c_{k}\;\lambda_{k+1},$$ where $$\lambda_{k+1} \in \arg\min_{\lambda \in \mathbb{R}^n}\left\{ f^{*}(\lambda) - \left\langle  \lambda\,,\, x_{k} \right\rangle + \frac{c_{k}}{2}\lVert \lambda \rVert^2 \right\}$$
>- **Augmented Lagrangian algorithm**  $$\lambda_{k+1} = \text{Dual-Prox}(\lambda_{k}) \implies \lambda_{k+1} = \lambda_{k} + c_{k}\,u_{k+1},$$ where $$u_{k+1} \in \arg\min_{u \in \mathbb{R}^{m}}\left\{ p(u) + \left\langle  \lambda_{k}\,,\,u \right\rangle + \frac{c_{k}}{2}\lVert u \rVert^2 \right\}.$$ This is equivalent to 
>  $$
>  \begin{align*}
>  u_{k+1} &= Ax_{k+1} - b\\
>  x_{k+1} &\in \arg\min_{x \in \mathcal{X}}L_{c_{k}}(x, \lambda_{k})
>  \end{align*}
> $$



## Comparison

>[!quote]
>Thus all three *proximal-type methods*, 
>- **proximal gradient**, 
>- **ADMM**, and 
>- **augmented Lagrangian**, 
>
>have *similarities*, and **relative strengths** and **weaknesses**. The choice between them hinges largely on the given problem's structure.
>
>-- [[Convex Optimization Algorithms by Bertsekas]] pp 337

- [[Dual Proximal Gradient Algorithm]]
- [[Alternating Direction Method of Multipliers Algorithm]]




-----------
##  Recommended Notes and References


- [[Methods of Lagrangian Multipliers]]
- [[Augmented Lagrangian Function]]

- [[Approximation Method for Optimization]]

- [[Convex Set]]
- [[Convex Function]]

- [[Nonlinear Programming by Bertsekas]] pp 303, 397
- [[Convex Optimization Algorithms by Bertsekas]] pp 259