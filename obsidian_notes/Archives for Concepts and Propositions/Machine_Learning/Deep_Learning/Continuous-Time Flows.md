---
tags:
  - concept
  - machine_learning/models
  - deep_learning/generative_models
  - math/differential_equation
  - numerical_methods/numerical_differential_equations
keywords:
  - ordinary_differential_equations
  - normalizing_flow_model
  - continuous_time_flows
topics:
  - deep_learning/generative_models
  - differential_equation
  - numerical_differential_equation
name: Continuous-Time Flows
date of note: 2024-08-16
---

## Concept Definition

>[!important]
>**Name**: Continuous-Time Flows

![[Normalizing Flows#^294151]]

![[Normalizing Flows#^8d93c1]]

>[!important] Definition
>We can consider the *normalizing flow* as a sequence of bijections $f_{1}\,{,}\ldots{,}\,f_{T}$.
>- Starting from $x_{0} = z$, this create a sequence of outputs $x_{1}\,{,}\ldots{,}\,x_{T}$ as $$x_{t} = f_{t}(x_{t-1})$$
>  
>An alternative way is to have the a *continuous output* $x(t)$ described in terms of *ordinary differential equations* with *initial value condition*
>$$\left\{
>\begin{align}
> \frac{d}{dt} x(t) &= F(x(t), t) \\[5pt] 
> x(0) &= z
>\end{align}
>\right.
>$$
>where
>- $$F: \mathbb{R}^{d} \times [0,T] \to \mathbb{R}^{d}$$ is *continuously differentiable*, and defines a *vector field* that characterized the ODE.
>- By existence and uniqueness of solution of ODE, there **exists** a **unique** *solution* for the *IVP* if $F$ is *Lipschitz continuous* with *Lipschitz constant* not depending on $t$ $$\lvert F(x_{1}, t) - F(x_{2}, t) \rvert \le L\,\lVert x_{1} - x_{2} \rVert $$
>- The **continuous flow** $f_{t}$ is a function $$f_{t}: \mathbb{R}^{d} \to \mathbb{R}^{d}, \quad \forall t\in [0,T]$$ that takes in the input $x(0) = z$ and maps it to $x(t)$ *along the solution of IVP* $$f_{t}(z) := f(z;\,0, t) = x(t)$$
>	- We have $$f_{0}(z) = z\, \quad f_{T}(z) = x(T)$$
>	- We can express $f_{t}$ in terms of the integral equation $$f_{t}(z) = f(x(0), t) = x(0) + \int_{0}^{t}F(x(s), s;\, w)\,ds$$
>	- $f_{t}$ satisfies the *group axiom* 
>		- $$f_{t} \circ f_{s} = f_{t+ s}$$
>		- $$f_{0} = I$$
>	- Thus $f_{t}$ is a *one-parameter group action*.
>- The **Jacobian determinant** cannot be expressed analytically, but we can define it via a separate *ODE*
>	- Define the **log Jacobian determinant** of $f_{t}$ as $$L(t) := \log \lvert \det D f(x_{0}; t) \rvert $$
>		- We have $$L(0) = \log \lvert \det I \rvert = 0$$
>	- It can be shown that $L(t)$ satisfies the *ordinary differential equation* with *initial condition* $$\left\{\begin{align}\frac{d}{dt} L(t) &= \text{tr}\left[(D_{x}F(\cdot, t))\,(x(t))\right]  \\[5pt]  L(0) &= 0\end{align}\right.$$
>		- The *rate of change* for the *log-det of Jacobian matrix* is equal to the *Jacobian trace* of vector field $F(\cdot,t)$
>		- $L(T)$ corresponds to the *Jacobian determiant* of $f:= f(T)$.
>- Finally, we can have joint ODE for $(x(t), L(t))$ as
>$$\left\{
>\begin{align}
> \frac{d}{dt} (x(t), L(t)) &= \left[ \begin{array}{c}F(x(t), t) \\[5pt] \text{tr}\left[(D_{x}F(\cdot, t))\,(x(t))\right] \end{array} \right]  \\[5pt] 
> (x(0), L(0)) &= (z, 0)
>\end{align}
>\right.
>$$

^f77037

- [[Normalizing Flows]]
- [[Residual Flows]]
- [[Ordinary Differential Equations]]
- [[Vector Field as Infinitesimal Generator of Global Flow]]
- [[Global Flow on Smooth Manifold]]
- [[Maximal Integral Curve of Vector Field]]
- [[Existence and Uniqueness of Solution of Ordinary Differential Equations]]
- [[Lipschitz Continuous Function]]

>[!info] Proof
>Note that 
>$$
>\frac{d}{dX} \log |\det X| = (X^{-1})^{T} 
>$$
>Thus
>$$
>\begin{align*}
> \frac{d}{d D f_{t}} \log \lvert \det D f_{t} \rvert &= (\left(D f_{t}\right)^{-1})^{T} \\[10pt]
> \frac{d}{dt} L(t) &= \frac{d}{dt} \log \lvert \det D f_{t} \rvert \\[10pt]
> &= \text{tr}\left\{\left[ \frac{d}{d D f_{t}} \log \lvert \det D f_{t} \rvert  \right]^{T} \frac{ d D\,f_{t} }{ dt }  \right\} \\[10pt]
> &= \text{tr}\left\{\left(D f_{t}\right)^{-1} \frac{ d D\,f_{t} }{ dt }  \right\} \\[10pt] 
> &= \text{tr}\left\{\left(D f_{t}\right)^{-1}  D\;\frac{ df_{t} }{ dt }  \right\} \\[10pt]
> &= \text{tr}\left\{\left(D f_{t}\right)^{-1} D\,F(f_{t}, t)\,(D f_{t}) \right\} \\[10pt]
>  &= \text{tr}\left\{D\,F(\cdot, t)(x(t))  \right\} \\[10pt]
>\end{align*}
>$$
>where the second last equality comes from the fact that
>$$
>\frac{d}{dt} f_{t}(x) = F(f_{t}(x), t)
>$$
>thus
>$$
>\frac{ \partial  }{ \partial x^{i} } \frac{d}{dt} f_{t}(x) = \frac{ \partial  }{ \partial u^{j} }\,F(u, t)\;\frac{ \partial u^{j} }{ \partial x^{i} } = \frac{ \partial  }{ \partial u^{j} }\,F(u, t)\;\frac{ \partial  f_{t}^{j} }{ \partial x^{i} }(z)
>$$
>where $$u := x(t) := f_{t}(z).$$

- [[Matrix CookBook by Petersen]]

### Continuous Flow for Stochastic Process

>[!important] Definition
>Let $\{X(t): t\in [0,T]\}$ be a *stochastic process* in $\mathbb{R}^{d}$, and for each $\omega\in \Omega$, the *sample path* $$x(t) := X(t, \omega), \quad \omega \in \Omega$$ is a solution of the ODE
>$$\left\{
>\begin{align}
> \frac{d}{dt} x(t) &= F(x(t), t) \\[5pt] 
> x(0) &= z
>\end{align}
>\right.
>$$
>where 
>- $$F: \mathbb{R}^{d} \times [0,T] \to \mathbb{R}^{d}$$ is *Lipschitz continuous* in $x$ and *continuous* in $t$
>- $$z := Z(\omega)\in \mathbb{R}^{d}$$ is a sample at $t=0$.
>
>The *continuous flow* is defined as the mapping $f_{t}: \mathbb{R}^{d} \to \mathbb{R}^{d}$ such that $$f_{t}(x(0)) = f(x(0), t) = x(t), \quad \forall t\in [0,T]$$
>
>According to the *change of variable formula*, the **log probability density function of state** $x(t)$ is given by
>$$
>\log p(x(t)) = \log p(x(0)) - L(t) 
>$$
>where $L(t)$ is the *log-determinant of Jacobian of flow map*
>$$
>L(t) := \log \,\lvert \det D_{x} f(\cdot; t)(x(t)) \rvert
>$$
>
>Thus the **differential equation** that describes the *dynamic* of *log probability density function of state* $p(x(t))$ as follows
>$$
>\left\{
>\begin{align}
> \frac{d}{dt} \log p(x(t)) &= - \text{tr}\left[(D_{x}F(\cdot, t))\,(x(t))\right] \\[5pt] 
> x(0) &= Z
>\end{align}
>\right.
>$$
>where $$Z\sim p(x(0))$$

- [[Stochastic Process]]
- [[Push-forward Measure and Push-forward Operator]]

>[!info]
>$$
>\begin{align*}
>\log p(x(t)) &= \log p(x(0)) - L(t) \\[10pt]
> \frac{d}{dt}\log p(x(t)) &= - \frac{d}{dt} L(t) \\[10pt]
> &= - \text{tr}\left[(D_{x}F(\cdot, t))\,(x(t))\right] 
>\end{align*}
>$$
>where the last equality is based on previous ODE for *log-det of Jacobian of flow* $L(t)$



## Explanation


## Neural ODE

- [[Neural Ordinary Differential Equations]]



-----------
##  Recommended Notes and References




- [[Artificial Neural Network and Deep Learning]]


- [[Markov Chain and Markov Process]]

- [[Wasserstein Distance]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 834 - 837
- [[Deep Learning Foundations and Concepts by Bishop]] pp 555 - 559