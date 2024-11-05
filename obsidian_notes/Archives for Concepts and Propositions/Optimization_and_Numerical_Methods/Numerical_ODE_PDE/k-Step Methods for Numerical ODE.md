---
tags:
  - concept
  - numerical_methods/numerical_differential_equations
keywords:
  - k_step_linear_method_ode
  - linear_multistep_methods_ode
topics:
  - numerical_differential_equation
name: k-Step Methods for Numerical ODE
date of note: 2024-11-01
---

## Concept Definition

>[!important]
>**Name**: k-Step Methods for Numerical ODE

>[!important] Definition
>Consider the *initial value problem (IVP)* of *ordinary differential equations*
>$$
>\left\{
>\begin{align*}
>\frac{d}{dt} x(t) &= f\left(x(t), t, \lambda\right),\\
>x(t_{0}) &= x_{0}
>\end{align*}
>\right.
>$$
>where 
>- $f: U \times J \times \Lambda \to \mathbb{R}^n$ is a smooth function, i.e. it is *continuous differentiable*. 
>- $J \subseteq \mathbb{R}$, $U \subseteq \mathbb{R}^n$, and $\Lambda \subseteq \mathbb{R}^k$ be open subsets.
>- The task is to find the *temporal discretization* of the *approximate solution* of the IVP.
>  
>The **general $k$-step linear method** for *temporal discretization of ODE solution*  takes the form
>$$
>x_{n+k} + \alpha_{k-1}x_{n+k-1} \,{+}\ldots{+}\,\alpha_{0}x_{n} = h\left( \beta_{k}f_{n+k} + \beta_{k-1}f_{n+k-1}  \,{+}\ldots{+}\, \beta_{0}f_{n}\right) 
>$$  
>where
>- $$x_{n+j} \approx x(t_{n+j}), \quad f_{n+j} = f(x_{n+j}, t_{n+j}, \lambda) \approx f(x(t_{n+j}), t_{n+j}, \lambda)$$
>- If $\beta_{k} = 0$, it is called the **$k$-step explicit linear method**.
>- If $\beta_{k} \neq 0$, it is called the **$k$-step implicit linear method**.
>- The *first and second characteristic polynomials* are given by $$\begin{align*}\rho(z) &= z^{k} + \alpha_{k-1}z^{k-1} \,{+}\ldots{+}\,\alpha_{0} \\[5pt] \sigma(z) &= \beta_{k}z^{k} + \beta_{k-1}z^{k-1} \,{+}\ldots{+}\, \beta_{0} \end{align*}$$
>- The associated *linear difference operator* is defined by $$\mathcal{L}_{h}\,z(t) := \sum_{j=0}^{k}\left[ \alpha_{j}\,z(t + j\,h) - h\,\beta_{j}\,z'(t + j\,h)  \right]$$
>- The *Taylor expansion* on RHS about $h=0$ and collecting the terms in powers of $h$ gives $$\mathcal{L}_{h}\,z(t) := C_{0}z(t) + C_{1}h\,z'(t) \,{+}\ldots{+}\,C_{p}h^{p}\,z^{(p)}(t) + C_{p+1}h^{p+1}\,z^{(p+1)}(t) + O(h^{p+2})$$ where
>	- $$C_{0} = \rho(1), \; C_{1} = \rho'(1) - \sigma(1) \,{,}\ldots{,}\,$$
>	- $\{C_{i}\}$ are *linear combinations* of coefficients $\beta_{0}\,{,}\ldots{,}\,\beta_{k}, \alpha_{0} \,{,}\ldots{,}\, \alpha_{k-1}, \alpha_{k}(=1)$
>- The above method is of **order p** if $$C_{0} = C_{1} \,{=}\ldots{=}\,C_{p} = 0.$$ The first nonzero coefficient $C_{p+1}$ is the **error constant.**

^57a043


- [[Characteristic Polynomials of Linear Multistep Methods for Numerical ODE]]
- [[Linear Multistep Methods for Numerical ODE]]



## Explanation

>[!important]
>The *general k-step LMM* use the values $(x_{n+j}, f_{n+j})$ in the **past $k$ steps**, as well as $f_{n+k}$ if for implicit method 
>- The coefficients $\alpha_{0}$ can be **normalized** to $1$.
>- The general **explicit k-step LMM** has $2k$ coefficients; 
>- The general **implicit k-step LMM** has $2k+1$ coefficients; 
>  
>Given the equation  $$C_{0} = C_{1} \,{=}\ldots{=}\,C_{p} = 0,$$ it is expected that we can achieves 
>- **order $2k$** for **implicit** method
>- **order $2k-1$** for **explicit** method

## Examples


- [[Implicit Euler Method for Discretization of ODE]]

- [[Adams-Bashforth Method for Numerical ODE]]

- [[Explicit Euler Method for Discretization of ODE]]

- [[Adams-Moulton Method for Numerical ODE]]

- [[Trapezoidal Rule as Two-Step Method for Numerical ODE]]

- [[Nyström Method for Numerical ODE]]


-----------
##  Recommended Notes and References



- [[Ordinary Differential Equations]]
- [[Autonomous and Nonautonomous Ordinary Differential Equations]]
- [[Bounded Linear Operator and Norm of Operator]]
- [[Space of Continuous Differentiable Functions]]

- [[Numerical Methods for Ordinary Differential Equations IVP by Griffiths]] pp 45 - 48, 56 - 57