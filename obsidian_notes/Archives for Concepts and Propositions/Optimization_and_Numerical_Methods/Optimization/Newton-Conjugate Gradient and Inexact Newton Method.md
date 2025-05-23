---
tags:
  - concept
  - optimization/algorithm
  - optimization/theory
keywords:
  - newton_cg_algorithm
  - inexact_newton_method
topics:
  - optimization/algorithm
name: Newton-Conjugate Gradient and Inexact Newton Method
date of note: 2024-07-02
---

## Concept Definition

>[!important]
>**Name**: Newton-Conjugate Gradient and Inexact Newton Method

### Inexact Newton Methods

>[!important] Definition
>Consider the problem of *large-scale optimization* $$\min f(x)$$ where $f$ is twice continuous differentiable.
>
>At each iteration, *Newton method* solves the *normal equation* for descent direction $d_{k}$:
>$$
>\nabla^2 f(x_{k})\,d_{k} = - \nabla f(x_{k})
>$$
>We can solve this *symmetric positive definite system* of equations using *iterative methods*
>- the *conjugate gradient method* when  $\nabla^2 f(x_{k}) \succ\, 0$;
>- or the *Lanczos iteration* which reduce the Hessian $\nabla^2 f(x_{k})$ into the tridiagonal matrix to handle *negative curvatures*.
>  
>We refer to this family of *iterative methods* by the general name **inexact Newton methods**.  

^85f6f1

- [[Newton Method]]
- [[Normal Equations and Newton System of Equations]]
- [[Iterative Methods to approximate Solution of Large-Scale Linear System]]
- [[Conjugate Gradient Algorithm Linear]]
- [[Conjugate Gradient Algorithm Lanczos]]
- [[Conjugate Gradient Algorithm Nonlinear]]
- [[Lanczos Iteration for Tridiagonal Reduction of Large Matrix]]
- [[Krylov Subspace Methods]]


>[!important] Definition
>Consider one step of *Newton's method* which solves the *symmetric positive definite system* for direction $d_{k}$
>$$
>\nabla^2 f(x_{k})\,d_{k} + \nabla f(x_{k}) = 0
>$$
>Define the **residual** as 
>$$
>r_{k} = \nabla^2 f(x_{k})\,d_{k} + \nabla f(x_{k}),
>$$
>where $d_{k}$ is the *inexact Newton direction*.
>
>The *termination condition* is set as
>$$
>\lVert r_{k} \rVert_{2}  \le \eta_{k} \lVert \nabla f(x_{k}) \rVert_{2} 
>$$
>where the sequence $$\eta_{k},\quad k=1\,{,}\ldots{,}\,$$ is called the **forcing sequence.**

### Local Convergence of Inexact Newton Methods

>[!important] Proposition
>Suppose that $\nabla^2 f(x)$ *exists* and is *continuous* in the neighborhood of a minimizer $x^{*}$, 
>- with **positive definite Hessian** at $x^{*}$ $$\nabla^2 f(x^{*}) \succ\, 0.$$
>
>Consider the iterates $$x_{k+1} = x_{k} + d_{k}$$ 
>- where $d_{k}$ satisfies the **termination condition** $$\lVert r_{k} \rVert_{2}  \le \eta_{k} \lVert \nabla f(x_{k}) \rVert_{2}$$ with $$r_{k} = \nabla^2 f(x_{k})\,d_{k} + \nabla f(x_{k}).$$
>- Assume that there exists some $\eta \in [0,1)$ such that $$\eta_{k} \le \eta, \quad k=1\,{,}\ldots{,}\,$$
>
>Then, if the starting point $x_{0}$ is *sufficiently near* $x^{*}$, 
>- the **sequence $\{x_{k}\}$ converges** to  $x^{*}$ and 
>- $\{x_{k}\}$ satisfies $$\lVert \nabla^2 f(x^{*})\left( x_{k+1} - x^{*} \right) \rVert_{2} \le \hat{\eta}\;\lVert \nabla^2 f(x^{*})\left( x_{k} - x^{*} \right) \rVert_{2} $$ for some $\hat{\eta} \in (\eta,1).$


