---
tags:
  - concept
  - machine_learning/models
  - deep_learning/generative_models
  - deep_learning/representation_learning
keywords:
  - autoencoder
  - representation_learning
  - stochastic_autoencoder
topics:
  - representation_learning
name: Auto-Encoder and Stochastic Auto-Encoder
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Auto-Encoder and Stochastic Auto-Encoder

>[!important] Definition
>An **autoencoder** is a neural network that is trained to attempt to copy its input to its output.
>
>It consists of two parts:
>- an **encoder function**  $f: \mathbb{R}^{d} \to \mathbb{R}^{s}$,  $$h = f(x)$$ where hidden layer $h\in \mathbb{R}^{s}$ describes a **code** represent the input. 
>- a **decoder function** $g: \mathbb{R}^{s} \to \mathbb{R}^{d}$, $$r = g(h)$$ where $r$ is the *reconstruction* of input.
>  
>The **autoencoder (AE)** learns both *encoder function* $f$ and *decoder function* $g$ that minimize the **reconstruction error** 
>$$
>\min_{f, g}\sum_{i=1}^{n}\lVert X_{i} - g(f(X_{i}))  \rVert_{2}^{2} 
>$$   
>In general, define a loss function $L: \mathbb{R}^{d} \times \mathbb{R}^{d} \to \mathbb{R}$ that measure the *similarity* between the *input* and the *reconstructed input*.
>$$
>\min_{f, g}\sum_{i=1}^{n}L(X_{i} , g(f(X_{i})) )
>$$   

^53810a

![[autoencoder.png]]

![[deep_autoencoder.png]]


### Stochastic Auto-Encoder

>[!important] Definition
>The **stochastic autoencoder** also consists of two parts
>- an **encoder distribution** $$h \sim p_{\text{encoder}}(h | x)$$
>- a **decoder distribution** $$r \sim p_{\text{decoder}}(x | h)$$
> 
>The goal of a stochastic autoencoder is to train a model that *maximize the likelihood function*
>$$
> - \sum_{i=1}^{n} p_{\text{decoder}}(X_{i} | h)
>$$

- [[Maximum Likelihood Estimation]]
- [[Variational Auto-Encoder]]

![[stochastic_autoencoder.png]]


### Score Matching

![[Score Matching and Denoising Score Matching#^6a12a8]]

- [[Score Matching and Denoising Score Matching]]


## Explanation

>[!quote]
>Copying the input to the output may sound useless, but we are typically not interested in the output of the decoder. Instead, we hope that training the autoencoder to perform the input copying task will result in h taking on useful properties.  
>
>One way to obtain useful features from the autoencoder is to constrain $h$ to have a *smaller dimension* than $x$. An autoencoder whose *code dimension is less than the input dimension* is called **undercomplete**. Learning an undercomplete representation forces the autoencoder to capture the most salient features of the training data.
>
>-- [[Deep Learning by Goodfellow]] pp 494

>[!info]
>In an autoencoder, $x$ is now the **target** as well as the **input**.



## Linear Autoencoder

![[Principle Component Analysis#^4f6696]]

![[Principle Component Analysis#^b1e550]]

>[!info]
>The above proposition shows that a **linear autoencoder** is equivalent to the **principle component analysis (PCA)**.

- [[Principle Component Analysis]]
- [[Probabilistic Principle Component Analysis]]

## Latent Variable Model

- [[Latent Variable Models]]
- [[Factor Analysis]]

## Sparse Autoencoder

![[Sparse Auto-Encoder and Regularized Auto-Encoder#^e81e41]]

- [[Sparse Auto-Encoder and Regularized Auto-Encoder]]

## Denoising Autoencoder

![[Denoising Auto-Encoder#^e81e41]]

- [[Denoising Auto-Encoder]]


## Variational Autoencoder

- [[Variational Auto-Encoder]]


## Other Models with Encoder-Decoder Architecture

### U-Net

- [[U-Net as Convolutional Autoencoder with Skip Connections]]

### Diffusion Network

- [[Denoising Diffusion Probabilistic Models and Diffusion Network]]

### Transformer Network

- [[Transformer Network]]
- [[Large Language Model and Pretrained Language Models]]
- [[Bidirectional Encoder Representation from Transformer or BERT]]
- [[Generative Pre-trained Transformer or GPT]]




-----------
##  Recommended Notes and References



- [[Variational Auto-Encoder]]
- [[Artificial Neural Network and Deep Learning]]

- [[Principle Component Analysis]]
- [[Probabilistic Principle Component Analysis]]



- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 635 - 636
- [[Deep Learning by Goodfellow]] pp 493 - 500
- [[Deep Learning Foundations and Concepts by Bishop]] pp 563 - 567