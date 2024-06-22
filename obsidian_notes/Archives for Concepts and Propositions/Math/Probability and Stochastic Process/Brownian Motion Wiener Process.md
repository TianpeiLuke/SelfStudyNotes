---
tags:
  - concept
  - math/stochastic_process
keywords:
  - brownian_motion
  - wiener_process
topics:
  - stochastic_process
name: Brownian Motion Wiener Process
date of note: 2024-06-05
---

## Concept Definition

>[!important]
>**Name**: *Brownian Motion* or *Wiener Process*

>[!important] Definition
>A real-valued *stochastic process* $\left\{ W_{t}: t \in T \right\}$ is called a **Brownian motion** (or **Wiener process**) if
>- **Initialization**: $W_{0} = 0$, **almost surely.**
>- **Gaussian increment**: The increment of process $$W_{t} - W_{s} \sim \mathcal{N}(0, t-s)$$ for $t \ge s \ge 0.$
>- **Independent increment**: for any $0 = t_{0} < t_{1} \,{<}\ldots{<}\,t_{n}$, the *increment* $$(W_{t_{i+1}} - W_{t_{i}}),\quad i=0 \,{,}\ldots{,}\,n-1$$ are **independent**

- [[Gaussian Process]]
- [[Stochastic Process]]

### Defining Brownian Motion from Finite Dimensional Distribution

- [[Kolmogorov Extension Theorem in Infinite Product Space]]



## Explanation

>[!info]
>By definition, a *Wiener process* is a **sub-Gaussian process**.

- [[Sub-Gaussian Process]]

## Mean and Covariance

>[!important] Proposition
>Suppose $W_{t}$ is a **one-dimensional Brownian motion.** 
>
>Then 
>- for any $t \ge 0$, we have **mean**  $$\mathbb{E}\left[  W_{t} \right] = 0$$ 
>- the **variance** $$\mathbb{E}\left[  W_{t}^2 \right] = t$$ 
>- the **covariance function** $$K(t, s) = \mathbb{E}\left[  W_{t}\,W_{s} \right] = t \wedge s = \min\{s, t\}, \quad s,t \ge 0.$$

- [[Covariance Function of Gaussian Process]]
- [[Mean Function]]

>[!info] Proof
>Assume $t > s$, we have
>$$
>\begin{align*}
>\mathbb{E}\left[  W_{t}\,W_{s} \right] &= \mathbb{E}\left[  (W_{t} - W_{s})\,W_{s} \right] + \mathbb{E}\left[  W^2_{s} \right] \\
>&= s
>\end{align*}
>$$
>The last equality holds since $(W_{t} - W_{s}) \perp W_{s}$. Q.E.D.

>[!info]
>Since the variance $$\mathbb{E}\left[  W_{t}^2 \right] = t,$$ it is expected that 
>$$dW_{t} \approx \left(dt\right)^{1 / 2}.$$


>[!important]
>The **covariance operator** $K: \mathcal{X}^{*} \to \mathcal{X}$ where $\mathcal{X} = \mathcal{C}[0,1]$, is defined as
>$$
>\text{cov}\left(\left\langle  f\,,\,W  \right\rangle\, \left\langle  g\,,\, W \right\rangle \right) = \left\langle  f\,,\,K\,g    \right\rangle.
>$$ 
>From above covariance function, we see that
>$$
>\left\langle  f\,,\,K\,g \right\rangle =  \mathbb{E}\left[W_{t}\,W_{s} \right] = \min\{ s, t \}  
>$$
>Based on [[Riesz-Markov Representation Theorem]], we can find a *unique measure* $\mu_{f}$ for each $f\in \mathcal{X}^{*}$,  so that
>$$
>f = \int_{[0,1]} \cdot \; d\mu_{f}.
>$$
>Thus 
>$$
>\begin{align*}
>\text{cov}\left(\left\langle  f\,,\,W  \right\rangle\, \left\langle  g\,,\, W \right\rangle \right) &= \mathbb{E}\left[ \int_{[0,1]} W d\mu_{f}\, \int_{[0,1]} W d\mu_{g}\right] \\
>&=  \mathbb{E}\left[ \int_{[0,1]} W(t) d\mu_{f}(t)\, \int_{[0,1]} W(s) d\mu_{g}(s)\right] \\
>&= \int_{[0,1]}\int_{[0,1]}  \mathbb{E}\left[W(t)W(s)\right]d\mu_{f}(t)\,d\mu_{g}(s)\\
>&= \int_{[0,1]}\int_{[0,1]} \min\{ s, t \} d\mu_{f}(t)\,d\mu_{g}(s)
>\end{align*}
>$$ 
>That is, the **covariance operator** and **covariance function** are related as below
>$$
>\left\langle  f\,,\, K\,g \right\rangle = \int_{[0,1]}\int_{[0,1]} \min\{ s, t \} d\mu_{f}(t)\,d\mu_{g}(s),
>$$
>or
>$$
>(K\,g)(t) = \int_{[0,1]}\min\{ s, t \} d\mu_{g}(s).
>$$

- [[Covariance Operator]]
- [[Covariance Function of Gaussian Process]]



