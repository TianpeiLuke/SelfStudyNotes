---
tags:
  - entry_point
  - concept
  - numerical_methods/numerical_differential_equations
keywords: 
topics:
  - differential_equation
name: 
date of note: 2024-05-12
---

## List of Concepts


### Ordinary Differential Equations and Stochastic Differential Equations

- [[Concepts and Theorems for Ordinary Differential Equations]]

>[!important]
>Numerical methods for ordinary differential equations refer to a class of *iterative methods*, which are used in **temporal discretization** for the *approximate solutions* of ODE.

### Euler Method

- [[Taylor Series for Local Polynomial Approximation of Smooth Function]]
- [[Explicit Euler Method for Discretization of ODE]]
- [[Implicit Euler Method for Discretization of ODE]]



![[classification_numerical_ode.png]]

### Taylor Series Methods

>[!quote]
>- **Use of higher derivatives**
>  
>For many practical problems, it is possible to derive formulae for the **second and higher derivatives** of $y$, making use of the formula for $y′$ given by a differential equation. This opens up many computational options, which can be used to **enhance** the performance of **multistage (Runge–Kutta)** and **multivalue (multistep) methods**. If these higher derivatives are available, then the most popular option is to use them to evaluate a number of terms in Taylor’s theorem.
>
>-- [[Numerical Methods for Ordinary Differential Equations by Butcher]] pp 92  

- [[Taylor Series Methods for Numerical ODE]]


### Linear Multi-Step Methods

>[!quote]
>- **Greater dependence on previous values**
>
>After the first step of a numerical method has been completed, approximations are available, to be used in the computation of $y_{n}$, not only for $y(x_{n-1})$ and $y'(x_{n-1})$ but  also for $y(x_{n-2})$ and $y'(x_{n-2})$. 
>
>After further steps, even more previous information is available. Instead of computing $y_{n}$ in a complicated manner *from just the value of* $y_{n-1}$, we could consider **making more use of the values computed in past steps**, as they become available.
>
>-- [[Numerical Methods for Ordinary Differential Equations by Butcher]] pp 92

- [[Linear Multistep Methods for Numerical ODE]]

- [[Characteristic Polynomials of Linear Multistep Methods for Numerical ODE]]
- [[k-Step Methods for Numerical ODE]]
- [[Stability of Linear Multistep Methods for Numerical ODE]]

- [[Trapezoidal Rule as Two-Step Method for Numerical ODE]]
- [[Adams-Bashforth Method for Numerical ODE]]
- [[Adams-Moulton Method for Numerical ODE]]
- [[Nyström Method for Numerical ODE]]



### Runge-Kutta Methods

>[!quote]
>- **More computations in a step**
>
>Instead of computing $f$ only once in each time step, as in the Euler method, we might look for methods that **evaluate** $f$ (with different arguments, of course) **two or more times**.
>
>-- [[Numerical Methods for Ordinary Differential Equations by Butcher]] pp 90

- [[Runge-Kutta Methods for Numerical ODE]]


### Hamiltonian System

- [[Concepts and Theorems for Calculus of Variations]]
- [[Lagrangian Function in Mechanics and Variational Calculus]]
- [[Euler–Lagrange Equations]]
- [[Hamiltonian Function in Mechanic and Variational Calculus]]
- [[Hamiltonian Systems of Differential Equations]]

- [[Symplectic Euler Method for Hamiltonian System]]


### Numerical Solution of Stochastic Differential Equations

- [[Concepts and Theorems for Stochastic Differential Equations]]

- [[Explicit Euler-Maruyama Method for Discretization of SDE]]





## Explanation





-----------
##  Recommended Notes and References




- [[Partial Differential Equations by Evans]]
- [[Ordinary Differential Equations by Chicone]]
- [[Numerical Methods for Ordinary Differential Equations IVP by Griffiths]]
- [[Numerical Methods for Ordinary Differential Equations by Butcher]]
- [[Numerical Solution of Stochastic Differential Equations by Kloeden]]