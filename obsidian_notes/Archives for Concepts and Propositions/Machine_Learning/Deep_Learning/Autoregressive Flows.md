---
tags:
  - concept
  - machine_learning/models
  - deep_learning/generative_models
keywords:
  - normalizing_flow_model
  - global_flow_smooth_manifold
  - local_flow_smooth_manifold
  - autoregressive_flow
topics:
  - deep_learning/generative_models
name: Autoregressive Flows
date of note: 2024-08-16
---

## Concept Definition

>[!important]
>**Name**: Autoregressive Flows

![[Normalizing Flows#^294151]]

>[!important] Definition
>Let $z := (z^1 \,{,}\ldots{,}\,z^{d})\in \mathbb{R}^{d}$. 
>
>An **autoregressive bijection** $f$ is a map $$f: \mathbb{R}^{d} \to \mathbb{R}^{d}$$ and which coordinate output is given by 
>$$
>x^{i} = h(z^{i}; \;\Theta(x^{1:i-1})), \quad i=1\,{,}\ldots{,} d,
>$$
>where
>- each output $x^{i}$ depends on the corresponding input $z^{i}$ and *all previous outputs* $$x^{1: i-1} := (x^{1}\,{,}\ldots{,}\,x^{i-1})$$
>- and the function $$h(\cdot, \theta): \mathbb{R} \to \mathbb{R}$$ is a *scalar bijection* parameterized $\theta$
>- and $$\Theta_{i}: \mathbb{R}^{i-1} \to \mathbb{R}^{p} \implies \theta_{i} := \Theta_{i}(x^{1: i-1})$$ is a **conditioner** that outputs parameters $\theta_{i}$ that yield $x_{i}$, given all previous outputs $x^{1: i-1}$.
>	- Like in *coupling flows*, $\Theta_{i}$ can be an *arbitrary non-linear function*, and is often parameterized as a *deep neural network*.
>- The overall function $f$ is *bijection* since $h$ is *bijection*. 
>- The **inverse** of $f$ is given by $$z^{i} = h^{-1}\left(x^{i};\; \Theta_{i}(x^{1: i-1})\right), \quad i=1\,{,}\ldots{,} d,$$
>- An important **property** of $f$ is that each output $x^{i}$ depends on $z^{1:i}$ but *not* $z^{i+1:d}$, i.e. $$x^{i} \perp z^{i+1:d} \;|\;z^{1:i}$$
>	- This means that $$\frac{ \partial x^{i} }{ \partial z^{j} } = 0,\quad j=i+1\,{,}\ldots{,}\,d$$
>- The **Jacobian** is **triangular**; and its **determinant** is the *product of diagonal entries* $$\text{det}\;D\,f = \prod_{i=1}^{d}\;\frac{ \partial x^{i} }{ \partial z^{i} } :=\prod_{i=1}^{d}\;\frac{d h}{d z^{i} } $$
>	- The *autoregressive bijection* $f$ has efficient computation of *Jacobian determinant* $$O(d)$$
>- Note that *autoregressive bijection* is **computationally asymmetric**
>	- evaluation of $f$ is **inherently sequential**; $$x^{i} \leftarrow (x^{1: i-1}, z^{i})$$
>	- while evaluation of $f^{-1}$ is **inherently parallel**. $$z^{i} \leftarrow (x^{1: i-1}, x^{i})$$

- [[Autoregressive Models]]
- [[Normalizing Flows]]
- [[Normalizing Flows Construction]]
- [[Latent Variable Models]]
- [[Bijective Function and Inverse Function]]
- [[Conditional Independence]]
- [[Jacobian Matrix and Jacobian Determinant]]
- [[Triangular Matrix and Block Triangular Matrix]]

### Affine Autoregressive Flow

>[!important] Definition
>Let $z := (z^1 \,{,}\ldots{,}\,z^{d})\in \mathbb{R}^{d}$. 
>
>The **affine autoregressive flows** $f$ is given by
>$$
>x^{i} = z^{i}\,\exp \left(\alpha_{i}\left(x^{1:i-1}\right)\right) + \mu_{i}(x^{1:i-1}), \quad i=1\,{,}\ldots{,} d,
>$$
>where 
>- $$\alpha_{i}: \mathbb{R}^{i-1} \to \mathbb{R},\; \quad \mu_{i}: \mathbb{R}^{i-1} \to \mathbb{R}$$ are both functions of $x^{1: i-1}$
>- That is, $h$ is an **affine scalar bijection** *parameterized* by a *log scale* $\alpha$ and a *bias* $\mu$.
>- The **inverse** of the flow is given by $$z^{i} = (x^{i} - \mu_{i}(x^{1:i-1}))\; \exp\left(-\alpha_{i}\left(x^{1:i-1}\right)\right), \quad i=1\,{,}\ldots{,} d,$$
>- The **log-Jacobian determiant** is given by $$\log |\det D f| = \log \left\lvert  \prod_{i=1}^{d}\;\exp \left(\alpha_{i}(x^{1: i-1})\right)  \right\rvert = \sum_{i=1}^{d}\alpha_{i}(x^{1:i-1}). $$


![[affine_autogressive_flow.png]]


### Masked Autoregressive Flow

>[!important] Definition
>We can define a single model $$\Theta: \mathbb{R}^{d} \to \mathbb{R}^{d}$$ for parameterization of bijection.
>
>- In order to maintain the *autoregressiveness*, we must constrain $\Theta$ so that $\theta_{i}$ *only depends on* $x^{1:i-1}$.
>- One way to achieve this is to start with an arbitrary network (e.g. CNN, MLP, ResNet etc.), and *drop connections* until $\theta_{i}$ is *only function* of $x^{1:i-1}$.
>  
>An example is the **masked autoregressive flow (MAF)**, which is an *affine autoregressive flow*, combined with *permutation layer*
>- The **MAF** implements the **conditioner** $$\theta =  \sigma \left((B \odot W)\,x\right)$$  where $B \in \{ 0,1 \}^{d\times d}$
>- This mask makes sure that $$B_{i,j} =0, \quad j \ge i.$$
>- The **key advantage** of **MAF** (and of related models) is that, given $x$, all *parameters* $$(\theta^{1} \,{,}\ldots{,}\,\theta^{d})$$ can be computed efficiently with **one neural network evaluation**
>	- The *computation of inverse* is *fast*.

>[!quote]
>However, in order to compute $f$, the *conditioner* $\Theta$ must **be called** a total of $d$ **times**, since *not all entries* of $x$ are available to start with. 
>
>Thus, **generating new samples** from the flow is $d$ times **more expensive** than **evaluating** its **probability density function**. 
>- This makes MAF **suitable** for **density estimation**, 
>- but *less* so for **data generation**.
>  
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 830  

- [[Causal Convolutional Neural Network]]

### Inverse Autoregressive Flow

>[!important] Definition
>Let $z := (z^1 \,{,}\ldots{,}\,z^{d})\in \mathbb{R}^{d}$. 
>
>The **inverse autoregressive flow (IAF)** swap $f$ and its inverse $f^{-1}$. That is,  the coordinate output of map $f: \mathbb{R}^{d} \to \mathbb{R}^{d}$ is given by 
>$$
>x^{i} = h(z^{i}; \;\Theta(z^{1:i-1})), \quad i=1\,{,}\ldots{,} d,
>$$
>where
>- each output $x^{i}$ depends on the corresponding input $z^{i}$ and **all previous inputs** $$z^{1: i-1} := (z^{1}\,{,}\ldots{,}\,z^{i-1})$$
>- The **inverse** of $f$ is given by $$z^{i} = h^{-1}\left(x^{i};\; \Theta_{i}(z^{1: i-1})\right), \quad i=1\,{,}\ldots{,} d,$$
>- Compared to original autoregressive flow,  each input $z^{i}$ depends on $x^{1:i}$ but *not* $x^{i+1:d}$, i.e. $$z^{i} \perp x^{i+1:d} \;|\;x^{1:i}$$
>	- This means that $$\frac{ \partial x^{i} }{ \partial z^{j} } = 0,\quad i=j+1\,{,}\ldots{,}\,d$$
>- The **Jacobian** is **triangular**; and its **determinant** is the *product of diagonal entries* $$\text{det}\;D\,f = \prod_{i=1}^{d}\;\frac{d h}{d z^{i} } $$
>- Similar to autoregressive flow, the *inverse autoregressive flow* is also asymmetric:
>	- evaluation of $f$ is **inherently parallel**; $$x^{i} \leftarrow (z^{1: i-1}, z^{i})$$
>	- while evaluation of $f^{-1}$ is **inherently sequential**. $$z^{i} \leftarrow (z^{1: i-1}, x^{i})$$


![[inverse_autoregressive_flow.png]]

>[!quote]
>Although not so suitable for *density estimation* or *maximum-likelihood training*, **IAFs** are wellsuited for parameterizing **variational posteriors** in **variational inference**. 
>- This is because in order to estimate the **variational lower bound (ELBO)**, we *only need samples* from the *variational posterior* and their associated *probability densities*, both of which are efficient to obtain.
>  
>Another useful application of IAFs is training them to **mimic models** whose *probability density* is **fast to evaluate** but which are **slow to sample from**. 
>- A notable example is the **parallel wavenet**.  
>  
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 831  



## Explanation



## Autoregressive Model

>[!quote]
>**Autoregressive flows** can be thought of as *generalizing* **autoregressive models** of continuous random variables, discussed in Section 22.1. 
>- Specifically, **any** continuous autoregressive model can be **reparameterized** as a *one-layer* autoregressive flow.
>  
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 831  


- [[Autoregressive Models]]



## Density Estimation with Autogressive Flow


![[autoregressive_flow_density_estimation.png]]






-----------
##  Recommended Notes and References


- [[Artificial Neural Network and Deep Learning]]

- [[Wasserstein Distance]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 826 - 832
- [[Deep Learning Foundations and Concepts by Bishop]] pp 552 - 554
- [[Foundations of Computer Vision by Torralba]]