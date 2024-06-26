---
tags:
  - concept
  - math/stochastic_process
  - math/differential_equation
keywords:
  - weak_solution
  - stochastic_differential_equations
topics:
  - stochastic_process
  - differential_equation
name: Weak Solution to SDE
date of note: 2024-06-13
---

## Concept Definition

>[!important]
>**Name**: Weak Solution to SDE

>[!important] Definition
>If there exists a probability space $(\Omega, \mathscr{F}, \mathcal{P})$ with a *filtration* $(\mathcal{F}_{t})$,  a *Wiener process* $(\widehat{W}_{t})$ and a process $\widehat{X}(t)$ adapted to that *filtration*, such that 
>- $\widehat{X}(0)$ has the *given distribution* $\mathcal{P}$, for all $t$ where the following integral is defined
>- and $\widehat{X}(t)$ *satisfies* 
>$$
>\begin{align*}
>\widehat{X}(t) &= \widehat{X}(0) + \int_{0}^{t}\mu\left(\widehat{X}(u), u\right)\,du + \int_{0}^{t}\,\sigma\left(\widehat{X}(u), u\right)\,d\widehat{W}(u),
>\end{align*}
>$$
>
>then   $\widehat{X}(t)$ is called a **weak solution** to the *stochastic differential equation*
>$$
>\begin{align*}
>dX(t) &= \mu\left(X(t), t\right)\,dt + \sigma\left(X(t), t\right)\,dW(t)
>\end{align*}
>$$


- [[Filtration]]
- [[Adapted Stochastic Process and Non-anticipating Process]]
- [[Introduction to Stochastic Calculus by Klebaner]] pp 136

## Explanation

>[!info]
>The *Brownian motion* $(\widehat{W}_{t})$ from *the weak solution* is a *random function* on a **different function space**, which is usually more *regular* than the original space so that the **existence and uniqueness** conditions for SDE holds.
>
>$$
>\widehat{W}: \Omega \to \mathcal{C}(T, \mathcal{X}) \subset \mathcal{X}^{T} \quad \text{ v.s. } \quad W: \Omega \to \mathcal{X}^{T}.
>$$


- [[Existence and Uniqueness of Solution for Stochastic Differential Equation]]

>[!info]
>The **weakness** of solution is due to the fact that conditions on $\mu(x,t)$ and $A(x, t)$ is less strict.

>[!info]
>The idea of weak solution is to **construct a solution** to *the SDE* under *some regularity assumption* on function space.

- [[Construction of Weak Solution to SDE]]

>[!important]
>The concept of **weak solutions** allows us to give a meaning to an **SDE** *when strong solutions* do not exist. 
>
>Weak solutions are **solutions in distribution**, they can be realized (defined) on *some other probability space* and exist under *less stringent conditions* on the coefficients of the SDE.

## Construction of Weak Solution

- [[Construction of Weak Solution to SDE]]
- [[Martingale Problem]]



-----------
##  Recommended Notes and References

- [[Linear Stochastic Differential Equation]]
- [[Stochastic Differential Equations]]

- [[Markov Transition Kernel and Transition Function]]


- [[Introduction to Stochastic Calculus by Klebaner]]