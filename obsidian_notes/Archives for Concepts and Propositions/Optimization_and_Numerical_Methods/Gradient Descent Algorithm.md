---
tags:
  - concept
  - optimization/algorithm
keywords:
  - gradient_descent_algorithm
topics:
  - optimization
  - optimization/algorithm
name: Gradient Descent Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Gradient Descent Algorithm

>[!important] Definition
>Consider the *unconstrained  minimization problem* of a *continuous differentiable* function $f: \mathbb{R}^{n} \to \mathbb{R}$. 
>
>The **gradient methods** or **gradient descent algorithm** works as follows
>1. initiate at $x_{0}$
>2. for $k=0,1 \,{,}\ldots{,}\,$:
>	1. $$x_{k+1} = x_{k}+ \alpha_{k}\;d_{k}$$ 
>		- where if $\nabla f(x_{k}) \neq 0$, the **direction** $d_{k}$ is chosen so that $$\left\langle  d_{k}\,,\,\nabla f(x_{k})    \right\rangle <0.$$
>		- the **stepsize** $\alpha_{k}$ is *positive*.

^613ed7

>[!important] Definition
>For most of time, $d = - \nabla f(x_{k})$, and the **steepest descent** algorithm is
>$$
>x_{k+1} = x_{k} - \alpha_{k}\;\nabla f(x_{k})
>$$
>The optimal stepsize $\alpha_{k}$ is chosen based on *line search strategies*.

- [[Line Search Strategies for Optimal Stepsize]]

## Riemannian Manifold

>[!important] Definition
>Let $(\mathcal{M}, g)$ be a *Riemannian manifold* and $R: T\mathcal{M} \to \mathcal{M}$ is the *retraction map* on $\mathcal{M}$.
>
>The **gradient descent algorithm on Riemannian manifold $\mathcal{M}$** works as follows
>1. initiate at $x_{0} \in \mathcal{M}$
>2. for $k=0,1 \,{,}\ldots{,}\,$:
>	1. $$x_{k+1} = R_{x_{k}}\left(-\alpha_{k}\; \nabla f(x_{k})\right)$$
>		- the **step size** $\alpha_{k}>0$

- [[Retraction on Smooth Manifold]]
- [[Riemannian Metric and Riemannian Manifold]]
- [[Gradient of Smooth Map]]
- [[An Introduction to Optimization on Smooth Manifolds by Boumal]] pp 57


## Explanation




## Generalization

>[!important] Definition
>The **(generalized) gradient methods** works as follows
>1. initiate at $x_{0}$
>2. for $k=0,1 \,{,}\ldots{,}\,$:
>	1. $$x_{k+1} = x_{k} - \alpha_{k}\;D_{k}\;\nabla f(x_{k}) $$ 
>		- where if $\nabla f(x_{k}) \neq 0$, the matrix $D_{k} \in \mathbb{R}^{n \times n}$ is **symmetric positive definite matrix**  $$D_{k} \succ 0.$$
>		- the **stepsize** $\alpha_{k}$ is *positive*.

### Steepest Descent

>[!example]
>In **steepest descent method**,
>$$
>D_{k} := I
>$$

### Newton's Method

>[!example]
>In **Newton's method**,
>$$
>D_{k} := \left(\nabla f(x_{k})\right)^{-1}
>$$

- [[Newton Method]]

### Quasi-Newton Method

>[!example]
>In **Quasi-Newton**,
>$$
>D_{k} := B_{k}^{-1}
>$$

- [[Secant Equation and Quasi-Newton Methods]]
### BFGS Method

>[!example]
>In **BFGS**,
>$$
>D_{k} := H_{k}
>$$

- [[BFGS Algorithm]]


## Conjugate Gradient Method

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
>The **conjugate-gradient methods** works as follows
>1. initiate at $x_{0}$
>2. for $k=0,1 \,{,}\ldots{,}\,$:
>	1. $$x_{k+1} = x_{k} + \alpha_{k}\;d_{k}$$ 
>	2. update adjustment factor 
>		- **Fletcher-Reeves method** $$\beta_{k+1} = \frac{\nabla f(x_{k+1})^T\,\nabla f(x_{k+1})}{\nabla f(x_{k})^T\,\nabla f(x_{k})} = \frac{\lVert \nabla f(x_{k+1}) \rVert_{2}^2}{\lVert \nabla f(x_{k}) \rVert_{2}^2 }$$
>		- **Polak-Ribiere method** $$\beta_{k+1} = \frac{\nabla f(x_{k+1})^T\,\left( \nabla f(x_{k+1}) - \nabla f(x_{k})\right)}{\nabla f(x_{k})^T\,\nabla f(x_{k})}$$
>	1. $$d_{k+1} = - \nabla f(x_{k+1})  + \beta_{k+1}\,d_{k} $$
>	

- [[Conjugate Gradient Algorithm Nonlinear]]

## Numerical Solution for System of Linear Equations

>[!important]
>It is important to note that all of the second-order gradient method is based on solving the **secant equation** [[Secant Equation and Quasi-Newton Methods]]
>$$
>\nabla^2 f(x_{k})\,s_{k} = y_{k} \quad \text{ or } \quad  \left(\nabla^2 f(x_{k})\right)^{-1}\,s_{k} = y_{k}
>$$
>Similarly, by [[Necessary and Sufficient Condition for Local Minimum of Smooth Function]], majority of *gradient methods* involves solving the first-order condition
>$$
>\nabla f(x_{k}) = 0
>$$
>
>This means that these methods can be used to solve the **systems of linear equations**.

## Convergence Analysis

- [[Fixed Point of Map]]
- [[Contraction Map Principle]]




-----------
##  Recommended Notes and References

- [[Iterative Descent]]


- [[Unconstrained Global Minimization]]
- [[Unconstrained Local Minimization]]

- [[Numerical Optimization by Nocedal]]
- [[Nonlinear Programming by Bertsekas]] pp 22 - 86
- [[Deep Learning by Goodfellow]] 