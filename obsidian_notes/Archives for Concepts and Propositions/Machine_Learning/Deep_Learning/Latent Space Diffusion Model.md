---
tags:
  - concept
  - deep_learning/generative_models
  - diffusion_models
  - latent_space_diffusion_models
  - latent_diffusion_model
keywords: 
topics: 
name: 
date of note: 2024-10-20
---

## Concept Definition

>[!important]
>**Name**: Latent Space Diffusion Model

>[!important] Definition
>The **Latent Diffusion Model (LDM)** is a generative model that 
>- learns to perform *denoising diffusion* 
>- not directly in the high-dimensional data space (e.g., pixel space for images), but instead in a *lower-dimensional latent space* produced by a pretrained encoder (such as a VAE).

- [[Variational Auto-Encoder]]
- [[Denoising Diffusion Probabilistic Models and Diffusion Network]]

![[latent_diffusion_model.png]]


### Training Algorithm

>[!info]
>During training, LDM 
>- first encodes input data into *latent representations* 
>- and then applies a *forward diffusion process* by gradually adding Gaussian noise to these latents. 
>- A denoising network is trained to *reverse this process* by predicting the noise added at each timestep.


>[!important] Definition
>The **training algorithm** for the **Latent Space Diffusion Model (LDM)** solves the regression problem 
>$$
>\min_{w} \hat{\mathcal{L}}(w) = \min_{w} \mathbb{E}_{ t \sim \mathcal{U}([T]) }\left[\mathbb{E}_{x \sim \mathcal{D} }\left[ \mathbb{E}_{ \epsilon_{t} \sim \mathcal{N}(0,I) }\left[ \left\lVert g\left( \sqrt{ \alpha_{t} } z(x) + \sqrt{ 1- \alpha_{t} }\epsilon_{t}, w, t\right) - \epsilon_{t} \right\rVert_{2}^2 \right] \right] \right]
>$$
>where $z(x)$ is the **latent encoding** of input $x$.
>
>The training process is described as below:
>- *Require*: training data $\mathcal{D}$
>- *Require*: a **frozen encoder** $z: \mathcal{X} \to \mathcal{Z}$ that maps input data $x$ to a latent representation $z(x)$
>- *Require*: a sequence of **noise schedule** $\{ \beta_{t} \}_{t=1}^{T}$ where $$\beta_{1} < \beta_{2} \,{<}\ldots{<}\,\beta_{T} < 1$$
>- Set $\alpha_{0} = 1$
>- For $t=1\,{,}\ldots{,}\,T$:
>	- Compute the parameter $\alpha_{t}$ for **$t$-step transition kernel** $q(z_{t}|z(x))$ as
>	  $$
>	  \alpha_{t} = (1 - \beta_{t})\,\alpha_{t-1}
>	  $$
>- While not *convergence*:
>	- Sample *input data* $x\sim \mathcal{D}$
>	- Encode input to latent space $$z_{0} = z(x)$$
>	- Sample the **time-step of diffusion chain** $$t \sim \text{Uniform}\{1, \ldots, T\}$$
>	- Sample **noise vector** from standard normal distribution $$\epsilon_{t} \sim \mathcal{N}(0,I)$$
>	- Generate **latent variable** $Z_{t}$ based on the *$t$-step noisy transition*:
>	  $$
>	  Z_{t} = \sqrt{ \alpha_{t} }\,z_{0} + \sqrt{ 1- \alpha_{t} }\,\epsilon_{t}
>	  $$
>	- Set the *loss function* as
>	  $$
>	  \hat{\mathcal{L}}(w) = \left\lVert g(Z_{t}, w, t) - \epsilon_{t} \right\rVert_{2}^2
>	  $$
>	  where $g(Z_{t}, w, t)$ is the *latent denoising decoder*.
>	- Take optimization step based on *stochastic gradient descent*:
>	  $$
>	  w \leftarrow w - \eta \nabla \hat{\mathcal{L}}(w)
>	  $$
>- *Return*: decoder network parameter $w$

