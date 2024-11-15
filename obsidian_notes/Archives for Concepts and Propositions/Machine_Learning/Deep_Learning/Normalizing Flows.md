---
tags:
  - concept
  - machine_learning/models
  - deep_learning/generative_models
keywords:
  - normalizing_flow_model
topics:
  - deep_learning/generative_models
name: Normalizing Flows
date of note: 2024-08-16
---

## Concept Definition

>[!important]
>**Name**: Normalizing Flows

>[!important] Definition
>Assume that a random variable is drawn from a *simple distribution*, called the **base distribution**, $$Z \sim p_{z}(z).$$
>
>- $Z$ is a latent variable for a *nonlinear function* $$x = f(z, w)$$ where $f$ is a *deep neural network* that transforms the *latent space* $\mathcal{Z}$ into the *data space* $\mathcal{X}$.
>	- Assume that $$\mathcal{X} \subset \mathbb{R}^{d},\quad \mathcal{Z} \subset \mathbb{R}^{d}$$
>- In order to compute the *data-space distribution*, it is required that the neural network $f$ is **bijective.** 
>- That is, there exists a neural network $g(x, w)$ so that $$z = g\left(f(x, w), w\right).$$
>	- This requires that for every $w$, each $x\in \mathcal{X}$ corresponds to a *unique* $z\in \mathcal{Z}$ and vice versa.
>	- The inverse mapping $g$ **normalizes** the *data distribution* by *mapping it back* to base distribution. $$X\sim p_{x}(x) \stackrel{g}{\longrightarrow} p_{z}(z)$$
>	  
>The **probability density function** of $x\in \mathcal{X}$ is given by $$\begin{align*}p_{x}(x; w)&= p_{z}(z)\;\lvert\, \det D\,f(z) \,\rvert^{-1}\\[7pt]     &= p_{z}\left(g(x, w)\right)\;\lvert\, \det D\,g(x) \,\rvert \end{align*}$$ where
>- $D\,g(x)$ is the *Jacobian matrix* of $g$, i.e. $$D\,g(x) := \frac{ \partial (g_{1} \,{,}\ldots{,}\,g_{d})}{ \partial (x^1 \,{,}\ldots{,}\,x^{d}) }\Big|_{x} := \frac{ \partial g }{ \partial x } (x) $$
>- $D\,f(z)$ is the *Jacobian matrix* of $f$, i.e. $$D\,f(z) := \frac{ \partial (f_{1} \,{,}\ldots{,}\,f_{d})}{ \partial (z^1 \,{,}\ldots{,}\,z^{d}) }\Big|_{z}  := \frac{ \partial f }{ \partial z } (z) $$
>- The Jacobian matrix is *invertible* $$\left(\frac{ \partial f }{ \partial z } (z)\right)^{-1} = \frac{ \partial g }{ \partial x } (f(z))$$
>- This is a *change-of-variable* formula.
>
>The **log likelihood function** on data $\mathcal{D}:= \{ x_{1}\,{,}\ldots{,}\,x_{n} \}$ is given by $$\begin{align*}\ell(w; \mathcal{D}) &= \sum_{i=1}^{n}\log p_{x}(x_{i}; w) \\[8pt] &= \sum_{i=1}^{n}\left\{ \log p_{z}(g(x_{i}, w))  + \log \,\lvert \det D\,g(x_{i}) \rvert  \right\}  \end{align*}$$
>- To have *bijective neural network* $f$, each layer of $f$ is *bijective*. 
>	- For example, assume that $f$ have *$l$ layers*, $$f = f^{1} \circ f^{2} \,{\circ}\ldots{\circ}\, f^{l} \iff g = g^{l} \,{\circ}\ldots{\circ}\, g^{2} \circ g^{1}$$ where $g^{i} = (f^{i})^{-1}$
>	- and the *Jacobian matrix* can be decomposed following the *chain rule* $$\frac{ \partial g }{ \partial x } = \frac{ \partial g^{l} }{ \partial g^{l-1} }\,{}\ldots{}\, \frac{ \partial g^{2} }{ \partial g^{1} }\,\frac{ \partial g^{1} }{ \partial x } $$
>	- The corresponding *log-determinant* can be *factorized*  $$\log \, \det D\,g(x) = \sum_{s=2}^{l} \log\det \left(D\,g^{s}\right)(u^{s}) +  \log \,\det D\,g^1(x).$$ where $$u^{s} := g^{s-1} \,{\circ}\ldots{\circ}\, g^{1}(x)$$
>- The above approach to modeling a *flexible distribution* is called a **normalizing flow.**

^294151


- [[Latent Variable Models]]
- [[Bijective Function and Inverse Function]]
- [[Probability Density Function of Random Variable]]
- [[Jacobian Matrix and Jacobian Determinant]]


