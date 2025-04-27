---
tags:
  - concept
  - optimization/algorithm
  - numerical_methods/numerical_linear_algebra
  - math/matrix_analysis
  - optimization/convex_optimization
  - conjugate_gradient_algorithm/lanczos
  - Lanczos_iteration
  - CG_Lanczos
keywords:
  - conjugate_gradient_linear
  - lanczos_iteration
topics:
  - optimization/algorithm
name: Conjugate Gradient Algorithm Lanczos
date of note: 2024-10-05
---

## Concept Definition

>[!important]
>**Name**: Conjugate Gradient Algorithm Lanczos

### Conjugate Gradient Lanczos Version

>[!important] Definition
>Consider the task of solving a *large-scale linear system* $$Ax = b$$ where $A \succ\, 0$ is *symmetric positive definite.*
>
>The **Lanczos version of conjugate gradient (CG-Lanczos) algorithm** solves above equations *iteratively* in following steps
>1. Call the *Lanczos iteration* to reduce $A$ into tridiagonal matrix $T_{k}$ in each iteration $k$ as $$T_{k} = Q_{k}^{T}AQ_{k}$$ where  $$T_{k} = \left[ \begin{array}{ccccc}\alpha_{1} & \beta_{1} & & 0 \\[5pt] \beta_{1} & \alpha_{2} & \ddots &   \\[5pt]   & \ddots & \ddots &   \beta_{k-1} \\[5pt]  &    & \beta_{k-1} & \alpha_{k}\end{array} \right]  \in \mathbb{R}^{k\times k}$$ and $Q_{k} = [q_{1}\,{,}\ldots{,}\,q_{k}]$ are the collection of *Lanczos vectors* at iteration $k$.
>2. Perform *$LDL^{T}$ factorization* on $T_{k}$ i.e. $$T_{k} = L_{k}\,C_{k}\,L_{k}^{T}$$ where $$L_{k} := \left[ \begin{array}{cccc}1 &  & & 0 \\[5pt] \ell_{1} & 1 &  &   \\[5pt]   & \ddots & \ddots &   0 \\[5pt]  &    & \ell_{k-1} & 1\end{array} \right], \quad  C_{k} := \left[ \begin{array}{cccc} c_{1} & & & \\[5pt] & c_{2}  & & \\[5pt] & & \ddots & \\[5pt] & & & c_{k}\\[5pt]\end{array} \right]  \in \mathbb{R}^{k\times k}$$
>3. Define the **conjugate gradient direction** matrix $D_{k} = [d_{1}\,{,}\ldots{,}\,d_{k}]\in \mathbb{R}^{n\times k}$ that satisfies the equation $$D_{k}L_{k}^{T} = Q_{k}$$
>4. Define **step size vector** for solution update $v_{k} = [\nu_{1} \,{,}\ldots{,}\,\nu_{k}]$ that satisfies the equation $$L_{k}\,C_{k}\,v_{k} = \beta_{0}e_{1}$$ where $r_{0} = b - Ax_{0}.$
>
>
>Specifically, the **CG-Lanczos** algorithm is described as below:
>- *Require*: $A \succ\, 0$ is *symmetric positive definite.* and $b\in \mathbb{R}^{n}$
>- *Require*: initial solution $x_{0}$
>- Initialize 
>	- *residual* $r_{0} = b - Ax_{0}$
>		- If $r_{0} = 0$, *Return* $x_{0}.$
>	- $\beta_{0} = \lVert r_{0} \rVert$,  $q_{0} = 0$, $d_{0} = 0$
>- Set the first Lanczos vector by **normalization** the residual $$q_{1} = \frac{r_{0}}{\beta_{0}}$$
>- For $k=1\,,2\,{,}\ldots{,}\,$
>	- Call **Lanczos iteration** and perform **$LDL^{T}$ factorization**
>		- Compute *diagonal term* of $T_k$  $$\alpha_{k} = q_{k}^{T}Aq_{k}$$
>		- If $k=1$:
>			- Compute the *first diagonal term* of $C$, *first step size* $\nu_{1}$ and the first **conjugate gradient direction** $d_{1}$ as $$c_{1} = \alpha_{1},\quad \nu_{1} = \frac{\beta_{0}}{c_{1}}, \quad d_{1} = q_{1}$$
>		- Else:
>			- Compute the *off-diagonal term* of $L_{k}$ $$\ell_{k-1} = \frac{\beta_{k-1}}{c_{k-1}}$$
>			- Compute the *diagonal term* of $C_{k}$  $$c_{k} = \alpha_{k} - \beta_{k-1}\,\ell_{k-1}$$
>			- Update the **step size** $$\nu_{k} = - \frac{\beta_{k-1}}{c_{k}}\,\nu_{k-1}$$
>			- Update the **conjugate gradient direction** $$d_{k} = q_{k} - \ell_{k-1}\,d_{k-1}$$
>	- Generate new point via **conjugate gradient direction**: $$x_{k} = x_{k-1} + \nu_{k}\,d_{k}$$
>	- Compute **residual** of $Aq_{k}$ on span of $q_{k-1}, q_{k}$, $$r_{k} = Aq_{k} - \beta_{k-1}\,q_{k-1} - \alpha_{k}\,q_{k}$$
>	- Set **off-diagonal term** of $T_k$ as the *norm of residual* $$\beta_{k} = \lVert r_{k} \rVert $$
>	- *Terminate the process* if $\beta_{k} = 0$, 
>		- *Return*: $x_k$ as the solution of linear system.
>	- Compute **new Lanczos vector** via *normalization of residual* $$q_{k+1} = \frac{r_{k}}{\beta_{k}}$$

