---
tags:
  - concept
  - machine_learning/models
  - deep_learning/generative_models
  - math/differential_equation
  - math/stochastic_process
keywords:
  - diffusion_network
  - score_matching
topics:
  - generative_model
  - deep_learning/models
  - deep_learning/algorithm
  - deep_learning/generative_models
name: Diffusion Network Score Matching Equivalence
date of note: 2024-10-19
---

## Concept Definition

>[!important]
>**Name**: Diffusion Network Score Matching Equivalence

### Denoising Diffusion Probabilistic Model

![[Denoising Diffusion Probabilistic Models and Diffusion Network#^de66ca]]


![[Denoising Diffusion Probabilistic Models and Diffusion Network#^e4a1ab]]

![[Denoising Diffusion Probabilistic Models and Diffusion Network#^e4a1ab]]

![[Denoising Diffusion Probabilistic Models and Diffusion Network#^03693f]]


![[Denoising Diffusion Probabilistic Models and Diffusion Network#^bf4525]]

- [[Denoising Diffusion Probabilistic Models and Diffusion Network]]

### Denoising Score Matching

![[Score Matching and Denoising Score Matching#^bbecdb]]

- [[Score Matching and Denoising Score Matching]]

### DDPM as DSM

>[!important] Definition
>The **denoising diffusion probabilistic models (DDPM)** can be reformulated as a **score matching** problem.
>
>- The **forward diffusion kernel** for DDPM is given by $$q(z_{t} | x) = \mathcal{N}(z_{t}\;|\; \sqrt{ \alpha_{t} }x,\, (1-\alpha_{t})I )$$ where $$z_{t} = \sqrt{ \alpha_{t} }x + \sqrt{ 1- \alpha_{t} }\epsilon_{t}$$
>- The **smoothed data distribution** at $t$ becomes $$q(z_{t}) = \int p_{D}(x)\,q(z_{t}|x)\,dx$$
>- The **reverse transition** for DDPM is approximated by the **diffusion network** as $$p(z_{t-1}|z_{t}, w) = \mathcal{N}(z_{t-1}\,|\, \mu(z_{t}, w, t),\, \beta_{t}I)$$ where $\mu$ is further represented by a *network* $g$ that **predicts noise** as $$\mu(z_{t}, w, t)= \frac{1}{\sqrt{ 1- \beta_{t} }}\left[ z_{t} - \frac{\beta_{t}}{\sqrt{ 1 - \alpha_{t} }}  g(z_{t}, w, t) \right] :=\frac{1}{\sqrt{ 1- \beta_{t} }}\left[ z_{t} + \beta_{t}s(z_{t}, w, t)\right] $$ 
>	- We can instead define the **score model** as $$s(z_{t}, w, t) = - \frac{1}{\sqrt{ 1 - \alpha_{t} }}g(z_{t}, w, t)$$
>- The **data score function** is defined as $$\begin{align*}\nabla_{z_{t}} \log q(z_{t} |  x)&= \nabla_{z_{t}} \left(- \frac{(z_{t} -  \sqrt{ \alpha_{t} }x )^2 }{2(1- \alpha_{t})} \right) \\[5pt] &= -\frac{z_{t} -  \sqrt{ \alpha_{t} }x}{1- \alpha_{t}} \\[5pt] &:= -\frac{1}{\sqrt{ 1- \alpha_{t} }} \epsilon_{t} \end{align*}$$ 
>- The **score function** of diffusion model is that $$\begin{align*}\nabla_{z_{t-1}} \log p(z_{t-1}|z_{t}, w) &= - \frac{z_{t-1} - \mu(z_{t}, w, t)}{\beta_{t}} \\[5pt] &= \frac{1}{\sqrt{ 1 - \beta_{t} }} s(z_{t}, w, t) + \sqrt{ \frac{\beta_{t}}{1- \beta_{t}} }\epsilon_{t} \\[5pt]  &= \frac{1}{\sqrt{ 1 - \beta_{t} }} \left[  s(z_{t}, w, t) + \sqrt{\beta_{t}}\epsilon_{t} \right]  \\[5pt] \text{when }  (1-\beta_{t}) \approx 1, \; \beta_{t} \approx 0 \\[5pt]  \nabla_{z_{t-1}} \log p(z_{t-1}|z_{t}, w)&\approx s(z_{t}, w, t) \\[5pt] &=- \frac{1}{\sqrt{ 1 - \alpha_{t} }}g(z_{t}, w, t) \end{align*}$$ 

>[!important] Definition
>Thus the **DDPM** approximately minimize the **denoising score matching objective**
>$$
>\begin{align*}
>\mathcal{L}(q, w; x) &=\mathbb{E}_{t\sim U([T]),\, x\sim \mathcal{D},\, Z_{t} \sim q(\cdot|x) }\left[\left\lVert  \nabla_{z_{t-1}} \log p(z_{t-1}|z_{t}) - \nabla_{z_{t}} \log q(z_{t} |  x)   \right\rVert_{2}^2\right]  \\[5pt] 
>&\propto \mathbb{E}_{t\sim U([T]),\, x\sim \mathcal{D},\, Z_{t} \sim q(\cdot|x) }\left[\lambda_{t} \left\lVert  s(Z_{t}, w, t)  + \frac{1}{\sqrt{ 1- \alpha_{t} }} \epsilon_{t}   \right\rVert_{2}^2\right]  \\[5pt] 
>&=\;\mathbb{E}_{t\sim U([T]),\, x\sim \mathcal{D},\, Z_{t} \sim q(\cdot|x) }\left[\frac{\lambda_{t}}{1-\alpha_{t}}\left\lVert  g(Z_{t}, w, t)  -  \epsilon_{t}   \right\rVert_{2}^2\right] \end{align*}
>$$
>where
>- $$\lambda_{t} = \frac{1}{1- \beta_{t}}$$
>- This is equivalent to the **simplied ELBO objective** for DDPM is $$\begin{align*}\mathcal{L}(w) &=\mathbb{E}_{t\sim U([T]), x\sim \mathcal{D}, Z_{t} \sim q(\cdot|x) }\left[\lVert g(Z_{t}, w, t) - \epsilon_{t} \rVert_{2}^2\right]  \end{align*}$$  

- [[Score Matching and Denoising Score Matching]]
- [[Markov Chain and Markov Process]]
- [[Markov Transition Kernel and Transition Function]]

>[!info]
> $$
> \begin{align*}
> \nabla_{z_{t-1}} \log p(z_{t-1}|z_{t}) &= \nabla_{z_{t-1}} \left(- \frac{(z_{t-1} -  \mu(z_{t}, w, t) )^2 }{2\beta_{t}} \right) \\[5pt] 
> &= -\frac{z_{t-1} -  \mu(z_{t}, w, t)}{\beta_{t}} \\[5pt] 
> &= - \frac{1}{\beta_{t}} z_{t-1} + \frac{1}{\beta_{t}\sqrt{ 1- \beta_{t} }}\left[ z_{t} + \beta_{t}s(z_{t}, w, t)\right]\\[5pt] 
> &\text{ use the fact } z_{t} = \sqrt{ 1 - \beta_{t} } z_{t-1} + \sqrt{ \beta_{t} }\epsilon_{t}\\[5pt] 
> &= \frac{1}{\beta_{t}} \sqrt{\frac{\beta_{t}}{1- \beta_{t}}}\epsilon_{t} + \frac{1}{\sqrt{ 1- \beta_{t} }}s(z_{t}, w, t)
>  \end{align*}$$ 



>[!info]
>The **score matching objective**
>$$
>\begin{align*}
>\mathcal{L}(q, w; x) &=-\sum_{t=1}^{T}\mathbb{E}_{Z_{t} \sim q(\cdot|x) }\left[\left\lVert  \nabla_{z_{t-1}} \log p(z_{t-1}|z_{t}) - \nabla_{z_{t}} \log q(z_{t} |  x)   \right\rVert_{2}^2\right]  \\[5pt] 
>&=-\sum_{t=1}^{T}\mathbb{E}_{Z_{t} \sim q(\cdot|x) }\left[\left\lVert  \frac{\sqrt{ \beta_{t} }}{\beta_{t}\sqrt{ 1- \beta_{t} }}\epsilon_{t} + \frac{1}{\sqrt{ 1- \beta_{t} }}s(z_{t}, w, t) + \frac{(Z_{t} - \sqrt{ \alpha_{t} }x)}{1 - \alpha_{t}}   \right\rVert_{2}^2\right]  \\[5pt]
>&=-\sum_{t=1}^{T}\mathbb{E}_{Z_{t} \sim q(\cdot|x) }\left[\left\lVert  \frac{1}{\sqrt{\beta_{t}}\sqrt{ 1- \beta_{t} }}\epsilon_{t} + \frac{1}{\sqrt{ 1- \beta_{t} }}s(z_{t}, w, t)  -\frac{1}{\sqrt{ 1- \alpha_{t-1} }} \epsilon_{t}  \right\rVert_{2}^2\right]  \\[5pt]
>&= -\sum_{t=1}^{T}\mathbb{E}_{Z_{t} \sim q(\cdot|x) }\left[\left\lVert \frac{1}{\sqrt{ 1- \beta_{t} }} \frac{g(z_{t}, w, t)}{\sqrt{ 1 - \alpha_{t} }}  - \rho_{t} \epsilon_{t}  \right\rVert_{2}^2\right]  \\[5pt]
>&= -\sum_{t=1}^{T}\frac{1}{(1- \beta_{t})(1- \alpha_{t}) }\mathbb{E}_{Z_{t} \sim q(\cdot|x) }\left[\left\lVert  g(z_{t}, w, t)  - \hat{\rho_{t}} \epsilon_{t}  \right\rVert_{2}^2\right]  
>\end{align*}
>$$
>where $$\rho_{t} = \sqrt{ (1- \beta_{t})(1- \alpha_{t})  }\left[-\frac{1}{\sqrt{ 1- \alpha_{t} }} +  \frac{1}{\sqrt{\beta_{t}}\sqrt{ 1- \beta_{t} }} \right] $$



## Explanation




-----------
##  Recommended Notes and References

- [[Denoising Diffusion Probabilistic Models and Diffusion Network]]


- [[Gaussian Random Vector]]
- [[Diffusion Process]]
- [[Markov Chain and Markov Process]]
- [[Time-Reversible Markov Chain]]
- [[Markov Transition Kernel and Transition Function]]
- [[Artificial Neural Network and Deep Learning]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 864 - 867
- [[Deep Learning Foundations and Concepts by Bishop]] pp 581 - 603
- Song, Y., & Ermon, S. (2019). Generative modeling by estimating gradients of the data distribution. _Advances in neural information processing systems_, _32_.
- Song, Y., Sohl-Dickstein, J., Kingma, D. P., Kumar, A., Ermon, S., & Poole, B. (2020). Score-based generative modeling through stochastic differential equations. _arXiv preprint arXiv:2011.13456_.