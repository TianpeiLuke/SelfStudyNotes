---
tags:
  - concept
  - numerical_methods/numerical_differential_equations
keywords:
  - runge_kutta_method
topics:
  - numerical_differential_equation
name: Runge-Kutta Methods for Numerical ODE
date of note: 2024-10-31
---

## Concept Definition

>[!important]
>**Name**: Runge-Kutta Methods for Numerical ODE

### General Multi-Stage Runge-Kutta Method

>[!important] Definition
>Consider the *initial value problem (IVP)* of *ordinary differential equations (ODEs)*
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
>The **general $s$-stage Runge-Kutta method** that solves *temporal discretization problem*  the may be written in the form
>$$
>\begin{align*}
>k_{i} &= f\left(x_{n} + h\,\sum_{j=1}^{s}a_{i,j}\,k_{j}\,,\, t_{n} + c_{i}\,h\,,\,\lambda \right), \quad i=1\,{,}\ldots{,}\,s \\[5pt]
>x_{n+1} &= x_{n} + h\left(\sum_{i=1}^{s}\,b_{i}\,k_{i}\right)
>\end{align*}
>$$  
>where each stage $\{k_{i}\}$ is computed via a system of $s$ *nonlinear equations*.
>- The above describe the **implicit method**.
>- It is natural to impose the **equality constraint** $$c_{i} = \sum_{j=1}^{s}a_{i,j}, \quad i=1\,{,}\ldots{,}\,s$$ where $c_{i}$ is equal to the $i$-th *row sum* of $A$.
>- For given $s$, the general RK method depends on *$s^2 + s$ free parameters* $\{ a_{i,j}, b_{j} \}$
>- We can represent all parameters for *Runge-Kutta method* in a tableau called the **Butcher array**, which is of the form 
>$$
>\begin{array}{c|c}
> c & A \\[5pt] \hline
>  & b^{T}
>\end{array}
>$$
>where $$A = [a_{i,j}] \in \mathbb{R}^{s\times s}, \quad b = [b_{i}] \in \mathbb{R}^{s}, \, c = [c_{i}]  \in \mathbb{R}^{s}$$
>
>The **explicit Runge-Kutta method** requires that $A$ is **strictly lower triangular** and $\{ k_{i} \}$ can be computed in turn without solving the nonlinear equation. 
>- The **Butcher array** for *explicit Runge-Kutta method* is given by 
>$$
>\begin{array}{c|ccccc}
>0 & 0 & &  &  \\[5pt] 
>c_{2} & a_{2,1} & 0 &  &  \\[5pt] 
>\vdots & \cdots & \cdots & \ddots \\[5pt] 
>c_{s} & a_{s,1} & a_{s,2} & \cdots & 0 \\[5pt] 
 \hline
>  & b_{1} & b_{2} & \cdots & b_{s} 
>\end{array}
>$$
>- Thus each stage $k_{i}$ for *explicit RK method* is given by
>$$
>\begin{align*}
>k_{1} &:= f\left(x_{n}\,,\, t_{n}\,,\,\lambda \right) \\[8pt]
>k_{i} &:= f\left(x_{n} + h\,\sum_{j=1}^{i-1}a_{i,j}\,k_{j}\,,\, t_{n} + c_{i}\,h\,,\,\lambda \right), \quad i=2\,{,}\ldots{,}\,s
>\end{align*}
>$$

- [[Triangular Matrix and Block Triangular Matrix]]
- [[Forward Substitution of Lower Triangular System]]

### Two-Stage Runge-Kutta Method

>[!important] Definition
>A **two-stage general explicit Runge-Kutta method** is given by 
>$$
>\begin{align*}
> k_{1} &= f(x_{n}, t_{n}, \lambda)\\[5pt]
> k_{2} &= f\left( x_{n} +  h\,a\,k_{1}\,,\, t_{n} + a\,h \,,\, \lambda \right)\\[5pt]
> x_{n+1} &= x_{n} + h\,(b_{1}k_{1} + b_{2}k_{2}) \\[5pt]
> t_{n+1} &= t_{n} + h
>\end{align*}
>$$
>- The corresponding *Butcher array* for $\theta \neq 0$ is given by
>$$
>\begin{array}{c|cc}
>0 & 0 &  \\[5pt] 
> \dfrac{1}{2\theta} & \dfrac{1}{2\theta} & 0  \\[5pt] 
 \hline
