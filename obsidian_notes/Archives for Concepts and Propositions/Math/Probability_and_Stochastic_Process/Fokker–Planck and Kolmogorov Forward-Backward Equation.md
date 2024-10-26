---
tags:
  - concept
  - math/differential_equation
  - math/stochastic_process
keywords:
  - fokker_planck_kolmogorov_equation
  - kolmogorov_forward_equation
  - kolmogorov_backward_equation
topics:
  - differential_equation
  - stochastic_process
name: Fokker–Planck Equation and Kolmogorov Forward-Backward Equation
date of note: 2024-06-11
---

## Concept Definition

>[!important]
>**Name**: *Fokker–Planck Equation* and *Kolmogorov Forward-Backward Equation*

![[Infinitesimal Generator of Stochastic Differential Equation#^1bd4b1]]

### Kolmogorov Backward Equation

>[!important] Definition
>Let $L$ be a *differential operator* such that
>$$
>(L_{s}\,f)(x ,s) = \mu(x, s)\,\frac{\partial }{\partial x }f(x, s) +  \frac{1}{2}\sigma^2(x,s)\frac{\partial^2 }{ \partial x^2 }f(x,s). 
>$$
>
>A **fundamental solution** of the *PDE*
>$$
>\begin{align*}
> \frac{ \partial}{ \partial s }u(x, s) + L_{s}\,u(x, s) = 0 
>\end{align*}
>$$
>is a *non-negative function* $p(s, x, t, y)$ with the following properties:
>- it is *jointly continuous* in $(s, x, t, y)$,  *twice continuous differentiable* in $x$ and satisfies above PDE *with respect to* $s$ and $x$.
>- for any *bounded continuous* function $f: \mathbb{R} \to \mathbb{R}$, and any $t >0$, 
>  $$
>  \begin{align*}
>  u(x , s) = \int_{\mathbb{R}}\,f(y)\;p(s, x, t, dy)
>\end{align*}
> $$
> is *bounded*, satisfies *the above PDE* and $$\lim_{ s \to t }u(x ,s) = f(x),$$ for $x\in \mathbb{R}.$

- [[Infinitesimal Generator of Stochastic Differential Equation]]
- [[Markov Transition Kernel and Transition Function]]
- [[Stochastic Differential Equations]]
- [[Feynman-Kac Formula]]

>[!important] Definition
>Let $L$ be a *partial differential operator*:
>$$
>L_{s} := \mu(x, s) \,\frac{\partial }{\partial x }  +  \frac{1}{2}\sigma^2(x, s)\frac{\partial^2 }{ \partial x^2 }.
>$$
>
>The *partial differential equation*
>$$
>\begin{align*}
> \frac{ \partial}{ \partial s }u(x, s) + L_{s}\,u(x, s) = 0 
>\end{align*}
>$$
>is called the **Kolmogorov's backward equation**, since it is a PDE in *backward variable* $(x,s)$.

^89943e

- [[Partial Differential Equations]]
- [[Congruence Relation between Matrices]]

### Kolmogorov Forward Equation (Fokker–Planck Equation)

>[!important] Theorem (Kolmogorov Forward Equation)
>Suppose that $\sigma(x, t)$ and $\mu(x, t)$ are *bounded* and *continuous functions* such that 
>- $$\sigma^2(x, t) \ge c > 0,$$
>- $\mu(x, t)$ and $\sigma^2(x, t)$ satisfies a **Hölder condition** *with respect to* $x$ and $t$, that is, for all $x, y \in \mathbb{R}$ and $s,t >0$, 
>  $$
>  \lvert \mu(y, t) - \mu(x ,s) \rvert + \lvert \sigma^2(y, t) - \sigma^2(x, s) \rvert \le K\left(\lvert y -x \rvert^{\gamma} + \lvert t - s \rvert^{\gamma}  \right).  
> $$
>
>Then the *PDE*
>$$
>\begin{align*}
> \frac{ \partial}{ \partial s }u(x, s) + L_{s}\,u(x, s) = 0 
>\end{align*}
>$$
>has a **fundamental solution** $p(s, x, t, y)$, which is **unique** and is **strictly positive.**
>
>If in addition $\sigma(x, t)$ and $\mu(x, t)$ have **two partial derivatives** with respect to $x$, which are *bounded* and *Hölder condition* with respect to $x$, then $p(s, x, t, y)$ as a *function in $y$ and $t$*, satisfies the PDE
>$$
>\begin{align*}
>- \frac{\partial}{ \partial t } p + \frac{1}{2}\frac{\partial^2 }{ \partial y^2 }\left(\sigma^2\, p\right) - \frac{\partial }{\partial y }\left(\mu\,p\right) = 0
>\end{align*}
>$$

- [[Hölder Condition and Hölder Continuous Function]]
- [[Existence and Uniqueness of Solution for Stochastic Differential Equation]]
- [[Introduction to Stochastic Calculus by Klebaner]] pp 144


>[!important] Definition
>The *partial differential equation* of $v(y, t) := p(s, x, t, y)$ 
>$$
>\begin{align*}
>- \frac{\partial}{ \partial t } v(y, t) + \frac{1}{2}\frac{\partial^2 }{ \partial y^2 }\left(\sigma^2(y,t)\, v(y,t)\right) - \frac{\partial }{\partial y }\left(\mu(y,t)\,v(y,t)\right) = 0
>\end{align*}
>$$
>is called the **Kolmogorov's forward equation**, since it is a PDE in *forward variable* $(y,t)$.
>
>It is also known as the **Fokker–Planck equation**, *diffusion equation*.

^6aedc0

- [[Partial Differential Equations]]

### Markov Process as Weak Solution of SDE

>[!important] Theorem
>Suppose that $\sigma(x, t)$ and $\mu(x, t)$ are *bounded* and *continuous functions* such that 
>- $$\sigma^2(x, t) \ge c > 0,$$
>- $\mu(x, t)$ and $\sigma^2(x, t)$ satisfies a **Hölder condition** *with respect to* $x$ and $t$, that is, for all $x, y \in \mathbb{R}$ and $s,t >0$, 
>  $$
>  \lvert \mu(y, t) - \mu(x ,s) \rvert + \lvert \sigma^2(y, t) - \sigma^2(x, s) \rvert \le K\left(\lvert y -x \rvert^{\gamma} + \lvert t - s \rvert^{\gamma}  \right).  
> $$
>
>Then 
>- the *PDE* 
>  $$
>\begin{align*}
> \frac{ \partial}{ \partial s }u(x, s) + L_{s}\,u(x, s) = 0 
>\end{align*}
>$$
> has a **unique** *fundamental solution* $p(s, x, t, y)$.
>
>- The function $$P(s, x, t, y) := \int_{-\infty}^{y}p(s, x, t, du)$$ uniquely defines a **transition function**.
>  
>- Moreover, this function has the property that for any bounded function $f(x, t)$ *twice continuously differentiable* in $x$ and  *once continuously differentiable* in $t$, i.e. $f\in \mathcal{C}_{b}^{2,1}(\mathbb{R} \times [0,T])$
>  $$
>  \begin{align*}
>  &\int_{\mathbb{R}}f(y, t)\;p(s, x, t, dy) - f(x ,s)\\
>  &= \int_{s}^{t}\int_{\mathbb{R}}\,\left(\frac{\partial}{\partial u } + L_{u} \right)f(y, u)\;p(s, x, u, dy)\,du,
>\end{align*}
> $$
> for all $0 \le s <t$, $x\in \mathbb{R}.$

- [[Martingale via Solution of SDE and Backward Equation]]
- [[Introduction to Stochastic Calculus by Klebaner]] pp 143 - pp 144


>[!info] 
>The above theorem states that the solution of **Kolmogorov backward equation** with *boundary condition*
>$$
>\begin{align*}
>\left\{
>\begin{array}{cc}
> &\dfrac{ \partial}{ \partial t }u(x, t) + L_{t}\,u(x, t) = 0 \\[5pt] 
> &u(x, T) = g(x)
>\end{array}
>\right. 
>\end{align*}
>$$
>is 
>$$
>u(x, t) := \mathbb{E}\left[g(X_{T}) \,|\,X_{t} = x \right]
>$$
>where $X_{t}$ is the *diffusion process* with **generator** $L_{t}.$

- [[Feynman-Kac Formula]]

### Dynkin Formula

- [[Dynkin Formula]]

### Weak Solution of SDE and Martingale Problem

>[!info]
>The above theorem states that the probability $$\mathcal{P}_{x,s}(A) : = \int_{A} p(s,x,t,dy)$$ is the **unique solution** to the **Martingale problem**

- [[Weak Solution to Stochastic Differential Equation]]
- [[Martingale Problem]]
- [[Martingale via Solution of SDE and Backward Equation]]

## Explanation

>[!important]
>The above theorem provides an **one-to-one correspondence** of **Kolmogorov's forward equation** 
>$$
>\begin{align*}
> \frac{ \partial}{ \partial s }u(x, s) + L\,u(x, s) = 0 
>\end{align*}
>$$
>and **backward equation** 
>$$
>\begin{align*}
>- \frac{\partial}{ \partial t } v(y, t) + \frac{1}{2}\frac{\partial^2 }{ \partial y^2 }\left(\sigma^2(y,t)\, v(y,t)\right) - \frac{\partial }{\partial y }\left(\mu(y,t)\,v(y,t)\right) = 0
>\end{align*}
>$$
>via the **stochastic differential equation** 
>$$
>\begin{align*}
>dX_{t} &= \mu(X_{t}, t)\,dt + \, \sigma\left(X_{t}, t\right)\,dW_{t}. 
>\end{align*}
>$$

## Diffusion Process

>[!important]
>The function $p(s, x, t, y)$ in above theorem, satisfies both **Kolmogorov's forward equation**, and **Kolmogorov's backward equation**. 
>
>Thus its indefinite integral $P(s, x, t, y)$ **uniquely** determines a *Markov chain* $(X_{t})$ with *transition function*
>$$
>P(s, x, t, y) = \mathcal{P}(X_{t} \le y | X_{s} = x).
>$$
>

- [[Markov Chain and Markov Process]]
- [[Markov Transition Kernel and Transition Function]]
- [[Infinitesimal Generator of Stochastic Differential Equation]]

>[!important] Definition
>The Markov process defined above is called a **diffusion process** and the differential operator $L$ is called its **generator.**

>[!important]
>In particular, the theorem states that the **diffusion process** $X_{t}$ satisfies the **stochastic differential equation**
>$$
>\begin{align*}
>dX_{t} &= \mu(X_{t}, t)\,dt + \, \sigma\left(X_{t}, t\right)\,dW_{t}. 
>\end{align*}
>$$
>In other word, $X_{t}$ is the *weak solution* of SDE.

- [[Stochastic Differential Equations]]
- [[Weak Solution to Stochastic Differential Equation]]






## Multi-dimensional Case

>[!info]
>Consider 
>$$
>d\boldsymbol{X} = \boldsymbol{b}(\boldsymbol{X}, t)dt + \boldsymbol{A}(\boldsymbol{X}, t)\,d\boldsymbol{W}
>$$
>where $\boldsymbol{b} = [b^1 \,{,}\ldots{,}\,b^n]$ and $\boldsymbol{A} = [a^{i,j}]_{n \times m}$

>[!important] Definition
>Let $L$ be a *partial differential operator*: (under *Einstein Summation*)
>$$
>\begin{align*}
>L &:=  b^i\frac{ \partial  }{ \partial x^i } + c^{i,j}\frac{ \partial^2  }{ \partial x^i\,x^{j} }
>\end{align*} 
>$$ 
>and $$c^{i,j} := \frac{1}{2} \sum_{k=1}^{m} a^{i,k}a^{j,k}.$$
>
>The *partial differential equation*
>$$
>\begin{align*}
> \frac{ \partial}{ \partial s }u(x, s) + L\,u(x, s) = 0 
>\end{align*}
>$$
>is called the **Kolmogorov's backward equation**, since it is a PDE in *backward variable* $(x,s) \in \mathbb{R}^n \times [0,T]$.

- [[Einstein Summation Convention]]


>[!important] Definition
>The *partial differential equation* of $v(y, t) := p(s, x, t, y)$ (under *Einstein convention*)
>$$
>\begin{align*}
>- \frac{\partial}{ \partial t } v(y, t) + \frac{1}{2}\frac{ \partial^2  }{ \partial y^i\,y^{j} }\left(c^{i,j}(y,t)\, v(y,t)\right) - \frac{\partial }{\partial y^i }\left(b^i(y,t)\,v(y,t)\right) = 0
>\end{align*}
>$$
>is called the **Kolmogorov's forward equation**, since it is a PDE in *forward variable* $(y,t)$.
>
>It is also known as the **Fokker–Planck equation**, *diffusion equation*.


## Functional Form

 ![[Infinitesimal Generator of Stochastic Differential Equation#^8f9111]]


>[!important]
>The **backward equation** can be represented by generator $\mathcal{A}$ of Markov process $X_{t}$ as
>$$
>\frac{ \partial  }{ \partial t }u + \mathcal{A}u = 0 
>$$
>and the **forward equation** can be represented by the **adjoint** of $\mathcal{A}$ as
>$$
>\frac{ \partial}{ \partial t }p - \mathcal{A}^{*}p = 0 
>$$
>where
>$$
>\mathcal{A}^{*}p := L^{*}p = \frac{1}{2}\frac{ \partial^2  }{ \partial y^i\,y^{j} }\left(c^{i,j}(y,t)\, p(\cdot, \cdot, t, y)\right) - \frac{\partial }{\partial y^i }\left(b^i(y,t)\,p(\cdot, \cdot, t, y)\right)
>$$
>and the *adjoint* is defined by 
>$$
>\left\langle g\,,\,Lf \right\rangle_{L^2} = \left\langle  L^{*}g\,,\,f \right\rangle_{L^2}
>$$

- [[Infinitesimal Generator of Stochastic Differential Equation]]
- [[Adjoint of Bounded Operator in Hilbert Space]]

- [[Introduction to Stochastic Calculus by Klebaner]] pp 158

## Vector Field and Operator Form

>[!important]
>The **Fokker–Planck equation** has also a **differential operator** form
>$$
>\frac{ \partial}{ \partial t }v - \frac{1}{2} \Delta \left(\boldsymbol{\sigma}^T\boldsymbol{\sigma}  v\right) + \nabla \cdot \left(\boldsymbol{\mu} v\right) = 0 
>$$
>where $$\nabla \cdot \boldsymbol{f} := \text{div}(\boldsymbol{f}) = \sum_{i}\frac{ \partial}{ \partial x^i }f^{i}(x) $$ is the **divergence operator** and
>$$
>\Delta g := \sum_{i}^{n}\frac{ \partial^2  }{ (\partial x^i)^2 }g
>$$
>is **the Laplace operator**
>
>$$
>\Delta f = \nabla \cdot \left( \nabla f \right)
>$$

- [[Divergence Operator of Vector Field on Riemannian Manifold]]
- [[Laplacian of Smooth Map on Riemannian Manifold]]



## Gradient Flow in Wasserstein Space

- [[Heat Equation and Fokker–Planck Equation via Wasserstein Distance]]



-----------
##  Recommended Notes and References


- [[Second-Order Linear Partial Differential Equations]]
- [[Partial Differential Equations]]

- [[Stochastic Differential Equations]]

- [[Ito Stochastic Integration]]
- [[Stochastic Process]]
- [[Brownian Motion Wiener Process]]

- [[Markov Transition Kernel and Transition Function]]
- [[Congruence Relation between Matrices]]

- [[Partial Differential Equations]]
- [[Wasserstein Space]]
- [[Wasserstein Distance]]

- [[Introduction to Stochastic Calculus by Klebaner]]
- [[Optimal Transport for Applied Mathematicians by Santambrogio]]
- [[Partial Differential Equations by Evans]]
- Oksendal, B. (2013). _Stochastic differential equations: an introduction with applications_. Springer Science & Business Media. pp 141

- Wikipedia [Fokker-Planck_equation](https://en.wikipedia.org/wiki/Fokker%E2%80%93Planck_equation)
- Wikipedia [Kolmogorov_backward_equations](https://en.wikipedia.org/wiki/Kolmogorov_backward_equations_(diffusion))
- Wikipedia [Kolmogorov_equations](https://en.wikipedia.org/wiki/Kolmogorov_equations)