---
tags:
  - concept
  - optimization/theory
  - math/convex_analysis
  - optimization/convex_optimization
keywords:
  - kkt_optimality_condition
topics:
  - convex_analysis
  - optimization/theory
name: KKT Optimality Condition
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Karush-Kuhn-Tucker Optimality Condition

>[!info]
>A  **general constrained optimization problem** is defined as below
>$$
>\begin{align*}
>\min_{x \in X}\; & f_{0}(x) \\
>\text{s.t.}\;& f_{i}(x) \leq 0, \quad i =1 \,{,}\ldots{,}\, m\\
>&h_{j}(x) = 0, \quad j =1 \,{,}\ldots{,}\, p\\
\end{align*} 
>\quad (P)
>$$
>where both the *objective function* $f_{0}$ and *inequality constraint functions* $f_{i}$ are **continuously differentiable** functions.Let $X$ be the *primal feasible region*.



>[!important] Definition
>The vector $[\lambda_{1} \,{,}\ldots{,}\, \lambda_{m}, \nu_{1} \,{,}\ldots{,}\,\nu_{p}]$ is called a vector of **Kuhn-Tucker coefficients** or a **Kuhn-Tucker vector** for the primal problem $(P)$ if
>- $\lambda_{i} \ge 0$ for $i=1 \,{,}\ldots{,}\,m$
>- and the *infimum* of the *proper convex function* is finite $$\inf\left\{ f_{0}(x) + \sum_{i=1}^{m}\lambda_{i}\, f_{i}(x) + \sum_{j=1}^{p}\nu_{j}\,h_{j}(x): x\in X \right\} > -\infty$$
>- and the infimum is equal to the *primal optimal value* $$\inf\left\{ f_{0}(x) + \sum_{i=1}^{m}\lambda_{i}\, f_{i}(x) + \sum_{j=1}^{p}\nu_{j}\,h_{j}(x): x\in X\right\} = p^{*}.$$

- [[Lagrangian Dual Function]]
- [[Methods of Lagrangian Multipliers]]
- [[Convex Analysis by Rockafellar]] pp 274

### Complementary Slackness

>[!important] Theorem
>Let $(P)$ be an ordinary *convex program*. Let $(\lambda_{1} \,{,}\ldots{,}\,\lambda_{m}, \nu_{1} \,{,}\ldots{,}\,\nu_{p})$ be a **Kuhn-Tucker vector** for $(P)$, and let $$L = f_{0} + \sum_{i=1}^{m}\lambda_{i}\,f_{i} + \sum_{j=1}^{p}\nu_{j}\,h_{j}.$$
>Let $D$ be the set of points where $L$ **attains its infimum** over $\mathbb{R}^n$. Let $I$ be the set of indices $i$ such that $1 \le i \le m$ and **$\lambda_{i} = 0,$** and let $J$ be the **complement** of $I$ in $\{1 \,{,}\ldots{,}\,m\}$. Let $D_{0}$ be the set of points $\bar{x} \in D$ such that 
>$$
>\begin{align*}
> f_{i}\left(\bar{x}\right) &\le 0, \quad \forall i \in I\\
> f_{j}\left(\bar{x}\right) &= 0, \quad \forall  j \in J\\
> h_{k}\left(\bar{x}\right) &= 0, \quad \forall  k =1 \,{,}\ldots{,}\,p.\\
>\end{align*}
>$$
>
>Then $D_{0}$ is the set of **all optimal solutions** to $(P)$.

- [[Theorems of Alternatives]]
- [[Convex Optimization Problem]]
- [[Convex Analysis by Rockafellar]] pp 275


>[!info]
>For any feasible solution $x$ to $(P)$, we have 
>$$
>f_{0}(x) + \sum_{i=1}^{m}\lambda_{i}\,f_{i}(x) + \sum_{j=1}^{p}\nu_{j}\,h_{j}(x) \le f_{0}(x)
>$$
>with equality attained *if and only if*
>$$
> \lambda_{i}\,f_{i}(x) = 0, \quad i=1 \,{,}\ldots{,}\,m.
>$$

>[!important] Corollary
>Let $(P)$ be an ordinary *convex program*. Let $(\lambda_{1} \,{,}\ldots{,}\,\lambda_{m}, \nu_{1} \,{,}\ldots{,}\,\nu_{p})$ be a **Kuhn-Tucker vector** for $(P)$. Assume that the functions $f_{i}$ and $h_{j}$ are all **closed**.
>
>If the **infimum** of $$h = f_{0} + \sum_{i=1}^{m}\lambda_{i}\,f_{i} + \sum_{j=1}^{p}\nu_{j}\,h_{j}$$ is **attained** at a **unique point** $\bar{x}$,  this $\bar{x}$ is the **unique optimal solution** to $(P).$

