---
tags:
  - concept
  - deep_learning/generative_models
  - deep_learning/models
  - deep_learning/algorithms
  - math/stochastic_process
  - math/stochastic_differential_equations
keywords:
  - stochastic_differential_equations
  - denoising_diffusion_probabilistic_models
topics:
  - differential_equation
  - stochastic_differential_equation
  - deep_learning/generative_models
name: Continuous-Time Diffusion Network via Stochastic Differential Equations
date of note: 2024-10-19
---

## Concept Definition

>[!important]
>**Name**: Continuous-Time Diffusion Network via Stochastic Differential Equations

![[diffusion_network_sde_ode.png]]

### Stochastic Differential Equations for Forward and Reverse Diffusion Process

>[!important] Definition
>The *denoising diffusion probabilistic model (DDPM)* can be formulated as two **continuous-time stochastic differential equations (SDE)**:
>- **Forward SDE**: $$dX_{t} = f(X_{t}, t)\,dt + \sigma(t)\,dW_{t}$$
>- **Reverse SDE**: $$dX_{t} = \left[f(X_{t},t) - \sigma^2(t)\,\nabla_{x} \log p(X_{t}; t)\right]\,dt + \sigma(t)\,d\widehat{W}_{t}$$
>	- $\widehat{W}_{t}$ is a *standard Wiener process* when time flows *backwards* from $T$ to $0$ 
>	- The **drift term**  in *Reverse SDE* $$f(X_{t},t) - \sigma^2(t)\,\nabla_{x} \log p(X_{t}; t)$$  corresponds to the **score matching** objective
>	- We can recover original signal by *subtracting* $$\sigma^2(t)\,\nabla_{x} \log p(X_{t}; t)$$ in the **drift term**

^e99b7e

- [[Stochastic Differential Equations]]
- [[Score Matching and Denoising Score Matching]]
- [[Fokker–Planck and Kolmogorov Forward-Backward Equation]]
- Anderson, B. D. (1982). Reverse-time diffusion equation models. _Stochastic Processes and their Applications_, _12_(3), 313-326.

### SDE for DDPM

