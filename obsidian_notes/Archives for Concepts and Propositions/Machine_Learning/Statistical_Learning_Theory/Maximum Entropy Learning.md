---
tags:
  - concept
  - machine_learning/theory
  - machine_learning/models
keywords:
  - maximum_entropy_learning
topics:
  - machine_learning_theory
name: Maximum Entropy Learning
date of note: 2024-05-14
---

## Concept Definition

>[!important]
>**Name**: Maximum Entropy Learning

>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F})$ be a measurable space and  $\mathscr{P}(\mathcal{X})$ be the *space of all probability measures* on $\mathcal{X}$.
>
>- Denote $\mathcal{P}_{0}\in \mathscr{P}(\mathcal{X})$ as a probability distribution, i.e. *prior measure*. 
>- Let $\mathcal{D} := \left\{ X_{1}\,{,}\ldots{,}\, X_{n}\right\}$ be i.i.d samples in $\mathcal{X}$ and let the *empirical measure* be $$\mathcal{P}_{n} = \frac{1}{n}\sum_{i=1}^{n}\;\delta_{X_{i}}.$$
>- Define a *feature map* $\phi$ as $$\phi: \mathcal{X} \to \mathcal{H}$$ with $$\lVert \phi \rVert_{\infty} := \sup_{x\in \mathcal{X}}\;\lVert \phi(x) \rVert_{\mathcal{H}}  \le r.$$
>  
>The **maximum entropy learning** or the **principle of maximum entropy** can be formulated as the following optimization problem:
>$$
>\begin{align*}
> \min_{P\in \mathscr{P}(\mathcal{X})}\;&\; \mathbb{KL}\left( \mathcal{P} \left\|\right. \mathcal{P}_{0} \right) \\[8pt]
>\text{s.t. } & \lVert \;\mathbb{E}_{ \mathcal{P} }\left[  \phi(X) \right] - \mathbb{E}_{ \mathcal{P}_{n} }\left[  \phi(X) \right] \;\rVert_{\mathcal{H}} \le \lambda 
>\end{align*}
>$$
>
>- The constraint corresponds to the bound on the *maximum mean discrepancy* $$\lVert \;   \mathbb{E}_{ \mathcal{P} }\left[\phi(X) \right] - \mathbb{E}_{ \mathcal{P}_{n} }\left[\phi(X) \right] \;\rVert_{\mathcal{H}} := \lVert \; \mu(\mathcal{P}) - \mu(\mathcal{P}_{n}) \;\rVert_{\mathcal{H}} \le \lambda $$ where $\mu: \mathscr{P}(\mathcal{X}) \to \mathcal{H}$ is the *kernel mean embedding.*

^7f19cd


- [[Space of Bounded Signed Measures]]
- [[Probability Space]]
- [[Measure Space and Countably Additive Measure]]
- [[Empirical Process and Empirical Measure]]
- [[Variational Formula for Kullback-Leibler Divergence]]
- [[Kullback-Leibler Divergence]]
- [[Feature Map for Reproducing Kernels in RKHS]]
- [[Kernel Mean Embedding of Distribution]]
- [[Maximum Mean Discrepancy between Probability Measures via RKHS]]

### Solution of Maximum Entropy Learning

>[!important] Theorem
>Let $(\mathcal{X}, \mathscr{F})$ be a measurable space and  $\mathscr{P}(\mathcal{X})$ be the *space of all probability measures* on $\mathcal{X}$.
>
>- Denote $\mathcal{P}_{0}\in \mathscr{P}(\mathcal{X})$ as a probability distribution, i.e. *prior measure*. 
>- Let $\mathcal{D} := \left\{ X_{1}\,{,}\ldots{,}\, X_{n}\right\}$ be i.i.d samples in $\mathcal{X}$ and let the *empirical measure* be $$\mathcal{P}_{n} = \frac{1}{n}\sum_{i=1}^{n}\;\delta_{X_{i}}.$$
>- Define a *feature map* $\phi$ as $$\phi: \mathcal{X} \to \mathcal{H}$$ with $$\lVert \phi \rVert_{\infty} := \sup_{x\in \mathcal{X}}\;\lVert \phi(x) \rVert_{\mathcal{H}}  \le r.$$
>  
>Then there exists a **unique optimal solution** $\mathcal{P}^{*}\in \mathscr{P}(\mathcal{X})$ for the **maximum entropy learning problem** i.e.
>$$
>\begin{align*}
> \mathcal{P}^{*} = \arg\min_{P\in \mathscr{P}(\mathcal{X})}\;&\; \mathbb{KL}\left( \mathcal{P} \left\|\right. \mathcal{P}_{0} \right) \\[8pt]
>\text{s.t. } & \lVert \;\mathbb{E}_{ \mathcal{P} }\left[  \phi(X) \right] - \mathbb{E}_{ \mathcal{P}_{n} }\left[  \phi(X) \right] \;\rVert_{\mathcal{H}} \le \lambda 
>\end{align*}
>$$
>
>- Moreover, the p.d.f. of $\mathcal{P}^{*}$ is of the form of a **Gibbs distribution**, i.e. $$p^{*}(x) =  \frac{d\mathcal{P}^{*}(x)}{dx} = p_{0}(x)\,\exp \left( \left\langle  f^{*}\,,\, \phi(x)   \right\rangle_{\mathcal{H}} - A(f) \right)$$ where 
>	- $A(f)$ is the **log-partition function** of $\mathcal{P}^{*}$ i.e. $$A(f) := \log\,\int_{x\in \mathcal{X}}p_{0}(x)\,\exp \left( \left\langle  f^{*}\,,\, \phi(x)   \right\rangle_{\mathcal{H}} \right)dx $$
>- And the **optimal** (functional) parameter $f^{*}\in \mathcal{H}$ can be found by solving the **regularized risk mimization** problem $$\sup_{f\in \mathcal{H}}\; \frac{1}{n} \sum_{i=1}^{n}\;\left\langle  f\,,\, \phi(x_{i})   \right\rangle_{\mathcal{H}} - \lambda\,\lVert f \rVert_{\mathcal{H}}   $$