>[!important] Proposition
>Suppose the *conditions in above proposition* hold, and suppose that $\{x_{k}\}$ generated by **inexact Newton methods converge** to $x^{*}$.
>
>Then the **rate of convergence** is **super-linear** i.e. $$\lim_{ k \to \infty } \frac{\lVert \nabla f_{k+1} \rVert}{\lVert \nabla f_{k} \rVert } = 0$$ if $$\eta_{k} \to 0.$$ 
>
>
>If, in addition, 
>- $\nabla^2 f(x)$ is **Lipschitz continuous** for $x$ near $x^{*}$, 
>- and if $$\eta_{k} = O(\lVert \nabla f_{k} \rVert_{2}),$$
>
>then the *convergence* is **quadratic**, i.e. $$\nabla f_{k+1} = O(\lVert \nabla f_{k} \rVert^2 ).$$  

- [[Lipschitz Continuous Function]]
- [[Algorithm Big-O Notations and Dominance Relation]]
- [[Algorithm RAM Model and Running-Time Complexity Analysis]]

### Line-Search Newton-Conjugate Gradient

>[!important] Definition
>The **line-search Newton-Conjugate Gradient method** or **truncated Newton method** compute the *search direction* by applying the *CG method* to the Newton equation. $$\nabla^2 f(x_{k})\,d_{k} = - \nabla f(x_{k})$$ 
>- It attempts to satisfies the termination condition $$\lVert r_{k} \rVert_{2}  \le \eta_{k} \lVert \nabla f(x_{k}) \rVert_{2}$$ with $$r_{k} = \nabla^2 f(x_{k})\,d_{k} + \nabla f(x_{k}).$$
>- It terminates the CG iterations when a direction of *negative curvature* (when $\nabla^2 f(x_{k})$ has *negative spectrum*) is generated.

>[!quote]
>- This adaptation of the CG method produces a search direction $d_{k}$ that is a **descent direction**. 
>- Moreover, the adaptation **guarantees** that the **fast convergence rate** of the pure Newton method is **preserved**, provided that the step length $\alpha_{k} = 1$ is used whenever it satisfies the acceptance criteria.
>  
>-- [[Numerical Optimization by Nocedal]]  pp  169

>[!important] Definition
>Consider the problem of solving the following *large-scale optimizataion*:
>$$
> \min_{x}\; f(x)
>$$
>where $f: \mathbb{R}^{d} \to \mathbb{R}$ is *twice continuous differentiable.*
>
>We consider the *Newton system of equations* $$B_{k}\,p_{k} = - \nabla f_{k}$$ at step $k$, where
>- $$B_{k} = \nabla^2 f(x_{k}), \quad \nabla f_{k} := \nabla f(x_{k})$$
>
>The **line-search Newton-conjugate gradient method** or **truncated Newton method** is described as follows:
>- *Require*: Procedures to compute Hessian and gradient for $f$.
>- *Require*: initial *solution* $x_{0}$
>- For $k=0,\,1,\,2\,{,}\ldots{,}\,$
>	- Compute Hessian and gradient $B_k = \nabla^2 f(x_k)$ and gradient $\nabla f_k := \nabla f(x_k)$ for $x_k$
>	- Set *tolerance* $$\epsilon_{k} := \min\left\{ 0.5, \lVert \nabla  f_{k} \rVert  \right\} \lVert \nabla  f_{k} \rVert  $$
>	- Update **descent direction** $p_{k}$ by calling the **Conjugate Gradient subroutine (inner loop)** $$p_{k} = \text{Conjugate-Gradient}(B_{k}, \nabla f_{k},  \epsilon_{k})$$
>	- Update solution via **Newton Method (outer loop)** $$x_{k+1} = x_{k} + \alpha_{k}\,p_{k}$$ where
>		- $\alpha_{k}$ satisfies the **Wolfe, Goldstein, or Armijo** backtracking conditions
>		  
>
>And the **CG-subroutine**, $$\text{Conjugate-Gradient}(B_{k}, \nabla f_{k}, \epsilon_{k}),$$ is described as below:
>- *Require*: the Hessian at $x_{k}$, $B_{k}$
>- *Require*: the gradient at $x_{k}$, $\nabla f_{k}$
>- Set $z_{0} =0$,  $r_{0} = \nabla f_{k}$; and $d_{0} = - r_{0} = -\nabla f_{k}$
>- For $j=0,\,1\,{,}\ldots{,}\,$
>	- If $d_{j}^T\,B_{k}\,d_{j} \le 0$, i.e. the **curvature is negative** 
>		- If $j=0$:
>			- *Return*: $p_{k} = -\nabla f_{k}$
>		- Else:
>			- *Return*: $p_{k} = z_{j}$
>	- compute **step size** $$\alpha_{j} = - \frac{r_{j}^T\,r_{j}}{d_{j}^T\,B_{k}\,d_{j}}$$
>	- generate **new direction** via **conjugate gradient direction**: $$z_{j+1} = z_{j} + \alpha_{j}\,d_{j}$$
>	- update **residual**: $$r_{j+1} = r_{j} + \alpha_{j}\,B_{k}\,d_{j}$$
>	- If the **termination condition** met $\lVert r_{j+1} \rVert \le \epsilon_{k}$:
>		- *Return*: $p_{k} = z_{j+1}.$
>	- compute **step size** for *conjugate gradient update*: $$\beta_{j+1} = \frac{r_{j+1}^T\,r_{j+1}}{r_{j}^T\,r_{j}}$$ 
>	- generate new **conjugate gradient direction**: $$d_{j+1} = - r_{j+1} + \beta_{j+1}\,d_{j}$$