- [[Hermitian or Symmetric Matrix]]
- [[Positive Semidefinite Transformation]]
- [[Conjugate Gradient Algorithm Linear]]
- [[LDU Factorization of Symmetric Matrix]]
- [[Lanczos Iteration for Tridiagonal Reduction of Large Matrix]]


#### Derivations

>[!info] Definition
>Consider the task of solving a *large-scale linear system* $$Ax = b$$ where $A$ is *symmetric.*
>
>Then at iteration $k$, the **Lanczos-based conjugate gradient algorithm** solves the above optimization problem on the *Krylov subspace*
>$$ 
> \begin{align*}
> \min_{x} \;&\;\; \frac{1}{2} x^{T}Ax - b^{T}x\\
> \text{s.t. }\;&\; x \in x_{0} + \mathcal{K}(A, b, k)
>\end{align*}
> $$
> where $$\mathcal{K}(A, b, k) := \text{span}\left\{ b,\,Ab \,{,}\ldots{,}\, A^{k-1}b\right\}$$
> 
>Or equivalently, 


>[!important]
>The *Lanczos iteration* provides the *tridiagonal reduction* on $A$, i.e.
> $$AQ_{k} = Q_{k}\hat{T_{k}} = Q_{k}T_{k} + r_{k}e_{k}^{T}$$ 
>where
>- $Q_{k} = [q_{1}\,{,}\ldots{,}\,q_{k}]$ is the first $k$ columns of *unitary matrix* $Q$ 
>- $r_{k} \in \text{Im}(Q_{k})^{\perp}$
>- and $\hat{T}_{k}$ is the top-left $(k+1)\times k$ blocks of *symmetric tridiagonal matrix* $T$ $$\hat{T}_{k} = \left[ \begin{array}{ccccc}\alpha_{1} & \beta_{1} & & 0 \\[5pt] \beta_{1} & \alpha_{2} & \ddots &   \\[5pt]   & \ddots & \ddots &   \beta_{k-1} \\[5pt]  &    & \beta_{k-1} & \alpha_{k}\\[5pt]  0 &    & & \beta_{k}\end{array} \right] = \left[ \begin{array}{c}T_{k} \\ 0 \quad \beta_{k} \end{array} \right]  \in \mathbb{C}^{(k+1)\times k}$$
>- Moreover, $$T_{k}= Q_{k}^{T}AQ_{k}.$$ and $$Q_{k}^{T}K(A, b, k)= R_{t}$$
>- And $$x \in x_{0} + \mathcal{K}(A, b, k) \iff x = x_{0} + Q_{k}y_{k},\,\; \exists y_{k}$$