- [[Gibbs Distribution]]
- [[Gibbs Measure and Energy-based Model]]
- [[Exponential Family of Distributions]]
- [[Log-Partition Function of Exponential Family]]
- [[Representer Theorem]]

## Explanation

### Extension to Bregman Divergence Minimization

>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F})$ be a measurable space and  $\mathscr{P}(\mathcal{X})$ be the *space of all probability measures* on $\mathcal{X}$.
>
>- Denote $\mathcal{P}_{0}\in \mathscr{P}(\mathcal{X})$ as a probability distribution, i.e. *prior measure*. 
>- Let $\mathcal{D} := \left\{ X_{1}\,{,}\ldots{,}\, X_{n}\right\}$ be i.i.d samples in $\mathcal{X}$ and let the *empirical measure* be $$\mathcal{P}_{n} = \frac{1}{n}\sum_{i=1}^{n}\;\delta_{X_{i}}.$$
>- Define a *feature map* $\phi$ as $$\phi: \mathcal{X} \to \mathcal{H}$$ with $$\lVert \phi \rVert_{\infty} := \sup_{x\in \mathcal{X}}\;\lVert \phi(x) \rVert_{\mathcal{H}}  \le r.$$
>- The *Bregman divergence* associated with a *convex function* $\psi: \mathscr{P}(\mathcal{X})\to \mathbb{R}$ for p.d.f. $p,q \in \mathscr{P}(\mathcal{X})$  is defined as $$\mathbb{D}_{\psi}\left( p \left\|\right. q\right) = \psi(p) - \psi(q) - \left\langle  \nabla \psi(p)\,,\,  p - q \right\rangle$$
>  
>The **Bregman divergence minimization** can be seen as an extension of the *maximum entropy learning*, which is described as follow:
>$$
>\begin{align*}
> \min_{\mathcal{P}\in \mathscr{P}(\mathcal{X})}\;&\; \mathbb{D}_{\psi}\left( \mathcal{P} \left\|\right. \mathcal{P}_{0}\right) \\[8pt]
>\text{s.t. } & \lVert \;\mathbb{E}_{ \mathcal{P} }\left[  \phi(X) \right] - \mathbb{E}_{ \mathcal{P}_{n} }\left[  \phi(X) \right] \;\rVert_{\mathcal{H}} \le \lambda 
>\end{align*}
>$$

- [[Bregman Divergence]]
- [[Bregman Divergence Minimization]]


## Applications


### Exponential Family and Mixture Family

![[Maximum Entropy Learning of Exponential Family#^e73c44]]

- [[Maximum Entropy Learning of Exponential Family]]
- [[Mixture Family of Distributions]]


### Boosting

- [[Iterative Maximum Entropy Learning for AdaBoost]]


### Probabilistic Graphical Model

![[Energy Functional for Probabilistic Graphical Model#^c01c98]]

![[Bethe Entropy Approximation and Factorized Energy Functional#^64315b]]

- [[Bethe Entropy Approximation and Factorized Energy Functional]]
- [[Energy Functional for Probabilistic Graphical Model]]
- [[Maximum Entropy Learning of Clique Tree PGM]]

![[Maximum Entropy Learning for Approximate Inference in PGM#^5fbd75]]

- [[Maximum Entropy Learning for Approximate Inference in PGM]]
- [[Marginal Polytope and Local Consistent Polytope]]

![[Mean Field Approximation for PGM#^ddaaef]]

- [[Mean Field Approximation for PGM]]
- [[Mean Field Approximation for Exponential Family]]


### Reinforcement Learning

- [[Maximum Entropy Reinforcement Learning]]



-----------
##  Recommended Notes and References

- [[Information Projection and Moment Projection]]
- [[Polyhedron and Polytope]]

- [[Gibbs Measure and Energy-based Model]]



- [[Probabilistic Graphical Models]]

- [[Maximum Likelihood Estimation]]


- [[Elements of Information Theory by Cover]] pp 409 - 425
- [[Foundations of Machine Learning by Mohri]] pp 295 - 308, 312 - 319, 330
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 64
- [[Probabilistic Graphical Models by Koller]] pp 956 - 958