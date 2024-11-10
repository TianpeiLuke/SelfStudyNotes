---
tags:
  - concept
  - optimization/algorithm
  - optimization/convex_optimization
keywords:
  - BFGS_algorithm
topics:
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
> \text{s.t. }&\; B\,s_{k} = y_{k}
>\end{align*}
>$$
>This is similar to a **least equation estimation** problem.

^044857

- [[Convex Optimization Problem]]
- [[Space of Symmetric Positive Semidefinite Matrices]]
- [[Least Square Estimation]]
- [[Positive Semidefinite Transformation]]
- [[Hermitian or Symmetric Matrix]]
- [[Frobenius Norm of Matrix]]

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


#### Proof

>[!info] Proof
>Denote $$\hat{B} = W^{1/2}BW^{1/2}, \quad \hat{B}_{k} = W^{1/2}BW^{1/2} $$ so
>$$
>\begin{align*}
>\lVert B - B_{k} \rVert_{W}^2 &= \lVert W^{1/2}BW^{1/2} - W^{1/2}B_{k}W^{1/2} \rVert_{F}^2 \\
>&:= \lVert \hat{B} - \hat{B}_{k} \rVert_{F}^2
>\end{align*}
>$$
>Since 
>$$
>\begin{align*}
> Wy_{k}  &= s_{k}\\
> W^{1/2}y_{k}  &= W^{-1/2}s_{k}
>\end{align*}
>$$
>Denote $$\hat{y}_{k} = W^{1/2}y_{k}, \quad \hat{s}_{k} = W^{-1/2}s_{k}.$$  The above have
>$$
>\hat{y}_{k} = \hat{s}_{k} \quad (1)
>$$
>Finally
>$$
>\begin{align*}
>W^{1/2}Bs_{k} &= W^{1/2}y_{k} = \hat{y}_{k} \\
> \iff W^{1/2}BW^{1/2} W^{-1/2}s_{k} &= \hat{y}_{k} \\
> \iff \hat{B}\hat{s}_{k} &= \hat{y}_{k} \quad (\text{ substitute }(1))\\
> \implies \hat{B}\hat{s}_{k} &= \hat{s}_{k} 
>\end{align*}
>$$

>[!important]
>So the optimization becomes
>$$
>\begin{align*}
> \min_{B \in \mathbb{R}^{n\times n} } &\lVert \hat{B} - \hat{B}_{k} \rVert_{F}^2 \\
> \text{s.t. }&\; \hat{B}\,\hat{s}_{k} = \hat{s}_{k} 
>\end{align*}
>$$
>where
>- The constraint states that $\hat{s}_{k}$ is the **eigenvector** of $\hat{B}$ associated with **eigenvalue** $1$.
>- This problem is closely related to **low-rank approximation problem.**

- [[Low Rank Approximation of Matrix and Eckhart-Young Theorem]]


>[!info]
>Define $$u = \frac{\hat{s}_{k}}{\lVert \hat{s}_{k} \rVert }.$$ Let the eigendecomposition of symmetric $\hat{B}$ be $$\hat{B} = U\Lambda U^{T}$$ where $$\Lambda = \text{diag}(1, \lambda_{2} \,{,}\ldots{,}\,\lambda_{n})$$
>
>The orthogonal matrix $U$ has $u$ as one column, and others are orthornormal to $u$, i.e. 
>$$U = [u, u_{\perp}]$$

- [[Eigenvalue and Eigenvector for Linear Map]]
- [[Spectral Theorem of Self-Adjoint Map and Eigen decomposition]]

>[!info]
>Note that $u_{\perp}$ and $u$ are **$\hat{B}$-conjugate** since $$\left\langle  u_{\perp}\,,\,\hat{B}u  \right\rangle = \left\langle  u_{\perp}\,,\, u   \right\rangle =0$$ while $$\left\langle  u\,,\,\hat{B}u  \right\rangle = \left\langle  u\,,\, u   \right\rangle =1.$$ This is due to $$\hat{B}u = u.$$

- [[Conjugate Vector with respect to Positive Definite Transformation]]
- [[Perron-Frobenius Theorem on Irreducible Nonnegative Matrix]]
- [[Stochastic Matrix and Doubly Stochastic Matrix]]

