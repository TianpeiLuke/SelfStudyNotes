---
tags:
  - concept
  - deep_learning/generative_models
  - statistics/monte_carlo_simulation
keywords: 
topics: 
name: 
date of note: 2024-11-08
---

## Concept Definition

>[!important]
>**Name**: Monte Carlo Simulation vs Generative Adversarial Network

>[!quote]
>To develop a probabilistic formulation for GANs, it is useful to first distinguish between two types of probabilistic models: “**prescribed probabilistic models**” and “**implicit probabilistic models**” [DG84]. 
>- **Prescribed probabilistic models**, which we will call **explicit probabilistic models**, provide an explicit parametric specification of the distribution of an observed random variable $x$, specifying a *log-likelihood function* $\log q_{\theta}(x)$ with parameters $\theta$. Most models we encountered in this book thus far are of this form, whether they be state-of-the-art classifiers, large-vocabulary sequence models, or fine-grained spatio-temporal models. 
>- Alternatively, we can specify an **implicit probabilistic model** that defines a *stochastic procedure* to *directly generate data*. Such models are the natural approach for problems in climate and weather, population genetics, and ecology, since the mechanistic understanding of such systems can be used to *directly describe the generative model*. We illustrate the difference between implicit and explicit models in Figure 26.1.
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 883


### Monte Carlo Simulation by Explicit Generative Model

![[Fundamental Theorem of Simulation#^640e95]]


- [[Fundamental Theorem of Simulation]]
- [[Importance Sampling]]
- [[Markov Chain Monte Carlo Methods]]

- [[Metropolis-Hastings Algorithm]]
- [[Gibbs Sampling]]
- [[Gibbs Sampling for Graphical Model]]


- [[Hamiltonian Monte Carlo]]
- [[Langevin Dynamics and Langevin Sampling]]

### Adversarial Simulation from Implicit Generative Models

![[Principle of Learning by Comparison for Implicit Generative Models#^1fd0d6]]

![[Principle of Learning by Comparison for Implicit Generative Models#^d5e48f]]


- [[Principle of Learning by Comparison for Implicit Generative Models]]
- [[Generative Adversarial Network]]
- [[f-Generative Adversarial Network]]
- [[Variational Formula for f-Divergence]]
- [[Wasserstein Generative Adversarial Network]]
- [[Variational Representation of Wasserstein Distance]]
- [[Maximum Mean Discrepancy between Probability Measures via RKHS]]
- [[Kernel Mean Embedding of Distribution]]




## Explanation





-----------
##  Recommended Notes and References


- [[Monte Carlo and Applications]]
- [[Markov Chain Monte Carlo Methods]]
- [[Principle of Learning by Comparison for Implicit Generative Models]]

- [[f-Divergence]]
- [[Wasserstein Distance]]
- [[Density Ratio Estimation via Binary Classifiers]]