---
tags:
  - concept
  - numerical_methods/numerical_differential_equations
keywords:
  - nystrom_method_ode
topics:
  - numerical_differential_equation
name: Nyström Method for Numerical ODE
date of note: 2024-11-01
---

## Concept Definition

>[!important]
>**Name**: Nyström Method for Numerical ODE
- [[Ordinary Differential Equations]]
- [[Space of Continuous Differentiable Functions]]

![[k-Step Methods for Numerical ODE#^57a043]]

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
>The **$k$-step Nyström method** is an *explicit $k$-step LMM*, which is of the form
>$$
>x_{n+k} - x_{n+k-2} = h\left(  \beta_{k-1}f_{n+k-1}  \,{+}\ldots{+}\, \beta_{0}f_{n}\right) 
>$$ 
>where
>- $$x_{n+j} \approx x(t_{n+j}), \quad f_{n+j} = f(x_{n+j}, t_{n+j}, \lambda) \approx f(x(t_{n+j}), t_{n+j}, \lambda)$$
>- The *first characteristic polynomial* is given by $$\rho(z) = z^{k} - z^{k-2}$$

- [[k-Step Methods for Numerical ODE]]

### 2-Step Method

>[!important] Definition
>The **$2$-step Nyström method**  is of the form
>$$
>x_{n+2} - x_{n} =2h\,f_{n+1}
>$$ 
>where
>- $$x_{n+j} \approx x(t_{n+j}), \quad f_{n+j} = f(x_{n+j}, t_{n+j}, \lambda) \approx f(x(t_{n+j}), t_{n+j}, \lambda)$$
>- This method is also called the **second-order mid-point rule**, or the **leap-frog method**.

- [[Hamiltonian Monte Carlo]]



## Explanation





-----------
##  Recommended Notes and References


- [[Linear Multistep Methods for Numerical ODE]]
- [[Ordinary Differential Equations]]
- [[Space of Continuous Differentiable Functions]]

- [[Numerical Methods for Ordinary Differential Equations IVP by Griffiths]] pp 45 - 48, 54 - 55, 66, 87, 134
- [[Numerical Methods for Ordinary Differential Equations by Butcher]] pp 111