---
tags:
  - concept
  - optimization/theory
  - optimization/algorithm
keywords:
  - simplex_method_linear
  - linear_optimization
topics:
  - optimization/algorithm
name: Simplex Method for Linear Optimization
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Simplex Method for Linear Optimization

![[Linear Optimization Problem#^099c2f]]

### Basic Solution

![[Basic Solution for Linear Optimization#^52390c]]

![[Basic Solution for Linear Optimization#^2fb7eb]]

- [[Basic Solution for Linear Optimization]]

### Feasible Direction

![[Feasible Direction and Reduced Cost for Linear Optimization#^670d89]]

- [[Feasible Direction and Reduced Cost for Linear Optimization]]
- [[Basic Solution for Linear Optimization]]

### Reduced Cost

![[Feasible Direction and Reduced Cost for Linear Optimization#^6f654f]]

- [[Feasible Direction and Reduced Cost for Linear Optimization]]

### Optimal Condition for LP

![[Optimality Condition for Linear Optimization#^521cec]]

- [[Optimality Condition for Linear Optimization]]

### Simplex Method for Linear Optimization

>[!important] Definition
>Consider the linear optimization problem in *standard form*
>$$
>\begin{align*}
>\min_{x}\; & \left\langle c ,  x\right\rangle\\
>\text{s.t.}\;& Ax = b\\
>\;&x \succeq 0\\
\end{align*}
>$$
>
>The **simplex method** for solving above problem is described as below:
>- *Initialize* at an arbitrary **basic feasible solution** $x$
>- While optimality condition not met:
>	- Let $$A_{B(1)} \,{,}\ldots{,}\,A_{B(m)}$$ be a set of **basis columns** and $x$ be the associated **basic feasible solution**
>	- Compute the **reduced costs** $$\bar{c}_{j} = c_{j}  - \left\langle  c_{B}\,,\,B^{-1}\,A_{j} \right\rangle,$$ for all *non-basic indices* $j \not\in \{ B(1) \,{,}\ldots{,}\,B(m)\}$
>	- If $\bar{c}_{j} \ge 0$ for all non-basic indices
>		- the current basic solution $x$ is **optimal**; 
>		- *Return* $x$ and the **optimal cost** $\left\langle  c\,,\,x    \right\rangle$
>	- Else:
>		- Find $j$ such that $\bar{c}_{j} < 0$
>		- Compute $$u = B^{-1}A_{j}$$
>			- If **no** component in $u$ is **positive**, 
>				- *Return* with **optimal cost** $-\infty$; set $\theta^{*} = \infty$
>			- Else 
>				- i.e. there exists some component $i\in [m]$ in $u$ that is $u_{i} >0$  *positive*
>				- Compute $$\theta^{*} = \min_{\{ i=1 \,{,}\ldots{,}\,m: u_{i} > 0 \}}\; \frac{x_{B(i)}}{u_{i}}$$ Let $l$ be the index that attains the minimum $$\theta^{*} = \frac{x_{B(l)}}{u_{l}}$$
>				- Form a **new basis** by *replacing* $A_{B(l)}$ with $A_{j}$.
>				- If $y$ is the **new basic feasible solution**, then the value of new basic variable are $$\left\{\begin{array}{lc}y_{j} = \theta^{*} & \\y_{B(i)} = x_{B(i)} - \theta^{*}\;u_{i} & i \neq l  \end{array} \right.$$




## Explanation


>[!quote]
>Many optimization algorithms are structured as follows: given a *feasible solution*, we *search its neighborhood* to find a nearby feasible solution with *lower cost*. If no nearby feasible solution leads to a cost improvement , the algorithm *terminates* and we have a **locally optimal solution**. For general optimization problems, a locally optimal solution need not be (globally) optimal. Fortunately, in linear programming, **local optimality implies global optimality**; this is because we are minimizing a convex function over a convex set.
>
>-- [[Introduction to Linear Optimization by Bertsimas]] PP 82

## Analysis




-----------
##  Recommended Notes and References

- [[Linear Optimization Problem]]
- [[Polyhedron and Polytope]]
- [[Generalized Simplex]]
- [[Interior Point Method for Linear Optimization]]

- [[Karush-Kuhn-Tucker Optimality Condition]]

- [[Introduction to Linear Optimization by Bertsimas]] pp 87 - 92
- [[Convex Optimization by Boyd]]
- [[Numerical Optimization by Nocedal]]
- [[Nonlinear Programming by Bertsekas]]
- [[Introduction to Algorithms by Cormen]]