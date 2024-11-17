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
>- The **continuous flow** $f$ is a function $$f: \mathbb{R}^{d} \to \mathbb{R}^{d}$$ that takes in the input $z$ and *solves the ODE* with *initial value condition (IVP)*. That is, $$f(z) = x(T)$$
>	- By existence and uniqueness of solution of ODE, there **exists** a **unique** *continuous flow* $f$ if $F$ is *Lipschitz continuous* with *Lipschitz constant* not depending on $t$ $$\lvert F(x_{1}, t) - F(x_{2}, t) \rvert \le L\,\lVert x_{1} - x_{2} \rVert $$
>- The **Jacobian determinant** cannot be expressed analytically, but we can define it via a separate *ODE*
>	- Define the flow for time $t$ $$f_{t}: \mathbb{R}^{d} \to \mathbb{R}^{d}$$ as the unique solution of *IVP* of *ODE* with $x(0)  = z.$ i.e. $$f_{t}(z) = x(t)$$
>		- We have $$f_{0} = I\, \quad f_{T} = f$$
>	- Define the **log Jacobian determinant** of $f_{t}$ as $$L(t) := \log \lvert \det D f_{t}(x_{0}) \rvert $$
>		- We have $$L(0) = \log \lvert \det I \rvert = 0$$
>	- It can be shown that $L(t)$ satisfies the *ordinary differential equation* with *initial condition* $$\left\{\begin{align}\frac{d}{dt} L(t) &= \text{tr}\left[(D\,F(\cdot, t))\,(x(t))\right]  \\[5pt]  L(0) &= 0\end{align}\right.$$
>		- The *rate of change* for the *log-det of Jacobian matrix* is equal to the *Jacobian trace* of vector field $F(\cdot,t)$
>		- $L(T)$ corresponds to the *Jacobian determiant* of $f:= f(T)$.
>- Finally, we can have joint ODE for $(x(t), L(t))$ as
>$$\left\{
>\begin{align}
> \frac{d}{dt} (x(t), L(t)) &= \left[ \begin{array}{c}F(x(t), t) \\[5pt] \text{tr}\left[(D\,F(\cdot, t))\,(x(t))\right] \end{array} \right]  \\[5pt] 
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