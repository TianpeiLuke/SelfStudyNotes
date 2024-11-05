---
tags:
  - concept
  - numerical_methods/numerical_differential_equations
keywords:
  - symplectic_euler_method_hamiltonian_ode
topics:
  - numerical_differential_equation
name: Symplectic Euler Method for Hamiltonian System
date of note: 2024-10-31
---

## Concept Definition

>[!important]
>**Name**: Symplectic Euler Method for Hamiltonian System

![[Hamiltonian Systems of Differential Equations#^ad0948]]

>[!important] Definition
>Let  $H: \mathbb{R}^{n} \times \mathbb{R}^{n} \to \mathbb{R}$ be a *smooth function*, called **Hamiltonian**, given by
>$$
>(q_{1} \,{,}\ldots{,}\,q_{n}, p_{1} \,{,}\ldots{,}\,p_{n}) \mapsto H(q_{1} \,{,}\ldots{,}\,q_{n}, p_{1} \,{,}\ldots{,}\,p_{n})
>$$
>and define the associated **Hamiltonian system** on $\mathbb{R}^{2n}$ with *Hamiltonian* $H$
>$$
>\left\{\begin{align*}
> \frac{d}{dt} q_{i} &= \dfrac{ \partial H }{ \partial p_{i} }, \quad i=1 \,{,}\ldots{,}\, n \\[5pt]
> \frac{d}{dt} p_{i} &= - \dfrac{ \partial H }{ \partial q_{i} }, \quad i=1 \,{,}\ldots{,}\, n
>\end{align*}
>\right.
>$$
>- The task is to find the *temporal discretization* of the *approximate solution* of the *Hamiltonian ODEs*.
>
>The **symplectic Euler method** is of the form ($i=1$)
>$$
>\begin{align*}
> p_{n+1} &= p_{n} - h\,\dfrac{ \partial H }{ \partial q}(p_{n+1}, q_{n}) \\[5pt]
> q_{n+1} &= q_{n} + h\,\dfrac{ \partial H }{ \partial p}(p_{n+1}, q_{n}) 
>\end{align*}
>$$
>- This is a combination of *implicit Euler* and *explicit Euler method*
>	- the update for $p$ follows the *implicit Euler rule*
>	- the update for $q$ follows the *explicit Euler rule.*
>- This method is **symplectic** since $$\det \left(\left[ \begin{array}{cc} \dfrac{\partial p_{n+1} }{ \partial p_{n} } & \dfrac{\partial p_{n+1} }{ \partial q_{n} } \\[5pt] \dfrac{\partial q_{n+1} }{ \partial p_{n} } & \dfrac{\partial q_{n+1} }{ \partial q_{n} }   \end{array} \right] \right) = 1$$
>- If the *Hamiltonian* is **separable** i.e. $$H(p, q) := T(p) + V(q),$$ then the above *symplectic Euler method* is **explicit** 
>$$
>\begin{align*}
> p_{n+1} &= p_{n} - h\,\dfrac{d}{dq}V(q_{n}) \\[5pt]
> q_{n+1} &= q_{n} + h\,\dfrac{d}{dp}T(p_{n+1}) 
>\end{align*}
>$$


- [[Hamiltonian Systems of Differential Equations]]
- [[Hamiltonian Function in Mechanic and Variational Calculus]]
- [[Explicit Euler Method for Discretization of ODE]]
- [[Implicit Euler Method for Discretization of ODE]]
- [[Symplectic Matrix]]


## Explanation




- [[Hamiltonian Monte Carlo]]


-----------
##  Recommended Notes and References


- [[Ordinary Differential Equations]]
- [[Autonomous and Nonautonomous Ordinary Differential Equations]]


- [[Numerical Methods for Ordinary Differential Equations IVP by Griffiths]] pp 210 - 217
