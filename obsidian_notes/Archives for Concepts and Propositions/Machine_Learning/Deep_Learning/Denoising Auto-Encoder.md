---
tags:
  - concept
  - machine_learning/models
  - deep_learning/generative_models
  - deep_learning/representation_learning
keywords:
  - autoencoder
  - representation_learning
  - denoising_autoencoder
topics:
  - representation_learning
name: Denoising Auto-Encoder
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Denoising Auto-Encoder

![[Auto-Encoder and Stochastic Auto-Encoder#^53810a]]

- [[Auto-Encoder and Stochastic Auto-Encoder]]

>[!important] Definition
>Let $X_{i}$ be $n$ i.i.d samples from unknown distribution and $\widetilde{X}_{i}$ be a copy of $X_{i}$ that has been **corrupted** by some *noise*. $$\widetilde{X}_{i} \sim K(X_{i}, \widetilde{X}_{i})$$
>
>The **denoising autoencoder (DAE)** learns both *encoder function* $f$ and *decoder function* $g$ that minimize the *reconstruction error* between 
>$$
>\min_{f, g}\sum_{i=1}^{n}L(X_{i} , g(f(\widetilde{X}_{i})) ) 
>$$   
>where $L: \mathbb{R}^{d} \times \mathbb{R}^{d} \to \mathbb{R}$ is the loss function that measures the *similarity* between the *input* and the *reconstructed input* from *corrupted copy*.

^e81e41

- [[Auto-Encoder and Stochastic Auto-Encoder]]
- [[Markov Transition Kernel and Transition Function]]


### Training DAE via MLE

>[!important] Definition
>The **training procedure** of **denoising autoencoder (DAE)** to learn a **reconstruction distribution** $$p_{\text{reconstruction}}(x | \tilde{x})$$ is described as below:
>- *Require*: training data $\mathcal{D}:= \{ X_{i}, i=1\,{,}\ldots{,}\,n \}$
>- *Require*: a *corruption process*, described by transition kernel $K(X, \widetilde{X}) = \mathcal{P}(\widetilde{X}\,|\, X)$
>- **Sample** a training minibatch $$B^{(s)} := \left\{ X_{i}^{(s)}\,|\; i=1\,{,}\ldots{,}\,n_{s} \right\}$$ from training data $\mathcal{D}$
>- **Sample** a *corrupted version* of minibatch $$\widetilde{X}_{i} \sim \mathcal{P}(\widetilde{X}\,|\, X_{i}), \quad i=1\,{,}\ldots{,}\,n_{s}$$
>- **Learn** the *autoencoder reconstruction distribution* $$p_{\text{reconstruction}}(x | \tilde{x}) = p_{\text{decoder}}(x | h)$$ with the pair of minibatch $\{(X_{i}, \widetilde{X}_{i} ): i=1\,{,}\ldots{,}\,n_{s}  \}$ where
>	-  $h$ is the output of the **encoder**$$h = f( \tilde{x})$$
>	- and $p_{\text{decoder}}$ is defined by the **decoder** $$p_{\text{decoder}}(x | h) = g(h)$$

>[!important] Definition
>The **objective function** for training DAE is defined via the *maximum likelihood estimation* 
>$$
>\min_{f, p_{\text{decoder}}} \sum_{i=1}^{n} \mathbb{E}_{ \widetilde{X}_{j} \sim \mathcal{P}(\widetilde{X}\,|\, X_{i}) }\left[  -\log p_{\text{decoder}}\left(X_{i}\;|\; h = f(\widetilde{X}_{j})\right)  \right]  
>$$

- [[Maximum Likelihood Estimation]]

### Denoising Score Matching

![[Score Matching and Denoising Score Matching#^bbecdb]]

- [[Score Matching and Denoising Score Matching]]

## Explanation

![[denoising_autoencoder_data_manifold.png]]


## Stochastic Autoencoder

- [[Auto-Encoder and Stochastic Auto-Encoder#Stochastic Auto-Encoder]]







## Vector Field

![[denoising_autoencoder_vector_field.png]]





-----------
##  Recommended Notes and References


- [[Latent Variable Models]]
- [[Artificial Neural Network and Deep Learning]]

- [[Principal Component Analysis]]
- [[Probabilistic Principle Component Analysis]]
- [[Factor Analysis]]

- [[Denoising Diffusion Probabilistic Models and Diffusion Network]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
- [[Deep Learning by Goodfellow]] pp 496 - 498, 501 - 505 
- [[Deep Learning Foundations and Concepts by Bishop]] pp 567 - 568