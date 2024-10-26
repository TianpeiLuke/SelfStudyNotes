---
tags:
  - concept
  - math/differential_equation
  - math/optimal_transport
  - math/partial_differential_equation
keywords:
  - gradient_flow_wasserstein
topics:
  - partial_differential_equation
name: Gradient Flows in Wasserstein Space
date of note: 2024-10-25
---

## Concept Definition

>[!important]
>**Name**: Gradient Flows in Wasserstein Space


![[Gradient Flow on Euclidean Space#^33863e]]

- [[Gradient Flow on Euclidean Space]]


>[!important] Definition
>Let $(\Omega, \mathscr{F})$ be a measurable metric space and  $\mathscr{P}(\Omega)$ be the *space of probability measures* on $\Omega$. Assume that $\Omega$ is *compact*.
>
>Define $f: \mathscr{P}(\Omega) \to \mathbb{R}\cup \{ \infty \}$ as  a *functional* on probability measures and assume that $f$ is *lower semi-continuous*.
>
>Consider the **continuity equation** for a vector field $V$ in **Wasserstein space** $\mathbb{W}_{2}(\Omega)$ as $$\frac{ \partial }{ \partial t }\rho_{t} + \text{div}\left(\rho_{t}\; V_{t} \right)  = 0$$
>where
>- $\rho_{t} \in \mathbb{W}_{2}(\Omega)$ is a *parameterized curve*, parameterized by $t$
>- $V_{t}$ is a *vector field* along the curve $\rho_{t}$
>  
>The **discretization** of **gradient flow** of $f$ on  **Wasserstein space** $\mathbb{W}_{2}(\Omega)$ is given by the *iterated minimization* for $k=0,\,1\,{,}\ldots{,}\,$
>$$
>\rho_{k+1}^{\tau} \in \arg\min_{\rho}\left\{ f(\rho) + \frac{W_{2}^2(\rho, \rho_{k}^{\tau}) }{2\tau}  \right\}  
>$$
>where 
>- $W_{2}(\mu, \rho)$ is the *Wassterstein-2 distance* between two probability measures $\mu$ and $\rho.$
>- This gradient flow is the *solution* of *continuity equation* $$\frac{ \partial }{ \partial t }\rho_{t} - \text{div}\left(\rho_{t}\; \nabla \left( \frac{\delta f}{\delta \rho} \right)(\rho_{t}) \right)  = 0$$

^1e5b9f


- [[Probability Space]]
- [[Measure Space and Countably Additive Measure]]
- [[Space of Bounded Signed Measures]]
- [[Compactness]]
- [[Semi-Continuous Function]]

- [[Wasserstein Space]]
- [[Parameterized Curve on Manifold]]
- [[Vector Field on Manifold]]
- [[Divergence Operator of Vector Field on Riemannian Manifold]]
- [[Wasserstein Distance]]


## Explanation


### Generalized Proximal Algorithm

>[!info]
>The iterated minimization 
>$$
>\rho_{k+1}^{\tau} \in \arg\min_{\rho}\left\{ f(\rho) + \frac{W_{2}^2(\rho, \rho_{k}^{\tau}) }{2\tau}  \right\}  
>$$
>can be seen as **generalized proximal algorithm** where the *Wasserstein distance* is the *proximity measure* in space of probability measures.

- [[Generalized Proximal Method]]



## Heat Equation

- [[Heat Equation and Diffusion Equation]]
- [[Heat Equation and Fokker–Planck Equation via Wasserstein Distance]]

## Fokker-Planck Equation

- [[Heat Equation and Fokker–Planck Equation via Wasserstein Distance]]
- [[Fokker–Planck and Kolmogorov Forward-Backward Equation]]




-----------
##  Recommended Notes and References



- [[Gradient Flow on Smooth Manifold]]


- [[Heat Equation and Diffusion Equation]]

- [[Vector Field Along a Curve]]
- [[Optimal Transport in Space of Measures]]
- [[Radon Measure]]

- [[Gradient Flows in Metric Spaces and in Space of Probability Measures by Ambrosio]]
- [[An Introduction to Optimization on Smooth Manifolds by Boumal]]
- [[Optimal Transport for Applied Mathematicians by Santambrogio]]
- [[Optimal Transport Old and New by Villani]] pp 629 - 635, 681, 694
- [[Ordinary Differential Equations by Chicone]]