- [[Convex Analysis by Rockafellar]] pp 276

>[!info]
>The complementary slackness implies that 
>- either $\lambda_{i} =0$; or
>- $f_{i} = 0$ is **active**.


### Existence of KKT vector

>[!important] Theorem
>Let $(P)$ be an ordinary *convex program*, and let $I$ be the set of indices $i\neq 0$ such that $f_{i}$ is **not affine**. Assume that the *optimal value* in $(P)$ is not $-\infty$, and that $(P)$ has **at least one feasible solution** in $\text{relint}(X) \subset \text{relint}(\text{dom}(f_{0})),$ which satisfies with **strict inequality** all the **inequality constraints** for $i\in I.$
>
>Then a **Kuhn-Tucker vector** (*not necessarily unique*) **exists** for $(P).$

- [[Relative Interior of Convex Set]]

>[!important] Corollary
>Let $(P)$ be an ordinary *convex program*, with **only inequality constraints**. Assume that the optimal value in $(P)$ is not $-\infty$, and that there exists **at least one** $x\in X$ such that 
>$$
>f_{i}(x) < 0, \quad i=1 \,{,}\ldots{,}\,m.
>$$
>
>Then a **Kuhn-Tucker vector** **exists** for $(P).$


### First-Order Necessary Conditions

>[!important] Theorem (Karush-Kuhn-Tucker Optimality Condition)
>Suppose that $x^{*}$ is a **local minimum** of the primal problem $(P)$, and that the functions $f_{0}, f_{i}, h_{j}$ are **continuously differentiable**, and that the set of **active constraints gradients** *at* $x^{*}$, i.e. $$\{ \nabla f_{i}(x^{*}): i =1 \,{,}\ldots{,}\,m \text{ such that }f_{i}(x^{*}) < 0 \}$$ are **linearly independent**.
>
>Then there exists a **Lagrangian multiplier vector** $(\lambda_{1}^{*} \,{,}\ldots{,}\,\lambda_{m}^{*}, \nu_{1}^{*} \,{,}\ldots{,}\, \nu_{p}^{*})$ such that the following conditions are satisfied:
>- **first-order condition for Lagrangian** $$\nabla_{x} L(x^{*}, \lambda^{*}, \nu^{*}) = \nabla_{x} f_{0}(x^{*}) + \sum_{i=1}^{m}\lambda_{i}^{*}\, \nabla_{x} f_{i}(x^{*}) + \sum_{j=1}^{p}\nu_{j}^{*}\, \nabla_{x} h_{j}(x^{*}) = 0$$
>- **primal feasible (inequality constraint)**: $$f_{i}(x^{*}) \le 0, \quad i=1 \,{,}\ldots{,}\,m.$$
>- **primal feasible (equality constraint)**: $$h_{j}(x^{*}) = 0, \quad j=1 \,{,}\ldots{,}\,p.$$
>- **dual feasible**: $$\lambda_{i}^{*} \ge 0, \quad i=1 \,{,}\ldots{,}\,m.$$
>- **complementary slackness**: $$\lambda_{i}^{*}\,f_{i}(x^{*}) = 0, \quad i=1 \,{,}\ldots{,}\,m.$$
>  
>The conditions above are known as **the Karush-Kuhn-Tucker (KKT) condition**.

^a09722

- [[Unconstrained Local Minimization]]
- [[Necessary and Sufficient Condition for Local Minimum of Smooth Function]]
- [[Methods of Lagrangian Multipliers]]
- [[Theorems of Alternatives]]
- [[Numerical Optimization by Nocedal]]  pp 321


