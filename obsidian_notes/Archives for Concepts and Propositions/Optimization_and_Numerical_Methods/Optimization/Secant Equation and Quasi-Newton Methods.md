---
tags:
  - concept
  - optimization/algorithm
  - optimization/convex_optimization
  - quasi_Newton_method
  - secant_equation
keywords:
  - gradient_descent_algorithm
  - line_search
topics:
  - optimization/algorithm
name: Quasi-Newton Methods
date of note: 2024-07-02
---

## Concept Definition

>[!important]
>**Name**: Quasi-Newton Methods

### Taylor Expansion for Hessian Approximation

>[!info]
>For a *second-order continuous differentiable* function $f$,  the **Taylor expansion** of gradient $\nabla f$ at $x$ with increment $p$ is
>$$
>\nabla f(x + p) = \nabla f(x) + \nabla^2 f(x)\,p + \int_{0}^{1}\left(\nabla^2 f(x + t\,p) - \nabla^2 f(x) \right)p\,dt.
>$$
>Since $\nabla f$ is continuous, the size of final integral term is $o(\lVert p \rVert)$.
>
>Let $p = x_{k+1} - x_{k}$, we have
>$$
>\nabla f(x_{k+1}) - \nabla f(x_{k}) = \nabla^2 f(x_{k})\,\left(x_{k+1} - x_{k}\right) + o\left(\lVert x_{k+1} - x_{k} \rVert \right).
>$$
>
>For $x_{k}$ and $x_{k+1}$in the neighborhood of the *local minimal* $x^*$, the Hessian is *positive definite* $\nabla^2 f(x_{k}) \succ 0$, thus the final term $o\left(\lVert x_{k+1} - x_{k} \rVert \right)$ is *dominated* by the  term $\nabla^2 f(x_{k})\,\left(x_{k+1} - x_{k}\right)$. We have the **approximation**
>$$
>\nabla^2 f(x_{k})\,\left(x_{k+1} - x_{k}\right) \approx \nabla f(x_{k+1}) - \nabla f(x_{k}).
>$$

^85e2d7

- [[Taylor Series for Local Polynomial Approximation of Smooth Function]]
- [[Unconstrained Local Minimization]]
- [[Necessary and Sufficient Condition for Local Minimum of Smooth Function]]

>[!important] Definition
>We choose a *Hessian approximation* $B_{k} \succ 0$ so that it mimics the property
>$$
>B_{k}\left(x_{k+1} - x_{k}\right) = \nabla f(x_{k+1}) - \nabla f(x_{k}).
>$$
>This condition is called **the secant equation**. Let $s_{k} = x_{k+1} - x_{k}$, and $y_{k} = \nabla f(x_{k+1}) - \nabla f(x_{k})$. We have
>$$
>B_{k}\,s_{k} = y_{k}.
>$$
>
>Moreover, it impose additional condition that $B_{k}$ is **symmetric**, i.e.
>$$
>B_{k} \in \mathcal{S}_{++}^{n} := \left\{ B\in \mathbb{R}^{n\times n}: B \succ 0, \;\; B^{T} = B \right\}. 
>$$

^035e08

- [[Positive Semidefinite Transformation]]
- [[Hermitian or Symmetric Matrix]]
- [[Normal Equations and Newton System of Equations]]
- [[Space of Symmetric Positive Semidefinite Matrices]]

>[!info]
>The **secant equation** is also called **Newton equation** and it is used in *Newton's method*
>$$
> \nabla^2 f(x_{0})\, d = - \nabla f(x_{0})
>$$

- [[Newton Method]]
### Symmetric Rank-One Formula

>[!important] Definition
>The **symmetric-rank-one (SR1) formula** for updating the approximation of Hessian is
>$$
>\begin{align*}
>B_{k+1} &= B_{k} + \frac{\left(y_{k} - B_{k}\,s_{k}\right)\left(y_{k} - B_{k}\,s_{k}\right)^T}{(y_{k} - B_{k}s_{k})^T\,s_{k}}
>\end{align*}
>$$

>[!info]
>This is a **rank-1 update** formula.

### BFGS Method

>[!important] Definition
>The **BFGS formula** for updating the approximation of Hessian is
>$$
>\begin{align*}
>B_{k+1} &= B_{k} - \frac{B_{k}\,s_{k}\,s_{k}^T\,B_{k}}{s_{k}^T\,B_{k}\,s_{k}} + \frac{y_{k}^T\,y_{k}}{y_{k}^T\,s_{k}}
>\end{align*}
>$$

>[!info]
>This is a **rank-2 update** formula.

- [[BFGS Algorithm]]

### Quasi-Newton Method 

