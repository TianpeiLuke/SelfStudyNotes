---
tags:
  - concept
  - optimization/algorithm
keywords:
  - BFGS_algorithm
topics:
  - optimization
  - optimization/algorithm
name: BFGS Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: BFGS algorithm or *Broyden-Fletcher-Goldfarb-Shanno algorithm*

>[!important] Definition
>Consider the *unconstrained  minimization problem* of a *twice continuous differentiable* function $f: \mathbb{R}^{n} \to \mathbb{R}$. 
>
>The **BFGS algorithm** is a *quasi-Newton algorithm*, and it works as follows
>0. Initiate with  $x_{0}$ and *convergence tolerance* $\epsilon >0$ and *inverse Hessian approximation* $H_{0} \succ 0.$
>1. $k \leftarrow 0$
>2. While $\lVert \nabla f(x_{k}) \rVert > \epsilon$:
>	1. compute the **search direction** $$d_{k} = - H_{k}\,\nabla f(x_{k})$$
>	2. set new point via **generalized gradient descent** $$x_{k+1} = x_{k} + \alpha_{k}\;d_{k}$$ where $\alpha_{k}$ is computed from a *line search procedure* to satisfies the *Wolfe conditions*
>	3. compute the **displacement** of *position* and *change of gradient* $$s_{k} = x_{k+1} - x_{k}; \quad y_{k} = \nabla f(x_{k+1}) - \nabla f(x_{k})$$
>	4. update the **approximation** of **inverse Hessian** via the **DFP updating formula**
>	   $$H_{k+1} = \left(I - \rho_{k}\;s_{k}\,y_{k}^{T}\right)\,H_{k}\,\left(I - \rho_{k}\;y_{k}\,s_{k}^{T}\right) + \rho_{k}s_{k}\,s_{k}^T$$ where the *weight* is computed via  $$\rho_{k} = \frac{1}{y_{k}^T\,s_{k}}.$$
>	5. update index $k \leftarrow k+ 1.$   

^954dd0

- [[Secant Equation and Quasi-Newton Methods]]
- [[Gradient Descent Algorithm]]
- [[Newton Method]]


## Explanation

>[!quote]
>**Quasi-Newton search directions** provide an attractive alternative to **Newton’s method** in that they *do not require computation* of the **Hessian** and yet still attain a **superlinear** *rate of convergence*. In place of the true Hessian $\nabla^2 f(x_{k})$, they use an *approximation* $B_{k}$, which is *updated after each step* to take account of the additional knowledge gained during the step. The updates make use of the fact that **changes in the gradient** $g$ provide information about the *second derivative* of $f$ along the search direction.
>
>-- [[Numerical Optimization by Nocedal]] pp 23

>[!quote]
>Some **practical implementations** of quasi-Newton methods *avoid* the need to **factorize** $B_{k}$ at each iteration by **updating the inverse** of $B_{k}$, instead of $B_{k}$ itself. In fact, the equivalent formula applies to inverse $H_{k} =B_{k}^{-1}.$

>[!quote]
>This is the **fundamental idea** of **quasi-Newton updating**: Instead of *recomputing the approximate Hessians (or inverse Hessians)* from scratch at every iteration, we apply a *simple* modification that **combines the most recently observed information** about the *objective function* with the **existing knowledge** embedded in our *current Hessian approximation*.
>
>-- [[Numerical Optimization by Nocedal]] pp 139


## Secant Equation

