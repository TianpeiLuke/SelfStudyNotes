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
name: Logarithmic Barrier Function and Central Path for Interior Point Methods
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Logarithmic Barrier Function and Central Path for Interior Point Methods

![[Convex Optimization Problem#^bc3f9c]]

### Log-Barrier Function

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
>We can rewrite the optimization problem as
>$$
>\begin{align*}
>\min_{x \in X}\; & f_{0}(x) + \sum_{i=1}^{m}\delta_{-}\{ f_{i}(x)\}\\
>\text{s.t.}\;& Ax  = b
\end{align*}
>$$
>where 
>$$
>\delta_{-}(u) = \left\{\begin{array}{cc}
> 0 & u \le 0\\
> +\infty & u > 0
>\end{array}
>\right.
>$$
>
>The basic idea of the **barrier method** is to *approximate* the bifunction $\delta_{-}$ by the function
>$$
>\hat{\delta}_{-}(u) = -\left(\frac{1}{t}\right)\log\left(-u\right),\, \quad \text{where }\; \text{dom}(\hat{\delta}_{-}) = - \mathbb{R}_{++}, 
>$$
>and $t >0$ is a *parameter* that set the accuracy of the approximation. Moreover,
>- $\hat{\delta}_{-}$ is a *convex function* and *non-decreasing*.
>- $\hat{\delta}_{-} = \infty$ if $u >0$
>- $\hat{\delta}_{-}$ is *differentiable* and *closed*
>  
>Substituting the approximation  $\hat{\delta}_{-}$, the optimization problem becomes
>$$
>\begin{align*}
>\min_{x \in X}\; & f_{0}(x) - \frac{1}{t}\sum_{i=1}^{m}\log\left(-f_{i}(x)\right)\\
>\text{s.t.}\;& Ax  = b
\end{align*}
>$$  
>which is also a *convex optimization problem*. 

^8b91e9

>[!important] Definition
>The function 
>$$
>\phi(x) :=  -\sum_{i=1}^{m}\log\left(-f_{i}(x)\right), 
>$$
>with domain
>$$
>\text{dom }(\phi) := \{ x\in \mathcal{X}: f_{i}(x) <0, \; i=1 \,{,}\ldots{,}\,m \},
>$$
>is called the **logarithmic barrier** or **log barrier** for the convex optimization problem $(P)$

^779aa5

- [[Convex Optimization Problem]]
- [[Bifunction and Convex Bifunction]]
- [[Operations that Preserve Convexity]]

![[log_barrier_fun.png]]


>[!info]
>The **domain** of log barrier function is the interior of inequality constraint set, where all of inequality constraints are *strict inequality* or *inactive*.

>[!important] 
>The **gradient** and **Hessian** of **log-barrier function** is given by
>- $$\nabla \phi = \sum_{i=1}^{m} \frac{1}{-f_{i}(x)} \nabla f_{i}(x)$$
>- $$\nabla^2 \phi = \sum_{i=1}^{m} \frac{1}{f_{i}^2(x)} \nabla f_{i}(x)\,(\nabla f_{i}(x))^T + \sum_{i=1}^{m} \frac{1}{-f_{i}(x)} \nabla^2 f_{i}(x)$$

^86dd4f


### Central Path

>[!important] Definition
>Consider a sequence of *log-barrier minimization problems*
>$$
>\begin{align*}
>\min_{x \in X}\; &\; t\,f_{0}(x) + \phi(x)\\
>\text{s.t.}\;&\; Ax  = b
>\end{align*}
>\;\; (B_{t})
>$$  
>where  $t >0$ and the log-barrier is
>$$
>\phi(x) :=  -\sum_{i=1}^{m}\log\left(-f_{i}(x)\right), 
>$$
>- Assume that this problem can be solved by *Newton's method* and the *optimal solution* is *unique* for each $t$, denoted as $x^{*}(t)$.
>
>The **central path** associated with the problem
>$$
>\begin{align*}
>\min_{x \in X}\; & f_{0}(x) \\
>\text{s.t.}\;& f_{i}(x) \leq 0, \quad i =1 \,{,}\ldots{,}\, m\\
>&Ax = b
>\end{align*}
>\;\; (P)
>$$
>is defined as the set $$\left\{ x^{*}(t): \; x^{*}(t) \text{ is the optimal solution to }(B_{t}), \quad  t >0 \right\}$$
>- Each optimal solution $x^{*}(t)$ for some $t>0$ is called a **central point**. 

![[central_path.png]]

#### Characterization of Central Path 

>[!important] Constraints that define the Central Path 
>According to KKT condition, the following *characterize the central points*:
>- The **central points** $x^{*}(t)$ are **strictly primal feasible** i.e. $$ Ax^{*}(t)  = b, \quad f_{i}(x^{*}(t)) < 0, \;i=1\,{,}\ldots{,}\,m$$
>- $x^{*}(t)$ satisfies the **dual feasible condition**, i.e. there exists some $\hat{\nu}(t)\in \mathbb{R}^{p}$ such that $$\begin{align*}t \;\nabla f_{0}(x^{*}(t)) + \nabla \phi(x^{*}(t)) + A^{T}\hat{\nu}^{*}(t) &= 0 \\[5pt] \implies t \;\nabla f_{0}(x^{*}(t)) + \sum_{i=1}^{m} \frac{1}{-f_{i}(x^{*}(t))} \nabla f_{i}(x^{*}(t))+ A^{T}\hat{\nu}^{*}(t) &= 0 \\[5pt]  \implies  \nabla f_{0}(x^{*}(t)) + \sum_{i=1}^{m} \lambda_{i}^{*}(t)\, \nabla f_{i}(x^{*}(t))+ A^{T} \nu^{*}(t) &= 0 \end{align*}$$ where $$\lambda_{i}^{*}(t) = \frac{1}{-t\,f_{i}(x^{*}(t))} >0,  \quad \nu^{*}(t) = \frac{\hat{\nu}^{*}(t)}{t}$$ is *dual optimal solution* for $(B_{t})$.
>	- We can show that  $(\lambda^{*}(t), \nu^{*}(t))$ is also a *dual feasible solution* for the **original problem** $(P)$.


- [[Constrained Optimization Problem]]
- [[Convex Optimization Problem]]
- [[Newton Method]]

>[!info]
>To show the **central point** associated with problem $(B_{t})$ also yields a *dual feasible solution* for $(P)$
>$$
>\begin{align*}
>t \;\nabla f_{0}(x^{*}(t)) + \sum_{i=1}^{m} \frac{1}{-f_{i}(x^{*}(t))} \nabla f_{i}(x^{*}(t))+ A^{T}\hat{\nu}^{*}(t) &= 0 \\[5pt] 
>\implies \nabla f_{0}(x^{*}(t)) + \sum_{i=1}^{m} \frac{1}{-t\,f_{i}(x^{*}(t))} \nabla f_{i}(x^{*}(t))+ A^{T} \frac{ \hat{\nu}^{*}(t)}{t} &= 0 \\[5pt] 
>\implies \nabla f_{0}(x^{*}(t)) + \sum_{i=1}^{m} \lambda_{i}(t)\, \nabla f_{i}(x^{*}(t))+ A^{T} \nu^{*}(t) &= 0 \quad (*)\\[5pt] 
>\end{align*}
>$$
>where $$\lambda_{i}(t) = \frac{1}{-t\,f_{i}(x^{*}(t))} >0,  \quad \nu^{*}(t) = \frac{\hat{\nu}^{*}(t)}{t}.$$
>- Note that the above equation $(*)$ is the equivalent for gradient of **Lagrangian** $\nabla L$ where $$L(x, \lambda, \nu) := f_{0}(x) + \sum_{i=1}^{m} \lambda_{i}\,  f_{i}(x) + \left\langle \nu , Ax - b \right\rangle$$ 
>
>This shows that the solution to dual feasible equation for central path $(\lambda^{*}, v^{*})$ are the *dual feasible solution* of $(P)$.

>[!important] 
>Given that $(\lambda^{*}(t), \nu^{*}(t))$ is a dual feasible solution of $(P)$,  the **Lagrangian dual function** along the **central path** is *finite* and it is given by 
>$$
>\begin{align*}
>g(\lambda^{*}(t), \nu^{*}(t)) &=  f_{0}(x^{*}(t)) + \sum_{i=1}^{m} \lambda_{i}^{*}(t)\, f_{i}(x^{*}(t)) + \left\langle \nu^{*}(t) , Ax^{*}(t) - b \right\rangle \\[5pt]
>&=  f_{0}(x^{*}(t))  - \frac{m}{t}\\[5pt]
>&\le p^{*}  
>\end{align*}
>$$
>where $p^{*}$ is the *primal optimal value* for problem $(P)$. 
>- The inequality is due to **weak duality** since $(\lambda^{*}(t), \nu^{*}(t))$ are dual feasible for $(P)$
>- The **duality gap** associated with primal optimal $x^{*}(t)$ and the dual optimal $(\lambda^{*}(t), \nu^{*}(t))$ for problem $(B_{t})$ is simply $$\frac{m}{t} = f_{0}(x^{*}(t)) -  g(\lambda^{*}(t), \nu^{*}(t)) $$
>- Moreover, we have $$f_{0}(x^{*}(t))  - p^{*} \le \frac{m}{t}$$ That is the central point $x^{*}(t)$ is **at most $m / t$-suboptimal**.
>- As $t\to \infty$, $$x^{*}(t) \to x^{*} \text{ optimal solution for (P)}$$

- [[Lagrangian Dual Function]]
- [[Lagrange Dual Problem]]

#### The characteristic for Central Path and Relation to KKT

>[!important] Definition
>In summary, the **central path** $\{x^{*}(t)\}$ and  its associated dual $(\lambda^{*}(t), \nu^{*}(t))$ must satisfy the **modified KKT conditions**
>$$
>\begin{align*}
> Ax &= b\\[5pt]
> f_{i}(x) & \le 0, \quad i=1\,{,}\ldots{,}\,m \\[5pt]
> \lambda_{i} &\ge 0 , \quad i=1\,{,}\ldots{,}\,m \\[5pt]
> \nabla f_{0}(x) + \sum_{i=1}^{m} \lambda_{i}\, \nabla f_{i}(x)+ A^{T} \nu &= 0\\[5pt]
> -\lambda_{i} f_{i}(x) &= \frac{1}{t}, \quad i=1\,{,}\ldots{,}\,m
>\end{align*}
>$$
>Note that compared to **KKT conditions** for **primal problem** $(P)$, the only difference is that the **complementary slackness** 
>$$
>-\lambda_{i} f_{i}(x) =0 \implies -\lambda_{i} f_{i}(x) = \frac{1}{t}
>$$
>- As $t\to \infty$, the KKT condition would met and then the central path would end with the *primal optimal solution* of $(P).$

^1d97b8


## Explanation


## Barrier Methods

- [[Barrier Method for Convex Optimization]]


## Primal-Dual Interior Point Methods

- [[Primal-Dual Interior Point Method for Convex Optimization]]



-----------
##  Recommended Notes and References


- [[Primal-Dual Interior Point Method for Convex Optimization]]
- [[Newton Method]]
- [[Secant Equation and Quasi-Newton Methods]]
- [[BFGS Algorithm]]



- [[Sequential Quadratic Programming]]
- [[Convex Optimization Problem]]
- [[Convex Set]]
- [[Convex Function]]
- [[Karush-Kuhn-Tucker Optimality Condition]]

- [[Convex Optimization by Boyd]] pp 563 - 568
- [[Numerical Optimization by Nocedal]] pp 563 - 594
- [[Nonlinear Programming by Bertsekas]] pp 446 - 473