>  & 1- \theta & \theta
>\end{array}
>$$
>- When $\theta = 1$, it is the **modified Euler method** 
>$$
>\begin{align*}
> k_{1} &= f(x_{n}, t_{n}, \lambda)\\[5pt]
> k_{2} &= f\left( x_{n} + \frac{1}{2} h\,k_{1}\,,\, t_{n} + \frac{1}{2} h \,,\, \lambda \right)\\[5pt]
> x_{n+1} &= x_{n} + h\,k_{2} \\[5pt]
> t_{n+1} &= t_{n} + h
>\end{align*}
>$$
>- When $\theta = 1 / 2$, it is called the **improved Euler method**, where 
>$$
>\begin{align*}
> k_{1} &= f(x_{n}, t_{n}, \lambda)\\[5pt]
> k_{2} &= f\left( x_{n} +  h\,k_{1}\,,\, t_{n} +  h \,,\, \lambda \right)\\[5pt]
> x_{n+1} &= x_{n} + \frac{1}{2}\,h\,(k_{1} + k_{2}) \\[5pt]
> t_{n+1} &= t_{n} + h
>\end{align*}
>$$


>[!important] Definition
>A **two-stage implicit Runge-Kutta method** is given by the *nonlinear equations*
>$$
>\begin{align*}
> k_{1} &= f\left( x_{n} + \frac{1}{4}h\,k_{1}+ \left(\frac{1}{4} - \gamma\right)h\,k_{2}\,,\, t_{n} + \left(\frac{1}{2} - \gamma\right)h\,,\, \lambda \right)\\[5pt]
> k_{2} &= f\left( x_{n} + \left(\frac{1}{4} + \gamma\right)\,h\,k_{1} + \frac{1}{4}h\,k_{2}\,,\, t_{n} + \left(\frac{1}{2} + \gamma\right)h \,,\, \lambda \right)\\[5pt]
> x_{n+1} &= x_{n} + \frac{1}{2}h\,(k_{1} + k_{2}) \\[5pt]
> t_{n+1} &= t_{n} + h
>\end{align*}
>$$
>

### Three-Stage Runge-Kutta Methods

>[!important] Definition
>The *Butcher array* for **Heun's third-order rules**  is given by 
>$$
>\begin{array}{c|cccc}
>0 & 0 & &    \\[5pt] 
>\dfrac{1}{3} & \dfrac{1}{3} & 0 &    \\[5pt] 
>\dfrac{2}{3} & 0 & \dfrac{2}{3} & 0 \\[5pt] 
 \hline
>  & \dfrac{1}{4} & 0 & \dfrac{3}{4} 
>\end{array}
>$$


>[!important] Definition
>The *Butcher array* for **Kutta's third-order rules**  is given by 
>$$
>\begin{array}{c|cccc}
>0 & 0 & &    \\[5pt] 
>\dfrac{1}{2} & \dfrac{1}{2} & 0 &    \\[5pt] 
>1 & -1 &  2 & 0 \\[5pt] 
 \hline
>  & \dfrac{1}{6} & \dfrac{4}{3}  & \dfrac{1}{6} 
>\end{array}
>$$



### Four-Stage Classic Runge-Kutta Method

>[!important] Definition
>The **Butcher array** for **explicit four-stage fourth-order Runge-Kutta method** is given by 
>$$
>\begin{array}{c|ccccc}
>0 & 0 & &  &  \\[5pt] 
>\dfrac{1}{2} & \dfrac{1}{2} & 0 &  &  \\[5pt] 
>\dfrac{1}{2} & 0 & \dfrac{1}{2} & 0 \\[5pt] 
>1 & 0 & 0 & 1 & 0 \\[5pt] 
 \hline
>  & \dfrac{1}{6} & \dfrac{1}{3} & \dfrac{1}{3} & \dfrac{1}{6}
>\end{array}
>$$
>- This specific method is commonly referred to as **the Runge-Kutta method.**
>- In general, a *four-stage Runge-Kutta method* has $$\frac{1}{2}(s(s+1)) = 10$$ free parameters.




## Explanation

>[!info]
>The *one-stage Runge-Kutta method* is **Euler method**.

- [[Explicit Euler Method for Discretization of ODE]]
- [[Implicit Euler Method for Discretization of ODE]]



-----------
##  Recommended Notes and References


- [[Ordinary Differential Equations]]
- [[Space of Continuous Differentiable Functions]]



- [[Numerical Methods for Ordinary Differential Equations by Butcher]] pp 91, 97, 118, 129, 335, 392
- [[Numerical Methods for Ordinary Differential Equations IVP by Griffiths]] pp 3, 19, 123 - 143, 197, 203