![[Denoising Diffusion Probabilistic Models and Diffusion Network#^de66ca]]

![[Langevin Equation#^b373a8]]

>[!important] Definition
>The **stochastic differential equations (SDE)** corresponding to the **denoising diffusion probabilistic models (DDPM)** as $T\to \infty$ are given by 
>- **Forward SDE**: $$dX_{t} = - \frac{1}{2}\beta(t)\,X_{t}\,dt + \sqrt{\beta(t)}\,dW_{t}$$ where $$\beta\left( \frac{t}{T} \right) = T\,\beta_{t}.$$
>	- This SDE is the **Langevin equation**.
>- **Reverse SDE**: $$dX_{t} = \left[ -\frac{1}{2}\beta(t)\,X_{t} - \beta(t)\,\nabla_{x} \log p(X_{t}; t) \right]\,dt + \sqrt{ \beta(t) }\,d\widehat{W}_{t} $$

^82e0e4

- [[Stochastic Differential Equations]]
- [[Langevin Equation]]
- [[Ornstein–Uhlenbeck Process]]

>[!info] Proof
>For DDPM, the update of *forward diffusion* is given by $$x_{t} = \sqrt{ 1 - \beta_{t} }\,x_{t-1} + \sqrt{ \beta_{t} }\epsilon_{t}$$
>
>Let $\beta_{t} = \beta(t)\Delta t$ so the update becomes 
>$$
>\begin{align*}
>x_{t} &= \sqrt{ 1 - \beta_{t} }\,x_{t-1} + \sqrt{ \beta_{t} }\,\epsilon_{t} \\[5pt]
>&= \sqrt{ 1 -  \beta(t)\Delta t }\,x_{t-1} + \sqrt{  \beta(t)\Delta t }\,\epsilon_{t}
>\end{align*}
>$$
>We approximate the first term via *first-order Taylor expansion*
>$$
>\begin{align*}
>\sqrt{ 1 -  \beta(t)\Delta t } &\approx 1 - \frac{\beta(t)\Delta t}{2} 
>\end{align*}
>$$
>so 
>$$
>\begin{align*}
>x_{t} &\approx x_{t-1} - \frac{\beta(t)\Delta t}{2}\,x_{t-1}  + \sqrt{  \beta(t)\Delta t }\,\epsilon_{t}
>\end{align*}
>$$
>This leads to 
>$$
>\begin{align*}
> \frac{x_{t} - x_{t-1}}{\Delta t} &\approx - \frac{\beta(t)}{2}\,x_{t-1}  + \sqrt{  \frac{\beta(t)}{\Delta t }}\,\epsilon_{t} \\[5pt]
> \lim_{ \Delta t \to 0 }  \frac{x_{t} - x_{t-1}}{\Delta t} &= - \frac{\beta(t)}{2}\,x_{t-1}  + \sqrt{ \beta(t) } \lim_{ \Delta t \to 0 } \frac{\mathcal{N}(0,I)}{\sqrt{\Delta t }}\,\\[5pt]
> \implies \frac{d}{dt} X(t) &=  - \frac{\beta(t)}{2}\,X(t)  + \sqrt{ \beta(t) } \frac{d}{dt} W_{t}\\[5pt]
>  dX(t) &=  - \frac{\beta(t)}{2}\,X(t)\,dt  + \sqrt{ \beta(t) }\,dW(t)
>\end{align*}
>$$
>End-of-Proof.

- [[Brownian Motion Wiener Process]]
- [[Ito Chain Rule and Ito Formula]]
- [[Ito Isometry]]

![[continuous_time_diffusion_network_sde_visual.png]]


### ODE for Diffusion Network

>[!quote]
>For all diffusion processes governed by an *SDE*, there exists a corresponding **deterministic process** described by an **ODE** whose trajectories have the **same marginal probability densities** $p(z|t)$ as the SDE. 
>
>...
>The ODE formulation allows the use of efficient **adaptive-step solvers** to reduce the number of function evaluations dramatically. Moreover, it allows probabilistic diffusion models to be related to **normalizing flow models**, from which the change-of-variables formula (18.1) can be used to provide an exact evaluation of the log likelihood.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 599

- [[Normalizing Flows]]

![[Continuous-Time Diffusion Network via Stochastic Differential Equations#^e99b7e]]

>[!important] Definition
>The **ordinary differential equation (ODE)** that shared the same marginal density as the diffusion network above can be obtained from the *forward-time SDE*
>$$
> \frac{d}{dt}x(t) = f(x(t), t) - \frac{1}{2}\sigma^{2}(t)\;\nabla_{x} \log p(x(t))
>$$
>This is called the **probability flow ODE**.
>
>For **DDPM**, the corresponding **ODE** is given by
>$$
>\frac{d}{dt}x(t) = -\frac{1}{2}\beta(t)\,x(t) - \beta(t)\;\nabla_{x} \log p(x(t))
>$$

- [[Ordinary Differential Equations]]
- [[Fokker–Planck and Kolmogorov Forward-Backward Equation]]

>[!important] Definition
>We can also define the **probability flow ordinary differential equation (ODE)** from the *reverse-time SDE*
>$$
> \frac{d}{dt}x(t) = f(x(t), t) - \frac{1}{2}\sigma^{2}(t)\;s(x(t), w, t)
>$$ 
>where $$s(x, w, t) \approx \nabla_{x} \log p(x; t)$$ is the *score function*.
>- This is also a special case of **neural ordinary differential equations** or **continuous-time normalizing flow.**

- [[Score Matching and Denoising Score Matching]]
- [[Normalizing Flows]]


### Compare SDE and ODE approach

>[!important] 
>We can decompose the **forward stochastic differential equation** for *DDPM* into two parts:
>$$
>dX_{t} = \underbrace{ -\frac{1}{2}\beta(t)\left[ X_{t} + s(X_{t}, w, t) \right]\,dt }_{ \text{probability flow ODE} } \underbrace{ - \frac{1}{2}\beta(t)\,s(X_{t}, w, t) + \sqrt{ \beta(t) }\,d \widehat{W}_{t} }_{ \text{Langevin diffusion SDE} } 
>$$

- [[Langevin Dynamics and Langevin Sampling]]
- [[Langevin Equation]]

>[!quote]
>The **continuous noise injection** can *compensate for errors* introduced by the **numerical integration** of the *ODE term*. Consequently, the resulting samples often look better. However, the **ODE approach can be faster**. Fortunately it is possible to combine these techniques, as proposed in [Kar+22]. The basic idea is illustrated in Figure 25.9: we **alternate** between performing a *deterministic step* using an ODE solver, and then *adding a small amount noise* to the result. This can be repeated for some number of steps. (We discuss ways to reduce the number of required steps in Section 25.5.)
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 871


## Explanation


>[!quote]
>The **main drawback** of *diffusion models* for generating data is that they require **multiple sequential inference passes** through the *trained network*, which can be computationally expensive. One way to speed up the sampling process is first to convert the **denoising process** to a **differential equation over continuous time** and then to use alternative efficient *discretization methods* to solve the equation efficiently.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 593

>[!info]
>The formulation of **SDE** for **DDPM** is **varience preserving SDE**
>$$dX_{t} = - \frac{1}{2}\beta(t)\,X_{t}\,dt + \sqrt{\beta(t)}\,dW_{t}$$ 
>where $$q(x_{t}\,|\,x_{0}) = \mathcal{N}(x_{t}\,|\, \gamma_{t}\,x_{0},\, \sigma_{t}^2I )$$



## Neural Ordinary Differential Equations

- [[Neural Ordinary Differential Equations and Continuous Flows]]


## Numerical Solution for SDE 
















-----------
##  Recommended Notes and References


- [[Denoising Diffusion Probabilistic Models and Diffusion Network]]
- [[Score Matching and Denoising Score Matching]]
- [[Diffusion Network Score Matching Equivalence]]
- [[Normalizing Flows]]
- [[Neural Ordinary Differential Equations and Continuous Flows]]


- [[Wasserstein Distance]]


- [[Deep Learning Foundations and Concepts by Bishop]] pp 598 - 599
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 867 - 872
- **CVPR 2023 Tutorial**: [link](https://cvpr2023-tutorial-diffusion-models.github.io);
	- [Youtube recording](https://www.youtube.com/watch?v=1d4r19GEVos)

- Anderson, B. D. (1982). Reverse-time diffusion equation models. _Stochastic Processes and their Applications_, _12_(3), 313-326.
- Song, Y., Sohl-Dickstein, J., Kingma, D. P., Kumar, A., Ermon, S., & Poole, B. (2021). Score-Based Generative Modeling through Stochastic Differential Equations. In _International Conference on Learning Representations_.