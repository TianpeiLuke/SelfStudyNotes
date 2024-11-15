---
tags:
  - concept
  - machine_learning/models
  - deep_learning/generative_models
keywords:
  - normalizing_flow_model
topics:
  - deep_learning/generative_models
name: Normalizing Flows Construction
date of note: 2024-08-16
---

## Concept Definition

>[!important]
>**Name**: Normalizing Flows Construction

![[Normalizing Flows#^294151]]

- [[Normalizing Flows]]
- [[Latent Variable Models]]
- [[Bijective Function and Inverse Function]]
- [[Probability Density Function of Random Variable]]
- [[Jacobian Matrix and Jacobian Determinant]]


### Elementwise Flows

>[!important] Definition
>The **elementwise flows** assume that the each dimension of output of *generative network* $f:\mathbb{R}^{d} \to \mathbb{R}^{d}$ is given by a single non-linear bijection 
>$$
>f(z) = (h(z^1) \,{,}\ldots{,}\,h(z^d))
>$$
>where 
>- $$h: \mathbb{R} \to \mathbb{R}, \quad i=1\,{,}\ldots{,}\,d$$ is *scalar-valued univariate bijection*.
>	- $h$ can be seen as *activation functions*, e.g. the *Leaky ReLU* can be used
>- Then the *Jacobian determinant* can be represented as $$\det (Df)\, = \prod_{i=1}^{d}\frac{dh}{d z^{i}} $$
>


>[!quote]
>On their own, **elementwise flows are limited**, since they do not model *dependencies* *between* the elements. 
>
>However, they are useful **building blocks** for more complex flows, such as 
>- **coupling flows** (Section 23.2.3) 
>- and **autoregressive flows**
>  
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]]  

>[!info]
>Some of choice of function $h$ include:

#### Combination of Strictly Monotonic Scalar Function

>[!info]
>Let $h_{1}, \,{,}\ldots{,}\,h_{K}$ be *strictly monotone increasing*, then for any $(\alpha_{1}\,{,}\ldots{,}\,\alpha_{K}) \succeq\,0$, we have  $$\sum_{i=1}^{K}\alpha_{i}\,h_{i}$$ is *strictly monotone increasing*


#### Bijective Activation Functions

- [[Rectified Linear Unit as Activation for Deep Learning]]
- [[Sigmoid Function as Activation for Deep Learning]]

#### B-Spline Function

- [[B-Spline Functions]]

### Affine Flows

>[!important] Definition
>The **affine flows** use the *affine transformation* as the *generative model* 
>$$
>x = f(z) := Az + b
>$$
>where 
>- $A$ is invertible,  $$A\in \text{GL}(d, \mathbb{R}) \subset \mathbb{R}^{d\times d}, \quad b\in \mathbb{R}^{d}.$$
>- The inverse (*normalizing flow*) is given by $$z = g(x) = A^{-1}(x - b)$$

- [[General Linear Group]]
- [[Affine Map]]

>[!quote]
>On their own, **affine flows** are *limited* in their **expressive power**.
>- For example, suppose the *base distribution* is Gaussian, $p(z) = N (z|\mu, \Sigma)$. Then the *pushforward distribution* after an affine bijection is still *Gaussian*, $$p(x) = N (x|A\mu + b, A\Sigma A^{T}).$$ 
>- However, affine bijections are useful **building blocks** when composed with the non-affine bijections we discuss later, as they encourage “*mixing*” of dimensions through the flow.


### Coupling Flows

![[Coupling Flows#^f016a0]]

- [[Coupling Flows]]


### Autoregressive Flows


- [[Autoregressive Flows]]


### Residual Flows


- [[Residual Flows]]


### Continuous Flows


- [[Neural Ordinary Differential Equations]]



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


- [[Artificial Neural Network and Deep Learning]]



- [[Wasserstein Distance]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 822 - 925
- [[Deep Learning Foundations and Concepts by Bishop]] pp 547 - 559
- [[Foundations of Computer Vision by Torralba]]