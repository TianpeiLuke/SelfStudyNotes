---
tags:
  - concept
  - optimization/theory
  - optimization/convex_optimization
keywords:
  - optimization_terminology
topics:
  - optimization
name: General Optimization Problem
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Constrained Optimization Problem

>[!important] Definition
>A general **constrained optimization problem** is defined as below
>$$
>\begin{align*}
>\min_{x \in X}\; & f_{0}(x) \\
>\text{s.t.}\;& f_{i}(x) \leq 0, \quad i =1 \,{,}\ldots{,}\, m\\
>&h_{j}(x) = 0, \quad j =1 \,{,}\ldots{,}\, p\\
\end{align*}
>$$

^0430c8

>[!important] Definition
>In above problem:
>- The variable $x\in X$ is called the **optimization variable**.
>- The function $f_{0}: \text{dom}(f_{0}) \to \mathbb{R}$ to be optimized is called the **objective function**, or **cost function**.
>- The *inequalities* $f_{i}(x) \leq 0$ are called the **inequality constraints**.
>	- The functions $f_{i}: \text{dom}(f_{i}) \to \mathbb{R}$ are called the **inequality constraint functions**.
>- The *equalities* $h_{j}(x) = 0$ are called the **equality constraints**.
>	- The functions $h_{j}: \text{dom}(h_{j}) \to \mathbb{R}$ are called the **equality constraint functions**.
>- The set of points for which the objective functions and constraint functions are defined is called the **domain** of *the optimization problem.*
>$$
>X := \text{dom}(f_{0}) \; \cap \; \bigcap_{i=1}^{m}\text{dom}(f_{i}) \; \cap \; \bigcap_{j=1}^{p}\text{dom}(h_{j})
>$$ 
>- A point $x \in X$ is called **feasible** if it satisfies *all constraints*.
>- The problem is called **feasible** if there exists *at least one* $x\in X$ that satisfies *all constraints*.
>	- Otherwise, the problem is called **infeasible**.
>- The set of *all feasible points* is called **feasible set**, or **feasible region** or **constraint sets**, i.e.
>$$
>\Omega := \left\{ x\in X:  f_{i}(x) \leq 0, \; i =1 \,{,}\ldots{,}\, m;\quad h_{j}(x) = 0, \; j =1 \,{,}\ldots{,}\, p \right\}
>$$

^7c9083


>[!important] Definition
>If both $m=p=0$, i.e. there are *no constraints*, then the optimization problem above is called **unconstrained optimization**.

>[!important] Definition
>The **optimal value** $p^{*}$ of above problem is defined as
>$$
>p^{*} := \inf\left\{ f_{0}(x): f_{i}(x) \leq 0, \; i =1 \,{,}\ldots{,}\, m;\; h_{j}(x) = 0, \; j =1 \,{,}\ldots{,}\, p; \; x\in X \right\}
>$$
>- $p^{*}$ can take extended value $\pm \infty$.
>- If $\Omega = \emptyset$, i.e. the problem is *infeasible*, then we have $p^{*} = + \infty.$
>- If there exists a sequence of $x_{n} \in \Omega$ and $\lim_{ n \to \infty }f_{0}(x_{n}) = -\infty$, then $p^{*} = -\infty.$ The problem is then called **unbounded below**.

>[!important] Definition
>A point $x^{*} \in X$ is called an **optimal point**, or **optimal solution**, or **solves** above problem if $x^{*}$ is *feasible* and *attains the optimal value* $p^{*}.$
>
>That is,
>$$
>x^{*} \text{ is optimal point } \implies x^{*} \in \Omega, \text{ and }f_{0}(x^{*}) = p^{*}.
>$$

>[!important] Definition
>If there exists an optimal point $x^{*}$, then we say that *the optimal value* is **attained** and the *optimization problem* is **solvable**, or **achievable**.

## Active and Inactive Constraints

>[!important] Definition
>- If $x$ is feasible, and $f_{i}(x) = 0$ for *inequality constraint* $i$, we say that the corresponding *inequality constraint* $f_{i}(x) \leq 0$ is **active**.
>- If the inequality constraint is *strict*,  $f_{i}(x) < 0$, we say the inequality constraint is **inactive**.

^9a3b41

>[!important] Definition
>We say a constraint is **redundant** if deleting that constraint *does not change* the feasible set $\Omega$. 

## Feasible Problem

>[!important] Definition
>The problem of identifying if $\Omega \neq \emptyset$ is called **feasible problem.** 
>
>It can be achieved by 
>$$
>\begin{align*}
>\min_{x \in X}\; &\; c \\
>\text{s.t.}\;& f_{i}(x) \leq 0, \quad i =1 \,{,}\ldots{,}\, m\\
>&h_{j}(x) = 0, \quad j =1 \,{,}\ldots{,}\, p\\
\end{align*}
>$$
>where $c$ is some constant.

## Equivalent Problem

>[!important] Definition
>Two problems are **equivalent** if given solution of one problem, we can readily find the solution of another problem.


## Sub-Optimal Solutions


>[!important] Definition
>A *feasible point* $x \in \Omega$ with 
>$$
>f_{0}(x) \leq p^{*} + \epsilon
>$$ 
>for some $\epsilon >0$ is called a **$\epsilon$-suboptimal point.**
>
>The set of all **$\epsilon$-suboptimal points** is called  **$\epsilon$-suboptimal set** for the optimization problem.


## Locally Optimization Problem

>[!important] Definition
>A  **locally optimization problem** *with respect to $x$* is defined as below
>$$
>\begin{align*}
>\min_{z \in X}\; & f_{0}(z) \\
>\text{s.t.}\;& f_{i}(z) \leq 0, \quad i =1 \,{,}\ldots{,}\, m\\
>&h_{j}(z) = 0, \quad j =1 \,{,}\ldots{,}\, p\\
>&\lVert z - x \rVert \leq R 
\end{align*}
>$$

>[!important] Definition
>A feasible point $x \in \Omega$ is called a **locally optimal point**, if there exists $R>0$, such that $x$ solves the problem
>
>That is,
>$$
>f_{0}(x) = \inf\left\{ f_{0}(z): f_{i}(z) \leq 0, \; i =1 \,{,}\ldots{,}\, m;\; h_{j}(z) = 0, \; j =1 \,{,}\ldots{,}\, p; \; \lVert z - x \rVert \leq R  \right\}
>$$


-----------
##  Recommended Notes and References

- [[Space of Continuous Differentiable Functions]]


- [[Convex Analysis by Rockafellar]]
- [[Convex Optimization by Boyd]]
- [[Numerical Optimization by Nocedal]]
- [[Nonlinear Programming by Bertsekas]]
- [[Artificial Intelligence Modern Approach by Russell]]