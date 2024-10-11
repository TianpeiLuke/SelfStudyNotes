---
tags:
  - concept
  - optimization/theory
  - optimization/algorithm
  - math/convex_analysis
  - optimization/convex_optimization
keywords:
  - interior_point_method
  - logarithmic_barrier
  - barrier_method
topics:
  - optimization
name: Interior Point Method for Convex Optimization
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Barrier Method for Convex Optimization

![[Convex Optimization Problem#^bc3f9c]]

![[Logarithmic Barrier Function and Central Path for Interior Point Methods#^8b91e9]]

![[Logarithmic Barrier Function and Central Path for Interior Point Methods#^779aa5]]

- [[Logarithmic Barrier Function and Central Path for Interior Point Methods]]
- [[Convex Optimization Problem]]

>[!important] Definition
>Consider the *convex optimization problem*
>$$
>\begin{align*}
>\min_{x \in X}\; & f_{0}(x) \\
>\text{s.t.}\;& f_{i}(x) \leq 0, \quad i =1 \,{,}\ldots{,}\, m\\
>&Ax = b
>\end{align*}
>\;\; (P)
>$$
>where both the *objective function* $f_{0}$ and *inequality constraint functions* $f_{i}$ are **convex** and **twice continuously differentiable** functions and $A \in \mathbb{R}^{p \times n}$ is of **full rank** $\text{rank}(A) = p < n.$
>
>The **Barrier method** that solve the problem $(P)$ is described as below:
>- *Require*: the convex program $(P)$
>- *Require*: initial **strictly feasible solution** $x_{0}$
>- *Require*: initial parameter $t_{0} >0$
>- *Require*: *tolerance* $\epsilon >0$
>- *Require*: *growth rate* $\mu >1$
>- While the *tolerance criterion* not met:
>	- If first iteration:
>		- $$x \leftarrow x_{0}, \quad t\leftarrow t_{0}$$
>		- skip the centering and update steps below
>	- **Centering Step**:
>		- Solve the *log-barrier subprogram* $$\begin{align*}\min_{x \in X}\; &\; t\,f_{0}(x) + \phi(x)\\ \text{s.t.}\;&\; Ax  = b \end{align*} \;\; (B_{t})$$ where the log-barrier function is defined as $$\phi(x) :=  -\sum_{i=1}^{m}\log\left(-f_{i}(x)\right).$$
>		- Let $x^{*}(t)$ be the **optimal solution**
>	- **Update** primal feasible solution along the **central path** $$x \leftarrow x^{*}(t)$$
>	- **Increase** $t$ by rate $\mu$ as $$t \leftarrow \mu\,t$$
>	- If the **duality gap** $m / t < \epsilon$:
>		- *Return*: optimal solution $x^{*} = x$


## Explanation


## Primal-Dual Interior Point Methods

- [[Primal-Dual Interior Point Method for Convex Optimization]]



-----------
##  Recommended Notes and References



- [[Newton Method]]
- [[Secant Equation and Quasi-Newton Methods]]
- [[BFGS Algorithm]]



- [[Sequential Quadratic Programming]]
- [[Convex Optimization Problem]]
- [[Convex Set]]
- [[Convex Function]]
- [[Karush-Kuhn-Tucker Optimality Condition]]

- [[Convex Optimization by Boyd]] pp 568 - 596, 596 - 608
- [[Numerical Optimization by Nocedal]] pp 563 - 594
- [[Nonlinear Programming by Bertsekas]] pp 446 - 473