>[!important] Theorem
>Let $(P)$ be an ordinary *convex program*. Let $(\lambda^{*}, \nu^{*})$ and $x^{*}$ be vectors in $\mathbb{R}^{m+p}$ and $\mathbb{R}^{n}$, respectively. In order that $(\lambda^{*}, \nu^{*})$ be a **Kuhn-Tucker vector** for $(P)$ and $x^{*}$ be an **optimal solution** for $(P)$, it is **necessary** and **sufficient** that $(x^{*}, \lambda^{*}, \nu^{*})$ be a **saddle point** of the *Lagrangian* $L(x, \lambda, \nu)$ of $(P)$, i.e.
>$$
>L(x^{*}, \lambda, \nu) \le L(x^{*}, \lambda^{*}, \nu^{*}) \le L(x, \lambda^{*}, \nu^{*})\; \quad \forall (\lambda, \nu) \in \mathbb{R}^{m+p}, \; \forall x \in \mathbb{R}^{n}.
>$$
>
>Moreover, this condition holds **if and only if**  $(x^{*}, \lambda^{*}, \nu^{*})$ satisfy 
>- **primal feasible (inequality constraint)**: $$f_{i}(x^{*}) \le 0, \quad i=1 \,{,}\ldots{,}\,m.$$
>- **primal feasible (equality constraint)**: $$h_{j}(x^{*}) = 0, \quad j=1 \,{,}\ldots{,}\,p.$$
>- **dual feasible**: $$\lambda_{i}^{*} \ge 0, \quad i=1 \,{,}\ldots{,}\,m.$$
>- **complementary slackness**: $$\lambda_{i}^{*}\,f_{i}(x^{*}) = 0, \quad i=1 \,{,}\ldots{,}\,m.$$
>- **sub-gradient of Lagrangian**: $$0\in \left[\partial f_{0}(x^{*}) +  \sum_{i=1}^{m}\lambda_{i}^{*}\, \partial f_{i}(x^{*}) + \sum_{j=1}^{p}\nu_{j}^{*}\, \partial h_{j}(x^{*})\right].$$

- [[Saddle Point of Lagrangian Function]]
- [[Methods of Lagrangian Multipliers]]
- [[Convex Analysis by Rockafellar]] pp 281
- [[Necessary and Sufficient Condition for Local Minimum of Smooth Function]]

>[!important] Corollary (Kuhn-Tucker Theorem)
>Let $(P)$ be an ordinary *convex program*, and let $I$ be the set of indices $i\neq 0$ such that $f_{i}$ is **not affine**. Assume that the *optimal value* in $(P)$ is not $-\infty$, and that $(P)$ has **at least one feasible solution** in $\text{relint}(X) \subset \text{relint}(\text{dom}(f_{0})),$ which satisfies with **strict inequality** all the **inequality constraints** for $i\in I.$
>
>In order that $x^{*}$ be an **optimal solution** for $(P)$, it is **necessary** and **sufficient** that there exists a vector $(\lambda^{*}, \nu^{*})$ such that $(x^{*}, \lambda^{*}, \nu^{*})$ is a **saddle point** of the *Lagrangian* $L(x, \lambda, \nu)$ of $(P)$, i.e.
>$$
>L(x^{*}, \lambda, \nu) \le L(x^{*}, \lambda^{*}, \nu^{*}) \le L(x, \lambda^{*}, \nu^{*})\; \quad \forall (\lambda, \nu) \in \mathbb{R}^{m+p}, \; \forall x \in \mathbb{R}^{n}.
>$$
>
>*Equivalently*,  $x^{*}$ is an *optimal solution* for $(P)$ *if and only if* there exists Lagrangian multiplier values $(\lambda^{*}, \nu^{*})$ which, together with $x^{*}$, satisfy the  **the Karush-Kuhn-Tucker condition** for $(P)$. 

### Second-Order Necessary Condition