![[Secant Equation and Quasi-Newton Methods#^85e2d7]]

![[Secant Equation and Quasi-Newton Methods#^035e08]]

- [[Secant Equation and Quasi-Newton Methods]]

>[!important] Definitiion
>*Secant equation* holds for positive definition matrix $B_{k}$ *only if* the **curvature condition** is satisfied
>$$
>y_{K}^T s_{k} > 0.
>$$

## DFP Updating Formula

>[!info]
>If the *curvature condition* is satisfied, the *secant equation* always has a solution in $\mathcal{S}_{++}^{n}.$ Moreover, since $\text{dim}(\mathcal{S}_{++}^n) = \frac{n(n+1)}{2}$, and the number of constraints of secant equation is $n$, the *solutions* of the system of equations is a **subspace**.

>[!important] Definition
>To uniquely determine $B_{k+1}$ given $B_{k}$, we impose a **proximity constraint** which choose, among all *symmetric positive definite matrices satiefying the secant equation*, the *closest* to 
>$B_{k}$. That is, we solve the *convex optimization problem*
>$$
>\begin{align*}
> \min_{B \in \mathcal{S}_{++}^n} &\lVert B - B_{k} \rVert_{W}^2 \\
> \text{s.t. }&\; B\,s_{k} = y_{k}
>\end{align*}
>$$
>where $$\lVert A \rVert_{W} = \lVert W^{1 / 2}\,A\,W^{1 / 2} \rVert_{F} = \sqrt{ \sum_{i,j = 1}^{n} C_{i,j}^2 }$$ is the **weighted Frobenius norm** of matrix and the *weight matrix* $W$ is any matrix satisfying $$W\,y_{k} = s_{k}.$$
>
>We can further relax the constraint on $B \in \mathcal{S}_{++}^n$ so that we *only require symmetric matrix*. This gives
>$$
>\begin{align*}
> \min_{B \in \mathbb{R}^{n\times n} } &\lVert B - B_{k} \rVert_{W}^2 \\
> \text{s.t. }&\; B\,s_{k} = y_{k} \\
> &\; B = B^T
>\end{align*}
>$$
>This is similar to a **least equation estimation** problem.

- [[Convex Optimization Problem]]
- [[Least Square Estimation]]
- [[Positive Semidefinite Transformation]]

>[!info]
>The choice of *weighted Frobenius norm* is to have **scale-invariant solution**.
>
>A choice of $W_{k}$ is 
>$$
>W_{k} = \left(\tilde{G}_{k}\right)^{-1}, \quad \tilde{G}_{k} := \int_{0}^{1}\nabla^2 f\left(x_{k} + \tau\,\alpha_{k}\,p_{k}\right)d\tau. 
>$$
>This way
>$$
>y_{k} = \tilde{G}_{k}\,s_{k} = \tilde{G}_{k}\,\alpha_{k}\,p_{k}. 
>$$


>[!important] Definition
>The **unique solution** of above optimization problem is
>$$
>\begin{align*}
> B_{k+1} &= \left(I - \rho_{k}\,y_{k}s_{k}^T\right) \,B_{k}\,\left(I - \rho_{k}\,s_{k}y_{k}^T\right) + \rho_{k}\,y_{k}\,y_{k}^T
>\end{align*}
>$$
>where
>$$\rho_{k} = \frac{1}{s_{k}^T\,y_{k}}.$$ 
>
>This formula is called the **DFP updating formula**.

## DFP Updating Formula for Inverse

>[!important] Definition
>Denote $$H_{k} = B_{k}^{-1}.$$
>The **Sherman-Morrison-Woodbury formula** leads to the update of *inverse of Hessian approximate* as
>$$
>\begin{align*}
>H_{k+1} &= H_{k} - \frac{H_{k}\,y_{k}\,y_{k}^T\,H_{k}}{y_{k}^T\,H_{k}\,y_{k}} + \frac{s_{k}^T\,s_{k}}{s_{k}^T\,y_{k}}
>\end{align*}
>$$
>This is a **rank-2 modification**.

- [[Sherman-Morrison-Woodbury Matrix Inversion Formula]]

## BFGS Updating Formula

>[!important] Definition
>Instead of imposing constraint on *Hessian approximate* $B_{k}$, we directly impose constraint on the *inverse of Hessian approximate* $H_{k} := B_{k}^{-1}$. The **secant equation** becomes
>$$
> H_{k+1}y_{k} = s_{k}.
>$$
>The **proximity condition** leads to the optimization problem
>$$
>\begin{align*}
> \min_{H \in \mathbb{R}^{n\times n} } &\lVert H - H_{k} \rVert_{W}^2 \\
> \text{s.t. }&\; H\,y_{k} = s_{k} \\
> &\; H = H^T
>\end{align*}
>$$
>where $$\lVert A \rVert_{W} = \lVert W^{1 / 2}\,A\,W^{1 / 2} \rVert_{F}$$ is the **weighted Frobenius norm** of matrix and the *weight matrix* $W$ is any matrix satisfying $$W\,s_{k} = y_{k}.$$

>[!important] Definition
>The **unique solution** of above optimization problem is
>$$
>\begin{align*}
> H_{k+1} &= \left(I - \rho_{k}\,s_{k}y_{k}^T\right) \,H_{k}\,\left(I - \rho_{k}\,y_{k}s_{k}^T\right) + \rho_{k}\,s_{k}\,s_{k}^T
>\end{align*}
>$$
>where
>$$\rho_{k} = \frac{1}{y_{k}^T\,s_{k}}.$$ 
>
>This formula is called the **DFP updating formula**.

>[!info]
>Notice that compare to **DFP updating formula**, the **BFGS updating formula** has the same form and the only changes are 
>$$
>B_{\cdot} \leftarrow H_{\cdot}, \;\; y_{k} \leftarrow s_{k}, \;\; s_{k} \leftarrow y_{k}.
>$$
>This is due to **homogeneity of scant equation**, 
>$$
>B_{k}s_{k} = y_{k} \;\; \iff \;\; H_{k}y_{k} = s_{k}.
>$$
>
>However, the **stability** and **convergence speed** for *BFGS* is much better than *DFP*. This is due to the **instability** of **numerical matrix inversion**.





-----------
##  Recommended Notes and References

- [[Limited Memory BFGS]]
- [[Newton Method]]
- [[Unconstrained Global Minimization]]
- [[Positive Semidefinite Transformation]]

- [[Numerical Optimization by Nocedal]] pp 139
- [[Nonlinear Programming by Bertsekas]]
- [[Deep Learning by Goodfellow]] pp 307 - 308