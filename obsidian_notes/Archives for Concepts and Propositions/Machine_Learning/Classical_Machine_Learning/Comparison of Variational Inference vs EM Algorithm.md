---
tags:
  - thought
  - machine_learning/models
  - machine_learning/algorithms
  - machine_learning/latent_variable_model
  - deep_learning/variational_learning
keywords:
  - variational_inference
  - em_algorithm
  - expectation_maximization
  - evidence_lower_bound
topics:
  - machine_learning_models
  - machine_learning_algorithm
name: Variational Inference vs EM Algorithm
date of note: 2024-07-05
---

## Concept Definition

>[!important]
>**Name**: Variational Inference vs EM Algorithm

>[!info] 
>Let $(X, Z) \in \mathcal{X} \times \mathcal{Z}$ be a pair of random variables with *joint p.d.f.* $p_{\theta}(x, z)$ where $\theta\in \Theta$.  The *marginal distribution* of $Z$ is denoted as $p(z)$, and the *conditional probability* of $X$ given $Z$ is $p_{\theta}(x | z)$. Note that the joint density function with respect to some nominating measure $\nu$ is
>$$
>p_{\theta}(x, z) = p_{\theta}(x | z)\,p(z).
>$$
>
>Given an arbitrary density $q(z)$ on latent variable $Z$, the **evidence lower bound (ELBO)** or the **variational lower bound**, 
>$$
>\begin{align*}
>\mathcal{L}(q, \theta; x) &:= \mathbb{E}_{ q }\left[ \log \left(\frac{p_{\theta}(x, z)}{q(z)}\right) \right] \\[5pt]
>&= \int_{\mathcal{Z}}\;q(z)\log \left(\frac{p_{\theta}(x | z)\,p(z)}{q(z)}\right)d\nu_{Z}.
\end{align*}
>$$
>
>Let $p(z| x. \theta)$ be the *posterior density* of $Z$ given $X$, associated with *joint p.d.f.* $$p(z | x, \theta) = \frac{p_{\theta}(x, z)}{p(x)} = \frac{p_{\theta}(x | z)\,p(z)}{p(x)}.$$ Then the following equation holds
>$$
>\log p_{\theta}(x) = \mathcal{L}(q, \theta; x) + \mathbb{KL}\left( q(z) \left\|\right. p(z | x, \theta) \right), \quad \forall q\in \mathscr{P}_{Z}, \; \forall \theta \in \Theta
>$$ 
>where 
>- $$p_{\theta}(x) = \int_{\mathcal{Z}}p_{\theta}(x | z)\,p(z)\,d\nu_{Z} = \int_{\mathcal{Z}}p_{\theta}(x , z)\,d\nu_{Z}$$ is the **marginal density (evidence)** of $x$.
>- $\mathbb{KL}\left( q(z) \left\|\right. p(z | x, \theta) \right)$ is the *relative entropy* from $p(\cdot|x)$ to $q$.

- [[Evidence Lower Bound]]
- [[Kullback-Leibler Divergence]]

>[!important]
>Consider a set of $n$ i.i.d. samples $\{ (X_{i}, Z_{i}): i=1 \,{,}\ldots{,}\,n \}$ and  $\mathcal{D}:= \{ X_{1} \,{,}\ldots{,}\,X_{n}\}$ represents the **observed data**, then the **log-marginal-likelihood** of *observed data* $\mathcal{D}$ satisfies the equation
>$$
>\log p_{\theta}(\mathcal{D}) = \sum_{i=1}^{n}\mathcal{L}(q, \theta; X_{i}) + \sum_{i=1}^{n}\mathbb{KL}\left( q(Z_{i}) \left\|\right. p(Z_{i} | X_{i}, \theta) \right)
>$$
>where $Z_{i}$ is the **hidden variable** *associated with each* $X_{i}$ and $$q(z) = \prod_{i=1}^{n}q(z_{i})$$ is assumed to a product density. The ELBO for each sample is
>$$\mathcal{L}(q, \theta; X_{i}) := \mathbb{E}_{ Z_{i} }\left[ \log \left(\frac{p_{\theta}(X_{i}, Z_{i})}{q(Z_{i})}\right) \right] = \int_{\mathcal{Z}}\;q(z_{i})\log \left(\frac{p_{\theta}(X_{i} | z_{i})\,p(z_{i})}{q(z_{i})}\right)d\nu_{Z}(z_{i})$$


