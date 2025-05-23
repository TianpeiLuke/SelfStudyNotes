---
tags:
  - concept
  - machine_learning/models
  - deep_learning/generative_models
  - math/game_theory
  - generative_adversarial_network
  - f_divergence
  - f_gan
  - f_generative_adversarial_network
  - f-GAN
keywords:
  - generative_adversarial_network
  - f_divergence
  - f_gan
topics:
  - deep_learning/generative_models
  - game_theory
name: f-Generative Adversarial Network
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: f-Generative Adversarial Network

### Training Objective

![[Variational Formula for f-Divergence#^9e3cf2]]

![[Principle of Learning by Comparison for Implicit Generative Models#^ebcbb0]]

>[!important] Definition
>Let $p^{*}$ be the unknown true data distribution, and $q_{\theta}$ is a distribution from **generative model** $\mathcal{P}_{\Theta}.$
>
>Let $X$ and $X'$ be samples generated by true data distribution $p^{*}$ and *generative model* $q_{\theta}$
>$$
>X\sim p^{*}, \quad X' = g_{\theta}(Z) \sim q_{\theta}(Z),\; Z\sim p(z)
>$$
>
>At iteration $t$, the *training* for **$f$-Generative Adversarial Network ($f$-GAN)** consists of two sub-routines
>- Given $\theta^{(t-1)}$,  training of **discriminator** or **critic** $D_{\psi}$ for $K$ steps via 
>$$
>\begin{align*}
>\psi &= \arg\max_{\psi}\left\{ \mathbb{E}_{p^{*}}\left[ D_{\psi}(X)   \right] -  \mathbb{E}_{Z\sim p(z)}\left[ f^{*}\left( D_{\psi}(g_{\theta^{(t-1)}}(Z)) \right) \right]  \right\} 
> \end{align*}
>$$ 
>where $f^{*}$ is the *convex-conjugat* of *convex function* $f$
>- Given $\psi^{(t)}$,  training of **generator** or *generative model* $g_{\theta}$ via 
>$$
>\begin{align*}
>\theta &= \arg\min_{\theta}\left\{ \mathbb{E}_{p^{*}}\left[ D_{\psi^{(t)}}(X)   \right] -  \mathbb{E}_{Z\sim p(z)}\left[ f^{*}\left( D_{\psi^{(t)}}(g_{\theta}(Z)) \right) \right]  \right\}
> \end{align*}
>$$
>

- [[Principle of Learning by Comparison for Implicit Generative Models]]
- [[f-Divergence]]
- [[Variational Formula for f-Divergence]]
- [[Monte Carlo and Applications]]
- [[Generative Adversarial Network]]

### Game Perspective

>[!important] Defintion
>The *training objective* for **$f$-GAN** can be seen as a **two-player zero-sum game** where the two players are
>1. the **discriminator** or **critic**, whose objective is 
>$$
>\begin{align*}
>\psi &= \arg\max_{\psi}\left\{\mathbb{E}_{p^{*}}\left[ D_{\psi}(X)   \right] -  \mathbb{E}_{Z\sim p(z)}\left[ f^{*}\left( D_{\psi}(g_{\theta}(Z)) \right) \right]    \right\} 
> \end{align*}
>$$
>2. the **generator**, whose objective is 
>$$
>\begin{align*}
>\theta &= \arg\min_{\theta}\left\{\mathbb{E}_{p^{*}}\left[ D_{\psi}(X)   \right] -  \mathbb{E}_{Z\sim p(z)}\left[ f^{*}\left( D_{\psi}(g_{\theta}(Z)) \right) \right]   \right\} 
> \end{align*}
>$$
>
>The overall **value** of **min-max game** is bounded above by the **minimal $f$-divergence**
>$$
>\begin{align*}
>V(\theta^{*}, \psi^{*})&:= \min_{\theta}\max_{\psi}\left\{ \mathbb{E}_{p^{*}}\left[ D_{\psi}(X)   \right] -  \mathbb{E}_{Z\sim p(z)}\left[ f^{*}\left( D_{\psi}(g_{\theta}(Z)) \right) \right]  \right\} \\[5pt]
>&\le \min_{\theta}\mathbb{D}_{f}\left( p^{*} \left\|\right. q_{\theta} \right) 
> \end{align*}
>$$
>- Thus the $\theta^{*}$ that *minimize the $f$-divergence* is the **Nash equilibrium** $\theta^{*}$

^ebb70c

- [[Von Neumann Min-Max Theorem]]
- [[Two-Player Finite Game and Matrix Representation]]
- [[Jensen-Shannon Divergence]]

## Explanation

![[Density Ratio Estimation via Binary Classifiers#^4f1f3a]]

- [[Density Ratio Estimation via Binary Classifiers]]

![[divergence_vs_ipm.png]]

>[!quote]
>While the definition of $f$-divergences relies on *density ratios* (Equation (26.21)), we have seen that to train *implicit generative models* we use **approximations** to those divergences obtained using a parametric critic $D_{\psi}.$ 
>
>- If the function *family of the critic* used to approximate the divergence (via the bound or class probability estimation) contains *only smooth functions*, it will not be able to model the **sharp true density ratio**, which jumps from $0$ to $\infty$, but it can provide a **smooth approximation**. 
>- We show an example in Figure 26.4b, where we show the density ratio for two distributions **without overlapping support** and an **approximation** provided by an MLP trained to approximate the KL divergence using Equation 26.25. 
>	- Here, the smooth decision surface provided by the MLP can be used to train a generative model while the underlying KL divergence cannot be; 
>	- the learned *MLP* provides the gradient signal on how to *move distribution mass* to areas with **more density** under the data distribution, while the *KL divergence* provides a *zero gradient* almost everywhere in the space. 
>- This ability of approximations to $f$-divergences to **overcome non-overlapping support issues** is a desirable property of generative modeling training criteria, as it allows models to learn the data distribution regardless of initialization [Fed+18]. 
>- Thus while the case of non-overlapping support provides an important theoretical difference between IPMs and f -divergences, it is less significant in practice since bounds on $f$-divergences or class probability estimation are used with smooth critics to approximate the underlying divergence.
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 893 - 894




-----------
##  Recommended Notes and References



- [[Artificial Neural Network and Deep Learning]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 883 - 914
- [[Deep Learning Foundations and Concepts by Bishop]] pp 533 - 544
- [[Deep Learning by Goodfellow]] pp 679, 690
- [[Foundations of Computer Vision by Torralba]] pp 487 - 489