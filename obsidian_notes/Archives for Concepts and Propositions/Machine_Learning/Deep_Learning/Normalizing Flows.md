---
tags:
  - concept
  - machine_learning/models
  - deep_learning/generative_models
  - normalizing_flow_model
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
- [[Real Non-Volume-Preserving as Coupling Flows for Deep Density Estimation]]

### Autoregressive Flows


- [[Autoregressive Flows]]

### Residual Flows


- [[Residual Flows]]

### Continuous Flows and Neural ODE

- [[Continuous-Time Flows]]
- [[Neural Ordinary Differential Equations]]


## Applications

### Deep Density Estimation and Random Variable Generation

>[!quote]
> **Flow models** allow **exact density computation** and can be used to fit *multi-modal densities* to observed data. (see Figure 23.3 for an example). 
> - An early example is Gaussianization [CG00] who applied this idea to fit low-dimensional densities. Tabak and Vanden-Eijnden [TVE10] and Tabak 
> - and Turner [TT13] introduced the modern idea of **flows** (including the term ‘**normalizing flows**’), describing a flow as a composition of simpler maps. 
> - **Deep density models** [RA13] was one of the first to use neural networks for flows to parameterize *high-dimensional densities*. 
> 	- There has been a rich line of follow-up work including **NICE** [DKB15] and **Real NVP** [DSDB17]. (**NVP** stands for “*non-volume-preserving*”, which refers to the fact that the Jacobian of the transform is not unity.) 
> 	- **Masked autoregressive flows** (Section 23.2.4.2) further improved performance on unconditional and *conditional density estimation* tasks. 
> 
> Flows can be used for *hybrid models* which model the **joint density** of inputs and targets $p(x, y)$, as opposed to *discriminative classification models* which just model the conditional $p(y|x)$ and density models which just model the marginal $p(x)$. 
> - Nalisnick et al. [Nal+19b] proposed a **flow-based hybrid model** using invertible mappings for representation learning and showed that the joint density $p(x, y)$ can be computed efficiently, which can be useful for downstream tasks such as 
> 	- *anomaly detection*, 
> 	- *semi-supervised learning* 
> 	- and *selective classification*. 
> - **Flow-based hybrid models** are *memory-efficient* since most of the parameters are in the invertible representation which are shared between the *discriminative* and *generative models*; 
> 	- furthermore, the density $p(x, y)$ can be computed in a *single forwards pass* leading to computational savings. 
> - **Residual flows** [Che+19] use invertible residual mappings [Beh+19] for hybrid modeling which further improves performance. 
> - Flows have also been used to *fit densities* to **embeddings** [Zha+20b; CZG20] for anomaly detection tasks.
>   
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 836   

- [[Parzen Kernel Density Estimation]]
- [[Random Variable Generation with Inverse Cumulative Distribution Function]]

### Generative Models

>[!quote]
>Another task is **generation**, which involves generating novel samples from a fitted model $p^{*}(x)$. Generation is a popular *downstream task* for *normalizing flows*, which have been applied for different **data modalities** including images, video, audio, text, and structured objects such as graphs and point clouds.
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 836


### Inference

>[!quote]
>Normalizing flows have been used for **probabilistic inference**. 
>- Rezende and Mohamed [RM15] popularized normalizing flows in machine learning, and showed how they can be used for modeling *variational posterior distributions* in *latent variable models*. 
>- Various extensions such as 
>	- **Householder flows** [TW16], 
>	- **inverse autoregressive flows** [Kin+16], 
>	- **multiplicative normalizing flows** [LW17], 
>	- and **Sylvester flows** [Ber+18] 
>
>have been proposed for modeling the variational posterior for latent variable models, as well as posteriors for **Bayesian neural networks**. 
>
>Flows have been used as complex proposal distributions for **importance sampling**; examples include 
>- **neural importance sampling** [Mül+19b] 
>- and **Boltzmann generators** [Noé+19]. 
>- Hoffman et al. [Hof+19] used flows to improve the performance of **Hamiltonian Monte Carlo** (Section 12.5) by defining *bijective transformations* to transform random variables to simpler distributions and performing HMC in that space instead. 
>
>Finally, flows can be used in the context of **simulation-based inference**, where the likelihood function of the parameters is not available, but *simulating data* from the model is possible. 
>- The main idea is to *train* a **flow** on data *simulated from the model* in order to **approximate the posterior distribution** or the likelihood function. 
>- The flow model can also be used to guide simulations in order to make inference *more efficient* [PSM19; GNM19]. 
>- This approach has been used for inference of simulation models in 
>	- **cosmology** [Als+19] 
>	- and **computational neuroscience** [Gon+20].
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 837


- [[Latent Variable Models]]
- [[Variational Auto-Encoder]]
- [[Comparison of Variational Inference vs EM Algorithm]]
- [[Hamiltonian Monte Carlo]]
- [[Importance Sampling]]



-----------
##  Recommended Notes and References


- [[Artificial Neural Network and Deep Learning]]



- [[Wasserstein Distance]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 819 - 837, 765, 973
- [[Deep Learning Foundations and Concepts by Bishop]] pp 547 - 559
- [[Foundations of Computer Vision by Torralba]]