## Maximizing the ELBO vs. Minimizing the KL Divergence

>[!important]
>The above equation holds for any distribution $q(z)$, thus in order to **maximize the marginal likelihood**, we can **choose** $q$ such that
>-  **the ELBO is maximized** given data $\mathcal{D}$.
>$$
>q^{*} \in  \arg\max\left\{ \sum_{i=1}^{n}\mathbb{E}_{ Z_{i} \sim q }\left[ \log \left(\frac{p_{\theta}(X_{i} | Z_{i})p(Z_{i})}{q(Z_{i})}\right) \right]:\quad q \in \mathscr{P}_{\mathcal{Z}} \right\} 
>$$
>- This is equivalent to **minimizing the KL divergence**
>$$
>q^{*} \in  \arg\min\left\{ \sum_{i=1}^{n}\mathbb{KL}\left( q(Z_{i}) \left\|\right. p(Z_{i} | X_{i}, \theta) \right):\quad q \in \mathscr{P}_{\mathcal{Z}} \right\} 
>$$
>
>
>Note that since the ELBO depends on $x$, the optimal **variational density** $q^{*}$ is also a *function* of $x$, i.e. it is a posterior density of $Z$ given $x$, $$q^{*} = q(\cdot | x).$$

## EM Algorithm as Minimizing the KL Divergence

>[!important]
>In **Expectation-Maximization algorithm**, 
>- **E-step**: choose the *optimal variational density* $q_{t+1}$ to be **equal to** the *posterior density* $p(\cdot | x, \hat{\theta}_{k})$ i.e. $$
> \sum_{i=1}^{n}\mathbb{KL}\left( q_{t+1}(Z_{i}) \left\|\right. p(Z_{i} | X_{i}, \hat{\theta}_{k}) \right) = 0
>$$
>- **M-step**: choose $\theta$ that maximize the **ELBO** $$\hat{\theta}_{k+1} \in \arg\max_{\theta\in \Theta}\left\{ \mathcal{L}(q_{t+1}, \theta; x) \right\}.$$
>
>In this case, the **ELBO is maximized** so that it is **equal to the evidence (log-marginal-likelihood)** of $\mathcal{D}$ 
>$$
>\log p_{\theta}(\mathcal{D}) = \sum_{i=1}^{n}\mathcal{L}(p(\cdot|X_{i}, \theta), \theta; X_{i})
>$$

- [[Expectation-Maximization Algorithm]]
- [[Information Projection and Moment Projection]]

## Variational Inference as Maximizing the ELBO

>[!important]
>In **variational inference algorithm**, there are several additional **assumptions**:
>- Due to complexity of $p_{\theta}(x| z)$, we **cannot compute the posterior density function** $p(\cdot | x, \hat{\theta}_{k})$ directly.
>- assume that the variational density is from a parametric family as well $$q \in \left\{ q_{\psi}: \psi \in \Psi \right\} $$
>
>The **objective** of **variational auto-encoder (VAE)** is to *maximize* the ELBO with respect to parameter pair $(\theta, \psi)$ *jointly*
>$$
>\max_{\theta \in \theta, \psi \in \Psi}\sum_{i=1}^{n}\mathcal{L}(q_{\psi}, \theta; X_{i})
>$$
>where
>- $$q_{\psi} := q(z| x, \psi), \quad \forall x\in \mathcal{X}$$ as a function of $x$ is called an **encoder**
>- $$p(x | z, \theta), \quad \forall z\in \mathcal{Z}$$ as a function of $z$ is called a **decoder**.
>  
>The VAE trained two networks (encoder and decoder networks) **jointly**.

