---
tags:
  - concept
  - math/differential_equation
  - math/differential_geometry
  - optimization/theory
  - optimization/algorithm
  - deep_learning/generative_models
  - math/ordinary_differential_equation
keywords:
  - gradient_flow_euclidean
  - ordinary_differential_equations
topics:
  - differential_equation
  - ordinary_differential_equations
name: Gradient Flow in Euclidean Space
date of note: 2024-10-25
---

## Concept Definition

>[!important]
>**Name**: Gradient Flow in Euclidean Space


>[!important] Definition
>Let $f: \mathbb{R}^d \to \mathcal{X} \subset \mathbb{R}$ be a *smooth map* and $x_{0}\in \mathbb{R}^{d}$. 
>
>The **gradient flow** on $f$ is a smooth curve that is described by the *ordinary differential equation*
>$$\left\{
>\begin{align*}
>\frac{d}{dt} x(t) &= - \nabla f(x(t)) \\[5pt]
>x(0) &= x_{0}
>\end{align*}\right.
>$$
>- This *Cauchy problem* has a **unique solution** if $\nabla f$ is **Lipschitz continuous**.

^6fbd2b

- [[Gradient of Smooth Map]]
- [[Ordinary Differential Equations]]
- [[Local Flow on Smooth Manifold]]
- [[Lipschitz Continuous Function]]
- [[Existence and Uniqueness of Solution of Linear Equations]]

### Uniqueness of Gradient Flow

>[!important] Proposition
>Let $f: \mathbb{R}^{d} \to \mathbb{R}$ be a **convex function**, and let $x_{1}, x_{2}\in \mathbb{R}^{d}$ be two solutions of $$\frac{d}{dt} x(t) = - \nabla f(x(t))$$
>- If $f$ is *not differentiable*,  then consider the equation $$x(t) \in \partial f(x(t))$$
>
>Then we have $$\lVert x_{1}(t) - x_{2}(t)\Vert_{2} \le \lVert x_{1}(0) - x_{2}(0) \rVert_{2}, \quad \forall t >0   $$
>
>- In particular, this proves the **uniqueness** of the **solution** of the *Cauchy problem*.

- [[Convex Function]]
- [[Subdifferential of Convex Function]]

### Discretization of Gradient Flow

>[!important] Definition
>Let $f: \mathbb{R}^{d} \to \mathbb{R}$ be a *convex function*, and $x_{0}\in \mathbb{R}^{d}$.
>
>The **discretization** of **gradient flow** 
>$$\left\{
>\begin{align*}
>\frac{d}{dt} x(t) &= - \nabla f(x(t)) \\[5pt]
>x(0) &= x_{0}
>\end{align*}\right.
>$$
>is given by the following **update equation** for iteration $k=0,\,1\,{,}\ldots{,}\,$
>$$
>x_{k+1}^{\tau} \in \arg\min_{x}\left\{ f(x) + \frac{\lVert x - x_{k}^{\tau} \rVert_{2}^2 }{2\tau}  \right\}  
>$$
>where 
>- $\tau >0$ is a fixed *step parameter*.

- [[Proximal Gradient Algorithm]]

>[!info]
>We see that 
>$$
>x_{k+1}^{\tau} \in \arg\min_{x}\left\{ f(x) + \frac{\lVert x - x_{k}^{\tau} \rVert_{2}^2 }{2\tau}  \right\}  
>$$
>Then $$\nabla f(x_{k+1}^{\tau}) + \frac{x - x_{k}^{\tau}}{\tau} = 0 \implies \frac{x - x_{k}^{\tau}}{\tau} = - \nabla f(x_{k+1}^{\tau})$$
>
>This is the **discrete-time implicit Euler scheme** for $$\frac{d}{dt} x(t) = - \nabla f(x(t))$$

- [[Fixed Point of Map]]
- [[Contraction Map Principle]]


### Extension to Metric Space

>[!important] Definition
>Let $(\mathcal{X}, d)$ be a *metric space* with metric $d$, and  $f: \mathcal{X} \to \mathbb{R}\cup \{ \infty \}$ be a *lower semi-continuous function* which *bounded from below*, and $x_{0}\in \mathcal{X}$.
>
>The **discretization** of **gradient flow** 
>$$\left\{
>\begin{align*}
>\frac{d}{dt} x(t) &= - \nabla f(x(t)) \\[5pt]
>x(0) &= x_{0}
>\end{align*}\right.
>$$
>is given by the following **update equation** for iteration $k=0,\,1\,{,}\ldots{,}\,$
>$$
>x_{k+1}^{\tau} \in \arg\min_{x}\left\{ f(x) + \frac{d(x,x_{k}^{\tau})^2 }{2\tau}  \right\}  
>$$
>where 
>- $\tau >0$ is a fixed *step parameter*.

^33863e

- [[Metric Space]]
- [[Semi-Continuous Function]]

### Geodesic from Euclidean Space

>[!important] Definition
>We can reformulate the **discretized gradient flow** using **geodesic on Euclidean space** as 
>$$\left\{
>\begin{align*}
> x^{\tau}(t) &= x_{k}^{\tau}\\[5pt]
>\tilde{x}^{\tau}(t) &= \omega_{x_{k-1}^{\tau},\, x_{k}^{\tau}}\left(\frac{t - (k-1)\tau}{\tau}\right) 
>\end{align*}\right.
>$$
>where $$\omega_{x, y}(s)$$ denotes any **constant-speed geodesic** *connecting* $x$ and $y$, parameterized by unit interval $s\in [0,1]$

- [[Geodesic on Manifolds]]
- [[Exponential Map via Geodesic on Riemannian Manifold]]


### Minimizing Movement Curve

>[!important] Definition
>A curve $$x: [0, T] \to \mathcal{X}$$ is said to be a **minimizing movement** if there exists a sequence of time steps $\tau_{j} \to 0$ such that the *piecewise constant interpolations* $x^{\tau_{j}}$ , built from a sequence of solutions of iterated minimization 
>$$
>x_{k+1}^{\tau} \in \arg\min_{x}\left\{ f(x) + \frac{d(x,x_{k}^{\tau})^2 }{2\tau}  \right\},  
>$$
>*uniformly converge* to $x$ on $[0,T]$.

- [[Uniform Convergence]]



## Explanation


### Local and Global Minimum

>[!info]
>Let $f$ be a **smooth function**.
>
>A **gradient flow** $x(t)$ of $f$,
>$$\left\{
>\begin{align*}
>\frac{d}{dt} x(t) &= - \nabla f(x(t)) \\[5pt]
>x(0) &= x_{0}
>\end{align*}\right.
>$$
>starting from a point $x_{0}$, will *converge* to one of **stationary point (local minima)** of $f$ i.e. $$x(t) \to x^{*} \in \{ z: \; \nabla f(z) = 0 \}$$ 

- [[Necessary and Sufficient Condition for Local Minimum of Smooth Function]]

>[!info]
>Let $f$ be a **convex function**.
>
>A **gradient flow** $x(t)$ of $f$,
>$$\left\{
>\begin{align*}
>\frac{d}{dt} x(t) &= - \nabla f(x(t)) \\[5pt]
>x(0) &= x_{0}
>\end{align*}\right.
>$$
>starting from any point $x_{0}$, will all *converge* to the **optimal solution** $$x(t) \to x^{*} = \arg\min_{x} f(x)$$ 

- [[Necessary and Sufficient Condition for Local Minimum of Smooth Function]]





## Gradient Descent and Proximal Gradient

>[!important]
>We see that the **gradient flow** in Euclidean space is described by the *recursive minimization*
>$$
>x_{k+1}^{\tau} \in \arg\min_{x}\left\{ f(x) + \frac{\lVert x - x_{k}^{\tau} \rVert_{2}^2 }{2\tau}  \right\}  
>$$
>Then $$\nabla f(x_{k+1}^{\tau}) + \frac{x_{k+1}^{\tau} - x_{k}^{\tau}}{\tau} = 0 \implies \frac{x_{k+1}^{\tau} - x_{k}^{\tau}}{\tau} = - \nabla f(x_{k+1}^{\tau})$$
>Thus the update is equivalent to the **gradient descent**
>$$
>x_{k+1}^{\tau} = x_{k}^{\tau} - \tau\,\nabla f(x_{k}^{\tau})
>$$

- [[Gradient Descent Algorithm]]

>[!important]
>Let $$f(x) = F(x) + H(x)$$ where $F$ is **convex smooth**, while $H$ is **convex and nonsmooth**
>
>We see that the **gradient flow** of $F + H$ in Euclidean space is described by the *recursive minimization*
>$$
>x_{k+1}^{\tau} \in \arg\min_{x}\left\{ F(x) + H(x) + \frac{\lVert x - x_{k}^{\tau} \rVert_{2}^2 }{2\tau}  \right\}  
>$$
>Then $$\frac{x_{k+1}^{\tau} - x_{k}^{\tau}}{\tau} \in - \nabla F(x_{k+1}^{\tau}) - \partial H(x_{k+1}^{\tau})$$
>Thus the update is equivalent to the **proximal gradient descent**
>$$
>x_{k+1}^{\tau} = \text{Prox}_{H}\left(x_{k}^{\tau} - \tau\,\nabla F(x_{k}^{\tau})\right)
>$$

- [[Proximal Gradient Algorithm]]





-----------
##  Recommended Notes and References


- [[Wasserstein Space]]
- [[Wasserstein Distance]]
- [[Optimal Transport in Space of Measures]]




- [[Heat Equation and Fokker–Planck Equation via Wasserstein Distance]]
- [[Fokker–Planck and Kolmogorov Forward-Backward Equation]]



- [[Gradient Flows in Metric Spaces and in Space of Probability Measures by Ambrosio]] pp 279 - 283
- [[Optimal Transport for Applied Mathematicians by Santambrogio]] pp 285 - 287
- [[Optimal Transport Old and New by Villani]] pp 629
- [[An Introduction to Optimization on Smooth Manifolds by Boumal]]
- [[Ordinary Differential Equations by Chicone]]
- Wibisono, A. (2018, July). Sampling as optimization in the space of measures: The Langevin dynamics as a composite optimization problem. In _Conference on Learning Theory_ (pp. 2093-3027). PMLR.