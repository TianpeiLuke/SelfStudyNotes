---
tags:
  - concept
  - optimization/theory
  - optimization/algorithm
keywords:
  - linear_optimization
  - reduced_cost
  - feasible_direction
topics:
  - optimization/algorithm
name: Feasible Direction for Linear Optimization
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Optimality Condition and Feasible Direction for Linear Optimization

![[Linear Optimization Problem#^099c2f]]

### Feasible Direction

>[!important] Definition
>Let $x$ be an element of a *polyhedron* $P$. 
>
>A vector $d\in \mathbb{R}^{n}$ is said to be a **feasible direction** at $x$, if there exists a *positive* scalar $\theta$ for which $$x + \theta\,d \in P.$$

^670d89

- [[Polyhedron and Polytope]]

### Moving from one Basic Solution to Another 

![[Basic Solution for Linear Optimization#^52390c]]

- [[Basic Solution for Linear Optimization]]
- [[Extreme Points of Polyhedron]]
- [[Vertex Point of Polyhedron]]
- [[Active and Independent Constraints for Linear Optimization]]

![[Basic Solution for Linear Optimization#^2fb7eb]]


>[!info]
>Let $x$ be a **basic feasible solution** to the standard form problem, let $B(1) \,{,}\ldots{,}\, B(m)$ be the indices of the **basic variables**, and let $$B = [A_{B(1)} . . . A_{B(m)}]$$ be the corresponding **basis matrix**. 
>
>In particular, we have $x_i = 0$ for every *nonbasic variable*, while the vector $$x_{B} = (x_{B(1)}\,{,}\ldots{,}\,x_{B(m)})$$ of basic variables is given by  $$x_{B} = B^{-1}b.$$

^b9c192

- [[Basic Solution for Linear Optimization]]

>[!info]
>We consider the possibility of **moving away from** $x$, to a new vector $x + \theta\,d$, by 
>- selecting a **nonbasic variable** $x_{j}$ (which is initially at **zero level**) , and 
>- increasing it to a **positive value** $\theta$, 
>- while keeping the remaining *nonbasic variables* at **zero**.

^525e1b

>[!info]
>Algebraically, $$d_{j} = 1,$$ and $$d_{i} = 0$$ for **every nonbasic index** $i$ other than $j$. 
>
>At the same time, the vector $x_{B}$ of **basic variables** changes to $$x_{B} + \theta\,d_{B},$$ where $$d_{B} = (d_{B(1)} \,{,}\ldots{,}\, d_{B(m)})$$ is the vector with those *components* of $d$ that correspond to the *basic variables*.

^ff3015

>[!info]
>Given that we are only interested in **feasible solutions**, we require $$A(x + \theta\,d) = b,$$ and since $x$ is *feasible*, we also have $Ax = b.$
>
>Thus, for the *equality constraints* to be satisfied for $\theta > 0$, we need $$A\,d= 0.$$

^a9f410

>[!info]
>Since $d_{j}=1$ and $d_{i}=0$ for all other non-basic indices $i$ , we have
>$$
>\begin{align*}
>0 &= A\,d\\[5pt]
>&= \sum_{i=1}^{n}A_{i}\,d_{i}\\[5pt]
>&= \sum_{i=1}^{m}A_{B(i)}\,d_{B(i)} + A_{j}\\[5pt]
>&= B\,d_{B} + A_{j}
>\end{align*}
>$$

^439d88

>[!important] Definition
>Given the *basis matrix* $B$, the **$j$-th basic direction** is defined as
>$$
>d_{B} = - B^{-1}\,A_{j}
>$$
>where $A_{j}$ is the $j$-th column of the equality constraint matrix.
>
>If $x$ is a *basic feasible solution*, then $$x+ \theta\,d_{j}$$ is a *basic solution* that also satisfies the equality constraint $$Ax = b.$$

^50bb61

>[!info]
>Next step, we need to guarantee that the inequality constraint $x \succeq 0$ is satisfied.
>- We recall that the variable $x_{j}$ is **increased**, and all *other non-basic* variables stay at **zero** level.
>- Thus, we need only worry about the *basic variables*.

>[!info]
>There are two cases for basic variables:
>- Suppose that $x$ is a **nondegenerate basic feasible solution**. Then, $x_B > 0$, from which it follows that $$x_{B} + \theta\,d_{B} \ge 0,$$ and *feasibility* is maintained, when $\theta$ is **sufficiently small**. In particular, $d$ is a **feasible direction**.  
>- Suppose now that $x$ is **degenerate.** Then, $d$ is *not always a feasible direction*. Indeed, it is possible that a basic variable $x_{B(i)}$ is *zero*, while the corresponding component $d_{B(i)}$ of $d_{B} = -B^{-1} A_{j}$ is **negative**. 
>	- In that case, if we follow the *$j$-th basic direction*, the nonnegativity constraint for $x_{B(i)}$ is **immediately violated**, and we are led to *infeasible solutions*;


### Reduced Cost

>[!important] Definition
>Let $x$ be a *basic solution*, let $B$ be an *associated basis matrix*, and let $c_{B}$ be the *vector* of *costs of the basic variables*. $$c_{B} = (c_{B(1)}\,{,}\ldots{,}\,c_{B(m)}).$$ If $d$ is the $j$-th *basic direction*, then the *rate of cost change* is $$\left\langle  c\,,\,d \right\rangle = \left\langle  c_{B}\,,\, d_{B} \right\rangle + c_{j}$$
>
>For each $j$, we define the **reduced cost** $\bar{c}_{j}$ of the variable $x_{j}$ according to the formula
>$$
>\bar{c}_{j} := c_{j} - \left\langle  c_{B}\,,\, B^{-1}A_{j} \right\rangle
>$$

^6f654f

### Optimality Condition

![[Optimality Condition for Linear Optimization#^521cec]]

- [[Optimality Condition for Linear Optimization]]



## Explanation



>[!quote]
>Many optimization algorithms are structured as follows: given a *feasible solution*, we *search its neighborhood* to find a nearby feasible solution with *lower cost*. If no nearby feasible solution leads to a cost improvement , the algorithm *terminates* and we have a **locally optimal solution**. For general optimization problems, a locally optimal solution need not be (globally) optimal. Fortunately, in linear programming, **local optimality implies global optimality**; this is because we are minimizing a convex function over a convex set.
>
>-- [[Introduction to Linear Optimization by Bertsimas]] PP 82




-----------
##  Recommended Notes and References


- [[Linear Optimization Problem]]
- [[Polyhedron and Polytope]]
- [[Generalized Simplex]]
- [[Interior Point Method for Linear Optimization]]
- [[Simplex Method for Linear Optimization]]

- [[Karush-Kuhn-Tucker Optimality Condition]]

- [[Introduction to Linear Optimization by Bertsimas]] pp 81 - 85
- [[Convex Optimization by Boyd]]
- [[Numerical Optimization by Nocedal]]
- [[Nonlinear Programming by Bertsekas]]
- [[Introduction to Algorithms by Cormen]]