---
tags:
  - concept
  - optimization/algorithm
  - optimization/convex_optimization
keywords:
  - conjugate_gradient_nonlinear
topics:
  - optimization/algorithm
name: Conjugate Gradient Algorithm Nonlinear
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Conjugate Gradient Algorithm for Nonlinear Optimization

![[Conjugate Gradient Algorithm Linear#^e7cffe]]

## Fletcher-Reeves Method

>[!important] Definition
>Consider the unconstrained optimization problem $$\min_{x\in \mathbb{R}^n} f(x)$$ where $f$ is a *continuously differentiable function*.
>
>The **Fletcher-Reeves method** works as follows
>- initiate at $x_{0}$
>- Evaluate $f(x_{0})$, and $\nabla f(x_{0})$
>- Set $d_{0} = - \nabla f(x_{0})$, and $k \leftarrow 0$.
>- While $\nabla f(x_{k}) \neq 0$:
>	- Compute stepsize $\alpha_{k} >0$ that minimize the search direction $$\alpha_{k} \in \arg\min\phi(\alpha) := f(x_{k} + \alpha\,d_{k})$$
>	- Set $$x_{k+1} = x_{k} + \alpha_{k}\;d_{k}$$ 
>	- Evaluate $\nabla f(x_{k+1})$
>	- Update *stepsize* for *conjugate gradient update* $$\beta_{k+1} = \frac{\nabla f(x_{k+1})^T\,\nabla f(x_{k+1})}{\nabla f(x_{k})^T\,\nabla f(x_{k})} = \frac{\lVert \nabla f(x_{k+1}) \rVert_{2}^2}{\lVert \nabla f(x_{k}) \rVert_{2}^2 }$$
>	- Update **conjugate gradient direction** $$d_{k+1} = - \nabla f(x_{k+1})  + \beta_{k+1}\,d_{k} $$
>	- $k \leftarrow k + 1.$
>	

^c0a4df

- [[Numerical Optimization by Nocedal]] pp 121
- [[Conjugate Gradient Algorithm Linear]]
- [[Gradient Descent Algorithm]]

## Polak-Ribière Method and Variants

>[!important] Definition
>Consider the unconstrained optimization problem $$\min_{x\in \mathbb{R}^n} f(x)$$ where $f$ is a *continuously differentiable function*.
>
>The **Polak-Ribière method** works as follows
>- initiate at $x_{0}$
>- Evaluate $f(x_{0})$, and $\nabla f(x_{0})$
>- Set $d_{0} = - \nabla f(x_{0})$, and $k \leftarrow 0$.
>- While $\nabla f(x_{k}) \neq 0$:
>	- Compute stepsize $\alpha_{k} >0$ that minimize the search direction $$\alpha_{k} \in \arg\min\phi(\alpha) := f(x_{k} + \alpha\,d_{k})$$
>	- Set $$x_{k+1} = x_{k} + \alpha_{k}\;d_{k}$$ 
>	- Evaluate $\nabla f(x_{k+1})$
>	- **Update** *stepsize* for *conjugate gradient update* $$\beta_{k+1} = \frac{\nabla f(x_{k+1})^T\,\left(\nabla f(x_{k+1}) - \nabla f(x_{k})\right)}{\lVert \nabla f(x_{k}) \rVert_{2}^2 }$$
>	- Update **conjugate gradient direction** $$d_{k+1} = - \nabla f(x_{k+1})  + \beta_{k+1}\,d_{k} $$
>	- $k \leftarrow k + 1.$
>	

^1642a0

## Explanation

>[!info]
>For nonlinear objective function $f$, consider the approximation of $f$ by its **second-order Taylor expansion**
>$$
>f(x_{k} + \alpha d) \approx f(x_{k}) + \alpha\left\langle \nabla f(x_{k}) ,  d\right\rangle + \frac{\alpha^2}{2}d^{T}\nabla^2 f(x_{k}) d
>$$
>where the RHS achieve optimal value with $d$ satisfying the **Newton equation**
>$$
> \alpha \nabla^2 f(x_{k}) d = - \nabla f(x_{k})
>$$ 
>Then the **conjugate gradient method** iteratively solves above **Newton equation**. 

^edc131

- [[Normal Equations and Newton System of Equations]]
- [[Newton Method]]
- [[Newton-Conjugate Gradient and Inexact Newton Method]]
- [[Conjugate Gradient Algorithm Lanczos]]


>[!info]
>- For **gradient methods**, the direction $d_{k}$ depends on the *gradient* of objective only $$d_{k} = - D_{k}\nabla f(x_{k})$$
>- In **conjugate-gradient** method, the direction $d_{k}$ depends both on the *gradient* of objective at *current step* and the **direction at last step**
>$$
>d_{k} = -\nabla f(x_{k}) +  \beta_{k}\;d_{k-1}
>$$
>Moreover, the successive directions are *conjugate* to each other with respect to **Hessian** $$\left\langle  \nabla^2 f(x_{k})\,d_{k-1}\,,\, d_{k}   \right\rangle = 0.$$
>
>
>

## Convergence Analysis

- [[Conjugate Gradient Algorithm Nonlinear Convergence Analysis]]


## Equivalence to BFGS Algorithm


- [[BFGS Algorithm]]
- Shanno, D. F. (1978). Conjugate gradient methods with inexact searches. _Mathematics of operations research_, _3_(3), 244-256.
- Shanno, D. F. (1978). On the convergence of a new conjugate gradient algorithm. _SIAM Journal on Numerical Analysis_, _15_(6), 1247-1257.
- Andrei, N. (2007). Scaled conjugate gradient algorithms for unconstrained optimization. _Computational Optimization and Applications_, _38_(3), 401–416. [https://doi.org/10.1007/s10589-007-9055-7](https://doi.org/10.1007/s10589-007-9055-7)


## Scaled Conjugate Gradient

>[!info]
>Instead of solving *Newton's equations*
>$$
> \alpha \nabla^2 f(x_{k}) d = - \nabla f(x_{k})
>$$ 
>the **scaled conjugate gradient** solves the **secant equations** as approximation
>$$
> \alpha B_{k} s_{k} = y_{k}
>$$ 
>where 
>-  $s_{k} = x_{k+1} - x_{k}$, and 
>- $y_{k} = \nabla f(x_{k+1}) - \nabla f(x_{k})$
>- $B_{k} \approx \nabla^2 f(x_{k})$


- [[Secant Equation and Quasi-Newton Methods]]
- [[BFGS Algorithm]]
- [[Limited Memory BFGS]]
- Andrei, N. (2007). Scaled conjugate gradient algorithms for unconstrained optimization. _Computational Optimization and Applications_, _38_(3), 401–416. [https://doi.org/10.1007/s10589-007-9055-7](https://doi.org/10.1007/s10589-007-9055-7)




-----------
##  Recommended Notes and References

- [[Conjugate Gradient Algorithm Linear]]
- [[Newton Method]]

- [[Numerical Optimization by Nocedal]] pp 121
- [[Nonlinear Programming by Bertsekas]]
- [[Deep Learning by Goodfellow]] pp 307