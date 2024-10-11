---
tags:
  - concept
  - optimization/convex_optimization
  - optimization/theory
  - numerical_methods/numerical_linear_algebra
keywords:
  - kkt_system
  - kkt_matrix
topics:
  - convex_analysis
  - optimization/theory
  - numerical_linear_algebra
name: KKT Matrix and KKT System for Optimization with Equality Constraints
date of note: 2024-10-08
---

## Concept Definition

>[!important]
>**Name**: KKT Matrix and KKT System for Optimization with Equality Constraints

![[System of Linear Equations or Linear System#^818e89]]

![[Karush-Kuhn-Tucker Optimality Condition#^a09722]]


>[!important] Definition
>A matrix has the **Karush-Kuhn-Tucker (KKT) structure** if it is of the form
>$$
>\left[ \begin{array}{cc}
> H & A \\[5pt]
> A^{T} & 0
>\end{array} \right] 
>$$
>where 
>- $H\in \mathcal{S}_{++}^{p}$ is *positive definite*
>- $A\in \mathbb{R}^{p\times m}$ with *full column rank*, i.e. $\text{rank}(A) = m$.
>  
>The **KKT system of equations** is of the form  
>$$
>\left[ \begin{array}{cc}
> H & A \\[5pt]
> A^{T} & 0
>\end{array} \right] 
>\left[ \begin{array}{c}
> x  \\[5pt]
> v 
>\end{array} \right] = 
>\left[ \begin{array}{c}
>  -c \\[5pt]
>  b
>\end{array}\right]
>$$


- [[System of Linear Equations or Linear System]]
- [[Surjective Injective Invertible Linear Map and Rank]]
- [[Positive Semidefinite Transformation]]

### Properties of KKT System

![[Schur Complement and Inversion of Block Matrix#^eb8bd3]]


>[!important] Proposition
>If  a *symmetric matrix* $\tilde{H} \in \mathcal{S}^{m+p}$ has **KKT structure**
>$$
>\widetilde{H} = \left[ \begin{array}{cc}
> H & A \\[5pt]
> A^{T} & 0
>\end{array} \right] 
>$$
>where $H\in \mathcal{S}_{++}^{p}$ and $A\in \mathbb{R}^{p\times m}$ with *full column rank* with $p > m$, then the **Schur complement** of $H$ of $\widetilde{H}$ is **negative definite**
>$$
>S := \widetilde{H} / H := - A^{T}H^{-1}A \prec 0
>$$
>or $$- \widetilde{H} / H \in \mathcal{S}_{++}^{m}$$

- [[Schur Complement and Inversion of Block Matrix]]

>[!info]
>We can find **Cholesky factorization** of $-\widetilde{H} / H$
>$$
>-\widetilde{H} / H = GG^{T}
>$$
>where $G\in \mathbb{R}^{m\times m}$ is **lower triangular**.

- [[Cholesky Factorization of Hermitian Positive Definite Matrices]]
- [[Triangular Matrix and Block Triangular Matrix]]

>[!important] Proposition
>Let $\tilde{H} \in \mathcal{S}^{m+p}$ be a **KKT matrix**
>$$
>\widetilde{H} = \left[ \begin{array}{cc}
> H & A \\[5pt]
> A^{T} & 0
>\end{array} \right] 
>$$
>where $H \succeq\, 0$ in $\mathcal{S}_{+}^{p}$ and $A\in \mathbb{R}^{p\times m}$ with *full column rank*, i.e. $\text{rank}(A) = m$.
>
>Then the following statements are **equivalent**:
>- $\widetilde{H}$ is **nonsingular**;
>- $H$ and $A$ has **no non-trivial common null space**, i.e. $$\text{Ker}(H) \cap \text{Ker}(A) = \left\{ 0 \right\};$$  
>- $H$ is **positive definite** on **null space** of $A$, $$P|_{\text{ker}(A)} \succ\, 0\; \iff \;\; Ax = 0, \; x\neq 0 \;\; \implies \;\; x^{*}Hx > 0,$$
>- For any $F\in \mathbb{R}^{p\times (p - m)}$ where $$\text{Im}(F) = \text{Ker}(A)$$ we have  $$F^{T}HF \succ\, 0$$
>  
>Note that if $H \succ\, 0$, then the *KKT matrix is nonsingular*.  


- [[Surjective Injective Invertible Linear Map and Rank]]
- [[Range and Kernel of Linear Map]]
- [[Fundamental Subspaces from Linear Map]]
- [[Convex Optimization by Boyd]]  pp 523


## Explanation


### KKT System in Quadratic Programming with Equality Constraint

![[Quadratic Programming#^387671]]

- [[Quadratic Programming]]
- [[Fenchel Duality Theorem]]

>[!important] Definition
>A **quadratic programming (QP)** problem is easy if $H \succ 0$ is *symmetric positive definite*, and the constraints are the *equality constraints*
>$$
>\begin{align*}
> \min_{x\in \mathcal{X} \subset \mathbb{R}^{n}}&\; \frac{1}{2} \left\langle  x\,,\,H x \right\rangle + \left\langle  c\,,\,x  \right\rangle \\[5pt]
>\text{s.t. } &A^{T}x = b.
>\end{align*}
>$$
>Then the KKT conditions for **primal optimal** and **dual optimal solution** $x^{*}$ are two systems of equations
>- The **primal feasible equation** $$A^{T}x^{*} = b$$
>- The **dual feasible equation** $$Hx^{*} + c + A v^{*} = 0$$
>  
>Combining these two equations, we have the **KKT system**  
>$$
>\left[ \begin{array}{cc}
> H & A \\[5pt]
> A^{T} & 0
>\end{array} \right] 
>\left[ \begin{array}{c}
> x^{*}  \\[5pt]
> v^{*} 
>\end{array} \right] = 
>\left[ \begin{array}{c}
>  -c \\[5pt]
>  b
>\end{array}\right]
>$$
>- If the **KKT matrix** $\tilde{H}$ is **nonsingular**, then there exists a **unique primal-dual pair** $(x^{*}, v^{*})$ as the *optimal solution of the QP*.
>- If the **KKT matrix** $\tilde{H}$ is **singular** but the **KKT system is solvable**, then there **any** *primal-dual pair* $(x^{*}, v^{*})$ in $$\text{Ker}(\tilde{H})$$ is an *optimal solution of the QP*.
>- If  **KKT system is not solvable**, then the corresponding QP is **unbounded** and the optimal value is $-\infty$.

^f43071

- [[Karush-Kuhn-Tucker Optimality Condition]]
### KKT System in Convex Optimization with Equality Constraint

>[!important] Definition
>Consider a  **convex optimization** problem with the *equality constraints*
>$$
>\begin{align*}
> \min_{x\in \mathcal{X} \subset \mathbb{R}^{p}}&\; f(x)\\[5pt]
>\text{s.t. } &A^{T}x = b.
>\end{align*}
>$$
>where $f: \mathbb{R}^{p} \to \mathbb{R}$ is *convex* and *twice continuously differentiable* and $A\in \mathbb{R}^{p\times m}$ and $b\in \mathbb{R}^{m}$.
>
>The KKT conditions results in two equations
>- The **primal feasible equation** $$A^{T}x^{*} = b$$
>- The **dual feasible equation** $$\nabla f(x^{*}) + A v^{*}  = 0$$

>[!important] Definition
>Let  $x_{0}$ be a fixed *feasible solution* to above *convex optimization with equality constraint*. 
>
>Consider the **second-order Taylor approximation** of the objective function  
>$$
>\hat{f}(x_{0} + v) = f(x_{0}) + \left\langle v , \nabla f(x_{0}) \right\rangle + \frac{1}{2} \left\langle v , \nabla^2 f(x_{0})v  \right\rangle
>$$
>where $$A^{T}(x_{0} + v)  = b \implies A^{T}v = 0.$$
>
>Thus we can find the small incremental increase $\Delta x = v^{*}$ by solving the **quadratic programming problem**
>$$
>\begin{align*}
> \min_{v \in \mathbb{R}^{p}}&\; f(x_{0}) + \left\langle v , \nabla f(x_{0}) \right\rangle + \frac{1}{2} \left\langle v , \nabla^2 f(x_{0})v  \right\rangle \\[5pt]
>\text{s.t. } &A^{T}v = 0.
>\end{align*}
>$$
>The solution corresponding to one step in **Newton's method**  $$\Delta x = v^{*} := \Delta x_{\text{Newton}}$$ which can be obtained by solving a **KKT system**
>$$
>\left[ \begin{array}{cc}
> \nabla^2 f(x_{0}) & A \\[5pt]
> A^{T} & 0
>\end{array} \right] 
>\left[ \begin{array}{c}
> \Delta x  \\[5pt]
> w^{*} 
>\end{array} \right] = 
>\left[ \begin{array}{c}
>  -\nabla f(x_{0}) \\[5pt]
>  0
>\end{array}\right]
>$$
>- $w^{*}$ is the dual optimal solution for the quadratic problem.
>- The **KKT system** can be interpreted as the **linearized approximation** of the *KKT conditions* near a feasible point $x_{0}$ $$\begin{align*} A^{T}(x_{0} + \Delta x) &= b \\[5pt] \iff A^{T}  \Delta x &= 0\\[5pt]  \nabla f(x_{0} + \Delta x) + A w & =0 \\[5pt] \approx \nabla f(x_{0}) +  \nabla^2 f(x_{0})\,\Delta x  + A w  &= 0 \\[5pt] \iff \nabla^2 f(x_{0})\,\Delta x  + A w  &= - \nabla f(x_{0}) \end{align*}$$

^e0bfc8

- [[Convex Optimization Problem]]
- [[Karush-Kuhn-Tucker Optimality Condition]]
- [[Newton Method]]
- [[Secant Equation and Quasi-Newton Methods]]





## KKT System in Gaussian Belief Propagation

![[Gaussian Belief Propagation#^919312]]

![[Gaussian Belief Propagation#^d985d2]]

![[Gaussian Belief Propagation#^967ffd]]

- [[Gaussian Belief Propagation]]



-----------
##  Recommended Notes and References



- [[Sequential Quadratic Programming]]

- [[Convex Optimization Problem]]
- [[Methods of Lagrangian Multipliers]]
- [[Karush-Kuhn-Tucker Optimality Condition]]
- [[Least Square Estimation]]
- [[Normal Equations and Newton System of Equations]]
- [[Newton Method]]
- [[Secant Equation and Quasi-Newton Methods]]
- [[BFGS Algorithm]]
- [[Limited Memory BFGS]]


- [[Hermitian or Symmetric Matrix]]
- [[Positive Semidefinite Transformation]]

- [[Krylov Subspace and Krylov Matrix]]
- [[Krylov Subspace Methods]]
- [[GMRES as Regression on Krylov Space]]
- [[Schur Complement and Inversion of Block Matrix]]


- [[Gaussian Belief Propagation]]



- [[Numerical Optimization by Nocedal]] pp 275
- [[Convex Optimization by Boyd]]  pp 531 - 523, 542 - 547, 677