>[!important] Definition
>Consider the *unconstrained  minimization problem* of a *twice continuous differentiable* function $f: \mathbb{R}^{n} \to \mathbb{R}$. 
>
>The **quasi-newton algorithm** works as follows
>
>0. Initiate with  $x_{0}$ and *convergence tolerance* $\epsilon >0$ and *inverse Hessian approximation* $H_{0} \succ 0.$
>1. $k \leftarrow 0$
>2. While $\lVert \nabla f(x_{k}) \rVert > \epsilon$:
>	1. compute the **search direction** $$d_{k} = - B_{k}^{-1}\,\nabla f(x_{k})$$
>	2. set new point via **generalized gradient descent** $$x_{k+1} = x_{k} + \alpha_{k}\;d_{k}$$ where $\alpha_{k}$ is computed from a *line search procedure* to satisfies the *Wolfe conditions*
>	3. compute the **displacement** of *position* and *change of gradient* $$s_{k} = x_{k+1} - x_{k}; \quad y_{k} = \nabla f(x_{k+1}) - \nabla f(x_{k})$$
>	4. update the **approximation** of **inverse Hessian** via either the **SR1 formula** or **BFGS formula**
>		- **SR1** $$\begin{align*}B_{k+1} &= B_{k} + \frac{\left(y_{k} - B_{k}\,s_{k}\right)\left(y_{k} - B_{k}\,s_{k}\right)^T}{(y_{k} - B_{k}s_{k})^T\,s_{k}}\end{align*}$$
>		- **DFP** $$\begin{align*}B_{k+1} &= \left(I - \rho_{k}\,y_{k}s_{k}^T\right) \,B_{k}\,\left(I - \rho_{k}\,s_{k}y_{k}^T\right) + \rho_{k}\,y_{k}\,y_{k}^T\end{align*}$$ where $$\rho_{k} = \frac{1}{s_{k}^T\,y_{k}}.$$ 
>		- **BFGS** $$\begin{align*}B_{k+1} &= B_{k} - \frac{B_{k}\,s_{k}\,s_{k}^T\,B_{k}}{s_{k}^T\,B_{k}\,s_{k}} + \frac{y_{k}^T\,y_{k}}{y_{k}^T\,s_{k}}\end{align*}$$
>	1. update index $k \leftarrow k+ 1.$   

- [[Newton Method]]
- [[Line Search Strategies for Optimal Stepsize]]
- [[Positive Semidefinite Transformation]]

## Explanation

>[!quote]
>**Quasi-Newton search directions** provide an attractive alternative to **Newton’s method** in that they *do not require computation* of the **Hessian** and yet still attain a **superlinear** *rate of convergence*. In place of the true Hessian $\nabla^2 f(x_{k})$, they use an *approximation* $B_{k}$, which is *updated after each step* to take account of the additional knowledge gained during the step. The updates make use of the fact that **changes in the gradient** $g$ provide information about the *second derivative* of $f$ along the search direction.
>
>-- [[Numerical Optimization by Nocedal]] pp 23


>[!quote]
>This is the **fundamental idea** of **quasi-Newton updating**: Instead of *recomputing the approximate Hessians (or inverse Hessians)* from scratch at every iteration, we apply a *simple* modification that **combines the most recently observed information** about the *objective function* with the **existing knowledge** embedded in our *current Hessian approximation*.
>
>-- [[Numerical Optimization by Nocedal]] pp 139

## BFGS Method

>[!quote]
>Some **practical implementations** of quasi-Newton methods *avoid* the need to **factorize** $B_{k}$ at each iteration by **updating the inverse** of $B_{k}$, instead of $B_{k}$ itself. In fact, the equivalent formula applies to inverse $H_{k} =B_{k}^{-1}.$

## Numerical Solution for System of Linear Equations

>[!important]
>It is important to note that all of the second-order gradient method is based on solving the **secant equation**
>$$
>\nabla^2 f(x_{k})\,s_{k} = y_{k} \quad \text{ or } \quad  \left(\nabla^2 f(x_{k})\right)^{-1}\,s_{k} = y_{k}
>$$
>Similarly, by [[Necessary and Sufficient Condition for Local Minimum of Smooth Function]], majority of *gradient methods* involves solving the first-order condition
>$$
>\nabla f(x_{k}) = 0
>$$
>
>This means that these methods can be used to solve the **systems of linear equations**.

- [[System of Linear Equations or Linear System]]



-----------
##  Recommended Notes and References

- [[Gradient Descent Algorithm]]

- [[Nonlinear Programming by Bertsekas]] pp 148
- [[Numerical Optimization by Nocedal]] pp 22
- [[Convex Optimization by Boyd]] pp 496