## Brownian Motion from Diffusion Equation

>[!important]
>The development of Wiener process is based on the **diffusion process**, where the dynamic of particle's density is governed by the *diffusion equation*
>$$
>\frac{ \partial  }{ \partial t }u(x, t) = \frac{D}{2} \frac{ \partial^2  }{ \partial x^2 } u(x, t) 
>$$
>where $u(x, t)$ is the **density** of particles at *position* $x$ and *time* $t$.

- [[Heat Equation and Diffusion Equation]]

>[!info]
>Let $X_{t}$ be the position of particle at time $t = n\,\Delta t$. At each time, the particle takes an *increment* of $\Delta x$ with probability $1 /2$.
>
>Denote $X_{i} \in \{ 0, 1 \}$ as a *Bernoulli random variable* with $$p = \mathcal{P}(X_{i} =1) = \frac{1}{2}.$$ 
>Here $X_{i}$ determines if the particle takes $+\Delta x$ increments or $- \Delta x$ increments. Let 
>$$
>S_{n} = \sum_{i=1}^n X_{i}
>$$
>be the *total number* of $+\Delta x$ increments, whereas $(n- S_{n})$ be the *total number* of $-\Delta x$ increments.

>[!info]
>The position of particle at $t$ can be formulated as
>$$
>X_{t} = S_{n}\Delta x + (n - S_{n})(-\Delta x) = (2S_{n} - n)\Delta x
>$$
>The variance of $X_{t}$ can be computed as
>$$
>\text{Var}(X_{t}) = \Delta x^2\,n  =  \frac{(\Delta x)^2}{\Delta t}\,t := D\,t
>$$
>where  we assume that $$D:= \frac{(\Delta x)^2}{\Delta t}$$ is constant.

>[!info]
>We have
>$$
>X_{t} = (2S_{n} - n)\Delta x = \frac{S_{n} - n / 2}{\sqrt{ n / 4 }}\sqrt{ n }\Delta x = \frac{S_{n} - n / 2}{\sqrt{ n / 4 }}\sqrt{ t D }
>$$

>[!info]
>By [[Central Limit Theorem]], as $n\to \infty$, we have
>$$
>\begin{align*}
>\mathcal{P}\left(X_{t} \in (a, b)\right) &= \mathcal{P}\left(\frac{X_{t}}{\sqrt{ t D }} \in \left( \frac{a}{\sqrt{ tD }}, \frac{b}{\sqrt{ tD }} \right)\right) \\
>&\to \Phi\left(\frac{b}{\sqrt{ tD }} \right) - \Phi \left(\frac{a}{\sqrt{ tD }} \right)
>\end{align*}
>$$
>where $\Phi(t) = \mathcal{N}(X \le t)$ is the c.d.f. of Gaussian random variable.
>
>So $$X_{t} \sim \mathcal{N}(0, D\,t)$$

- [[De Moivre–Laplace Theorem]]

## Representation of Brownian Motion

- [[Coordinate Representation of Brownian Motion]]

## Sample Path Properties

