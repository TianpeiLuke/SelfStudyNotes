---
tags:
  - concept
  - optimization/algorithm
  - optimization/convex_optimization
  - L-BFGS
  - BFGS
  - limited_memory_BFGS
  - quasi_Newton_method
keywords:
  - limited_memory_bfgs
topics:
  - optimization/algorithm
name: Limited Memory BFGS
date of note: 2024-07-02
---

## Concept Definition

>[!important]
>**Name**: Limited Memory BFGS

![[BFGS Algorithm#^954dd0]]

>[!important] Definition
>Consider the *unconstrained  minimization problem* of a *twice continuous differentiable* function $f: \mathbb{R}^{n} \to \mathbb{R}$. 
>
>Denote $$s_{k} = x_{k+1} - x_{k}; \quad y_{k} = \nabla f(x_{k+1}) - \nabla f(x_{k}).$$ The *BFGS update* can be written as $$H_{k+1} = V_{k}^T\,H_{k}\,V_{k} + \rho_{k}s_{k}\,s_{k}^T$$ where $$V_{k} = I - \rho_{k}\;y_{k}\,s_{k}^{T}, \quad \rho_{k} = \frac{1}{y_{k}^T\,s_{k}}.$$
>
>The idea of **Limited-Memory BFGS (L-BFGS) algorithm** is that, at each iteration, instead of keeping a *large matrix* $H_{k}$ *in memory*, we *recompute* $H_{k}$ based on *repeated application* of the formula for *the most recent* $m$ vector pairs $\{s_{i} , y_{i} \}$ and a *newly initialized matrix* $H_{k}^{0}$. That is
>$$
>\begin{align*}
>H_{k} &= \left(\prod_{i=1}^{m}V_{k-i}\right)^T\,H_{k}^{0}\,\left(\prod_{i=1}^{m}V_{k-i}\right) \\
>&\quad +  \sum_{i=1}^{m}\rho_{k - i}\,\left(\prod_{j=1}^{i-1}V_{k-j}\right)^T s_{k - i} s_{k - i}^{T}\left(\prod_{j=1}^{i-1}V_{k-j}\right)
>\end{align*}
>$$
>

- [[BFGS Algorithm]]
- [[Secant Equation and Quasi-Newton Methods]]
- [[Sherman–Morrison–Woodbury Matrix Inversion Formula]]

>[!important] Definition
>Given a collection of $\{ (s_{i}, y_{i}) \}_{i=k-1}^{k-m}$ and the weight $$\rho_{i} = \frac{1}{y_{i}^T\,s_{i}},$$
>define the **L-BFGS two-loop recursion**:
>
>- $q \leftarrow \nabla f(x_{k})$
>- For $i= k-1, k-2, \,{,}\ldots{,}\, k-m$:
>	- $\alpha_{i} = \rho_{i}\;s_{i}^T\,q$
>	- $q \leftarrow q - \alpha_{i}\,y_{i}$
>
>- $r \leftarrow H_{k}^{0}\,q$
>- For $i= k-m, k-m+1, \,{,}\ldots{,}\, k-1$:
>	- $\beta \leftarrow \rho_{i}\,y_{i}^T\,r$
>	- $r \leftarrow r + s_{i}\,\left(\alpha_{i} - \beta\right)$
>
>- Stop with $$r = H_{k}\,\nabla f(x_{k}).$$ 

>[!important] Definition
>The **Limited-Memory BFGS (L-BFGS) algorithm** is described as
>
>- Choose starting point $x_{0}$, integer $m >0$
>- $k \leftarrow 0$
>- While not convergence:
>	- Choose $$H_{k}^0 = \gamma_{k}I, \quad \gamma_{k}:= \frac{s_{k-1}^T\,y_{k-1}}{y_{k-1}^T\,y_{k-1}}$$
>	- Compute $$p_{k} = - H_{k}\,\nabla f(x_{k})$$ by calling **L-BFGS two-loop recursion** with $\{ (s_{i}, y_{i}) \}_{i=k-1}^{k-m}$  and $H_{k}^0.$
>	- Compute $$x_{k+1} = x_{k} + \alpha_{k}\,p_{k},$$ where $\alpha_{k}$ is chosen to satisfies the *Wolfe condition*
>	- If $k > m$:
>		- Discard the vector pair $\{ s_{k-m}, y_{k - m} \}$
>	- Compute and Store $$s_{k} = x_{k+1} - x_{k}; \quad y_{k} = \nabla f(x_{k+1}) - \nabla f(x_{k}).$$ 
>	- $k \leftarrow k + 1$



## Explanation

>[!info]
>Since the inverse Hessian approximation $H_{k}$ will generally be *dense*, the *cost* of *storing* and *manipulating* it is prohibitive when the number of variables is large. To circumvent this problem, we store a **modified version** of $H_{k}$ *implicitly*, by storing a certain number (say, $m$) of the vector pairs $\{s_{i} , y_{i} \}$. After the new iterate is computed, the *oldest vector pairs* are replaced.




-----------
##  Recommended Notes and References

- [[BFGS Algorithm]]
- [[Secant Equation and Quasi-Newton Methods]]


- [[Numerical Optimization by Nocedal]] pp 177
- [[Nonlinear Programming by Bertsekas]] 
- [[Deep Learning by Goodfellow]] pp 307 - 308
- [[Probabilistic Graphical Models by Koller]] pp 991