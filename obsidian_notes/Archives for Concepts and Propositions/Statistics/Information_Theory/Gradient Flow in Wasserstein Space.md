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
name: Gradient Flow in Wasserstein Space
date of note: 2024-10-25
---

## Concept Definition

>[!important]
>**Name**: Gradient Flow in Wasserstein Space


![[Gradient Flow in Euclidean Space#^33863e]]

- [[Gradient Flow in Euclidean Space]]

![[Wasserstein Space#^998943]]

>[!info]
>The **first-variation of functional** $F$ $$\frac{\delta F}{\delta \rho}$$  is defined as a measurable function that satisfies the equation $$\frac{d}{dt}\Big|_{t=0} F(\rho + t\,\mu) = \int \frac{\delta F}{\delta \rho}(\rho)\, d\mu$$

- [[Variation of Functional]]

>[!important] Definition
>Let $(\Omega, \mathscr{F})$ be a measurable metric space and  $\mathbb{W}_{2}(\Omega)$ be the *Wasserstein space* of *order* $2$ on $\Omega$. 
>- Assume that $\Omega$ is *compact*.
>- The Wasserstein space is a subspace of space of probability measures $$\mathbb{W}_{2}(\Omega) \subset \mathscr{P}(\Omega)$$
>- Denote $W_{2}(\mu, \rho)$ as the *Wassterstein-2 distance* between two probability measures $\mu$ and $\rho.$
>
>Define $F: \mathscr{P}(\Omega) \to \mathbb{R}\cup \{ \infty \}$ as  a *functional* on probability measures.
>-  Assume that $F$ is *lower semi-continuous*.
>
>The **gradient flow** of  *functional* $F$ in *Wasserstein space* $\mathbb{W}_{2}(\Omega)$ is defined as $$\frac{ \partial }{ \partial t }\rho_{t} - \text{div}\left(\rho_{t}\; \nabla \left( \frac{\delta F}{\delta \rho} \right)(\rho_{t}) \right)  = 0$$
>where
>- $\rho_{t} \in \mathbb{W}_{2}(\Omega)$ is a *parameterized curve* in $\mathbb{W}_{2}(\Omega)$, parameterized by $t$
>- $$\nabla \left( \frac{\delta F}{\delta \rho} \right)$$ is the *gradient* of *first variational* of functional $f$, which is a *vector field* on $\mathbb{W}_{2}$ space.
>- The PDE above is a **continuity equation** for vector field $$X = \nabla \left( \frac{\delta F}{\delta \rho} \right)$$
>  
>The **discretization** of **gradient flow** of $F$ on $\mathbb{W}_{2}(\Omega)$ is given by the *iterated minimization*
>$$
>\rho_{k+1}^{\tau} \in \arg\min_{\rho}\left\{ F(\rho) + \frac{W_{2}^2(\rho, \rho_{k}^{\tau}) }{2\tau}  \right\}, \quad k=0,\,1\,{,}\ldots{,}\, 
>$$



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
- [[Laplacian of Smooth Map on Riemannian Manifold]]
- [[Wasserstein Distance]]


## Explanation


### Generalized Proximal Algorithm

>[!info]
>The iterated minimization 
>$$
>\rho_{k+1}^{\tau} \in \arg\min_{\rho}\left\{ F(\rho) + \frac{W_{2}^2(\rho, \rho_{k}^{\tau}) }{2\tau}  \right\}  
>$$
>can be seen as **generalized proximal algorithm** where the *Wasserstein distance* is the *proximity measure* in space of probability measures.

- [[Generalized Proximal Method]]



## Heat Equation

>[!info]
>If $F$ is the **entropy functional**,
>$$
>F(\rho) = \int_{\Omega} \rho \log(\rho)
>$$
>then the gradient flow is described by the **heat equation**
>$$\frac{ \partial }{ \partial t }\rho_{t} - \text{div}\left(\nabla \rho_{t} \right)  = 0$$

- [[Entropy Functional]]
- [[Heat Equation and Diffusion Equation]]
- [[Heat Equation and Fokker–Planck Equation via Wasserstein Distance]]

## Fokker-Planck Equation

>[!info]
>If $F$ is the **entropy functional** *plus* **expectation functional**,
>$$
>F(\rho) = \int_{\Omega} \rho \log(\rho) + \int_{\Omega }L d\rho
>$$
>then the gradient flow is described by the **Fokker-Planck equation**
>$$\frac{ \partial }{ \partial t }\rho_{t} - \text{div}\left(\nabla \rho_{t} \right) - \text{div}\left(\rho_{t}\,\nabla L \right) = 0$$


- [[Heat Equation and Fokker–Planck Equation via Wasserstein Distance]]
- [[Fokker–Planck and Kolmogorov Forward-Backward Equation]]




-----------
##  Recommended Notes and References



- [[Gradient Flow on Smooth Manifold]]


- [[Heat Equation and Diffusion Equation]]

- [[Vector Field Along a Curve]]
- [[Optimal Transport in Space of Measures]]
- [[Radon Measure]]
- [[Polish Space]]


- [[Gradient Flows in Metric Spaces and in Space of Probability Measures by Ambrosio]]
- [[An Introduction to Optimization on Smooth Manifolds by Boumal]]
- [[Optimal Transport for Applied Mathematicians by Santambrogio]] pp 290 - 304
- [[Optimal Transport Old and New by Villani]] pp 629 - 635, 681, 694
- [[Ordinary Differential Equations by Chicone]]