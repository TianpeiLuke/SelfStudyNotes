---
tags:
  - concept
  - statistics/monte_carlo_simulation
  - math/stochastic_process
keywords:
  - langevin_equation
  - langevin_dynamic
  - langevin_sampling
topics:
  - statistics/monte_carlo
  - deep_learning
name: Langevin Dynamics and Langevin Sampling
date of note: 2024-07-08
---

## Concept Definition

>[!important]
>**Name**: Langevin Dynamics and Langevin Sampling

![[Langevin Equation#^b373a8]]


![[Hamiltonian Monte Carlo#^d957f6]]


>[!important] Definition
>The **stochastic gradient Langevin dynamics** or simply **Langevin sampling** works as follows:
>- Initialized with starting point $X_{0} \in \mathbb{R}^d$, 
>- Set $T >0$, $N \in \mathbb{N}$, $\eta >0$
>- Input *first-order oracle* for $f:\mathbb{R}^n \to \mathbb{R}$
>- For $k = 1 \,{,}\ldots{,}\, N$ 
>	- Set $$q_{0} = X_{k-1}$$
>	- For $j = 0, 1 \,{,}\ldots{,}\,  T/\eta -1$:
>		- Generate **white noise** $$\xi_{j} \sim \mathcal{N}(0, I)$$
>		- **Update position** $$q_{j+1} = q_{j} - \eta\,\nabla f(q_{j}) + \sqrt{ 2 \eta }\, \xi_{j} $$
>	- Choose new sample as the end position$$X_{k} = q_{T / \eta}$$
>- Output $X := \left(X_{1} \,{,}\ldots{,}\,X_{N}\right)$

- [[Hamiltonian Monte Carlo]]
- [[Langevin Equation]]


## Explanation


## Gradient Flow in Wasserstein Space

>[!important]
>The **stochastic gradient Langevin dynamic** can be seen an equivalent **gradient flow** on **Wasserstein space** $\mathbb{W}_{2}$.
>
>$$
>\rho_{k+1}^{\tau} \in \arg\min_{\rho}\left\{ \mathbb{E}_{ \rho_{t} }\left[ \log \rho_{t}(X) \right] + \mathbb{E}_{ \rho_{t} }\left[ f(X) \right] + \frac{W_{2}^2(\rho, \rho_{k}^{\tau}) }{2\tau}  \right\}  
>$$

- [[Gradient Flow in Wasserstein Space]]
- [[Heat Equation and Fokker–Planck Equation via Wasserstein Distance]]





-----------
##  Recommended Notes and References


- [[Ornstein–Uhlenbeck Process]]

- [[Markov Chain Monte Carlo Methods]]
- [[Hamiltonian Monte Carlo]]


- [[Linear Stochastic Differential Equation Explicit Solution]]
- [[Homogeneous Linear Stochastic Differential Equation]]
- [[Stochastic Differential Equations]]

- [[Gibbs Measure and Energy-based Model]]
- [[Score Matching and Denoising Score Matching]]



- [[Monte Carlo Statistical Methods by Robert]] pp 326, 318
- Wibisono, A. (2018, July). Sampling as optimization in the space of measures: The Langevin dynamics as a composite optimization problem. In _Conference on Learning Theory_ (pp. 2093-3027). PMLR.
- Chen, T., Fox, E., & Guestrin, C. (2014, June). Stochastic gradient hamiltonian monte carlo. In _International conference on machine learning_ (pp. 1683-1691). PMLR.
- [[Deep Learning Foundations and Concepts by Bishop]] pp 454 
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 515, 527 - 529