>[!important] Definition
>The setup of **normaling flow** assume that the neural network map $f: \mathcal{Z} \to \mathcal{X}$ is a **diffomorphism**, i.e. it is a *smooth bijection* with *smooth inverse*. $$f\in \mathscr{D}$$
>
>For a neural network $f$ with $l$ layers, and its inverse $g$ i.e.   $$f = f^{1} \circ f^{2} \,{\circ}\ldots{\circ}\, f^{l} \iff g = g^{l} \,{\circ}\ldots{\circ}\, g^{2} \circ g^{1}$$ the *probability density* of  *data variables* can be seen as the **pushforward** of **base measure** $p_{z}$ by network function $f$, i.e. $$p_{x} = f_{*}\,p_{z}$$
>- Note that we can use the **pushforward operation** of density to represent the *distribution* of *intermediate latent variables* in *each layer* $k$, $$p_{u^{k}}\; = \left(f^{l-k+1} \,{\circ}\ldots{\circ}\, f^{l}\right)_{*}\,p_{z} $$
>- The name **normaling flow** comes from the continuous *transformation of distributions* through $l$ layers of neural network  
>	- The *flow* is from *base distribution* on latent space $\mathcal{Z}$ to data space $\mathcal{X}$ $$\begin{align*}p_{z} &\to f^{l}_{*}\,p_{z} \\[5pt] &\to (f^{l-1} \circ f^{l})_{*}\,p_{z} \\[5pt] &\,{\to}\ldots \\[5pt] & \to \left(f^{1} \circ f^{2} \,{\circ}\ldots{\circ}\, f^{l} \right)_{*}\,p_{z} \\[5pt] &:= f_{*}\,p_{z} := p_{x}\end{align*}$$  
>	- The *inverse flow* or the **normalizing flow** is from distribution on data space $\mathcal{X}$ to **base distribution** $\mathcal{Z}$  $$\begin{align*}p_{x} &\to g^{1}_{*}\,p_{x} \\[5pt] &\to (g^{2} \circ g^{1})_{*}\,p_{x} \\[5pt] &\,{\to}\ldots \\[5pt] & \to \left(g^{l}  \,{\circ}\ldots{\circ}\,g^{2} \circ  g^{1} \right)_{*}\,p_{x} \\[5pt] &:= g_{*}\,p_{x} := p_{z}\end{align*}$$  

^8d93c1

- [[Diffeomorphism]]
- [[Push-forward Measure and Push-forward Operator]]

### Training Normalizing Flows

- [[Normalizing Flows Training]]

### Construction Normalizing Flows

- [[Normalizing Flows Construction]]



## Explanation


>[!important]
>The **key characteristic** of **normalizing flow** include:
>- The neural network for decoder need to be a **diffeomorphism**, i.e. it is a *smooth bijective* function with *smooth inverse.*
>	- This means that *each layer* is of **same dimension.** $$\text{dim}(\mathcal{X}) = \text{dim}(\mathcal{U}^{1}) \,{=}\ldots{=}\,\text{dim}(\mathcal{U}^{l}) = \text{dim}(\mathcal{Z})$$
>- The network be **sufficiently expressive** to model the distribution of interest,
>- The model need to be **computationally efficient**, both in terms of computing $f$ and $g$ (depending on the application) but also in terms of the calculation of the **determinant of the Jacobian**.


>[!quote]
>... training nonlinear latent variable models that involves *restricting* the form of the neural network model such that the *likelihood function* can be **evaluated without approximation** while still ensuring that **sampling from the trained model** is straightforward.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 547

>[!quote]
>In this chapter we discuss **normalizing flows**, a class of *flexible density models* that can be easily sampled from and whose **exact** *likelihood function* is *efficient to compute*. 
>
>Such models can be used for many tasks, such as 
>- density modeling, 
>- inference and 
>- generative modeling.
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 819



>[!info]
>In order to define a **bijective neural network**, it is required that the input and output *dimensionality* are the **same**. 

### Flow 

>[!important] Definition
>The math term **flow** refers to a **one-parameter subgroup** $F \subset (\mathscr{D}, \circ)$ of *diffeomorphisms* $\mathscr{D}$, $$F: \mathbb{R}  \to \mathscr{D}$$ which is defined as $$F(t) := f^{t}.$$ This subgroup satisfies the condition
>- $$F(0) = I$$ where $I(x) = x, \forall x$ is the *identity map*;
>- $$F(t_{2} + t_{1}) = f^{t_{2}} \circ f^{t_{1}}$$ 

>[!important] Definition
>It induces the **one-parameter family of group actions** $$\tilde{F}: \mathbb{R} \times \mathscr{D} \to \mathscr{D}$$ from $F$ by $$\tilde{F}(t, h) := F(t)\circ h$$. This *one-parameter action group* satisfies the condition 
>- $$\tilde{F}(0, h) = F(0)\circ h =  h$$
>- $$\tilde{F}(t_{2}, F(t_{1}, h)) =  F(t_{2})\circ F(t_{1}) \circ h := \tilde{F}(t_{2}+ t_{1}, h)$$

- [[Topological Group Action]]
- [[Global Flow on Smooth Manifold]]
- [[Matrix Exponential as Global Flow in General Linear Group]]
- [[One-Parameter Subgroup of Lie Group as Integral Curve]]


## Variants

### Coupling Flows


- [[Coupling Flows]]

### Autoregressive Flows


- [[Autoregressive Flows]]

### Residual Flows


- [[Residual Flows]]

### Continuous Flows and Neural ODE



- [[Neural Ordinary Differential Equations and Continuous Flows]]


## Applications

### Density Estimation

- [[Parzen Kernel Density Estimation]]


### Generative Models



### Inference

- [[Variational Auto-Encoder]]
- [[Variational Inference vs EM Algorithm]]





-----------
##  Recommended Notes and References


- [[Artificial Neural Network and Deep Learning]]



- [[Wasserstein Distance]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 819 - 837, 765, 973
- [[Deep Learning Foundations and Concepts by Bishop]] pp 547 - 559
- [[Foundations of Computer Vision by Torralba]]