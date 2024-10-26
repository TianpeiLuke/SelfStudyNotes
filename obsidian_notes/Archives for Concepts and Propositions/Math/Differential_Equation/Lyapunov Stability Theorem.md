---
tags:
  - concept
  - math/differential_equation
keywords:
  - lyapunov_function
  - lyapunov_stability
topics:
  - differential_equation
name: Lyapunov Stability Theorem
date of note: 2024-06-14
---

## Concept Definition

>[!important]
>**Name**: Lyapunov Stability Theorem

![[Lyapunov Function#^0e5a54]]


>[!important] Lyapunov Stability Theorem
>Consider a *rest point* $x_{0}$ of the (autonomous) differential equation
>$$
>\begin{align*}
> \frac{d}{dt} x &= f(x), \quad x\in \mathbb{R}^n.
>\end{align*}
>$$
>and $U \subset \mathbb{R}^n$ is an open set with $x_{0} \in U.$
>
>If there is a **Lyapunov function** $V: U \to \mathbb{R}$ , then the **rest point** $x_{0}$ is **stable**. 
>
>If, in addition, the Lyapunov function is a **strict Lyapunov function**, then the *rest point* is **asymptotically stable**.

- [[Lyapunov Function]]
- [[Autonomous and Nonautonomous Ordinary Differential Equations]]
- [[Lyapunov Stable Asymptotically Stable Solution of ODE]]
- [[Continuous Function]]
- [[Gradient of Smooth Map]]
- [[Ordinary Differential Equations by Chicone]] pp 21

>[!important] Proposition
>Consider a *rest point* $x_{0}$ of the (autonomous) differential equation
>$$
>\begin{align*}
> \frac{d}{dt} x &= f(x), \quad x\in \mathbb{R}^n.
>\end{align*}
>$$
>and $U \subset \mathbb{R}^n$ is an open set with $x_{0} \in U.$
>
>Suppose that $V: U \to \mathbb{R}$ is a *smooth function* such that 
>- $$V(x_{0}) = 0$$
>- $$V(x) > 0, \quad x \in U \setminus \{ x_{0} \},$$
>  
>If $V$ has **positive value** somewhere in **each open set containing** $x_{0}$, then $x_{0}$ is **not stable**.

- [[Smooth Map between Euclidean Spaces]]



## Explanation






-----------
##  Recommended Notes and References



- [[Vector Field as Infinitesimal Generator of Local Flow]]
- [[Stochastic Differential Equations]]

- [[Ordinary Differential Equations by Chicone]]
