---
tags:
  - concept
  - machine_learning/models
  - deep_learning/generative_models
keywords:
  - variational_inference
  - variational_autoencoder
topics:
  - deep_learning
  - generative_model
name: Variational Auto-Encoder
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Variational Auto-Encoder

>[!important] Definition
>Let $(X, Z)$ be a sample from *parametric family* $$\{ p_{\theta}(x, z): \theta\in \Theta \}$$ where $p_{\theta}(x, z)$ is *p.d.f.* with respect to some nominating measure $\nu$ and $\Theta \subset \mathbb{R}^{d}$.  Assume $X\in \mathcal{X} \subset \mathbb{R}^{m}$ and $Z\in \mathcal{Z} \subset \mathbb{R}^{m}.$
>
>A **latent-variable model** is defined by a *conditional probability density function* $$p(x | z, \theta)$$ where $x \in \mathcal{X}$ is a list of **observed variables** and $z \in \mathcal{Z}$ is the list of **unobserved (latent) variables.** Define $p(z)$ on $\mathcal{Z}$ as the *marginal (prior) density* on latent variables $Z$ and $p_{\theta}(x)$ is the *marginal density* on the observed variables $X$. The **marginal log-likelihood** or **evidence** of $x$ is given by  $$\ell(\theta; x) :=  \log p_{\theta}(x) = \log \int p(x | z, \theta)\, p(z) \, d\nu_{Z}, \quad \forall \theta \in \Theta,$$ where $\nu_{Z}$ is the marginal measure of $\nu$ on $Z$. In the following setting, we assume $\nu$ and $\nu_{Z}$ are both the *Lebesgue measures* on $\mathbb{R}^{2m}$ and $\mathbb{R}^{m}$, respectively.
>
>The **variational autoencoder (VAE)** approximate the marginal log-likelihood using the **evidence lower bound (ELBO)** 
>$$
>\mathcal{L}(\psi, \theta; x) = \mathbb{E}_{ q(z|x, \psi) }\left[\log \left(\frac{p(x | z, \theta)\, p(z) }{q(z|x, \psi)}\right) \right],
>$$
>where
>- $p(x | z, \theta)$ defines a **decoder network** with weight parameter $\theta\in \Theta$
>- $q(z | x, \psi)$ defines an **encoder network** with weight parameter $\psi \in \Psi$

- [[Parametric Models]]
- [[Probability Density Function of Random Variable]]
- [[Conditional Probability]]
- [[Lebesgue Measure]]
- [[Evidence Lower Bound]]

>[!important] Key Idea
>There are three **key ideas** in the **VAE**:
>- use of the **evidence lower bound (ELBO)** to *approximate* the likelihood function, leading to a close relationship to the **EM algorithm**;
>- **amortized inference** in which a second model, the **encoder network**, is used to **approximate** *the posterior distributions* over latent variables in the **E step**, *rather than* evaluating the posterior distribution for each data point *exactly*,
>- making the training of the encoder model tractable using the **reparameterization trick**

- [[Expectation-Maximization Algorithm]]
- [[Variational Inference vs EM Algorithm]]

### Evidence Lower Bound

