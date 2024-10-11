---
tags:
  - concept
  - optimization/theory
  - optimization/algorithm
  - optimization/linear_optimization
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

### Development of Simplex Method

#### Moving from one Basic Feasible Solution to Another

![[Feasible Direction and Reduced Cost for Linear Optimization#^b9c192]]

![[Feasible Direction and Reduced Cost for Linear Optimization#^525e1b]]

![[Feasible Direction and Reduced Cost for Linear Optimization#^ff3015]]

![[Feasible Direction and Reduced Cost for Linear Optimization#^a9f410]]

![[Feasible Direction and Reduced Cost for Linear Optimization#^439d88]]

![[Feasible Direction and Reduced Cost for Linear Optimization#^50bb61]]


#### Reduced Cost

![[Feasible Direction and Reduced Cost for Linear Optimization#^6f654f]]

- [[Feasible Direction and Reduced Cost for Linear Optimization]]

>[!important] Definition
>This vector $$p^{T} = c_{B}^{T}\,B^{-1}$$ is called the **vector of simplex multipliers** associated with the basis $B$.

^3b2740


#### Optimal Condition for LP

![[Optimality Condition for Linear Optimization#^521cec]]

- [[Optimality Condition for Linear Optimization]]

#### Move from Basic Feasible Solution to Next Basic Solution

>[!info]
>Let us assume that every basic feasible solution is **nondegenerate**. This assumption will remain in effect until it is explicitly relaxed later.

>[!info]
>Suppose that we are at a **basic feasible solution** $x$ and that we have computed the **reduced costs** $\bar{c}_{j}$ of the *nonbasic variables*. 
>
>- If all of them are **nonnegative**, by above *optimal condition*, we have an **optimal solution** and we stop.
>- If on the other hand, the *reduced cost* $\bar{c}_{j}$ of a *nonbasic variable* $x_{j}$ is **negative,** the **$j$-th basic direction** $$d= -B^{-1}\,A_{j}$$ is a **feasible direction** of  cost *decrease*.

^0e8413

>[!important] Definition
>While moving along the *$j$-th basic direction* $$d= -B^{-1}\,A_{j},$$ the *nonbasic variable* $x_{j}$ becomes *positive* and all other nonbasic variables remain at *zero*.
>
>We describe this situation by saying that $x_{j}$ (or $A_{j}$) **enters** or is **brought into the basis**.

#### Line Search for step size

>[!info]
>Once we start moving away from $x$ along the direction $d$, we are tracing points of the form $x + \theta\,d,$ where $\theta \ge 0$.

>[!info]
>Since costs decrease along the direction $d$, it is desirable to **move as far as possible**. This takes us to the point $x + \theta^{*}\,d$ such that 
>$$
>\theta^{*} = \max\left\{\theta \ge 0:\; x+\theta\,d \in P  \right\} 
>$$
>The corresponding *cost change* is $$\theta^{*}\left\langle  c\,,\, d \right\rangle = \theta^{*}\,\bar{c}_{j}.$$

>[!info]
>We now derive formula for $\theta^{*}$. 
>
>Given that $Ad =0$, we have $$A\left(x+ \theta\,d\right) = Ax = b.$$ That is, the *equality constraints are always satisfied*. The only possible infeasibility is due to non-negative constraint $x \succeq 0$.

>[!info]
>We distinguish two cases
>- if $d \succeq 0$, then $$x + \theta\,d \succeq 0$$ for all $\theta \ge 0$, so the vector $x + \theta\,d$ is always *feasible*.
>- If $d_{i} < 0$ for some $i$, the constraint $$x_{i} + \theta\,d_{i} \ge 0 \implies \theta \le -\frac{x_{i}}{d_{i}}.$$ This inequality should be satisfies for *all $i$ such that* $d_{i} <0$. So $$\theta^{*} = \min_{i: d_{i} <0} \left(-\frac{x_{i}}{d_{i}}\right)$$
>	- If $x_{i}$ is non-basic variable, then  
>		- either $x_{i}$ is *entering the basis* which means that $d_{i} = 1$ 
>		- or $x_{i} =0$ and $d_{i} =0$.
>	- $d_{i}$ is *non-negative* for either case.

 >[!info]
 >Thus we only consider the basic variables 
>$$
>\theta^{*} = \min_{i\in [m]: d_{B(i)} <0} \left(-\frac{x_{B(i)}}{d_{B(i)}}\right)
>$$
>Note that $\theta^{*} > 0$, because $x_{B(i)} >0$ for all $i$ due to a consequence of *non-degeneracy.*

#### Update Basis 

>[!info]
>Once $\theta^{*}$ is chosen, and assuming it is finite, we move to a new feasible solution $$y = x + \theta^{*}\,d.$$
>
>Since $x_{j}=0$, and $d_{j}=1$, we have $$y_{j} = \theta^{*} >0.$$

>[!info]
>Let $l$ be a minimizing index, i.e. 
>$$
>\left(-\frac{x_{B(l)}}{d_{B(l)}}\right) = \min_{i\in [m]: d_{B(i)} <0} \left(-\frac{x_{B(i)}}{d_{B(i)}}\right) = \theta^{*}
>$$
>
>That is, $$d_{B(l)} <0, \quad x_{B(l)} + \theta^{*}\,d_{B(l)} = 0.$$
>
>We observe that the *basic variable* $x_{B(l)}$ has become **zero**, whereas the  *nonbasic variable* $x_{j}$ has now become **positive**, which suggests that $x_{j}$ should **replace** $x_{B(l)}$ in the **basis**.

>[!info]
>We take the **old basis matrix** $B$ and replace $A_{B(l)}$ with $A_{j}$, and the **new basis matrix**
>$$
>\overline{B} = \left[ A_{B(1)} \,{,}\ldots{,}\,A_{B(l-1)}, \, A_{j},\,A_{B(l+1)} \,{,}\ldots{,}\,A_{B(m)}  \right] 
>$$
>where
>$$
>\overline{B}(i) = \left\{ \begin{array}{cc}B(i) & i\neq l\\ j & j= l\end{array} \right.
>$$

>[!important] Theorem
>- The columns $$A_{B(i)}\,,\, i \neq l, \text{ and } A_{j} $$ are **linearly independent** and, therefore, $\overline{B}$ is a **basis matrix**.  
>- The vector $$y = x + \theta^{*}\, d$$ is a **basic feasible solution** associated with the *basis matrix* $\overline{B}$.


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
>		- Note that $x_{i} =0$ for all $i \not\in \{ B(1) \,{,}\ldots{,}\, B(m)\}$
>	- Compute the **reduced costs** $$\bar{c}_{j} = c_{j}  - \left\langle  p\,,\,A_{j} \right\rangle,$$ for all *non-basic indices* $j \not\in \{ B(1) \,{,}\ldots{,}\,B(m)\}$ where $$p^{T} = c_{B}^{T}\,B^{-1}$$ is the **vector of simplex multipliers** associated with the **basis matrix** $$B = [A_{B(1)} \ldots A_{B(m)}]$$
>	- If $\bar{c}_{j} \ge 0$ for all non-basic indices
>		- the current basic solution $x$ is **optimal**; 
>		- *Return* $x$ and the **optimal cost** $\left\langle  c\,,\,x    \right\rangle$
>	- Else:
>		- Find $j$ such that $\bar{c}_{j} < 0$
>		- Compute the $j$-th **basic direction** $$d_{B} = -B^{-1}A_{j}$$
>		- If **no** component in $d$ is **negative**, i.e. $$d_{B} \succeq 0$$
>			- *Return* with **optimal cost** $-\infty$; set $\theta^{*} = \infty$
>		- Else, i.e. there exists some component $i\in [m]$ in $d_{B}$ that is $d_{B(i)} <0$  *negative*
>			- Compute $$\theta^{*} = \min_{\{ i=1 \,{,}\ldots{,}\,m:\; d_{B(i)} < 0 \}}\; \left(-\frac{x_{B(i)}}{d_{B(i)}}\right)$$ Let $l$ be the index that attains the minimum $$\theta^{*} = -\frac{x_{B(l)}}{d_{B(l)}}$$
>			- Form a **new basis** by *replacing* $A_{B(l)}$ with $A_{j}$.
>			- Update a **new basic feasible solution** $y$ based on $x$, where the value of new basic variable are $$ y_{k} = \left\{\begin{array}{lc}\theta^{*} & k=j\\ x_{k} + \theta^{*}\;d_{k} & k \in \left\{ B(1) \,{,}\ldots{,}\, B(m) \right\}  \setminus \{ B(l) \} \\0 & \text{otherwise} \end{array} \right.$$

^933ad4

- [[Gaussian Elimination with Partial Pivoting]]
- [[LU Factorization of Matrix]]



## Explanation


>[!quote]
>Many optimization algorithms are structured as follows: given a *feasible solution*, we *search its neighborhood* to find a nearby feasible solution with *lower cost*. If no nearby feasible solution leads to a cost improvement , the algorithm *terminates* and we have a **locally optimal solution**. For general optimization problems, a locally optimal solution need not be (globally) optimal. Fortunately, in linear programming, **local optimality implies global optimality**; this is because we are minimizing a convex function over a convex set.
>
>-- [[Introduction to Linear Optimization by Bertsimas]] PP 82

>[!info]
>A **naive implemention** of the simplex method need to solve **two linear system of equations**
>- $$p^{T} = c_{B}^{T}\,B^{-1}$$
>- $$u = B^{-1}\,A_{j}$$
>  
>We need an *efficient method* for updating the matrix $B^{-1}$ each time that we effect a change of basis.

- [[BFGS Algorithm]]


## Performance Guarantee

>[!important] Theorem
>Assume that the feasible set is *nonempty* and that every **basic feasible solution** is **nondegenerate**. 
>
>Then, the **simplex method** *terminates* after a *finite number of iterations*. 
>
>At termination, there are the following two possibilities: 
>- We have an **optimal basis** $B$ and an associated **basic feasible solution** which is **optimal**. 
>- We have found a vector d satisfying $$A\,d = 0,\; d \succeq 0,$$ and $$\left\langle  c\,,\, d   \right\rangle <0,$$ and the **optimal cost** is $-\infty$ .






-----------
##  Recommended Notes and References

- [[Linear Optimization Problem]]
- [[Polyhedron and Polytope]]
- [[Generalized Simplex]]
- [[Barrier Method for Linear Optimization]]

- [[Karush-Kuhn-Tucker Optimality Condition]]

- [[Introduction to Linear Optimization by Bertsimas]] pp 87 - 92
- [[Convex Optimization by Boyd]]
- [[Numerical Optimization by Nocedal]] pp 355 - 389
- [[Nonlinear Programming by Bertsekas]]
- [[Introduction to Algorithms by Cormen]]