- [[Denoising Diffusion Probabilistic Models and Diffusion Network#Training Algorithm]]
- [[Stochastic Gradient Descent Algorithm]]
- [[Adam Algorithm]]

### Sampling Algorithm and Reverse Pass

>[!info]
>At sampling time, LDM 
>- generates random noise in the *latent space*, 
>- progressively denoises it, and 
>- finally *decodes* the cleaned latent back into the data space using the fixed decoder.


>[!important] Definition
>The **sampling algorithm** for the **Latent Space Diffusion Model (LDM)** generates samples by reversing the learned denoising process:
>
>- *Require*: trained *decoder network* $g(z, w, t)$ with learned parameters $w$
>- *Require*: a sequence of **noise schedule** $\{ \beta_{t} \}_{t=1}^{T}$ where $$\beta_{1} < \beta_{2} \,{<}\ldots{<}\,\beta_{T} < 1$$
>- Set $\alpha_{0} = 1$
>- For $t = 1\,{,}\ldots{,}\,T$:
>	- Compute the parameter $\alpha_{t}$ for **$t$-step transition kernel** as
>	  $$
>	  \alpha_{t} = (1 - \beta_{t})\,\alpha_{t-1}
>	  $$
>- **Initialize** latent variable $Z_{T}$ by sampling from the standard normal distribution:
>  $$
>  Z_{T} \sim \mathcal{N}(0,I)
>  $$
>- For $t = T, T-1, \ldots, 1$ (reverse diffusion):
>	- Predict the noise component $$\hat{\epsilon}_{t} = g(Z_{t}, w, t)$$
>	- Estimate the denoised latent variable:
>	  $$
>	  \hat{z}_{0} = \frac{1}{\sqrt{\alpha_{t}}}\left( Z_{t} - \sqrt{1-\alpha_{t}} \, \hat{\epsilon}_{t} \right)
>	  $$
>	- If $t > 1$:
>		- Sample Gaussian noise $$\epsilon' \sim \mathcal{N}(0,I)$$
>		- Generate the next latent variable $Z_{t-1}$:
>		  $$
>		  Z_{t-1} = \sqrt{\alpha_{t-1}} \, \hat{z}_{0} + \sqrt{1-\alpha_{t-1}} \, \epsilon'
>		  $$
>	- Else ($t = 1$):
>		- Set
>		  $$
>		  Z_{0} = \hat{z}_{0}
>		  $$
>- *Decode* the final latent variable $Z_{0}$ into the data space using the **frozen decoder** $\text{Dec}(\cdot)$:
>  $$
>  \hat{x} = \text{Dec}(Z_{0})
>  $$
>- *Return*: generated sample $\hat{x}$

- [[Denoising Diffusion Probabilistic Models and Diffusion Network#Reversed Pass and Sampling Procedure]]

|Step|Description|
|---|---|
|Initialize|Sample random noise in latent space|
|Reverse Diffusion|Denoise step-by-step using the trained model|
|Final Step|Decode the clean latent $Z_0$ back into the pixel space|



## Explanation

>[!info]
>- **LDM** operates entirely in the *compressed latent space* during sampling, making it *much faster* and *memory efficient* compared to pixel-space DDPMs.
>  
>- The **decoder $\text{Dec}(\cdot)$** is typically a powerful pretrained **VAE decoder** or **autoencoder decoder** that maps latent representations back to full-resolution images.

>[!info]
>This approach significantly improves *computational efficiency* while maintaining *high generation quality*, enabling fast and scalable synthesis of complex data like high-resolution images.

### Compare with DDPM

| Aspect                | **DDPM**                   | **Latent Diffusion Model (LDM)**                          |
| --------------------- | -------------------------- | --------------------------------------------------------- |
| Diffusion happens in  | Pixel space (image domain) | **Latent space** (compressed lower-dimensional embedding) |
| Encoder needed?       | No                         | ✅ Yes, frozen encoder $z(x)$                              |
| Purpose               | Direct generation          | Faster, scalable generation with high resolution          |
| Typical training data | Raw images                 | Latent encodings of images                                |






-----------
##  Recommended Notes and References


- [[Latent Variable Models]]
- [[Factor Analysis]]
- [[Gaussian Process Latent Variable Model]]



- [[Diffusion Network Score Matching Equivalence]]
- [[Continuous-Time Diffusion Network via Stochastic Differential Equations]]
- [[Score Matching and Denoising Score Matching]]

- [[Evidence Lower Bound]]


- [[Artificial Neural Network and Deep Learning]]
- [[Stochastic Differential Equations]]
- [[Markov Chain and Markov Process]]
- [[Time-Reversible Markov Chain]]
- [[Markov Transition Kernel and Transition Function]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 874 - 875
- **CVPR 2023 Tutorial**: [link](https://cvpr2023-tutorial-diffusion-models.github.io);
	- [Youtube recording](https://www.youtube.com/watch?v=1d4r19GEVos)