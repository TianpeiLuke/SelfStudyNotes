---
tags:
  - concept
  - math/information_theory
  - math/differential_equation
  - math/stochastic_process
  - math/optimal_transport
  - math/partial_differential_equation
keywords:
  - fokker_planck_equation
  - optimal_transport
  - gradient_flow_wasserstein
topics:
  - differential_equation
  - stochastic_process
name: Fokker–Planck Equation via Wasserstein Distance
date of note: 2024-06-11
---

## Concept Definition

>[!important]
>**Name**: Fokker–Planck Equation via Wasserstein Distance

![[Gradient Flow in Wasserstein Space#^1e5b9f]]

>[!important] Definition
>Let $(\Omega, \mathscr{F})$ be a measurable metric space and  $\mathscr{P}(\Omega)$ be the *space of probability measures* on $\Omega$. Assume that $\Omega$ is *compact*.
>
>Define $F: \mathscr{P}(\Omega) \to \mathbb{R}\cup \{ \infty \}$ as the **entropy functional**
>$$
>F(\rho) := \int_{\Omega} \rho(x)\,\log(\rho(x)) \,dx := -H(\rho)
>$$
>- We have $$\frac{\delta F}{\delta \rho} =\log \rho + 1$$
>- So $$\nabla \left(\frac{\delta F}{\delta \rho}\right) = \frac{\nabla \rho}{\rho}$$
>- The entropy functional $F$ is referred to as the **internal energy**.
>
>Also define $\mathcal{L}$ as a **linear functional** $$\mathcal{L}(\rho) := \int_{\Omega} L(x)\,d\rho(x) = \mathbb{E}_{ \rho }\left[  L(X) \right]$$ 
>- We have $$\frac{\delta \mathcal{L}}{\delta \rho} =L \implies \nabla \left(\frac{\delta \mathcal{L}}{\delta \rho}\right) = \nabla L$$
>- We could see $L$ as the *loss function* in machine learning.
>- The linear functional $\mathcal{L}$ is referred to as the **potential energy.**

- [[Entropy Functional]]
- [[Expectation of Random Variable]]
- [[Bounded Linear Functional]]
- [[Error Function or Loss Function for Deep Learning]]


### Heat Equation

>[!important] Definition
>Consider the **discretization** of **gradient flow** of $F$ on  **Wasserstein space** $\mathbb{W}_{2}(\Omega)$ is given by the *iterated minimization* for $k=0,\,1\,{,}\ldots{,}\,$
>$$
>\rho_{k+1}^{\tau} \in \arg\min_{\rho}\left\{ F(\rho) + \frac{W_{2}^2(\rho, \rho_{k}^{\tau}) }{2\tau}  \right\}  
>$$
>
>This gradient flow is the *solution* of **heat equation** 
>$$
>\begin{align*}
>\frac{ \partial }{ \partial t }\rho_{t} - \text{div}\left(\rho_{t}\; \nabla \left( \frac{\delta F}{\delta \rho} \right)(\rho_{t}) \right)  &= 0 \\[5pt]
> \implies \frac{ \partial }{ \partial t }\rho_{t} - \text{div}\left(\rho_{t}\;  \frac{\nabla \rho_{t}}{\rho_{t}} \right)  &= 0  \\[5pt]
> \implies \frac{ \partial }{ \partial t }\rho_{t} - \text{div}\left(\nabla \rho_{t}\right)  &= 0  \\[5pt]
> \implies \frac{ \partial }{ \partial t }\rho_{t} - \Delta \rho_{t}  &= 0  \\[5pt]
\end{align*}
>$$
>where $$\Delta g = \text{div}(\nabla g)$$ is the *Laplacian operator*.

- [[Entropy Functional]]
- [[Gradient Flow in Wasserstein Space]]
- [[Stochastic Differential Equations]]
- [[Heat Equation and Diffusion Equation]]

### Fokker-Planck Equation

>[!important] Definition
>Consider the **discretization** of **gradient flow** of $F+\mathcal{L}$ on  **Wasserstein space** $\mathbb{W}_{2}(\Omega)$ is given by the *iterated minimization* for $k=0,\,1\,{,}\ldots{,}\,$
>$$
>\rho_{k+1}^{\tau} \in \arg\min_{\rho}\left\{ F(\rho) + \mathcal{L}(\rho) + \frac{W_{2}^2(\rho, \rho_{k}^{\tau}) }{2\tau}  \right\}  
>$$
>  
>This gradient flow is the *solution* of **Fokker-Planck equation** 
>$$
>\begin{align*}
>\frac{ \partial }{ \partial t }\rho_{t} - \text{div}\left(\rho_{t}\; \nabla \left( \frac{\delta (F+ \mathcal{L})}{\delta \rho} \right)(\rho_{t}) \right)  &= 0 \\[5pt]
> \implies \frac{ \partial }{ \partial t }\rho_{t} - \text{div}\left(\rho_{t}\;  \frac{\nabla \rho_{t}}{\rho_{t}}  + \rho_{t} \nabla L\right)  &= 0  \\[5pt]
> \implies \frac{ \partial }{ \partial t }\rho_{t} - \Delta \rho_{t} - \text{div}(\rho_{t}\, \nabla L)  &= 0  \\[5pt]
\end{align*}
>$$

- [[Fokker–Planck and Kolmogorov Forward-Backward Equation]]
- [[Stochastic Differential Equations]]

>[!important]
>Note that the composite functional $F + \mathcal{L}$ is the **Kullback-Leibler divergence** if $\mathcal{L}$ is the *cross entropy* $$\mathcal{L} = \mathbb{E}_{ \rho }\left[  -\log \nu \right]$$ 
>Thus
>$$
>\begin{align*}
>J(\rho) &:= F(\rho) + \mathcal{L}(\rho) \\[5pt] 
>&:= -H(\rho) + \mathbb{E}_{ \rho }\left[  -\log \nu \right] \\[5pt] 
>&= \mathbb{E}_{ \rho }\left[ \log \left(\frac{\rho}{\nu}\right) \right] \\[5pt] 
>&:= \mathbb{KL}\left( \rho \left\|\right. \nu  \right)
>\end{align*}
>$$
>with loss function $L$ as the *negative log-likelihood function* of a *prior measure* $\nu$
>$$L = -\log \nu \quad \iff \quad \nu = e^{-L}$$
>
>Then the *discretized gradient flow* becomes the **entropy minimization algorithm**
>$$
>\rho_{k+1}^{\tau} \in \arg\min_{\rho}\left\{ \mathbb{KL}\left( \rho \left\|\right. \nu  \right) + \frac{W_{2}^2(\rho, \rho_{k}^{\tau}) }{2\tau}  \right\}  
>$$
>- The corresponding **Fokker-Planck equation** has the same form as the **score matching** algorithm 
>$$
>\begin{align*}
>\frac{ \partial }{ \partial t }\rho_{t} + \text{div}(\rho_{t}\, \left(\nabla \log \rho_{t}  - \nabla \log \nu\right)    )  &= 0 
\end{align*}
>$$

- [[Kullback-Leibler Divergence]]
- [[Entropy Minimization Algorithm]]
- [[Score Matching and Denoising Score Matching]]

### Uniqueness

>[!important] Proposition
>Let $(\Omega, \mathscr{F})$ be a measurable **compact metric space** and  $\mathscr{P}(\Omega)$ be the *space of probability measures* on $\Omega$. 
>
>Consider the following **functional** on $\mathscr{P}(\Omega)$  $$J(\rho) := \int_{\Omega} \rho \log \rho + \int_{\Omega}L d\rho$$ where $L$ is a **Lipschitz function** on compact domain $\Omega$. Assume that $\rho_{0}\in \mathscr{P}(\Omega)$ is an initital measure.
>
>Then 
>- the functional $J$ has a  **unique minimum** over $\mathscr{P}(\Omega)$ , i.e. $$\rho^{*} = \arg\min_{\rho \in \mathscr{P}(\Omega)}\;J(\rho).$$
>	- In particular, $$J > -\infty$$ is *bounded from below*.
>- Moreover, for each $\tau >0$, the following sequence of optimization problems recursively defined is **well-posed**  $$\rho_{k+1}^{\tau} \in \arg\min_{\rho}\left\{ J(\rho) + \frac{W_{2}^2(\rho, \rho_{k}^{\tau}) }{2\tau}  \right\}, \quad k=0\,{,}\ldots{,}\,$$
>	-  That is, there **exists** a **minimizer** at each step $k$, and the minimizer is **unique.** 


>[!info]
>As we just showed, the functional $J$ can be the KL-divergence, thus the conclusion of above proposition corresponds to the **maximum entropy learning**

- [[Maximum Entropy Learning]]
- [[Variational Formula for Entropy Functional]]



## Explanation


### Generalized Proximal Algorithm

>[!info]
>The iterated minimization 
>$$
>\rho_{k+1}^{\tau} \in \arg\min_{\rho}\left\{ f(\rho) + \frac{W_{2}^2(\rho, \rho_{k}^{\tau}) }{2\tau}  \right\}  
>$$
>can be seen as **generalized proximal algorithm.**


- [[Generalized Proximal Method]]

>[!info]
>If $f$ is the entropy functional,  the iterated minimization 
>$$
>\rho_{k+1}^{\tau} \in \arg\min_{\rho}\left\{ f(\rho) + V(\rho) + \frac{W_{2}^2(\rho, \rho_{k}^{\tau}) }{2\tau}  \right\}  
>$$
>can be seen as **entropy-regularized proximal algorithm**.

- [[Entropy Minimization Algorithm]]
- [[Bregman Divergence Minimization]]


## Logarithmic Sobolev Inequality

- [[Logarithmic Sobolev Inequality for Gaussian Random Variables]]




## Langevin Equation

>[!important] 
>The **gradient flow** 
>$$
>\rho_{k+1}^{\tau} \in \arg\min_{\rho}\left\{ -H(\rho) + \mathbb{E}_{ \rho }\left[  L(X) \right] + \frac{W_{2}^2(\rho, \rho_{k}^{\tau}) }{2\tau}  \right\}  
>$$
>can be seen as a **diffusion process** where
>- the *velocity* of each particle is given by $$-  \frac{\nabla\rho_{t}}{\rho_{t}} - \nabla L$$ 
>  
>The corresponding **stochastic differential equation** is the **Langevin equation**  
>$$
> dX_{t} = - \nabla L(X_{t})\,dt + \sqrt{2}\; dW_{t}
>$$
>- The **gradient flow** above is seen as the PDE formulation of the Langevin equation.

- [[Langevin Equation]]
- [[Diffusion Process]]
- [[Fokker–Planck and Kolmogorov Forward-Backward Equation]]
- [[Langevin Dynamics and Langevin Sampling]]
- [[Stochastic Gradient Descent Algorithm]]
- Wibisono, A. (2018, July). Sampling as optimization in the space of measures: The Langevin dynamics as a composite optimization problem. In _Conference on Learning Theory_ (pp. 2093-3027). PMLR.



-----------
##  Recommended Notes and References


- [[Probability Distribution of Random Variable]]
- [[Radon-Nikodym Derivative]]

- [[Wasserstein Space]]
- [[Wasserstein Distance]]

- [[Concepts and Theorems for Stochastic Differential Equations]]


- Jordan, R., Kinderlehrer, D., & Otto, F. (1998). The variational formulation of the Fokker--Planck equation. _SIAM journal on mathematical analysis_, _29_(1), 1-17.
- [[Introduction to Stochastic Calculus by Klebaner]]
- [[Optimal Transport for Applied Mathematicians by Santambrogio]] pp 292 - 300
- [[Optimal Transport Old and New by Villani]] pp 672  - 675
- [[Gradient Flows in Metric Spaces and in Space of Probability Measures by Ambrosio]] pp 281 - 284
- Oksendal, B. (2013). _Stochastic differential equations: an introduction with applications_. Springer Science & Business Media.
- Wikipedia [Fokker-Planck_equation](https://en.wikipedia.org/wiki/Fokker%E2%80%93Planck_equation)