- [[Lanczos Iteration for Tridiagonal Reduction of Large Matrix]]
- [[Krylov Subspace Methods]]
- [[Krylov Subspace and Krylov Matrix]]

>[!info]
>At iteration $k$, the CG algorithm solves the optimization 
>$$
>\begin{align*}
> \min_{x}\;&\; \phi(x)\\
> \text{s.t. }& x = x_{0} + Q_{k}\,y_{k}
>\end{align*}
>$$
>where $$\phi(x) = \frac{1}{2} x^{T}Ax - b^T x$$

>[!info]
>The objective function above can be reformulated as 
>$$ 
> \begin{align*}
> \phi(x)&:= \frac{1}{2} x^{T}A x - b^{T}x \\[5pt]
> &= \frac{1}{2}\left( x_{0} + Q_{k}y \right)^{T}A\left( x_{0} + Q_{k}y \right) - b^{T}\left( x_{0} + Q_{k}y \right)\\[5pt]
> &= \frac{1}{2}y^{T}(Q_{k}^{T}AQ_{k})y - y^{T}Q_{k}^{T}r_{0} + \phi(x_{0})\\[5pt]
> &= \frac{1}{2}y^{T}T_{k}y - y^{T}Q_{k}^{T}r_{0} + \phi(x_{0})
>\end{align*}
> $$
>where 
>- the *initial residual* $$r_{0} := b- Ax_{0}.$$
>- The solution of above quadratic programming is $$T_{k}\,y_{k} = Q_{k}^{T}r_{0} =  \lVert r_{0} \rVert\,e_{1}.$$ since $q_1 = r_{0} / \lVert r_{0} \rVert.$

- [[Tridiagonal Decomposition of Symmetric Matrix]]

>[!important]
>Thus the system $$Ax = b$$ has been transformed into the **tridiagonal system** $$T_{k}y_{k} = \lVert r_{0} \rVert e_{1} := \beta_{0}e_{1}$$ and $$x_{k} = x_{0} + Q_{k}y_{k}$$

- [[Tridiagonal System of Equations]]
- [[Minimal Residuals Algorithm and MINRES]]

>[!important]
>We want to update $x_{k}$ **without access to $q_{1}\,{,}\ldots{,}\, q_{k}$ explicitly**
>
>Since $T_{k} \succ\,0$, we have **$LDL^{T}$ factorization** of $T_{k}$,  $$Q_{k}^{T}AQ_{k} = T_{k} = L_{k}\,C_{k}\,L_{k}^{T}$$ where 
>$$L_{k} := \left[ \begin{array}{cccc}1 &  & & 0 \\[5pt] \ell_{1} & 1 &  &   \\[5pt]   & \ddots & \ddots &   0 \\[5pt]  &    & \ell_{k-1} & 1\end{array} \right], \quad  C_{k} := \left[ \begin{array}{cccc} c_{1} & & & \\[5pt] & c_{2}  & & \\[5pt] & & \ddots & \\[5pt] & & & c_{k}\\[5pt]\end{array} \right]  \in \mathbb{R}^{k\times k}$$
>
>The *Gaussian elimination* is 
>- $$c_{1} = \alpha_{1}$$
>- For $i=2\,{,}\ldots{,}\,k$:
>	- $$\ell_{i-1} = \frac{\beta_{i-1}}{c_{i-1}}$$
>	- $$c_{i} = \alpha_{i} - \ell_{i-1}\,\beta_{i-1}$$

- [[LDU Factorization of Symmetric Matrix]]
- [[Band Gaussian Elimination and Band LU Factorization]]