- [[Expectation-Maximization Algorithm#EM Algorithm as Coordinate Ascent Algorithm]]
- [[Parametric Models]]
- [[Variational Auto-Encoder]]
 
>[!important]
>In **variational inference algorithm**, there are several additional **assumptions**:
>- Due to complexity of $p_{\theta}(x| z)$, we **cannot obtain the closed form** of **posterior density function** $p(\cdot | x, \theta)$.
>- assume that the variational density is from a parametric family as well $$q \in \left\{ q_{\psi}: \psi \in \Psi \right\} $$
>
>The **objective** of **variational auto-encoder (VAE)** is to *maximize* the ELBO with respect to parameter pair $(\theta, \psi)$ *jointly*
>$$
>\max_{\psi \in \Psi,\, \theta \in \Theta}\sum_{i=1}^{n}\mathcal{L}(q_{\psi}, \theta; X_{i})
>$$
>where
>- $$q_{\psi} := q(z| x, \psi), \quad \forall x\in \mathcal{X}$$ as a function of $x$ is called an **encoder** with parameter $\psi \in \Psi$
>- $$p(x | z, \theta), \quad \forall z\in \mathcal{Z}$$ as a function of $z$ is called a **decoder** with parameter $\theta \in \Theta$.
>  
>The VAE trained two networks (encoder and decoder networks) **jointly**. Sometimes, the ELBO $\mathcal{L}(q_{\psi}, \theta; X_{i})$ is called an **energy functional**.

- [[Expectation-Maximization Algorithm#EM Algorithm as Coordinate Ascent Algorithm]]
- [[Parametric Models]]
- [[Variational Auto-Encoder]]
- [[Probabilistic Graphical Models by Koller]] pp 914


## Explanation

>[!important]
>Compare VAE and EM algorithm we see that
>1. In terms of the *functional form* of the **true posterior density** $p(z| x, \theta)$:
>	- in **EM algorithm**, the *true posterior density* $p(z| x, \hat{\theta}_{k})$  at given parameter $\hat{\theta}_{k}$ can be represented in **closed form**
>	- In **VAE**, the *posterior density* $p(z| x, \theta)$ has **no closed form**, and is *approximated* by an **encoder network** $q(z | x, \psi)$ with parameter $\psi$
>2. In terms of *algorithm*:
>	- in **EM algorithm**, we update the *posterior density* $p(z| x, \hat{\theta}_{k})$  and the *point estimator* $\hat{\theta}_{k}$ **iteratively** as in coordinate descent algorithm.
>	- in **VAE**, both parameters $(\psi, \theta)$ for **encoder-decoder** are trained **jointly**
>3. In terms of *performance guarantee*:
>	- **EM algorithm** guarantee to **maximize** the *marginal log-likelihood* $p_{\theta}(x)$ when converges.
>	- **VAE** has *no theoretical guarantee* as the choice of the *family of variational densities* (i.e. the function space of **encoder networks**) may not contain the *true posterior density.*

### Comparison via ChatGPT

>[!important]
>- _EM_ is a **special, exact** coordinate-ascent on the log-likelihood that works when the posterior moments are tractable. 
>- _Variational inference_ generalises the idea: replace the true posterior with a _learned approximation_ so expectation steps and gradients remain feasible, sacrificing *exactness* for *scalability* and flexibility in modern Bayesian and deep generative models.


| Aspect                               | **Expectation-Maximization (EM)**                                                                                                                                                                                                      | **Variational Inference (VI)**                                                                                                                                                                                    |
| ------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Goal**                             | Maximize the **log-likelihood** $$\log p_\theta(X)$$ for latent-variable models.                                                                                                                                                       | Approximate the **posterior** $$p_\theta(Z\mid X)$$ (and often the **evidence**) by optimisation over a *tractable family* $q(Z)$.                                                                                |
| **Core idea**                        | Alternate between <br>- **E-step:** exact expectation under the _true_ posterior $$p(Z\mid X,\theta^{\text{old}}).$$<br>- **M-step:** maximise that *expected complete-data log-likelihood* w.r.t. $\theta$.                           | Turn inference into *optimisation* of the **ELBO**  $$\mathcal L(q,\theta)=\mathbb E_q[\log p_\theta(X,Z)]-\mathbb E_q[\log q(Z)].$$ Update q and $\theta$ *jointly* or alternately.                              |
| **Update for latent variables**      | *Closed-form* when the posterior is in the *same exponential family* as the prior (e.g. **GMM**, **HMM**).                                                                                                                             | Choose a *factorised*/parameterised $q$ (**mean-field**, **structured**, **amortised**) and optimise its parameters with *closed-form*, *coordinate ascent*, or *gradient methods*.                               |
| **Update for parameters $\theta$**   | - *Closed-form* maximisation for many conjugate models; <br>- otherwise numerical.                                                                                                                                                     | **Same**: maximise ELBO w.r.t. $\theta$, but relies on the _approximate_ posterior $q$, not the true one.                                                                                                         |
| **Guarantees**                       | - Monotonically **increases** data log-likelihood; <br>- converges to a local maximum.                                                                                                                                                 | - Monotonically **increases** ELBO; <br>- converges to a local optimum of ELBO (a _lower bound_ on log-likelihood).                                                                                               |
| **When is EM a special case of VI?** | EM = VI with **delta-function $$q(\theta)=\delta(\theta− \theta^{old})$$** and exact E-step (i.e. q(Z)=p(Z\mid X,θ)).                                                                                                                  | –                                                                                                                                                                                                                 |
| **Computational trade-off**          | - Requires _exact_ posterior expectations ⇒ feasible only with *conjugacy* or small latent space.                                                                                                                                      | - Trades exactness for *tractability*; <br>- scales to massive, non-conjugate models via stochastic gradients, **re-parameterisation**, **amortisation** (VAE).                                                   |
| **Outputs**                          | - *MLE/MAP* estimate $\hatθ$.<br>- Optionally *posterior* $$p(Z\mid X,\hat θ)$$ (already computed in E-step).                                                                                                                          | - Full **variational posterior** $q(Z)$ (and sometimes $q(\theta)$).<br>- *Approximate* evidence lower bound for model comparison.                                                                                |
| **Typical uses**                     | - **GMM** [[Gaussian Mixture Models or GMM]]<br>- **HMM,** [[Hidden Markov Model]] <br>- mixture of experts,<br>- **factor analysis**, [[Factor Analysis]] <br>- **probabilistic PCA**. [[Probabilistic Principal Component Analysis]] | - **Latent Dirichlet Allocation**,  [[Latent Dirichlet Allocation or LDA]]<br>- **Bayesian neural networks**, <br>- **variational auto-encoders**, [[Variational Auto-Encoder]]<br>- deep latent Gaussian models. |
| **Strengths**                        | Simple, closed-form, fast per-iteration; **exact** in E-step.                                                                                                                                                                          | Flexible, handles non-conjugate models, yields uncertainty over latents/parameters, amenable to *stochastic and amortised variants.*                                                                              |
| **Weaknesses**                       | - Limited to models with **tractable posteriors**; <br>- no distribution over θ; <br>- can get stuck in poor local maxima.                                                                                                             | - Gives only an _approximate_ posterior; <br>- quality depends on variational family; <br>- optimisation can be sensitive and slower per iteration.                                                               |




## Variational EM

- [[Variational Expectation-Maximization]]
- [[Mean Field Approximation for PGM]]

## Variational Bayes

- [[Variational Bayesian Learning]]

## Variational Inference in Deep Learning

- [[Variational Auto-Encoder]]
- [[Denoising Diffusion Probabilistic Models and Diffusion Network]]



-----------
##  Recommended Notes and References

- [[Evidence Lower Bound]]
- [[Information Projection and Moment Projection]]

- [[Variational Inference for Clique Tree]]

- [[Marginalized Likelihood Function]]
- [[Likelihood Function]]
- [[Conditional Probability]]


- [[Elements of Statistical Learning by Hastie]]
- [[Deep Learning Foundations and Concepts by Bishop]] pp 569 - 578

- [[Probabilistic Graphical Models by Koller]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 433
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Deep Learning by Goodfellow]] pp 629