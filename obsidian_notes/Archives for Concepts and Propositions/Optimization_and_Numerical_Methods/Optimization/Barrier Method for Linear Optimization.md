---
tags:
  - concept
  - optimization/theory
  - optimization/algorithm
  - optimization/linear_optimization
keywords:
  - barrier_method
  - linear_optimization
topics:
  - optimization
name: Barrier Method for Linear Optimization
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Barrier Method for Linear Optimization

### Log-Barrier Centering Problem

![[Logarithmic Barrier Function and Central Path for Interior Point Methods#^779aa5]]

![[Logarithmic Barrier Function and Central Path for Interior Point Methods#^1d97b8]]

![[Linear Optimization Problem#^099c2f]]

>[!important] Definition
>Consider the **linear optimization** in *standard form*
>$$
>\begin{align*}
>\min_{x}\; & \left\langle c ,  x\right\rangle\\
>\text{s.t.}\;& Ax = b\\
>\;&x \succeq 0\\
\end{align*}
>\quad (P)
>$$
>where $A\in \mathbb{R}^{m\times n}$, $b\in \mathbb{R}^{m}$,  $c\in \mathbb{R}^{n}$, and $x\in \mathbb{R}^{n}$.
>
>The **central path** are optimal solutions for **log-barrier centering problem**
>$$
>\begin{align*}
>\min_{x}\; & t \left\langle c ,  x\right\rangle - \sum_{i=1}^{n}\log \left(x_{i}\right) \\
>\text{s.t.}\;& Ax = b
\end{align*}
>\quad (B_{t})
>$$

^56afa0

- [[Linear Optimization Problem]]

>[!important]
>The **central path** $\{x^{*}(t)\}$ and  its associated dual $(\lambda^{*}(t), \nu^{*}(t))$ must satisfy the **modified KKT conditions**
>$$
>\begin{align*}
> Ax &= b\\[5pt]
> x_{i} & \ge 0, \quad i=1\,{,}\ldots{,}\,m \\[5pt]
> \lambda_{i} &\ge 0 , \quad i=1\,{,}\ldots{,}\,m \\[5pt]
> c - \lambda \, + A^{T} \nu &= 0\\[5pt]
> \lambda_{i}x_{i} &= \frac{1}{t}, \quad i=1\,{,}\ldots{,}\,m
>\end{align*}
>$$

### Barrier Method

>[!important] Definition
>Consider the *linear optimization problem*
>$$
>\begin{align*}
>\min_{x}\; & \left\langle c ,  x\right\rangle\\
>\text{s.t.}\;& Ax = b\\
>\;&x \succeq 0\\
\end{align*}
>\quad (P)
>$$
>where $A \in \mathbb{R}^{p \times n}$ is of **full rank** $\text{rank}(A) = p < n.$
>
>The **Barrier method** that solve the problem $(P)$ is described as below:
>- *Require*: the convex program $(P)$
>- *Require*: initial **strictly feasible solution** $x_{0}$
>- *Require*: initial parameter $t_{0} >0$
>- *Require*: *tolerance* $\epsilon >0$
>- *Require*: *growth rate* $\mu >1$
>- While the *tolerance criterion* not met:
>	- If first iteration:
>		- $$x \leftarrow x_{0}, \quad t\leftarrow t_{0}$$
>		- skip the centering and update steps below
>	- **Centering Step**:
>		- Solve the *log-barrier subprogram* $$\begin{align*}\min_{x \in X}\; &\; t\,\left\langle c ,  x\right\rangle - \sum_{i=1}^{n}\log \left(x_{i}\right)\\ \text{s.t.}\;&\; Ax  = b \end{align*} \;\; (B_{t})$$ 
>		- Let $x^{*}(t)$ be the **optimal solution**
>	- **Update** primal feasible solution along the **central path** $$x \leftarrow x^{*}(t)$$
>	- **Increase** $t$ by rate $\mu$ as $$t \leftarrow \mu\,t$$
>	- If the **duality gap** $m / t < \epsilon$:
>		- *Return*: optimal solution $x^{*} = x$

^87009c


- [[Barrier Method for Convex Optimization]]

## Explanation

>[!important]
>The main effort in the **barrier method** is to compute the *Newton step* by solving the **KKT system**
>$$
>\begin{align*}
>\left[ \begin{array}{cc}
> H_{bar} & A^{T} \\[5pt] 
> A & 0
>\end{array} \right] \left[ \begin{array}{c}\Delta x \\[5pt] \Delta \nu\end{array} \right]  &= - \left[ \begin{array}{c} g\\[5pt] 0 \end{array} \right] 
>\end{align*}
>$$
>where
>$$
>H_{bar} := \sum_{i=1}^{m} \frac{1}{x_{i}^2}\,e_{i}\left(e_{i}\right)^{T} = \text{diag}(x)^{-2}
>$$
>and
>$$
>g := t c - \sum_{i=1}^{m} \frac{1}{x_{i}}\,e_{i} = tc - \text{diag}(x)^{-1}1
>$$
>
>This equation has solution
>$$
>\begin{align*}
>\Delta x &= \text{diag}(x)^{2}\left(-tc + \text{diag}(x)^{-1}1 - A^{T}\Delta \nu\right) \\[5pt]
>&= -t\,\text{diag}(x)^{2}c + x -  \text{diag}(x)^{2} A^{T}\Delta \nu
>\end{align*}
>$$
>Substituting this back to equation, we have the following **positive definite system of equations** of $\Delta \nu$
>$$
>(A\,\text{diag}(x)^2A^{T})\, \Delta \nu = -t\,A\,\text{diag}(x)^{2}c + b
>$$
>- This coefficient matrix $$A\,\text{diag}(x)^2A^{T} \succ 0$$
>- If $A$ is *sparse*, the coefficients $A\,\text{diag}(x)^2A^{T}$ is **sparse**. 
>- We can use **Cholesky factorization** or **sparse Cholesky factorization**

^e3946e

- [[Positive Semidefinite Transformation]]
- [[Cholesky Factorization of Hermitian Positive Definite Matrices]]
- [[LDU Factorization of Symmetric Matrix]]
- [[Sparse Matrix Representation]]




-----------
##  Recommended Notes and References



- [[Polyhedron and Polytope]]


- [[Primal-Dual Interior Point Method for Linear Optimization]]
- [[Simplex Method for Linear Optimization]]
- [[Logarithmic Barrier Function and Central Path for Interior Point Methods]]

- [[Primal-Dual Interior Point Method for Convex Optimization]]
- [[KKT Matrix and KKT System for Optimization with Equality Constraints]]

- [[Least Absolute Deviations]]
- [[Least Absolute Deviations Solution via Iterative Re-weighted Least Square]]

- [[Introduction to Linear Optimization by Bertsimas]] pp 303 - 438
- [[Convex Optimization by Boyd]] pp 571 - 573, 613 - 615, 616 - 618
- [[Numerical Optimization by Nocedal]] pp 392 - 418
- [[Nonlinear Programming by Bertsekas]]