>[!important]
>Given factorization $$T_{k} = L_{k}\,C_{k}\,L_{k}^{T}$$ then 
>$$T_{k}y_{k} = L_{k}\,C_{k}\,L_{k}^{T}y_{k} = \beta_{0} e_{1}$$
>
>- If we can find a vector $v_{k} = [\nu_{1} \,{,}\ldots{,}\,\nu_{k}]$ so that $$L_{k}\,C_{k}\,v_{k} = \beta_{0} e_{1}$$ or, $$\left[ \begin{array}{cccc}c_{1} &  & & 0 \\[5pt] c_{1}\ell_{1} & c_{2} & &   \\[5pt]   & \ddots & \ddots &  \\[5pt]  &    & c_{k-1}\ell_{k-1} & c_{k}\end{array} \right] \left[\begin{array}{c} \nu_{1} \\[5pt] \nu_{2} \\[5pt] \vdots \\[5pt] \nu_{k} \end{array} \right]  = \left[\begin{array}{c} \beta_{0}\\[5pt] 0 \\[5pt] \vdots \\[5pt] 0 \end{array} \right] $$ then we can find $y_{k}$ by solving  $$L_{k}^{T}y_{k} = v_{k}$$ 
>
>- By **forward substitution** $$\begin{align*}c_{1}\nu_{1} &= \beta_{0} \\[5pt] c_{i-1}\ell_{i-1}\nu_{i-1} + c_{i}\nu_{i} &= 0, \quad i=2\,{,}\ldots{,}\,k \\[5pt] \implies \beta_{i-1}\nu_{i-1} + c_{i}\nu_{i} &= 0 \end{align*}$$
>- This leads to the **update equations** for **step size** $\nu_{i}$:  $$\begin{align*} \nu_{1} &= \frac{\beta_{0}}{c_{1}} \\[5pt] \nu_{i} &= -\frac{\beta_{i-1}}{c_{i}}\,\nu_{i-1},\quad i=2\,{,}\ldots{,}\,k\end{align*}$$

- [[Band Forward Substitution and Band Back Substitution]]

>[!info]
>Let $D_{k} = [d_1 \,{,}\ldots{,}\,d_{k}]$ so that $$D_{k}L_{k}^{T} = Q_{k}$$
>
>Thus 
>$$
>\begin{align*}
>x_{k} &= x_{0} +  Q_{k}y_{k} \\[5pt]
>&= x_{0} + D_{k}L_{k}^{T}y_{k} \\
>&= x_{0} + D_{k}v_{k} = x_{0} + \sum_{i=1}^{k}\nu_{i}d_{i}
>\end{align*}
>$$

>[!important]
>The columns of $D_{k}$ can be found by solving the lower bidiagonal system
>so $$[d_{1}\,{,}\ldots{,}\,d_{k}]\,\left[ \begin{array}{cccc}1 & \ell_{1} & & 0 \\[5pt] & 1 & \ddots &   \\[5pt]   & & \ddots &  \ell_{k-1}  \\[5pt]  &    & & 1\end{array} \right] = [q_{1}\,{,}\ldots{,}\,q_{k}]$$
>This leads to the **update equations** of **CG-directions** from *Lanczos vectors*
>$$
>\begin{align*}
> q_{1} &= d_{1} \\
> q_{i} &= \ell_{i-1}d_{i-1} + d_{i},\quad i=2\,{,}\ldots{,}\,k
>\end{align*}
>$$
>or 
>$$
>\begin{align*}
>d_{1} &= q_{1} \\[5pt]
>d_{i} &= q_{i} - \ell_{i-1}d_{i-1},\quad i=2\,{,}\ldots{,}\,k.
>\end{align*}
>$$

>[!info]
>As the result
>$$
>\begin{align*}
>x_{k} &= x_{0} + D_{k}v_{k} \\[5pt]
>&= x_{0} + D_{k-1}v_{k-1} + \nu_{k}\,d_{k}\\[5pt]
>&= x_{k-1} + \nu_{k}\,d_{k}
>\end{align*}
>$$

### Conjugate Gradient Properties

>[!important] Proposition
>Let $$g_{k} := Ax_{k} - b = \nabla \phi(x_{k})$$ be the **gradient of objective** where $x_{k}$ are solutions from **CG-Lanczos**.
>
>Then 
>- the *gradients at different iterations* are **orthogonal** $$\left\langle g_{i} , g_{j} \right\rangle = 0, \quad \forall i\neq j.$$
>- And it is scale proportional to the **residual** $$g_{k} = \nu_{k}\,r_{k}$$ where $\nu_{k}$ is the **step size** for **CG-Lanczos update** and $r_{k}$ is the **residual**.


