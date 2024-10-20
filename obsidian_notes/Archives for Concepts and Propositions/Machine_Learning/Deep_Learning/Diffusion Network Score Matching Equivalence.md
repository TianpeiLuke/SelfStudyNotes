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

>[!important] Definition
>The **denoising diffusion probabilistic models (DDPM)** can be reformulated as a **score matching** problem.
>
>- The **forward diffusion kernel** for DDPM is given by $$q(z_{t} | x) = \mathcal{N}(z_{t}\;|\; \sqrt{ \alpha_{t} }x,\, (1-\alpha_{t})I )$$ where $$z_{t} = \sqrt{ \alpha_{t} }x + \sqrt{ 1- \alpha_{t} }\epsilon_{t}$$
>- The **data conditional reverse transition** is given by $$q(z_{t-1} | z_{t}, x) = \mathcal{N}(z_{t-1}\;|\; m_{t}(x, z_{t}),\,\sigma_{t}^2I)$$
>	- The mean can be reparameterized by noise term $$\begin{align*}m_{t}(x, z_{t}) &:= \frac{1}{1- \alpha_{t}}\left[ (1- \alpha_{t-1})\sqrt{ 1- \beta_{t} }\,z_{t} + \sqrt{ \alpha_{t-1} }\,\beta_{t}\,x \right]\\[5pt] \equiv  m_{t}(z_{t}, \epsilon_{t})&= \frac{1}{\sqrt{ 1 - \beta_{t} }}\left[ z_{t} - \frac{\beta_{t}}{\sqrt{ 1 - \alpha_{t} }}\epsilon_{t}\right] := \frac{1}{\sqrt{ 1 - \beta_{t} }}\left[ z_{t} + \beta_{t} \hat{\epsilon}_{t}\right]  \end{align*}$$
>	- The variance $$\sigma_{t}^2 := \frac{1 - \alpha_{t-1}}{1- \alpha_{t}}\,\beta_{t} := \rho_{t}\beta_{t} \approx \beta_{t}$$
>- The **reverse transition** for DDPM is approximated by the **diffusion network** as $$p(z_{t-1}|z_{t}, w) = \mathcal{N}(z_{t-1}\,|\, \mu(z_{t}, w, t),\, \beta_{t}I)$$ 
>	- The mean $\mu$ is further represented by a *network* $g$ that **predicts noise** as $$\begin{align*}\mu(z_{t}, w, t) &= \frac{1}{\sqrt{ 1- \beta_{t} }}\left[ z_{t} - \frac{\beta_{t}}{\sqrt{ 1 - \alpha_{t} }}  g(z_{t}, w, t) \right] \\[5pt] &:=\frac{1}{\sqrt{ 1- \beta_{t} }}\left[ z_{t} + \beta_{t}s(z_{t}, w, t)\right] \end{align*}$$ 
>	- We can instead define the **score model** as $$s(z_{t}, w, t) = - \frac{1}{\sqrt{ 1 - \alpha_{t} }}g(z_{t}, w, t)$$
>	- The **conditional mean estimator** of $z_{t-1}$ given $z_{t}$ under **diffusion model** can be obtained as $$\hat{z}_{t-1} = \frac{1}{\sqrt{ 1- \beta_{t} }}\left(z_{t} - \frac{\beta_{t}}{\sqrt{1 - \alpha_{t} }}g(z_{t}, w, t) \right) = \frac{1}{\sqrt{ 1- \beta_{t} }}\left( z_{t} + \beta_{t}s(z_{t}, w, t) \right)$$

- [[Denoising Diffusion Probabilistic Models and Diffusion Network]]

### Denoising Score Matching