>[!important] Theorem (Second-Order Necessary Condition)
>Suppose that $x^{*}$ is a **local minimum** of the primal problem $(P)$, and that the functions $f_{0}, f_{i}, h_{j}$ are **continuously differentiable**, and that the set of **active constraints gradients** *at* $x^{*}$, i.e. $$\{ \nabla f_{i}(x^{*}): i =1 \,{,}\ldots{,}\,m \text{ such that }f_{i}(x^{*}) < 0 \}$$ are **linearly independent**.
>
>Let $(\lambda^{*}, \nu^{*})$ be the **Lagrangian multiplier** vector for which the **KKT conditions** are satisfied. 
>
>Then $$w^T \nabla_{x x}^2\;L(x^{*}, \lambda^{*}, \nu^{*}) w \ge 0$$ for all  $w$ satisfying the conditions
>$$
>\left\{
>\begin{array}{cc}
> w^{T}\,\nabla_{x} h_{j}(x^{*}) = 0 & \forall j=1 \,{,}\ldots{,}\,p\\ 
> w^{T}\,\nabla_{x} f_{i}(x^{*}) = 0 & \forall i \in \left\{ i: f_{i}(x^{*}) = 0 \right\} \text{ and }\lambda_{i}^{*} > 0 \\   
>w^{T}\,\nabla_{x} f_{i}(x^{*}) \ge 0 & \forall i \in \left\{ i: f_{i}(x^{*}) = 0 \right\} \text{ and }\lambda_{i}^{*} = 0 \\
>\end{array}
>\right.
>$$

- [[Numerical Optimization by Nocedal]]  pp 332

### Second-Order Sufficient Condition

>[!important] Theorem (Second-Order Sufficient Condition)
>Suppose that for some **feasible solution** $x^{*} \in \mathbb{R}^{n}$ of $(P)$, there *exists* a **Lagrangian multiplier vector** $(\lambda^{*}, \nu^{*})$ such that the **KKT conditions** are satisfied.
>
>Suppose that $$w^T \nabla_{x x}^2\;L(x^{*}, \lambda^{*}, \nu^{*}) w \ge 0$$ for all  $w \neq 0$ satisfying the conditions
>$$
>\left\{
>\begin{array}{cc}
> w^{T}\,\nabla_{x} h_{j}(x^{*}) = 0 & \forall j=1 \,{,}\ldots{,}\,p\\ 
> w^{T}\,\nabla_{x} f_{i}(x^{*}) = 0 & \forall i \in \left\{ i: f_{i}(x^{*}) = 0 \right\} \text{ and }\lambda_{i}^{*} > 0 \\   
>w^{T}\,\nabla_{x} f_{i}(x^{*}) \ge 0 & \forall i \in \left\{ i: f_{i}(x^{*}) = 0 \right\} \text{ and }\lambda_{i}^{*} = 0. \\
>\end{array}
>\right.
>$$
>
>Then $x^{*}$ is a **strict local minimum** for $(P)$.

- [[Necessary and Sufficient Condition for Local Minimum of Smooth Function]]
- [[Unconstrained Local Minimization]]
- [[Numerical Optimization by Nocedal]]  pp 333

## Explanation

>[!info]
>For convex optimization problem, the **KKT conditions** are both **necessary** and **sufficient**.
>
>For general optimization problem. they are **only necessary conditions**.

>[!info]
>Let $\mathcal{A}(x^{*})$ be the index set of **active constraints**. Then the **KKT condition** implies
>$$
>\nabla_{x} f_{0}(x^{*}) + \sum_{i \in \mathcal{A}(x^{*})}\lambda_{i}^{*}\, \nabla_{x} f_{i}(x^{*}) + \sum_{j=1}^{p}\nu_{j}^{*}\, \nabla_{x} h_{j}(x^{*}) = 0
>$$

>[!important]
>Solving the **KKT necessary optimality condition** involves solving a **system of nonlinear equations**. 
>$$
>\begin{align*}
>\nabla_{x} f_{0}(x) + \sum_{i \in \mathcal{A}(x)}\lambda_{i}\, \nabla_{x} f_{i}(x) + \sum_{j=1}^{p}\nu_{j}\, \nabla_{x} h_{j}(x) &= 0\\
> h_{j}(x) &= 0,\quad j=1 \,{,}\ldots{,}\,p\\
> f_{i}(x) &= 0, \quad i\in \mathcal{A}(x) \\
> \lambda_{i}&\ge 0,   \quad i\in \mathcal{A}(x) 
\end{align*}
>$$


## Lagrangian System

>[!important] 
>Consider the primal problem with **equality constraint only**
>$$
>\begin{align*}
>\min_{x \in X}\; & f_{0}(x) \\
>\text{s.t.}\;& h_{j}(x) = 0, \quad j =1 \,{,}\ldots{,}\, p\\
\end{align*} 
>\quad (P)
>$$
>The *KKT necessary optimality condition* involves solving a **system of nonlinear equations** with respect to $(x, \nu)$
>$$
>\begin{align*}
>\nabla_{x} f_{0}(x)  + \sum_{j=1}^{p}\nu_{j}\, \nabla_{x} h_{j}(x) &= 0\\
> h_{j}(x) &= 0,\quad j=1 \,{,}\ldots{,}\,p
\end{align*}
>$$
>This system is called the **Lagrangian system**.

- [[Nonlinear Programming by Bertsekas]] pp 455



-----------
##  Recommended Notes and References

- [[Methods of Lagrangian Multipliers]]
- [[Theorems of Alternatives]]
- [[Constrained Optimization Problem]]
- [[Space of Continuous Differentiable Functions]]

- [[Convex Analysis by Rockafellar]] pp 282
- [[Convex Optimization by Boyd]] pp 243, 677
- [[Numerical Optimization by Nocedal]]  pp 321
- [[Nonlinear Programming by Bertsekas]] pp 315 - 321
- [[Optimization by Vector Space Methods by Luenberger]] pp 249 - 250