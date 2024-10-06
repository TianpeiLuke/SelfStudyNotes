---
tags:
  - concept
  - optimization/algorithm
  - optimization/convex_optimization
keywords:
  - augmented_lagrangian_function
topics:
  - optimization
name: Augmented Lagrangian Function
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Augmented Lagrangian Function

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
>
>The **augmented Lagrangian function** is defined as
>$$
>L_{c}(x, \lambda) = f(x) + \left\langle  \lambda\,,\, Ax - b \right\rangle + \frac{c}{2}\lVert Ax - b \rVert^2 
>$$
>for $x\in \mathbb{R}^{n}$ and $\lambda \in \mathbb{R}^{m}$


- [[Strongly Convex Function]]
- [[Convex Optimization Problem]]
- [[Legendre Transform]]
- [[Lagrangian Dual Function]]
- [[Closed Convex Function and Closure Operation]]
- [[Proper Convex Function]]


## Explanation

>[!info]
>Define 
>- the **primal function** $$p(u) := \inf\left\{ f(x): x\in \mathcal{X}, Ax - b = u \right\} $$ 
>- and the **dual function** $$q(\lambda) := \inf\left\{ f(x) + \left\langle  \lambda\,,\, Ax - b    \right\rangle: x\in \mathcal{X}  \right\} $$ 
>
>Assume that 
>- $p(u)$ is *closed* and *proper*.
>- the optimal value of primal problem $p(0) = p^{*}$ is *finite*.
>  
>
>Let $Ax - b = u$, we have
>$$
>\begin{align*}
> L_{c}(x, \lambda) &= f(x) + \left\langle  \lambda\,,\, Ax - b \right\rangle + \frac{c}{2}\lVert Ax - b \rVert^2 \\
> &=  f(x) + \left\langle  \lambda\,,\, u \right\rangle + \frac{c}{2}\lVert u \rVert^2
>\end{align*}
>$$
>Thus 
>$$
>\begin{align*}
> \inf_{x\in \mathcal{X}} L_{c}(x, \lambda) &= \inf_{x\in \mathcal{X}} \left\{  f(x) + \left\langle  \lambda\,,\, Ax - b \right\rangle + \frac{c}{2}\lVert Ax - b \rVert^2  \right\}  \\
> &= \inf_{u \in \mathbb{R}^{m}} \inf \left\{  f(x) + \left\langle  \lambda\,,\, u\right\rangle + \frac{c}{2}\lVert u\rVert^2: x\in \mathcal{X},\; Ax - b = u  \right\}\\
> &= \inf_{u \in \mathbb{R}^{m}}\left\{ \inf \left\{  f(x): x\in \mathcal{X},\; Ax - b = u  \right\} + \left\langle  \lambda\,,\, u\right\rangle + \frac{c}{2}\lVert u\rVert^2 \right\}\\
> &= \inf_{u \in \mathbb{R}^{m}}\left\{ p(u) + \left\langle  \lambda\,,\, u\right\rangle + \frac{c}{2}\lVert u\rVert^2 \right\}\\
>\end{align*}
>$$

- [[Bifunction and Convex Bifunction]]
## Strict Minimizer

>[!important]
>If $c$ is larger than some constant, then for some $\gamma >0$, and $\epsilon >0$, 
>$$
>L_{c}(x, \lambda^{*}) \ge L_{c}(x^{*}, \lambda^{*}) + \frac{\gamma}{2}\lVert x - x^{*} \rVert^2 \;\quad \forall x\in B_{\epsilon}(x_{0})
>$$
>This means that $x^{*}$ is a **strict local minimum** of the *augmented Lagrangian* $L_{c}(\cdot, \lambda^{*})$ for $\lambda^{*}.$
>
>This suggests that if $\lambda$ is close to $\lambda^{*}$, a good approximate of $x^{*}$ can be found by **unconstrained minimization** of $L_{c}(\cdot, \lambda).$

- [[Unconstrained Local Minimization]]
- [[Nonlinear Programming by Bertsekas]] pp 398



-----------
##  Recommended Notes and References

- [[Methods of Lagrangian Multipliers]]
- [[Augmented Lagrangian Algorithm]]

- [[Convex Optimization Algorithms by Bertsekas]] pp 259
- [[Nonlinear Programming by Bertsekas]] pp 303, 397