- [[Newton Method]]
- [[Conjugate Gradient Algorithm Linear]]
- [[Line Search Strategies for Optimal Stepsize]]


## Explanation

>[!quote]
>The **line-search Newton-CG** is well suited for large problems, but it has a **weakness**. 
>- When the *Hessian* $\nabla^2 f_{k}$ is **nearly singular**, the line search *Newton–CG direction* can be *long and of poor quality*, requiring many function evaluations in the line search and giving only a small reduction in the function. 
>- To alleviate this difficulty, we can try to **normalize the Newton step**, but good rules for doing so are difficult to determine. They run the risk of undermining the rapid convergence of Newton’s method in the case where the pure Newton step is well scaled. It is preferable to introduce a threshold value into the test $d_{j}^{T} B_{k} d_{j} \le 0$, but good choices of the threshold are difficult to determine. 
>- The **trust-region Newton–CG method** described below deals more effectively with this problematic situation and is therefore preferable, in our opinion.
>  
>-- [[Numerical Optimization by Nocedal]] pp 170
>

>[!quote]
>The line search Newton–CG method **does not require explicit knowledge of the Hessian** $B_{k} = \nabla^2 f_{k}$. Rather, it requires only that we can supply **Hessian–vector products** of the form $$\nabla^2 f_{k} d$$ for any given vector $d$. 
>
>When the user cannot easily supply code to calculate second derivatives, or where the Hessian requires too much storage, the techniques of Chapter 8 (*automatic differentiation and finite differencing*) can be used to calculate these Hessian–vector products. Methods of this type are known as **Hessian-free Newton methods**.
>
>-- [[Numerical Optimization by Nocedal]] pp 170

- [[Automatic Differentiation]]

## Newton-Lanczos Method

![[Newton-Lanczos Method for Large Scale Optimization#^7b8062]]

- [[Newton-Lanczos Method for Large Scale Optimization]]
- [[Minimal Residuals Algorithm and MINRES]]
- [[Conjugate Gradient Algorithm Lanczos]]





-----------
##  Recommended Notes and References





- [[BFGS Algorithm]]
- [[Line Search Strategies for Optimal Stepsize]]



- [[Secant Equation and Quasi-Newton Methods]]
- [[System of Linear Equations or Linear System]]


- [[Primal-Dual Interior Point Method for Convex Optimization]]
- [[Barrier Method for Convex Optimization]]
- [[Quadratic Programming]]
- [[Convex Optimization Problem]]
- [[Convex Function]]
- [[Positive Semidefinite Transformation]]
- [[Hermitian or Symmetric Matrix]]
- [[Taylor Series for Local Polynomial Approximation of Smooth Function]]


- [[Numerical Optimization by Nocedal]] pp 165 - 176