![[Sample Path of Brownian Motion#^192097]]


![[Sample Path of Brownian Motion#^46cc20]]

- [[Sample Path of Brownian Motion]]

## Martingale Characterization of Brownian Motion 

>[!important] Proposition
>The *Wiener process* $((W_{t}, \mathscr{F}_{t}), t\ge 0)$ is a **martingale** with respect to generated $\sigma$-algebra 
>$$
>\mathscr{F}_{t} := \sigma\left(W_{s},\; s\le t\right).
>$$
>
>That is, for any $t > s$,
>$$
>\mathbb{E}_{ \mathcal{N} }\left[ W_{t}- W_{s} | \mathscr{F}_{s} \right] = 0 \iff \mathbb{E}_{ \mathcal{N} }\left[ W_{t}| \mathscr{F}_{s} \right] = W_{s}, \quad \text{a.s.}
>$$

- [[Martingale]]

![[Lévy Characterization of Brownian Motion#^da976c]]

![[Lévy Characterization of Brownian Motion#^0e9de9]]

- [[Local Martingale]]
- [[Lévy Characterization of Brownian Motion]]
- Rogers, L. C., & Williams, D. (2000). _Diffusions, markov processes, and martingales: Volume 1, foundations_ (Vol. 1). Cambridge university press. pp 2
- [[Introduction to Stochastic Calculus by Klebaner]] pp 203



## Markov Process

>[!important] Theorem
>The *Wiener process* $(W_{t}, t\ge 0)$ is a **Markov process**.
>
>That is, for $\mathcal{F}_{s} := \sigma(W_{r}\,, \, 0 \le r \le s)$, 
>$$
>\begin{align}
>\mathcal{P}\left(W_t \in A \;|\; \mathcal{F}_{s} \right) &= \mathcal{P}\left(W_{t} \in A \;|\; W_{s} \right)
>\end{align}
>$$ 
>In particular, the **conditional probability** for $t > s$,
>$$
>\mathcal{P}\left(W_{t} | W_{s}\right) =  \mathcal{N}\left(W_{s}, t - s \right)\quad \text{ a.s.}
>$$
>i.e.  for any $B\in \mathcal{B}[\mathbb{R}]$
>$$
>\mathcal{P}\left(W_{t} \in B | W_{s}\right) = \left( \frac{1}{2\pi (t-s)} \right)^{n / 2} \int_{B} \exp \left( - \frac{|x - W_{s}|^2 }{2 (t-s)}\right) dx\, \quad \text{ a.s.}
>$$

- [[Markov Chain and Markov Process]]
- [[Introduction to Stochastic Differential Equations by Evans]]

>[!important] Proposition
>Let $(W_{t}, t \ge 0)$ be **Wiener process** and $\mathscr{F}_{t} := \sigma(W_{s}, s\le t)$ is a *filtration*.
>
>For any *Borel function* $f: \mathbb{R} \to \mathbb{R}$, and $s, t \ge 0$,  the **weak Markov property** holds
>$$
>\mathbb{E}\left[f(W_{t}) | \mathscr{F}_{s} \right] = T_{s,t}f(W_{s})
>$$
>where $(T_{s, t}, 0 \le s \le t)$ is the **semi-group** *associated with transition function* $p$, which is defined as
>$$
>T_{s, t}f(x) := \left\{ 
>\begin{array}{cc}
>\int_{\mathcal{X}}f(y)\;p(dy, t, x, s) & t > s\\
>f(x) & t = s
\end{array}
>\right.
>$$
>where $$p(y, t, x, s) =  \left(\frac{1}{2\pi (t - s)}\right)^{1/2}\,\exp \left(- \frac{\left(x- y\right)^2}{2(t - s)}\right)$$ is the **transition function** of *Wiener process*.

- [[Markov Chain and Markov Process]]
- [[Semigroup associated with Transition Function]]
- [[Markov Transition Kernel and Transition Function]]
- Rogers, L. C., & Williams, D. (2000). _Diffusions, markov processes, and martingales: Volume 1, foundations_ (Vol. 1). Cambridge university press. pp 5
- Friedman, A. (1975). *Stochastic differential equations and applications*. pp 23

## Infinitesimal Generator of Brownian Motion and PDE 

>[!important] 
>The **(infinitesimal) generator** of $(T_{s,t}, 0 \le s \le t)$ is defined as
>$$
>\mathcal{A}_{s} := \lim_{ h \to 0_{+} } \frac{1}{h}\left(T_{s, s+h} - I\right) 
>$$
>For **time-homogeneous process**,  we can drop dependency on initial time
>$$
>\mathcal{A} := \mathcal{A}_{s}
>$$

- Rogers, L. C., & Williams, D. (2000). _Diffusions, markov processes, and martingales: Volume 1, foundations_ (Vol. 1). Cambridge university press. pp 5
- Friedman, A. (1975). *Stochastic differential equations and applications*. pp 23


![[Infinitesimal Generator of Brownian Motion and Laplacian#^143824]]

- [[Infinitesimal Generator of Brownian Motion and Laplacian]]
- [[Infinitesimal Generator of Markov Process]]


>[!important] 
>The **Kolmogorov's backward equation** for the Wiener process **transition density** 
>$$
>\begin{align*}
> \frac{ \partial  }{ \partial s}p(s, x, t, y) &= \frac{1}{2}\frac{ \partial^2  }{ \partial x^2 } p(s, x, t, y)
>\end{align*}
>$$
>which is the **heat equation**.
>
>The transition density corresponds to the Transition Kernel
>$$
>\int_{A} p(s, x, t, dy) = K(x, A) = \mathcal{P}(X_{t} \in A | X_{s} = x)
>$$

- [[Fokker–Planck and Kolmogorov Forward-Backward Equation]]
- [[Markov Transition Kernel and Transition Function]]
- [[Heat Equation and Diffusion Equation]]

>[!important] 
>The **Kolmogorov's forward equation** for the Wiener process **transition density** 
>$$
>\begin{align*}
> \frac{ \partial  }{ \partial t }p(s, x, t, y) &= \frac{1}{2}\frac{ \partial^2  }{ \partial y^2 } p(s, x, t, y)
>\end{align*}
>$$
>which is also the **heat equation**.



## Self-Similarity

>[!important] Proposition
>The *Wiener process* $(W_{t}, t\ge 0)$ is  **$1/2$-self-similar**.
>
>That is, for any $c > 0$ the process $$Y(t) := \frac{W(ct)}{\sqrt{ c }}$$ is also a **Wiener process**.





-----------
##  Recommended Notes and References



- [[Gaussian Process]]
- [[RKHS of Gaussian Process]]
- [[Representation of Gaussian Random Function in Hilbert Space]]


- [[Markov Chain and Markov Process]]

- [[Martingale]]
- [[Sub-Gaussian Process]]

- [[Kolmogorov Extension Theorem in Infinite Product Space]]

- [[Probability and Measure by Billingsley]] pp 498
- [[Lectures on Gaussian Processes by Lifshits]]
- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]
- [[High Dimensional Probability An Introduction by Vershynin]]
- [[Introduction to Stochastic Differential Equations by Evans]]

