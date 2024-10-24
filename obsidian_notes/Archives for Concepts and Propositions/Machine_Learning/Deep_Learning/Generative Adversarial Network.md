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

### Generative Adversarial Networks

![[generative_adversarial_network.png]]




## Explanation





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