>[!info] 
>The above objective can be reformulated as
>$$
>\begin{align*}
>\lVert \hat{B} - \hat{B}_{k} \rVert_{F}^2 &= \lVert U^{T} \hat{B} U- U^{T} \hat{B}_{k} U \rVert_{F}^2 \\[5pt]
>&= \lVert \Lambda - U^{T} \hat{B}_{k} U \rVert_{F}^2 \\[5pt]
>&= \left\lVert \left[ \begin{array}{cc} 1 & \\ & u_{\perp}^{T} \hat{B} u_{\perp}\end{array} \right]  - \left[ \begin{array}{cc} u^{T} \hat{B}_{k} u & u^{T} \hat{B}_{k} u_{\perp} \\ u_{\perp}^{T} \hat{B}_{k} u & u_{\perp}^{T} \hat{B}_{k} u_{\perp}\end{array} \right]   \right\rVert_{F}^2 \\[10pt]
>&= (u^{T} \hat{B}_{k} u - 1)^2 + \lVert u^{T} \hat{B}_{k} u_{\perp}  \rVert_{F}^2 +   \lVert u_{\perp}^{T} \hat{B}_{k} u  \rVert_{F}^2 + \lVert u_{\perp}^{T} \hat{B} u_{\perp} -  u_{\perp}^{T} \hat{B}_{k} u_{\perp} \rVert_{F}^2 
>\end{align*}
>$$
>The first three terms are fixed since $\hat{B}_{k}$ is fixed. So to minimize the objective, we have to minimize
>$$
>\begin{align*}
>\lVert u_{\perp}^{T} \hat{B} u_{\perp} -  u_{\perp}^{T} \hat{B}_{k} u_{\perp} \rVert_{F}^2 
>\end{align*}
>$$
>which leads to **equation** $$ u_{\perp}^{T} \hat{B} u_{\perp} =  u_{\perp}^{T} \hat{B}_{k} u_{\perp}.$$
>The corresponding *optimal solution* for $\hat{B}$ becomes
>$$
>\begin{align*}
>\hat{B} &= U \left[ \begin{array}{cc} 1 & \\ & u_{\perp}^{T} \hat{B} u_{\perp}\end{array} \right] U^{T} \\[5pt]
>&= U \left[ \begin{array}{cc} 1 & \\ & u_{\perp}^{T} \hat{B}_{k} u_{\perp}\end{array} \right] U^{T}\\[5pt]
>&= uu^{T} + (u_{\perp}u_{\perp}^{T})\,\hat{B}_{k}\,(u_{\perp}u_{\perp}^{T}) 
>\end{align*}
>$$
>Note that $$I = [u, u_{\perp}][u, u_{\perp}]^{T} = uu^{T} + u_{\perp}u_{\perp}^{T}$$ so $$u_{\perp}u_{\perp}^{T} = I - uu^{T}$$

>[!important]
>The optimal solution has the form
>$$
>\hat{B} = (I - uu^{T})\,\hat{B}_{k}\,(I - uu^{T}) + uu^{T}
>$$
>where $u = \hat{s}_{k} / \lVert \hat{s}_{k} \rVert.$


>[!info]
>Convert it back to original form
>$$
>\begin{align*}
>W^{1/2}BW^{1/2} &=(I - uu^{T})\,\hat{B}_{k}\,(I - uu^{T}) + uu^{T} \\[5pt]
> \implies B &= W^{-1/2}(I - uu^{T})\,\hat{B}_{k}\,(I - uu^{T})W^{-1/2} + W^{-1/2}uu^{T}W^{-1/2}
>\end{align*}
>$$
>since $$Wy_{k}  = s_{k} \implies  W^{1/2}y_{k}  = W^{-1/2}s_{k} = \hat{s}_{k} \implies y_{k} =  W^{-1/2}\hat{s}_{k}$$ and $$\lVert \hat{s}_{k} \rVert^2 = \hat{s}_{k}^{T}\hat{s}_{k} = s_{k}^{T}W^{-1}s_{k} =  s_{k}^{T}y_{k}$$ we have
>$$
>\begin{align*}
>W^{-1/2}uu^{T}W^{-1/2}&= W^{-1/2}\frac{\hat{s}_{k}\hat{s}_{k}^{T}}{\lVert \hat{s}_{k} \rVert^2 }W^{-1/2} = \frac{y_{k}y_{k}^T}{s_{k}^{T}y_{k}}
>\end{align*}
>$$
>and
>$$
>\begin{align*}
>W^{-1/2}uu^{T}\,\hat{B}_{k}\,uu^{T}\,W^{-1/2}&= (W^{-1/2}uu^{T}\,W^{1/2})B_{k}(W^{1/2}\,uu^{T}\,W^{-1/2}) \\[10pt]
>\text{where } W^{-1/2}uu^{T}\,W^{1/2} &=  W^{-1/2}\frac{\hat{s}_{k}\hat{s}_{k}^{T}}{\lVert \hat{s}_{k} \rVert^2 }W^{1/2} \\[5pt]
>&=\frac{y_{k}y_{k}^TW}{s_{k}^{T}y_{k}} = \frac{y_{k}s_{k}^T}{s_{k}^{T}y_{k}}
>\end{align*}
>$$
>As a result
>$$
>\begin{align*}
>B &= W^{-1/2}(I - uu^{T})\,\hat{B}_{k}\,(I - uu^{T})W^{-1/2} + W^{-1/2}uu^{T}W^{-1/2} \\[5pt]
>&= \left(I -  \frac{y_{k}s_{k}^T}{s_{k}^{T}y_{k}}\right)\,B_{k}\,\left(I -  \frac{s_{k}y_{k}^T}{s_{k}^{T}y_{k}}\right) + \frac{y_{k}y_{k}^T}{s_{k}^{T}y_{k}} \\[5pt]
>&= \left(I -  \rho_{k}\, y_{k}s_{k}^T \right)\,B_{k}\,\left(I -  \rho_{k}\, s_{k}y_{k}^T \right) + \rho_{k}\, y_{k}y_{k}^T
>\end{align*}
>$$
>End of Proof.

- [Quasi-newton methods: Understanding DFP updating formula](https://math.stackexchange.com/questions/2091867/quasi-newton-methods-understanding-dfp-updating-formula)

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

^09e0ca

- [[Sherman–Morrison–Woodbury Matrix Inversion Formula]]

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

^7f5c27

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
>This formula is called the **BFGS updating formula**.

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


- [[Sherman–Morrison–Woodbury Matrix Inversion Formula]]
- [[System of Linear Equations or Linear System]]


- [[Numerical Optimization by Nocedal]] pp 139
- [[Nonlinear Programming by Bertsekas]]
- [[Deep Learning by Goodfellow]] pp 307 - 308