![[Score Matching and Denoising Score Matching#^bbecdb]]

- [[Score Matching and Denoising Score Matching]]

### DDPM as DSM

>[!important] 
>- The **data score function** is defined as $$\begin{align*}\nabla_{z_{t-1}} \log q(z_{t-1} | z_{t}, x) &= \nabla_{z_{t-1}} \left(- \frac{\lVert z_{t-1} -  m_{t}(z_{t}, \epsilon_{t}) \rVert^2 }{2\sigma_{t}^2} \right) \\[5pt]  &= -\frac{z_{t-1} -  m_{t}(z_{t}, \epsilon_{t}) }{\sigma_{t}^2} \\[5pt] \end{align*}$$
>- The **score function** of diffusion model is that $$\begin{align*}\nabla_{z_{t-1}} \log p(z_{t-1}|z_{t}, w) &= - \frac{z_{t-1} - \mu(z_{t}, w, t)}{\beta_{t}}\end{align*}$$ 

#### Denoising Score Matching using Reverse Transition Kernel

>[!important] Definition
>Thus the **DDPM** approximately minimize the **denoising score matching objective**
>$$
>\begin{align*}
>\mathcal{L}(w) &=\mathbb{E}_{t,\, x\sim \mathcal{D},\, Z_{t} \sim q(\cdot|x),\, Z_{t-1} \sim q(\cdot|z_{t}, x) }\left[\left\lVert  \nabla_{z_{t-1}} \log p(z_{t-1}|z_{t}, w) - \nabla_{z_{t-1}} \log q(z_{t-1} | z_{t}, x) \right\rVert_{2}^2\right]  \\[5pt] 
>&=\mathbb{E}_{t,\, x\sim \mathcal{D},\, Z_{t} \sim q(\cdot|x),\, Z_{t-1} \sim q(\cdot|z_{t}, x)}\left[\left\lVert  - \frac{z_{t-1} - \mu(z_{t}, w, t)}{\beta_{t}} + \frac{z_{t-1} -  m_{t}(x, z_{t}) }{\sigma_{t}^2} \right\rVert_{2}^2\right]  \\[5pt] 
>&=\mathbb{E}_{t,\, x\sim \mathcal{D},\, Z_{t} \sim q(\cdot|x),\, Z_{t-1} \sim q(\cdot|z_{t}, x)}\left[\left\lVert  - \frac{z_{t-1} - \mu(z_{t}, w, t)}{\beta_{t}} + \frac{z_{t-1} -  m_{t}(x, z_{t}) }{\rho_{t}\,\beta_{t}} \right\rVert_{2}^2\right]  \\[5pt] 
>&\propto \mathbb{E}_{t,\, x\sim \mathcal{D},\, Z_{t} \sim q(\cdot|x)}\left[\frac{1}{\beta_{t}^2} \lVert \mu(Z_{t}, w, t) - m_{t}(x, Z_{t}) \rVert_{2}^2\right]  \\[5pt] 
>&=\;\mathbb{E}_{t,\, x\sim \mathcal{D},\, Z_{t} \sim q(\cdot|x), \hat{\epsilon}_{t}}\left[\frac{1}{1-\beta_{t}}\left\lVert  s(Z_{t}, w, t)  -  \hat{\epsilon}_{t} \right\rVert_{2}^2\right]    \\[5pt] 
>&=\;\mathbb{E}_{t,\, x\sim \mathcal{D},\,\epsilon_{t} \sim \mathcal{N}(0,I)} \left[\frac{1}{(1-\beta_{t})(1- \alpha_{t})}\left\lVert  g(Z_{t}, w, t)  -  \epsilon_{t}   \right\rVert_{2}^2\right] \end{align*}
>$$
>where
>- $m(x, z_{t})$ is the *conditional mean* estimated based on *forward transition*.
>- This is equivalent to the **simplied ELBO objective** for DDPM is $$\begin{align*}\mathcal{L}(w) &=\mathbb{E}_{t, x\sim \mathcal{D}, \epsilon_{t} \sim \mathcal{N}(0,I) }\left[\lVert g(Z_{t}, w, t) - \epsilon_{t} \rVert_{2}^2\right]  \end{align*}$$  

^af368e

- [[Score Matching and Denoising Score Matching]]
- [[Markov Chain and Markov Process]]
- [[Markov Transition Kernel and Transition Function]]

#### Denoising Score Matching using Forward Transition Kernel

>[!important]
>We see that $$\mu(z_{t}, w,t) = \frac{1}{\sqrt{ 1- \beta_{t} }}\left[ z_{t} + \beta_{t}s(z_{t}, w, t)\right]$$
>- So the **conditional mean estimator** of $z_{t-1}$ given $z_{t}$ under model  is $$\hat{z}_{t-1} := \mathbb{E}_{w }\left[  Z_{t-1}|z_{t}, w \right] = \mu(z_{t}, w,t) = \frac{1}{\sqrt{ 1- \beta_{t} }}\left( z_{t} + \beta_{t}s(z_{t}, w, t) \right)$$
>	- $\hat{z}_{t-1}$ is the **denoised image** from *reverse diffusion process*.
>- The network $s$ corresponds to **Stein score function** given the **conditional mean estimator** $\hat{z}_{t-1}$ under **model**  $$\begin{align*} s(z_{t}, w, t)  &= - \frac{z_{t} -\sqrt{1- \beta_{t}}\,\mu(z_{t}, w,t)}{\beta_{t}} \\[5pt] &= \nabla_{z_{t}} \log \mathcal{N}(z_{t}\;|\; \sqrt{1- \beta_{t}}\,\mu(z_{t}, w,t),\, \beta_{t}I) \\[5pt] &= \nabla_{z_{t}} \log \mathcal{N}(z_{t} \,|\, \sqrt{1- \beta_{t}}\,\hat{z}_{t-1},\, \beta_{t}I) \end{align*}$$ where $$\hat{z}_{t-1} = \mathbb{E}_{w }\left[  Z_{t-1}|z_{t}, w \right]$$
>  
>So the **simplified objective** for ELBO is equivalent to the following **score matching objective**
>$$
>\begin{align*}
>&\sum_{t=2}^{T}\mathbb{E}_{ z_{t} }\left[  \left\lVert s(z_{t}, w, t)  - \hat{\epsilon}_{t}  \right\rVert^2  \right] \\[5pt]
>&=\sum_{t=2}^{T}\mathbb{E}_{  z_{t} }\left[  \left\lVert s(z_{t}, w, t)  + \frac{z_{t} -\sqrt{1- \beta_{t}}\,z_{t-1}}{\beta_{t}}   \right\rVert^2  \right] \\[5pt]
>&= \sum_{t=2}^{T}\mathbb{E}_{  z_{t} }\left[  \left\lVert \nabla_{z_{t}} \log \mathcal{N}(z_{t} \,|\, \sqrt{1- \beta_{t}}\,\hat{z}_{t-1}, \beta_{t}I)  - \nabla_{z_{t}} \log \mathcal{N}(z_{t} \,|\, \sqrt{1- \beta_{t}}\,z_{t-1}, \beta_{t}I)  \right\rVert^2  \right] \\[5pt]
>&= \sum_{t=2}^{T}\mathbb{E}_{  z_{t} }\left[  \left\lVert \text{ score(forward process | denoised image) }  - \text{ score(forward process | true image) } \right\rVert^2  \right] \\[5pt]
>\end{align*}
>$$   

- [[Conditional Expectation]]
- [[Minimum Mean Square Estimation]]


## Explanation

>[!info]
>By comparison, we see that the **denoising diffusion probabilistic model** learns the decoder (diffusion network) by continuously *matching*
>- the *score* of **denoised image** from the **model-based** *reverse diffusion process*, and 
>- the *score* of **corrupted image** from the **data-driven** *forward difussion process*
>
>under a **different level of noise variance** (continuously changing through time.)
>
>$$
>\begin{CD}
> x \to \ldots @>>> z_{t-1} @> +\hat{\epsilon}_{t} \sim \mathcal{N} >> z_{t}  \\ 
> @.  @VVV  @| \\ 
> @.  \hat{z}_{t-1} @<< s(z_{t}, w, t) < z_{t}  \\ 
>\end{CD}
>$$ 





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