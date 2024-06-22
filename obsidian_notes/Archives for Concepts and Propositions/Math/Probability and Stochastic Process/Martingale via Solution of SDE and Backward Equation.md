---
tags:
  - concept
  - math/stochastic_process
  - math/differential_equation
keywords:
  - martingale
  - ito_formula
  - stochastic_differential_equations
  - kolmogorov_backward_equation
topics:
  - differential_equation
  - stochastic_process
name: Martingale via Solution of SDE and Backward Equation
date of note: 2024-06-19
---

## Concept Definition

>[!important]
>**Name**: Martingale via Solution of SDE and Backward Equation

### Itô Formula in Compact Form

>[!important] Proposition
>Suppose $X_{t}$ is a Ito process that satisfies the equation
>$$
>dX = \mu(X, t)\,dt + \sigma\left(X,  t\right)\,dW
>$$
>and $L_{t}$ is the *infinitesimal generator* of $X_{t}$
>$$
>L_{t} := \frac{1}{2}\sigma^2(x, t)\,\frac{ \partial^2 }{ \partial x^2 } + \mu(x, t) \frac{ \partial  }{ \partial x }. 
>$$
>
>Then for any function $f: \mathcal{X} \times [0,T] \to \mathbb{R}$, $$(x,t) \mapsto f(x,t)$$ that is *twice continuous differentiable* in first argument, and *once continuous differentiable* in second argument, the stochastic differential
>$$
>df\left( X_{t}, t\right) = \left( L_{t} + \frac{ \partial  }{ \partial t}  \right)f(X_{t}, t)\,dt + \frac{ \partial  }{ \partial x }f(X_{t}, t)\,\sigma \left( X_{t}, t \right)\,dW. 
>$$

^2d4df5

- [[Itô Chain Rule and Itô Formula]]
- [[Infinitesimal Generator of Stochastic Differential Equation]]

### Martingale from Solution of SDE

>[!important] Theorem
>Let $X_{t}$ be a **solution** of the SDE, 
>$$
>dX_{t} = \mu(X_{t}, t)\,dt + \sigma\left(X_{t},  t\right)\,dW_{t}
>$$
>where the *drift coefficient* $\mu(x,t)$ and *diffusion coefficient* $\sigma(x,t)$ satisfies the *Lipschitz conditions* and *linear growth conditions*. That is, $X_{t}$ is the **unique solution** of SDE.  
>
>If $f(x,t)$  is *twice continuous differentiable* in $x$, and *once continuous differentiable* in $t,$ i.e. $f\in \mathcal{C}^{2,1}(\mathbb{R})$ with **bounded first derivative** in $x$, then the process
>$$
>\begin{align*}
> M_{f}(t) := f(X_{t}, t) - \int_{0}^{t}\left( L_{s} + \frac{ \partial  }{ \partial t}  \right)f(X_{s}, s)\,ds
>\end{align*}
>$$ 
>is a **martingale**.

^c8ae3e

- [[Properties of Solution for Stochastic Differential Equation]]
- [[Fokker–Planck and Kolmogorov Forward-Backward Equation]]

>[!important] Proposition
>Let $X_{t}$ be a **solution** of the SDE, 
>$$
>dX_{t} = \mu(X_{t}, t)\,dt + \sigma\left(X_{t},  t\right)\,dW_{t}
>$$
>where the *drift coefficient* $\mu(x,t)$ and *diffusion coefficient* $\sigma(x,t)$ satisfies the *Lipschitz conditions* and *linear growth conditions*. That is, $X_{t}$ is the **unique solution** of SDE.  
>
>- If $\lvert X_{0} \rvert$ has **finite moment generating function**, i.e. $$ \mathbb{E}\left[\exp \left(\lambda\, \lvert X_{0} \rvert \right) \right] < \infty,$$ for all $\lambda \in \mathbb{R}$, then **so does** $\lvert X_{t} \rvert$ for any $t \ge 0$, i.e. $$ \mathbb{E}\left[\exp \left(\lambda\, \lvert X_{t} \rvert \right) \right] < \infty.$$
>
>In this case, suppose $f(x, t)\in \mathcal{C}^{2,1}$, satisfying the following conditions:
>- for any $t$, there exists *constants* $c_{t}$ and $k_{t}$ such that *for all* $x$ and $t >0$, and all $0 \le u \le t$, 
>$$
>\max\left( \left\lvert \frac{ \partial }{ \partial t }f(x, t)  \right\rvert\,,\, \; \left\lvert \frac{ \partial }{ \partial x }f(x, t)  \right\rvert\,,\, \left\lvert \frac{ \partial^2 }{ \partial x^2 }f(x, t)  \right\rvert   \right) \le c_{t}\,\exp\left( k_{t} \lvert x \rvert   \right)
>$$
>
>Then the process
>$$
>\begin{align*}
> M_{f}(t) := f(X_{t}, t) - \int_{0}^{t}\left( L_{s} + \frac{ \partial  }{ \partial t}  \right)f(X_{s}, s)\,ds
>\end{align*}
>$$ 
>is a **martingale** 

