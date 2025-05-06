---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/models
  - machine_learning/latent_variable_model
  - LVM
  - latent_variable_model
keywords:
  - latent_variable_model
topics:
  - unsupervised_models
  - machine_learning_models
  - probabilistic_graphical_model
name: Latent Variable Models
date of note: 2024-09-04
---

## Concept Definition

>[!important]
>**Name**: Latent Variable Models

>[!important] Definition
>A **latent variable model (LVM)** is any probabilistic model in which some variables are always *latent* or *hidden*.
>

>[!important] Definition
>A simple form of **LVM** is the **decoder model**
>$$
>\left\{
>\begin{align*}
> Z &\sim p(z) \\[5pt]
> X | Z &\sim  p(x\,|\, f(z))
>\end{align*}
>\right.
>$$
>where $f(z)$ is called the **decoder**, and $p(z)$ is a **prior** on **latent variables**.
>
>Usually, we choose $$p(x\,|\, f(z)) \in \mathscr{P}_{\theta}$$ from an *exponential family* with natural / mean parameters $$\theta = f(z) \in \Theta$$ specified by the decoder.

^68d885

- [[Factor Analysis]]
- [[Exponential Family of Distributions]]

## Explanation

>[!info]
>In different literature the name of latent variables are different:
>- For **Gaussian mixtures**, we used the term **latent variable**. It is common to use $Z$ as symbol.
>- For **factor analysis**, we used the term **hidden factors** or **factors**. It is common to use either $h$ or $Z$ as symbols.
>- For general **deep learning**, they are called **hidden units**. It is common to use $h$ as symbol.
>- For **auto-encoder**, they are called **codes**, **encoded representation**, **embeddings**
>- For **representation learning**, they are called **embeddings**, or **representations**
>- For **topic model**, they are called **topics**
>- For **dynamic system** and **state space model**, they are called **states** or **hidden states**. It is common to use either $Z$ or $X$ as symbols.
>- For **Gaussian process**, they are called **states** or **index variables**. It is common to use either $t$ or $X$ as symbols.


## Example

### Auto-Encoder

- [[Auto-Encoder and Stochastic Auto-Encoder]]
- [[Variational Auto-Encoder]]

### Clustering

- [[Gaussian Mixture Models]]
- [[Gaussian Scale Mixtures]]

### Factor Analysis Models

- [[Factor Analysis]]
- [[Principal Component Analysis]]
- [[Probabilistic Principal Component Analysis]]
- [[Nonnegative Matrix Factorization or NMF]]
- [[Canonical Correlation Analysis or CCA]]

### State Space Models and Dynamic Systems

- [[State-Observation Models]]
- [[Linear Dynamic System]]
- [[State Space Models and Nonlinear Dynamic System]]
- [[Hidden Markov Model]]
- [[Kalman Filter Discrete-Time]]

### Topic Models

- [[Latent Dirichlet Allocation]]

### Gaussian Process

- [[Gaussian Process Latent Variable Model]]



-----------
##  Recommended Notes and References





- [[Exponential Family of Distributions]]


- [[Elements of Statistical Learning by Hastie]] pp 674 - 678
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 919 - 969
- [[Probabilistic Graphical Models by Koller]] pp 1012, 1048
- [[Deep Learning Foundations and Concepts by Bishop]] pp 459, 495
