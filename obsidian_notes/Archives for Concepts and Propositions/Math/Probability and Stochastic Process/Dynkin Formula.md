---
tags:
  - concept
  - math/stochastic_process
  - math/differential_equation
keywords:
  - dynkin_formula
topics:
  - differential_equation
  - stochastic_process
name: Dynkin Formula
date of note: 2024-06-19
---

## Concept Definition

>[!important]
>**Name**: Dynkin's Formula

![[Martingale via Solution of SDE and Backward Equation#^c8ae3e]]

![[Martingale via Solution of SDE and Backward Equation#^76bb2e]]

- [[Martingale via Solution of SDE and Backward Equation]]

### Dynkin Formula

>[!important] Corollary (Dynkin's Formula)
>Let $X_{t}$ satisfies the *stochastic differential equation*
>$$
>dX = \mu(X, t)\,dt + \sigma\left(X,  t\right)\,dW
>$$
>
>If the conditions of either of two above theorems holds, i.e. $f \in \mathcal{C}^{2,1}$ with additional conditions
>- either $f$ has *bounded first derivatives*
>- or the maximum variation of $\partial_{t} f$,   $\partial_{x} f$, and $\partial_{x}^2f$ has *exponential growth*.
>  
>then for  any $t$, with $0 \le t \le T$, the *expectation*
>$$
>\begin{align*}
>  \mathbb{E}\left[ f(X_{t}, t)  \right] &= f(X_{0}, 0)  +  \mathbb{E}\left[   \int_{0}^{t}\left( L_{s} + \frac{ \partial  }{ \partial t}  \right)f(X_{s}, s)\,ds\right]
>\end{align*}
>$$ 
>
>Moreover, if $\tau$ is a **bounded stopping time** with respect to the diffusion process $X_{t}$, i.e.  $0 \le \tau \le T$,  then the above holds by replacing $t$ with $\tau$, i.e.
>$$
>\begin{align*}
>  \mathbb{E}\left[ f(X_{\tau}, \tau)  \right] &= f(X_{0}, 0)  +  \mathbb{E}\left[   \int_{0}^{\tau}\left( L_{s} + \frac{ \partial  }{ \partial t}  \right)f(X_{s}, s)\,ds\right]
>\end{align*}
>$$ 

- [[Markov Chain and Markov Process]]
- [[Stopping Time and Stochastic Integral]]
- [[Strong Markov Property]]



## Explanation





-----------
##  Recommended Notes and References

- [[Fokker–Planck and Kolmogorov Forward-Backward Equation]]
- [[Infinitesimal Generator of Stochastic Differential Equation]]

- [[Martingale]]
- [[Stochastic Differential Equations]]

- [[Introduction to Stochastic Calculus by Klebaner]] pp 149
- Oksendal, B. (2013). _Stochastic differential equations: an introduction with applications_. Springer Science & Business Media. pp 127