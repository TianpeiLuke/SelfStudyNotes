---
tags:
  - concept
  - machine_learning/models
  - deep_learning/generative_models
  - math/game_theory
keywords:
  - generative_adversarial_network
topics:
  - deep_learning/generative_models
  - game_theory
name: Generative Adversarial Network
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Generative Adversarial Network

### Implicit Probabilistic Models

>[!quote]
>To develop a probabilistic formulation for GANs, it is useful to first distinguish between two types of probabilistic models: “**prescribed probabilistic models**” and “**implicit probabilistic models**” [DG84]. 
>- **Prescribed probabilistic models**, which we will call **explicit probabilistic models**, provide an explicit parametric specification of the distribution of an observed random variable $x$, specifying a *log-likelihood function* $\log q_{\theta}(x)$ with parameters $\theta$. Most models we encountered in this book thus far are of this form, whether they be state-of-the-art classifiers, large-vocabulary sequence models, or fine-grained spatio-temporal models. 
>- Alternatively, we can specify an **implicit probabilistic model** that defines a *stochastic procedure* to *directly generate data*. Such models are the natural approach for problems in climate and weather, population genetics, and ecology, since the mechanistic understanding of such systems can be used to *directly describe the generative model*. We illustrate the difference between implicit and explicit models in Figure 26.1.
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 883

>[!important] Definition
>**Implicit generative models** do not include a *likelihood function* or *observation model*. 
>- Instead, the *generating procedure* defines a valid *density* on the *output space* that forms an effective likelihood function: $$X = G_{\theta}(Z), \quad Z \sim \mathcal{P}$$ where $G_{\theta}$ is the *cumulative distribution function* of $X$ with respect to measure $\mathcal{P}$.
>- The p.d.f. of $X$ is given by $$p_{X}(x) = \frac{\partial}{ \partial x^{1}}\,{}\ldots{}\,\frac{\partial}{ \partial x^{d}}\int_{z: G_{\theta}(z) \le x}\,p_{Z}(z)\,dz$$
>	- We can use neural network to approximate $G_{\theta}$. 
>	- Such models are sometimes called **generator networks** or **generative neural samplers**; they can also be throught of as **differentiable simulators**.
>- The problem of learning an intractable implicit generative model is called **likelihood-free inference** or **simulation-based inference**.

- [[Fundamental Theorem of Simulation]]
- [[Cumulative Distribution Function of Random Variable]]
- [[Quantile Function]]

### Principle of Learning by Comparison

![[Principle of Learning by Comparison for Implicit Generative Models#^d5e48f]]

- [[Principle of Learning by Comparison for Implicit Generative Models]]



### Generative Adversarial Networks

![[generative_adversarial_network.png]]




## Explanation

>[!info]
>Compared to **explicit generative models** such as 
>- [[Gaussian Process]]
>- [[Factor Analysis]]
>- [[Variational Auto-Encoder]]
>- [[Denoising Diffusion Probabilistic Models and Diffusion Network]]
>- [[Normalizing Flows]]
>  
>the *Generative Adversarial Network (GAN)* do *not* need to know the **likelihood function** class before. Instead, it generate samples based on **simulation**.

- [[Monte Carlo and Applications]]

>[!info]
>*Likelihood-free inference* also forms the basis of the field known as **approximate Bayesian computation** or **ABC**.
>- Both approximate Bayesian and GAN rely on a learning principle based on **_comparing real and simulated data_**.
>  
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 884  








-----------
##  Recommended Notes and References

- [[Von Neumann Min-Max Theorem]]
- [[Wasserstein Distance]]
- [[Variational Representation of Wasserstein Distance]]
- [[Artificial Neural Network and Deep Learning]]
- [[Two-Player Finite Game and Matrix Representation]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 883
- [[Deep Learning Foundations and Concepts by Bishop]] pp 533 - 544
- [[Deep Learning by Goodfellow]] pp 679, 690
- [[Foundations of Computer Vision by Torralba]] pp 487 - 489