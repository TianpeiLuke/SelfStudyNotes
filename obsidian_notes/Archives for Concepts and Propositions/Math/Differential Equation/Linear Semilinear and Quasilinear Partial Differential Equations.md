---
tags:
  - concept
  - math/differential_equation
  - math/functional_analysis
keywords:
  - linear_partial_differential_equations
  - semilinear_partial_differential_equations
  - quasilinear_partial_differential_equations
topics:
  - differential_equation
name: Linear Semilinear and Quasilinear Partial Differential Equations
date of note: 2024-06-15
---

## Concept Definition

>[!important]
>**Name**: Linear, Semilinear, and Quasilinear Partial Differential Equations


![[Space of Functions of Rapid Decrease and Schwartz Class#^f10f2e]]


>[!important] Definition
>The partial differential equation
>$$
>\begin{align*}
> F\left(D^{k}u(x)\,,\,D^{k-1}u(x) \,{,}\ldots{,}\, Du(x)\,,\,u(x)\,,\, x\right) = 0, \quad x \in U
>\end{align*}
>$$
>is called a **linear**, if it has the form
>$$
>\sum_{|\alpha| \le k}a_{\alpha}(x)\,D^{\alpha}u(x) = f(x)
>$$ 
>for given functions $a_{\alpha}(x)$ for $|\alpha| \le k$ and $f(x)$. 
>
>This *linear partial differential equation* is **homogeneous** if $f\equiv 0.$

- [[Partial Differential Equations]]

>[!important] Definition
>The partial differential equation
>$$
>\begin{align*}
> F\left(D^{k}u(x)\,,\,D^{k-1}u(x) \,{,}\ldots{,}\, Du(x)\,,\,u(x)\,,\, x\right) = 0, \quad x \in U
>\end{align*}
>$$
>is called a **semilinear**, if it has the form
>$$
>\sum_{|\alpha| = k}a_{\alpha}(x)\,D^{\alpha}u(x) + a_{0}\left(D^{k-1}u(x) \,{,}\ldots{,}\, Du(x)\,,\,u(x)\,,\, x\right)= 0
>$$ 


>[!important] Definition
>The partial differential equation
>$$
>\begin{align*}
> F\left(D^{k}u(x)\,,\,D^{k-1}u(x) \,{,}\ldots{,}\, Du(x)\,,\,u(x)\,,\, x\right) = 0, \quad x \in U
>\end{align*}
>$$
>is called a **quasilinear**, if it has the form
>$$
>\sum_{|\alpha| = k}a_{\alpha}\left(D^{k-1}u(x) \,{,}\ldots{,}\, Du(x)\,,\,u(x)\,,\, x\right)\,D^{\alpha}u(x) + a_{0}\left(D^{k-1}u(x) \,{,}\ldots{,}\, Du(x)\,,\,u(x)\,,\, x\right)= 0
>$$ 

>[!important] Definition
>The partial differential equation
>$$
>\begin{align*}
> F\left(D^{k}u(x)\,,\,D^{k-1}u(x) \,{,}\ldots{,}\, Du(x)\,,\,u(x)\,,\, x\right) = 0, \quad x \in U
>\end{align*}
>$$
>is called a **nonlinear**, if it depends **nonlinearly** on the **highest order derivatives**.


## Explanation

>[!important]
>- In **linear PDE**, both the **linear coefficient** and **bias term** *__do not__ depend on any derivatives* of $u$;
>- In **semilinear PDE**, tthe **linear coefficient** is *independent* from derivative of $u$, *but* the **bias term** may depend on *lower-order derivatives* of $u$;
>- In **qusiilinear PDE**, both the **linear coefficient** and **bias term** may __depend__ on _lower-order derivatives_ of $u$;

## Example

>[!example]
>The Laplace's equation





-----------
##  Recommended Notes and References

- [[Partial Differential Equations]]

- [[Linear ODE with Constant Coefficients]]
- [[Homogeneous Linear Differential Equations]]
- [[Autonomous and Nonautonomous Ordinary Differential Equations]]
- [[Homogeneous Linear Stochastic Differential Equation]]
- [[Linear Stochastic Differential Equation]]

- [[Space of Functions of Rapid Decrease and Schwartz Class]]
- [[Space of Tempered Distributions]]

- [[Partial Differential Equations by Evans]]