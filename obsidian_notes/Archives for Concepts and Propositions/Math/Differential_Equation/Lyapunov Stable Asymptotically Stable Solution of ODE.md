---
tags:
  - concept
  - math/differential_equation
keywords:
  - lyapunov_stability
topics:
  - differential_equation
name: Lyapunov Stability
date of note: 2024-06-14
---

## Concept Definition

>[!important]
>**Name**: Lyapunov Stability

>[!quote]
>The concept of **Lyapunov stability** is meant to capture the intuitive notion of stability—an *orbit* is **stable** if *solutions* that **start nearby** **stay nearby**.
>-- [[Ordinary Differential Equations by Chicone]]. pp 21

>[!important] Definition
>A **rest point** $x_{0}$ of the (autonomous) differential equation
>$$
>\begin{align*}
> \frac{d}{dt} x &= f(x), \quad x\in U
>\end{align*}
>$$
 >is **stable** (in the sense of **Lyapunov**) if for each $\epsilon$, there exists a number $\delta>0$ such that
>$$
>\lvert \phi_{t}(x) - x_{0} \rvert < \epsilon 
>$$
>for all $t \ge 0$ *whenever* $|x − x_{0}| < \delta$. Here $\phi_{t}(\cdot)$ is the *flow* of ODE

- [[Ordinary Differential Equations]]
- [[Autonomous and Nonautonomous Ordinary Differential Equations]]
- [[Global Flow on Smooth Manifold]]

>[!important] Definition
>A **rest point** $x_{0}$ of the differential equation
>$$
>\begin{align*}
> \frac{d}{dt} x &= f(x), \quad x\in U
>\end{align*}
>$$
 >is **asymptotically stable** (in the sense of **Lyapunov**) if there exists a number $\delta>0$ such that
>$$
>\lim_{ t \to \infty } \lvert \phi_{t}(x) - x_{0} \rvert = 0
>$$
>for all $t \ge 0$ *whenever* $|x − x_{0}| < \delta$. Here $\phi_{t}(\cdot)$ is the *flow* of ODE



>[!important] Definition
>Consider the differential equation
>$$
>\begin{align*}
> \frac{d}{dt} x &= f(x), \quad x\in U
>\end{align*}
>$$
>and $x_{0}\in U$.
>
>The *solution* $$t \mapsto \phi_{t}(x_{0})$$ of this differential equation is **stable** (in the sense of **Lyapunov**) if each  $\epsilon$, there exists a number $\delta>0$ such that
>$$
>\lvert \phi_{t}(x) - \phi_{t}(x_{0}) \rvert < \epsilon 
>$$
>for all $t \ge 0$ *whenever* $|x − x_{0}| < \delta$.



>[!important] Definition
>Consider the differential equation
>$$
>\begin{align*}
> \frac{d}{dt} x &= f(x), \quad x\in U
>\end{align*}
>$$
>and $x_{0}\in U$.
>
>The *solution* $$t \mapsto \phi_{t}(x_{0})$$ of this differential equation is **asymptotically stable** (in the sense of **Lyapunov**) if it is *stable*, *and* there exists a constant $a > 0$ such that 
>$$
> \lim_{ t \to \infty }\; \lvert \phi_{t}(x) - \phi_{t}(x_{0}) \rvert = 0
>$$
>*whenever* $|x − x_{0}| < a$.


## Explanation

>[!info]
>In other word, if a set of **Lyapunov stable** flows $\{\phi_{t}, \; t\in J_{0} \}$ forms an **equicontinuous family**.

- [[Equicontinuity]]


## Smooth Manifold

>[!important]
>We can extend the definition of **Lyapunov Stability** to smooth manifold by using [[Local Flow on Smooth Manifold]]





-----------
##  Recommended Notes and References


- [[Lyapunov Stability Theorem]]
- [[Lyapunov Function]]
- [[Ordinary Differential Equations]]

- [[Ordinary Differential Equations by Chicone]]
- Wikipedia [Lyapunov_stability](https://en.wikipedia.org/wiki/Lyapunov_stability)