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
>	- $\widehat{W}_{t}$ is a *standard Wiener process* when time flows from $T$ to $0$ 
>	- The **drift term**  in *Reverse SDE* $$f(X_{t},t) - \sigma^2(t)\,\nabla_{x} \log p(X_{t}; t)$$  corresponds to the **score matching** objective
>	- We can recover original signal by *subtracting* $$\sigma^2(t)\,\nabla_{x} \log p(X_{t}; t)$$ in the **drift term**


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


## Explanation


>[!quote]
>The **main drawback** of *diffusion models* for generating data is that they require **multiple sequential inference passes** through the *trained network*, which can be computationally expensive. One way to speed up the sampling process is first to convert the **denoising process** to a **differential equation over continuous time** and then to use alternative efficient *discretization methods* to solve the equation efficiently.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 593


## Neural Ordinary Differential Equations

- [[Neural Ordinary Differential Equations]]


## Numerical Solution for SDE 
















-----------
##  Recommended Notes and References


- [[Denoising Diffusion Probabilistic Models and Diffusion Network]]
- [[Score Matching and Denoising Score Matching]]
- [[Diffusion Network Score Matching Equivalence]]
- [[Normalizing Flows]]
- [[Neural Ordinary Differential Equations]]

- [[Stochastic Differential Equations]]


- [[Deep Learning Foundations and Concepts by Bishop]] pp 598 - 599
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 867 - 872

- Anderson, B. D. (1982). Reverse-time diffusion equation models. _Stochastic Processes and their Applications_, _12_(3), 313-326.
- Song, Y., Sohl-Dickstein, J., Kingma, D. P., Kumar, A., Ermon, S., & Poole, B. (2021). Score-Based Generative Modeling through Stochastic Differential Equations. In _International Conference on Learning Representations_.