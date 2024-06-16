---
tags:
  - concept
  - math/differential_equation
keywords:
  - lyapunov_function
topics:
  - differential_equation
name: Lyapunov Function
date of note: 2024-06-14
---

## Concept Definition

>[!important]
>**Name**: Lyapunov Function

>[!important] Definition
>Consider a *rest point* $x_{0}$ of the (autonomous) differential equation
>$$
>\begin{align*}
> \frac{d}{dt} x &= f(x), \quad x\in \mathbb{R}^n.
>\end{align*}
>$$
>and $U \subset \mathbb{R}^n$ is an open set with $x_{0} \in U.$
>
>A *continuous function* $V: U \to \mathbb{R}$ is called a **Lyapunov function** *for the differential equation at* $x_{0}$ if
>- $$V(x_{0}) = 0$$
>- $$V(x) > 0, \quad x \in U \setminus \{ x_{0} \},$$
>- $V$ is **continuous differentiable** at $U \setminus \{ x_{0} \}$ and $$\left\langle  \nabla V(x)\,,\, f(x) \right\rangle \le 0.$$
>
>$V$ is called a **strict Lyapunov function**, if, in addition,
>- $$\frac{d}{dx} V(x) := \nabla V(x) <0, \quad x \in U \setminus \{ x_{0} \}.$$

^0e5a54

- [[Autonomous and Nonautonomous Ordinary Differential Equations]]
- [[Lyapunov Stable Asymptotically Stable Solution of ODE]]
- [[Continuous Function]]
- [[Gradient of Smooth Map]]
- [[Ordinary Differential Equations by Chicone]] pp 21

## Explanation


## Lyapunov Theorem

- [[Lyapunov Stability Theorem]]



-----------
##  Recommended Notes and References


- [[Autonomous and Nonautonomous Ordinary Differential Equations]]
- [[Lyapunov Stable Asymptotically Stable Solution of ODE]]
- [[Ordinary Differential Equations]]

- [[Ordinary Differential Equations by Chicone]]