^76bb2e

- [[Moment Generating Function]]

### Martingale from Solution of Kolmogorov Backward Equation

>[!important] Corollary
>Let $f(x, t)$ solve the **Kolmogorov backward equation** 
>$$
>\begin{align*}
>\left( L_{s} + \frac{ \partial  }{ \partial t}  \right)\,f(x, t) := \frac{ \partial  }{ \partial t}f(x, t) + L_{t}\,f(x, t) = 0 
>\end{align*}
>$$
>and the conditions of either of two above theorems holds, i.e. $f \in \mathcal{C}^{2,1}$ with additional conditions
>- either $f$ has *bounded first derivatives*
>- or the maximum variation of $\partial_{t} f$,   $\partial_{x} f$, and $\partial_{x}^2f$ has *exponential growth*.
>
>Then $$f(X_{t}, t)$$ is a **martingale**.

- [[Fokker–Planck and Kolmogorov Forward-Backward Equation]]

>[!important] Theorem
>Let $f(x, t)$ solve the **Kolmogorov backward equation** with **initial condition**
>$$
>\begin{align*}
>\left\{
>\begin{array}{cc}
>\dfrac{ \partial  }{ \partial t}f(x, t) + L_{t}\,f(x, t) = 0& \\
>f(x, T) = g(x)& \\
>\end{array}
>\right.
>\end{align*}
>$$
>and the conditions of either of two above theorems holds, i.e. $f \in \mathcal{C}^{2,1}$ with additional conditions
>- either $f$ has *bounded first derivatives*
>- or the maximum variation of $\partial_{t} f$,   $\partial_{x} f$, and $\partial_{x}^2f$ has *exponential growth*.
>
>Then 
>$$
>f(x, t) =  \mathbb{E}\left[ g(X_{T}) |\,X_{t} = x \right]
>$$

- [[Fokker–Planck and Kolmogorov Forward-Backward Equation#Markov Process as Weak Solution of SDE]]

>[!important] Theorem
>Let $f(x, t)$ solve the **second-order parabolic equation** with **initial condition**
>$$
>\begin{align*}
>\left\{
>\begin{array}{cc}
>\dfrac{ \partial  }{ \partial t}f(x, t) + L_{t}\,f(x, t) = -\phi(x)& \\
>f(x, T) = g(x)& \\
>\end{array}
>\right.
>\end{align*}
>$$
>and the conditions of either of two above theorems holds, i.e. $f \in \mathcal{C}^{2,1}$ with additional conditions
>- either $f$ has *bounded first derivatives*
>- or the maximum variation of $\partial_{t} f$,   $\partial_{x} f$, and $\partial_{x}^2f$ has *exponential growth*.
>
>Then 
>$$
>f(x, t) =  \mathbb{E}\left[ g(X_{T}) + \int_{0}^{T}\,\phi\left( X_{s} \right)ds  \;\Big|\; \,X_{t} = x \right]
>$$

^f4351f

### Dynkin Formula

- [[Dynkin Formula]]

### Feynman-Kac Formula

- [[Feynman-Kac Formula]]

## Explanation

>[!info]
>The above two theorems show that the **distribution** of the **weak solution of SDE**, $X_{t}$, solves the **Martingale problem**.

- [[Weak Solution to Stochastic Differential Equation]]
- [[Martingale Problem]]




-----------
##  Recommended Notes and References

- [[Dynkin Formula]]
- [[Itô Process]]
- [[Itô Chain Rule and Itô Formula]]

- [[Martingale Problem]]
- [[Martingale]]
- [[Stochastic Differential Equations]]

- [[Introduction to Stochastic Calculus by Klebaner]] pp 149
- Oksendal, B. (2013). _Stochastic differential equations: an introduction with applications_. Springer Science & Business Media pp 149