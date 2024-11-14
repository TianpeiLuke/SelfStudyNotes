---
tags:
  - concept
  - machine_learning/models
  - deep_learning/generative_models
keywords:
  - normalizing_flow_model
topics:
  - deep_learning/generative_models
name: Normalizing Flows Training
date of note: 2024-08-16
---

## Concept Definition

>[!important]
>**Name**: Normalizing Flows Training

![[Normalizing Flows#^294151]]

- [[Normalizing Flows]]
- [[Latent Variable Models]]
- [[Bijective Function and Inverse Function]]
- [[Probability Density Function of Random Variable]]
- [[Jacobian Matrix and Jacobian Determinant]]



- [[Evidence Lower Bound]]
- [[Variational Auto-Encoder]]


## Explanation

>[!quote]
>... training nonlinear latent variable models that involves *restricting* the form of the neural network model such that the *likelihood function* can be **evaluated without approximation** while still ensuring that **sampling from the trained model** is straightforward.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 547

>[!quote]
>In this chapter we discuss **normalizing flows**, a class of *flexible density models* that can be easily sampled from and whose **exact** *likelihood function* is *efficient to compute*. Such models can be used for many tasks, such as density modeling, inference and generative modeling.
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 819

>[!info]
>In order to define a **bijective neural network**, it is required that the input and output *dimensionality* are the **same**. 





-----------
##  Recommended Notes and References


- [[Variational Inference vs EM Algorithm]]


- [[Wasserstein Distance]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 821 - 922
- [[Deep Learning Foundations and Concepts by Bishop]] pp 547 - 559
- [[Foundations of Computer Vision by Torralba]]