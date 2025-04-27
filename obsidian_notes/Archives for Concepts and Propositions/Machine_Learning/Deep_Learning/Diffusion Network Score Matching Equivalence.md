---
tags:
  - concept
  - machine_learning/models
  - deep_learning/generative_models
  - math/differential_equation
  - math/stochastic_process
  - score_matching
  - diffusion_network
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

>[!info] 
>Recall that for **denoising diffusion probabilistic models (DDPM)**, the **forward diffusion kernel** for DDPM is given by $$q(z_{t} | x) = \mathcal{N}(z_{t}\;|\; \sqrt{ \alpha_{t} }x,\, (1-\alpha_{t})I )$$ where $$z_{t} = \sqrt{ \alpha_{t} }x + \sqrt{ 1- \alpha_{t} }\epsilon_{t}$$


![[Denoising Diffusion Probabilistic Models and Diffusion Network#^bf4525]]

- [[Denoising Diffusion Probabilistic Models and Diffusion Network]]

### Denoising Score Matching

![[Score Matching and Denoising Score Matching#^bbecdb]]

- [[Score Matching and Denoising Score Matching]]

### DDPM as DSM

>[!important] Definition
>Consider the *forward diffusion process* in *DDPM* as the **corruption process** and **diffusion kernel** defines a **noise kernel** as $$K_{\alpha_{t}}(x, z_{t}) := q(z_{t}\,|\,x) = \mathcal{N}(z_{t}\,|\, \sqrt{ \alpha_{t} }x,\, (1-\alpha_{t})\,I )$$
>
>The **(marginal) distribution** or **smoothed data density** of corrupted data $z_{t}$ at time $t$ is given by $$q(z_{t}) = \int q(z_{t}\,|\,x)\,p_{\text{data}}(x)\,dx.$$
>
>The **score matching algorithm** minimizes the mean squared error between a **model score network** $s(z_{t}, w, t)$ and the *smoothed data density*
>$$
>\mathcal{L}(w) := \frac{1}{2} \mathbb{E}_{ t\sim \mathcal{U}([T]) }\mathbb{E}_{ Z_{t} \sim q(z_{t}) }\left[ \lVert s(Z_{t}, w, t) -  \nabla_{z_{t}} \log q(Z_{t}) \rVert_{2}^2  \right] 
>$$
>- However, $q(z_{t})$ is **intractable**. Thus we *replace* it with the *diffusion kernel* $q(z_{t}|x)$
>
>This leads to the **denoising score matching (DSM)** objective functoin
>$$
>\begin{align}
>\mathcal{L}_{\text{DSM}}(w) &:= \frac{1}{2}\mathbb{E}_{ t\sim \mathcal{U}([T]) }\left[\mathbb{E}_{x \sim \mathcal{D} }\left[ \mathbb{E}_{ Z_{t} \sim q(\cdot|x) }\left[ \lVert s(Z_{t}, w, t) -  \nabla_{z_{t}} \log q(Z_{t}\,|\,x) \rVert_{2}^2  \right] \right] \right]
>\end{align}
>$$
>Note that  
>- $$\nabla_{z_{t}} \log q(z_{t}\,|\,x) = - \frac{z_{t} - \sqrt{ \alpha_{t} }x}{1- \alpha_{t}} := -\frac{1}{\sqrt{ 1- \alpha_{t} }}\,\epsilon_{t}$$ where $$z_{t} = \sqrt{ \alpha_{t} }x + \sqrt{ 1- \alpha_{t} }\epsilon_{t}, \quad \epsilon_{t}\sim \mathcal{N}(0,I)$$
>
>So the **DSM objective function** can be reformulated as 
>$$
>\begin{align}
>\mathcal{L}_{\text{DSM}}(w) &:= \frac{1}{2}\mathbb{E}_{ t\sim \mathcal{U}([T]) }\left[\mathbb{E}_{x \sim \mathcal{D} }\left[ \mathbb{E}_{ \epsilon_{t} \sim \mathcal{N}(0,I) }\left[ \left\lVert s\left(\sqrt{ \alpha_{t} }x + \sqrt{ 1- \alpha_{t} }\epsilon_{t}, w, t\right) + \frac{1}{\sqrt{ 1 - \alpha_{t} }}\epsilon_{t} \right\rVert_{2}^2  \right] \right] \right] \\[10pt]
> &=\frac{1}{2} \mathbb{E}_{ t\sim \mathcal{U}([T]) }\left[\mathbb{E}_{x \sim \mathcal{D} }\left[ \mathbb{E}_{ \epsilon_{t} \sim \mathcal{N}(0,I) }\left[ \frac{1}{1- \alpha_{t}}\,\left\lVert g\left(\sqrt{ \alpha_{t} }x + \sqrt{ 1- \alpha_{t} }\epsilon_{t}, w, t\right) -  \epsilon_{t} \right\rVert_{2}^2  \right] \right] \right]
>\end{align}
>$$
>where the **score network** from **DSM** and the **noise network** from **DDPM** have the following relation
>$$
>s\left(z_{t}, w, t\right) := - \frac{1}{\sqrt{ 1 - \alpha_{t} }}g(z_{t}, w, t)
>$$
>- This is exactly the **simplified ELBO objective** for **DDPM**
>- The exact **ELBO objective** of **DDPM** corresponds to the **weighted combinations** of *multiple DSMs*, i.e. $$\begin{align} \mathcal{L}(w; T) &= \frac{1}{2}\sum_{t=1}^{T}\mathbb{E}_{x \sim \mathcal{D} }\left[ \mathbb{E}_{ \epsilon_{t} \sim \mathcal{N}(0,I) }\left[ \frac{\lambda_{t}}{1- \alpha_{t}}\,\left\lVert g\left(\sqrt{ \alpha_{t} }x + \sqrt{ 1- \alpha_{t} }\epsilon_{t}, w, t\right) -  \epsilon_{t} \right\rVert_{2}^2  \right] \right] \\[5pt] &= \sum_{t=1}^{T}\lambda_{t}\,\mathcal{L}_{\text{DSM}}(w) \end{align}$$ where $$\lambda_{t} := \frac{\beta_{t}}{(1 - \beta_{t})}$$

^2dd27e

- [[Score Matching and Denoising Score Matching]]
- [[Markov Chain and Markov Process]]
- [[Markov Transition Kernel and Transition Function]]





## Explanation

>[!info]
>The **score network** $s(z, w, t)$ can be find in the formulation of mean function 
>$$\mu(z_{t}, w,t) = \frac{1}{\sqrt{ 1 - \beta_{t} }}\left[ z_{t} - \frac{\beta_{t}}{\sqrt{ 1 - \alpha_{t} }} g(z_{t}, w, t) \right] $$
>- $s(z, w, t)$  can be seen as the **Stein score function** for *forward transition* when the *corrupted image* $z_{t-1}$ is replaced by the *denoised image* $\hat{z}_{t-1}$ $$\begin{align*} s(z_{t}, w, t) :=  -\frac{1}{\sqrt{ 1 - \alpha_{t} }} g(z_{t}, w, t) &= - \frac{z_{t} -\sqrt{1- \beta_{t}}\,\mu(z_{t}, w,t)}{\beta_{t}} \\[5pt] &= \nabla_{z_{t}} \log \mathcal{N}(z_{t}\;|\; \sqrt{1- \beta_{t}}\,\mu(z_{t}, w,t),\, \beta_{t}I) \\[5pt] &= \nabla_{z} \log p(z_{t} | \sqrt{1- \beta_{t}}\,\hat{z}_{t-1}, \beta_{t}I) \end{align*}$$ where $$\hat{z}_{t-1} = \mu(z_{t}, w,t)$$


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


## Score Matching from Continuous-Time Diffusion Model
 ![[Continuous-Time Diffusion Network via Stochastic Differential Equations#^e99b7e]]


>[!important]
>The **reverse SDE** for diffusion network is given by
>$$dz_{t} = \left[f(z_{t},t) - \sigma^2(t)\,\nabla_{x} \log q(z_{t})\right]\,dt + \sigma(t)\,d\widehat{W}_{t}$$
>where the **drift term** can be interpreted as the **score matching** between 
>- the forward drift term $f(z_{t},t)$ and
>- the **score function of marginal** $$\nabla_{x} \log q(z_{t})$$ 
>  
>Ideally, we want to learn the **score function** $s(z_{t}, w, t)$ directly via regression 
>$$
>\min_{w}\;\mathbb{E}_{ t,\, Z_{t}\sim q(z_{t}) }\left[ \lVert s(Z_{t}, w, t) - \nabla_{x} \log q(Z_{t}) \rVert_{2}^2  \right]
>$$  
>but the unconditioned marginal is *intractable*.
>
>Instead, we use the *conditional reversal kernel* $$q(z_{t}|x) = \mathcal{N}(z_{t}\,|\,\gamma_{t}\,x,\, \sigma_{t}^2I)$$ as the **score of diffused data sample**. Thus, the **denoising score matching** corresponds to the solution of the following optimization
>$$
>\min_{w}\;\mathbb{E}_{ t, \,x\sim \mathcal{D},\,  Z_{t}\sim q(\cdot|x) }\left[ \lVert s(Z_{t}, w, t) - \nabla_{x} \log q(Z_{t}\,|\,x) \rVert_{2}^2  \right]
>$$  
>- This is the same as the discrete-time case.

- [[Continuous-Time Diffusion Network via Stochastic Differential Equations]]





-----------
##  Recommended Notes and References

- [[Denoising Diffusion Probabilistic Models and Diffusion Network]]


- [[Gaussian Random Vector]]
- [[Diffusion Process]]
- [[Markov Chain and Markov Process]]
- [[Time-Reversible Markov Chain]]
- [[Markov Transition Kernel and Transition Function]]
- [[Artificial Neural Network and Deep Learning]]
- [[Conditional Expectation]]
- [[Minimum Mean Square Estimation]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 864 - 867
- [[Deep Learning Foundations and Concepts by Bishop]] pp 581 - 603
- Torralba, A., Isola, P., & Freeman, W. T. (2024). _Foundations of Computer Vision_. The MIT Press. pp 484 - 487
- **CVPR 2023 Tutorial**: [link](https://cvpr2023-tutorial-diffusion-models.github.io);
	- [Youtube recording](https://www.youtube.com/watch?v=1d4r19GEVos)
- Song, Y., & Ermon, S. (2019). Generative modeling by estimating gradients of the data distribution. _Advances in neural information processing systems_, _32_.
- Song, Y., Sohl-Dickstein, J., Kingma, D. P., Kumar, A., Ermon, S., & Poole, B. (2020). Score-based generative modeling through stochastic differential equations. _arXiv preprint arXiv:2011.13456_.