>[!important] Propositions
>For all direction $d_{1}\,{,}\ldots{,}\,d_{k}$ generated in **CG-Lanczos** algorithm, 
>$$
>\left\langle d_{i} , Ad_{j} \right\rangle = \left\{\begin{array}{cl}c_{i} & \text{ if }i=j \\[5pt] 0 & \text{ otherwise}\end{array}\right.
>$$
>That is $d_{1}\,{,}\ldots{,}\,d_{k}$ are **conjugate with respect to** $A$.

- [[Conjugate Vector with respect to Positive Definite Transformation]]

>[!info] Proof
>Note that $$T_{k} = Q_{k}^{T}AQ_{k}, \quad Q_{k} = D_{k}L_{k}^{T}$$ where $D_{k} := [d_{1}\,{,}\ldots{,}\,d_{k}]$
>
>Then
>$$
>\begin{align*}
> T_{k} = L_{k}\,D_{k}^{T}AD_{k}\,L_{k}^{T}
>\end{align*}
>$$
>but $$T_{k} = L_{k}\,C_{k}\,L_{k}^{T}$$ is a *unique decomposition*. Thus $$C_{k} = \text{diag}(c_{1}\,{,}\ldots{,}\,c_{k}) = D_{k}^{T}AD_{k}$$



## Explanation

### MINRES - Minimum Residual Algorithm

![[Minimal Residuals Algorithm and MINRES#^ac4c95]]

- [[Minimal Residuals Algorithm and MINRES]]

>[!info]
>The **common** characteristics of both **MINRES** algorithm and **CG Lanczos** algorithm
> - both algorithms use **Lanczos process** to reduce a *symmetric positive definite* linear system into a *tridiagonal system*
> - both are **iterative methods**
> - both are used for **large-scale system**
> 
> 
>The **major differences** between two algorithms are that 
>- *CG Lanczos* do **not** use $Q_{k}$ *explicitly* to compute new solution $x_{k}$; while *MINRES* explicitly use $Q_{k}$ to update $x_{k}$ i.e. $$\begin{align*}x_{k} &= Q_{k}y_{k} & (\text{ MINRES }) \\[5pt] x_{k}&= x_{k-1} + \nu_{k}d_{k} & (\text{ CG })\end{align*}$$
>- *CG Lanczos* solves **symmetric positive definite** system while *MINRES* can be extended to **symmetric indefinite system**
>- *CG Lanczos* solves the linear system **exactly** while *MINRES* computes the **least square estimate**. 
>
>In order to drop reliance on $Q_{k}$, the *CG update* uses additional **$LDL^{T}$ factorization** on $T_{k}$ so that $$T_{k} = L_{k}\,C_{k}\,L_{k}^{T}$$
>- This leads to the relation between **CG direction** and **Lanczos vector** $$[d_{1}\,{,}\ldots{,}\,d_{k}]L_{k}^{T} = Q_{k} = [q_{1}\,{,}\ldots{,}\,q_{k}]$$
>- And the relation between the **step size** and $y$ $$L_{k}^{T}y_{k} = [\nu_{1}\,{,}\ldots{,}\,\nu_{k}]^{T}$$ 

^87babe





-----------
##  Recommended Notes and References



- [[Conjugate Gradient Algorithm Nonlinear]]
- [[Conjugate Gradient Algorithm Convergence Analysis]]
- [[Conjugate Gradient Algorithm Nonlinear Convergence Analysis]]
- [[Newton-Conjugate Gradient and Inexact Newton Method]]
- [[Gram-Schmidt Orthogonalization]]


- [[Tridiagonal Decomposition of Symmetric Matrix]]
- [[Tridiagonal Bidiagonal and Block Tridiagonal Matrix]]
- [[Hermitian or Symmetric Matrix]]
- [[Krylov Subspace and Krylov Matrix]]
- [[Nilpotent Linear Transformation and Matrix]]
- [[Nilpotent Linear Transformation Geometric Characterization]]



- [[System of Linear Equations or Linear System]]
- [[Existence and Uniqueness of Solution of Linear Equations]]
- [[Krylov Subspace Methods]]

- [[Quadratic Programming]]



- [[Matrix Analysis by Horn]]
- [[Matrix Computations by Golub]] pp 628 - 633
- [[Numerical Linear Algebra by Trefethen]] pp 245, 293 - 302