![[Evidence Lower Bound#^5bbff1]]

- [[Evidence Lower Bound]]

### I.I.D Samples

>[!important] Definition
>Consider a set of $n$ i.i.d. samples $\{ (X_{i}, Z_{i}): i=1 \,{,}\ldots{,}\,n \}$ and  $$\mathcal{D}:= \{ X_{1} \,{,}\ldots{,}\,X_{n}\}$$ represents the set of **observed data**, Assume that for each $X_{i}$, there exists a corresponding *latent variable* $Z_{i}$. In other word, the distribution on $Z$ is a *product measure* $$q(Z_{1} \,{,}\ldots{,}\,Z_{n}) = \prod_{i=1}^{n}q(Z_{i}).$$
>
>Using ELBO, we can represent the **incomplete log-likelihood** of $\theta$ given $\mathcal{D}$ as 
>$$
>\log p_{\theta}(\mathcal{D}) = \sum_{i=1}^{n}\mathcal{L}(q, \theta; X_{i}) + \sum_{i=1}^{n}\mathbb{KL}\left( q(Z_{i}) \left\|\right. p(Z_{i} | X_{i}, \theta) \right)
>$$
>where
>$$\mathcal{L}(q, \theta; X_{i}) := \mathbb{E}_{ Z_{i} }\left[ \log \left(\frac{p_{\theta}(X_{i}, Z_{i})}{q(Z_{i})}\right) \right] = \int_{\mathcal{Z}}\;q(z_{i})\log \left(\frac{p_{\theta}(X_{i} | z_{i})\,p(z_{i})}{q(z_{i})}\right)dz_{i}$$

## Amortized Inference

>[!important] Definition
>In the **variational autoencoder**, instead of trying to evaluate a separate *posterior distribution* $p(Z_{i} | X_{i}, \theta)$ for *each* of the data points $X_{i}$ individually, we train a *single neural network*, $$q_{\psi}(z) := q(z | x, \psi)$$  called the **encoder network**, to approximate all these distributions.
>
>This technique is called **amortized inference** and requires an *encoder* that produces a single *distribution* $q(z | x, \psi)$ that is conditioned on $x$, where $\psi\in \Psi$ represents the *parameters* of the network.

>[!info]
>The ELBO can be reparameterized via $\psi$ and $\theta$ as
>$$
>\mathcal{L}(q_{\psi}, \theta; x)  := \mathcal{L}(\psi, \theta; x) = \mathbb{E}_{ q(z|x, \psi) }\left[\log \left(\frac{p(x | z, \theta)\, p(z) }{q(z|x, \psi)}\right) \right].
>$$

## Distribution Family of Encoder Network

>[!important] 
>A typical choice for the encoder is a **Gaussian distribution** with a *diagonal covariance matrix* (i.e. *independent components*) whose **mean** and **variance** parameters are given by the **output** *of a neural network* that takes $x$ as input. 
>
>That is, 
>$$
>q(z | x, \psi) := \prod_{j=1}^{m}\mathcal{N}(z_{j}\;|\; \mu_{j}(x, \psi)\,,\, \sigma_{j}^2(x, \psi)\,).
>$$
>- $\mu_{j}: \mathcal{X} \times \Psi \to \mathbb{R}$ can be *linear function* for **output-unit activation**.
>- $\sigma_{j}^2: \mathcal{X} \times \Psi \to \mathbb{R}_{+}$ is *non-negative function*. Typically, we use $\exp(\cdot)$ as the **activation function** in *output unit*.
>  
>Also we assume the *prior* $p(z) = \mathcal{N}(0, I)$.

- [[Gaussian Random Variable]]
- [[Gaussian Random Vector]]

## Reparameterization Trick


>[!important]
>The **main challenge** for optimizing ELBO is that it depends on the **integration** of a **complicated decoder model**  $p_{\theta}(x_{i} | z_{i})$ with respect to a *output distribution of encoder over latent variable $z_{i}$*
>$$
>\begin{align*}
>\mathcal{L}(\psi, \theta; X_{i}) &= \int_{\mathcal{Z}}\;q(z_{i})\log \left(\frac{p_{\theta}(X_{i} | z_{i})\,p(z_{i})}{q(z_{i})}\right)dz_{i}\\[10pt]
>&= \mathbb{E}_{Z_{i} \sim q }\left[  \log p_{\theta}(X_{i} | Z_{i}) \right] - \mathbb{KL}\left( q(z_{i} |X_{i}, \psi) \left\|\right. p(z_{i})  \right)
>\end{align*}
>$$
>We can use **Monte Carlo sampling** to solve this issue. [[Markov Chain Monte Carlo Methods]]
>
>Specifically, we see that: 
>- The second term can be evaluated **analytically** since both $p(z)$ and $q(z|X_{i}, \psi)$ are assumed to be **Gaussian** *with independent component*. That is, for $i =1 \,{,}\ldots{,}\,m$,
> $$
>  \begin{align*}
>&\mathbb{KL}\left( q(z_{i} |X_{i}, \psi) \left\|\right. p(z_{i})  \right) \\[5pt]
>&= \mathbb{KL}\left( \mathcal{N}(z_{j}\;|\; \mu_{j}(x, \psi)\,,\, \sigma_{j}^2(x, \psi)\,) \left\|\right. \mathcal{N}(0, 1)  \right)\\[5pt]
>&= \frac{1}{2}\left\{  \frac{\sigma_{j}^2(x, \psi)}{1} -1  - \log \left(\frac{\sigma_{j}^2(x, \psi)}{1}\right) \right\} + \frac{\left(\mu_{j}(x, \psi) - 0\right)^2}{2 \times 1}\\
>&= \frac{1}{2}\left\{\mu_{j}^2(x, \psi) + \sigma_{j}^2(x, \psi) - 1 - \log \sigma_{j}^2(x, \psi)  \right\} 
>\end{align*}
>$$
>- The first term can be approximated using **Monte-Carlo estimator** $$\mathbb{E}_{Z_{i} \sim q }\left[  \log p_{\theta}(X_{i} | Z_{i}) \right] \approx \frac{1}{L} \sum_{l=1}^{L}\log p_{\theta}(X_{i} | Z_{i}^{l})$$ where $\{ Z_{i}^{l} \}_{l=1}^{L} \sim q(z|X_{i}, \psi)$ are **samples** drawn from the *encoder distribution* $q.$
>  

- [[Monte Carlo and Applications]]
- [[Markov Chain Monte Carlo Methods]]
- [[Annealed Importance Sampling]]

![[VAE_ELBO_backprop.png]]

>[!info]
>Our **goal** is the use back-propagation to take gradient of $\mathcal{L}$ with respec to both $\theta$ and $\psi.$
>
>However, when we use the *Monte-Carlo estimator*
>$$\mathbb{E}_{Z_{i} \sim q }\left[  \log p_{\theta}(X_{i} | Z_{i}) \right] \approx \frac{1}{L} \sum_{l=1}^{L}\log p_{\theta}(X_{i} | Z_{i}^{l}),$$ the *samples* $\{ Z_{i}^{l} \}_{l=1}^{L} \sim q(z|X_{i}, \psi)$  from the *encoder distribution* $q$ are **fixed**.
>
>On the other hand, changing $\psi$ will **change the distribution** $q(z|X_{i}, \psi)$ from which the samples are drawn and yet these samples are fixed values so that we do not have a way to obtain the **derivatives of these samples with respect to $\psi$**.

![[VAE_reparameterization_trick.png]]

>[!important] Definition
>We can resolve this by making use of the **reparameterization** trick in which we *reformulate* the *Monte Carlo sampling* procedure such that **derivatives** with respect to $\psi := (\mu, \sigma^2)$ can be calculated **explicitly**.
>
>Note that for $Z_{i,j}^{l} \sim \mathcal{N}(\mu_{j}(x_{i}; \psi), \sigma_{j}^2(x_{i}; \psi))$, we can represented as 
>$$
>Z_{i,j}^{l} = \mu_{j}(x_{i}; \psi)\, + \sigma_{j}(x_{i}; \psi)\,\xi_{i,j}^{l}
>$$
>where $\{ \xi_{i,j}^{l} \} \sim \mathcal{N}(0,1)$ are *i.i.d. standard normal random variables*.

- [[Representation of Gaussian Random Function in Hilbert Space]]



## Learning Objective Function and Optimization

>[!important] Definition
>Given $\mathcal{D}$, the **learning objective function** for **VAE** is  
>$$
>\begin{align*}
>&\sum_{i=1}^{n}\mathcal{L}(q, \theta; X_{i})  \\[5pt]
>&=\sum_{i=1}^{n}\mathbb{E}_{Z_{i} \sim q }\left[  \log p_{\theta}(X_{i} | Z_{i}) \right] - \sum_{i=1}^{n}\mathbb{KL}\left( q(z_{i} |X_{i}, \psi) \left\|\right. p(z_{i})  \right) \\[5pt]
>&= \sum_{i=1}^{n}\left\{ \frac{1}{L} \sum_{l=1}^{L}\log p_{\theta}(X_{i} | Z_{i}^{l}) + \frac{1}{2}\sum_{j=1}^{m}\left\{- \mu_{j}^2(X_{i}, \psi) - \sigma_{j}^2(X_{i}, \psi) + 1 + \log \sigma_{j}^2(X_{i}, \psi)  \right\}  \right\} 
\end{align*}
>$$
>where $Z_{i}^{l} := \left(Z_{i,1}^{l} \,{,}\ldots{,}\,Z_{i,m}^{l}\right) \in \mathcal{Z}$ and 
>$$
>Z_{i,j}^{l} = \mu_{j}(X_{i}; \psi)\, + \sigma_{j}(X_{i}; \psi)\,\xi_{i,j}^{l}
>$$
>and $\{ \xi_{i,j}^{l} \} \sim \mathcal{N}(0,1)$ are *i.i.d. standard normal random variables*.

>[!info]
>In most cases, it is sufficient to only sample once $L=1$.

### Training Procedure

>[!quote]
>We can summarize VAE training as follows. 
>- For each data point in a minibatch, 
>	- **forward propagate** through the **encoder network** to evaluate the **means** and **variances** of the *approximate latent distribution*, 
>	- **sample** from this distribution using the *reparameterization trick*, and 
>	- then **propagate** these samples through the **decoder network** to evaluate the **ELBO**. 
>	- The **gradients** with respect to $\theta$ and $\psi$ are then evaluated using **automatic differentiation**. [[Automatic Differentiation]]
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 576

>[!important] Training VAE
>- **INPUT**: 
>	- training data $\mathcal{D} = \{ X_{1} \,{,}\ldots{,}\, X_{n}\}$
>	- **encoder network** $\{ \mu_{j}(x, \psi), \sigma_{j}^2(x, \psi);\; j= 1 \,{,}\ldots{,}\,m \}$
>	- **decoder network** $g(z, \theta) := p_{\theta}(x | z)$
>	- initial weights $\theta$ and $\psi$
>	- learning rate $\eta$
>- **OUTPUT**: weight $\theta$ and $\psi$
>- While not converged:
>	- $\mathcal{L} \leftarrow 0$
>	- for $j =1 \,{,}\ldots{,}\,m$:
>		- **sample** $\xi_{i,j} \sim \mathcal{N}(0,1)$
>		- generate $$Z_{i,j} = \mu_{j}(X_{i}; \psi)\, + \sigma_{j}(X_{i}; \psi)\,\xi_{i,j}$$
>		- update **ELBO estimate** with *KL divergence* $$\mathcal{L} \leftarrow \mathcal{L} + \frac{1}{2}\left\{- \mu_{j}^2(X_{i}, \psi) - \sigma_{j}^2(X_{i}, \psi) + 1 + \log \sigma_{j}^2(X_{i}, \psi)  \right\} $$
>	- update **ELBO estimate** with the *Monte Carlo estimate* $$\mathcal{L} \leftarrow \mathcal{L} + \log p_{\theta}(X_{i}\,|\, Z_{i})$$ where $Z_{i} = (Z_{i,1} \,{,}\ldots{,}\,Z_{i, m}).$
>	- update **decoder weight** $\theta$ with **stochastic gradient descent**, $$\theta \leftarrow \theta + \eta\, \nabla_{\theta} \mathcal{L}$$
>	- update **encoder weight** $\psi$ with **stochastic gradient descent**, 
>	  $$\psi \leftarrow \psi + \eta\, \nabla_{\psi} \mathcal{L}$$

- [[Stochastic Gradient Descent Algorithm]]

>[!warning]
>When training VAEs, a **problem** can arise in which the **variational distribution** $q(z|x; \psi)$ converges to the *prior distribution* $p(z)$ and therefore becomes **uninformative** because it no longer depends on $x$. In effect, the latent code is *ignored*.
>
>This is known as **posterior collapse**. A symptom of this is that if we take an input and encode it and then *decode* it, we get a *poor reconstruction* that looks blurry.


## Explanation


### Compare to Diffusion Network

![[Denoising Diffusion Probabilistic Models and Diffusion Network#^90afc8]]

- [[Denoising Diffusion Probabilistic Models and Diffusion Network]]

## Other Variants

- [[Gumbel Softmax]]




-----------
##  Recommended Notes and References

- [[Artificial Neural Network and Deep Learning]]


- [[Deep Learning Foundations and Concepts by Bishop]] pp 569 - 578
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 781 - 810
- [[Deep Learning by Goodfellow]]
- [[Foundations of Computer Vision by Torralba]] pp 493 - 505