---
tags:
  - concept
  - math/differential_equation
  - math/functional_analysis
keywords:
  - nonlinear_partial_differential_equations
  - hamiltonian_system_ode
  - hamilton_jacobi_equation
topics:
  - differential_equation
name: Hamilton-Jacobi Equation
date of note: 2024-06-15
---

## Concept Definition

>[!important]
>**Name**: Hamilton-Jacobi Equation


>[!important] Definition
>Let $u: \mathbb{R}^n \times [0, \infty) \to \mathbb{R}$ be the unknown function, $x := (x^1 \,{,}\ldots{,}\,x^n)$. Denote $$Du := \nabla u  = \left(\frac{\partial}{\partial x^i }u \,{,}\ldots{,}\, \frac{\partial}{\partial x^n }u\right).$$
>
>Define the **Hamiltonian** $H: \mathbb{R}^n \to \mathbb{R}$ and the *initial function* $g: \mathbb{R}^n \to \mathbb{R}$.
>
>The **Hamilton-Jacobi equation** is defined as 
>$$
>\left\{
>\begin{align*}
> \frac{d}{dt} u + H\left(Du\right) &=0\\[5pt]
>  u(x,  0) &= g(x)
>\end{align*}
>\right.
>$$
>

- [[Partial Differential Equations]]
- [[Linear Semilinear and Quasilinear Partial Differential Equations]]


## Explanation

>[!info]
>The **Hamilton-Jacobi equation** is a **nonlinear PDE**.

## Hamiltonian Systems of Differential Equations

>[!important]
>The **characteristic equations** associated with *Hamilton-Jacobi equation* 
>$$
>\frac{d}{dt} u + H(Du, x) = 0
>$$
>are the **Hamiltonian systems of ODEs**
>$$
>\left\{
>\begin{align*}
> \frac{d}{dt} x^{i} &= \frac{ \partial  }{ \partial p^{i} }H(p, x), \quad i=1 \,{,}\ldots{,}\,n\\
>  \frac{d}{dt} p^{i} &= - \frac{ \partial  }{ \partial x^{i} }H(p, x), \quad i=1 \,{,}\ldots{,}\,n
>\end{align*}
>\right.
>$$
>where $H: \mathbb{R}^n \times \mathbb{R}^n \to \mathbb{R}$ is the **Hamiltonian** associated with **Lagrangian**.

- [[Hamiltonian Function in Mechanic and Variational Calculus]]
- [[Lagrangian Function in Mechanics and Variational Calculus]]
- [[Hamiltonian Systems of Differential Equations]]
- [[Legendre Transform]]


## Euler-Lagrange Equation

- [[Euler–Lagrange Equations]]





-----------
##  Recommended Notes and References


- [[Linear Semilinear and Quasilinear Partial Differential Equations]]
- [[Partial Differential Equations]]




- [[Optimal Transport in Space of Measures]]
- [[Wasserstein Space]]

- [[Partial Differential Equations by Evans]]
- [[Optimal Transport for Applied Mathematicians by Santambrogio]]