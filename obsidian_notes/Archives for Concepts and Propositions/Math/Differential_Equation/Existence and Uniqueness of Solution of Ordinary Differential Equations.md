---
tags:
  - concept
  - math/differential_equation
keywords:
  - existence_uniqueness_solution
  - ordinary_differential_equations
topics:
  - differential_equation
name: Existence and Uniqueness of Solution of Ordinary Differential Equations
date of note: 2024-06-14
---

## Concept Definition

>[!important]
>**Name**: Existence and Uniqueness of Solution of Ordinary Differential Equations


>[!important] Theorem
>Let $J \subseteq \mathbb{R}$, $U \subseteq \mathbb{R}^n$, and $\Lambda \subseteq \mathbb{R}^k$ be *open subsets*, and suppose that $f: U \times J \times \Lambda \to \mathbb{R}^n$ is a *smooth function*, and $(x_{0}, t_{0},\lambda_{0}) \in U \times J \times \Lambda$.
>
 >Then there **exist** *open subsets* $U_{0} \subseteq U$,   $J_{0} \subseteq J$,  $\Lambda_{0} \subseteq \Lambda$, with $(x_{0},t_{0},\lambda_{0}) ∈ U_{0}  \times J_{0} \times \Lambda_{0}$ and a *function* $\phi : U_{0} \times J_{0} \times  J_{0} \times \Lambda_{0} \to \mathbb{R}^n$ given by $$(x, t, s, \lambda) \mapsto \phi(x, t, s, \lambda)$$ such that for *each point* $(x_{1},t_{1},\lambda_{1}) ∈ U_{0}  \times J_{0} \times \Lambda_{0}$, the function $$t \mapsto \phi(x_{1}, t, t_{1}, \lambda_{1})$$ is the **unique solution** defined on $J_{0}$ of the **initial value problem** given by the differential equation 
>$$
>\left\{
>\begin{align*}
>\frac{d}{dt} x(t) &= f\left(x(t), t, \lambda\right),\\
>x(t_{1}) &= x_{1}
>\end{align*}
>\right.
>$$
>with *initial condition*.

- [[Space of Continuous Differentiable Functions]]
- [[Ordinary Differential Equations]]
- [[Ordinary Differential Equations by Chicone]] pp 3


## Explanation

>[!info]
>The existence and uniqueness theorem is so fundamental in science that it is sometimes called the “**principle of determinism.**” 
>
>The idea is that *if we know the initial conditions*, then we can **predict the future states of the system.** Although the principle of determinism is validated by the proof of the existence and uniqueness theorem, the **interpretation** of *this principle for physical systems is not as clear as it might seem.* The problem is that solutions of differential equations can be very complicated. For example, the future state of the system might **depend sensitively on the initial state** of the system. Thus, if we do not know the initial state exactly, the final state may be very difficult (if not impossible) to predict.

>[!important]
>We only specify explicit variables.
>
>We will write $$t \mapsto \phi(x, t)$$ to denote the solution such that $\phi(x, 0) = x_0$. 
>
>If we wish to **specify the parameter vector**, we use $$t \mapsto \phi(x, t, \lambda)$$ to denote the solution such that $\phi(x, 0, \lambda) = x_0$. 




## Proof

- [[Contraction Function]]
- [[Fixed Point of Map]]
- [[Contraction Map Principle]]




-----------
##  Recommended Notes and References


- [[Smoothness of Solution of ODE]]

- [[Existence and Uniqueness of Solution for Stochastic Differential Equation]]

- [[Ordinary Differential Equations]]
- [[Ordinary Differential Equations by Chicone]]
