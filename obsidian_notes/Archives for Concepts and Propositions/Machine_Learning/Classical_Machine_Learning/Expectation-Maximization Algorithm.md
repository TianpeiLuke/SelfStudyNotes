---
tags:
  - concept
  - machine_learning/algorithms
  - statistics/estimation
keywords:
  - expectation_maximization
topics:
  - machine_learning_models
  - machine_learning_algorithm
name: Expectation-Maximization Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Expectation-Maximization Algorithm

>[!important] Definition
>Let $(X, Z) \in \mathcal{X} \times \mathcal{Z}$ be a sample pair from *a parametric family* $\{p_{\theta}(x, z), \theta\in \Theta\}$ where $X$ is *observed* variable and $Z$ is the *latent* variable. The **complete log-likelihood function** of $\theta \in \Theta$ for $(X, Z)$ is $$\ell(\theta; x, z) = \log p_{\theta}(x, z).$$
>
>
>The **expectation-maximization (EM) algorithm** works as below:
>- Repeat the following steps until convergence:
>	- **E-Step**: Decide the **conditional expectation** of **complete log-likelihood function** based on previous *estimated parameters* $\hat{\theta}_{k}$ and observed data $x$ $$Q(\theta; \hat{\theta}_{k}) := \mathbb{E}_{ p }\left[  \ell(\theta; x, z) \;|\; x, \hat{\theta}_{k} \right]$$ where $p(z| x, \hat{\theta}_{k})$ is the *posterior density* of latent variable $Z$ given observed data $x$ and $\hat{\theta}_{k}$.
>	- **M-Step**: *Estimate* $\hat{\theta}_{k+1}$ by **maximizing** the *proposed log-likelihood function* $$\hat{\theta}_{k+1} \in \arg\max_{\theta \in \Theta}\,Q(\theta; \hat{\theta}_{k})$$
>	- $k \leftarrow k+1$.

^0c7718

- [[Parametric Models]]
- [[Statistical Estimation Problem]]
- [[Elements of Statistical Learning by Hastie]] pp 277


## EM Algorithm as Coordinate Ascent Algorithm

>[!important] Proposition
>The **Expectation-Maximization algorithm** is a **coordinate ascent algorithm** that **maximize** the **incomplete log-likelihood** $\log p_{\theta}(x)$.
>
>In particular, define the **evidence lower bound (ELBO)** with respect to arbitrary p.d.f. $q \in \mathscr{P}_{Z}$ on $\mathcal{Z}$
>$$
>\begin{align*}
>\mathcal{L}(q, \theta; x) &:= \mathbb{E}_{ q }\left[ \log \left(\frac{p_{\theta}(x, Z)}{q(Z)}\right) \right] \\[5pt]
>&=  \mathbb{E}_{q }\left[ \log \left(\frac{p_{\theta}(x | Z)\,p(Z)}{q(Z)}\right) \right] \\[5pt]
>&= \int_{\mathcal{Z}}\;q(z)\log \left(\frac{p_{\theta}(x | z)\,p(z)}{q(z)}\right)d\nu_{Z},
\end{align*}
>$$
>where $p_{\theta}(x, z)$ is the joint p.d.f. of $(X, Z)$,  $\nu_{Z}$ is the common dominating base measure on $\mathcal{Z}$ for both $q(z)$ and $p(z)$.
>
>Then **the (generalized) EM algorithm** is equivalent to the following *coordinate ascent algorithm*:
>- Repeat the following steps until convergence:
>	- **E-Step**: choose a *probability density function* $q \in \mathscr{P}_{Z}$ on $\mathcal{Z}$ so that $$q_{t+1} \in \arg\max_{q\in \mathscr{P}_{Z}}\left\{ \mathcal{L}(q, \hat{\theta}_{k}; x) \right\}$$
>	- **M-Step**: choose $\hat{\theta}_{k+1}$ that **maximize the ELBO** given $q_{t+1}$, i.e. $$\hat{\theta}_{k+1} \in \arg\max_{\theta\in \Theta}\left\{ \mathcal{L}(q_{t+1}, \theta; x) \right\}.$$
>	- $k \leftarrow k+1$.
>	  

^b34608

- [[Evidence Lower Bound]]
- [[Block Coordinate Descent Algorithm]]

### Variational EM

>[!important] Definition
>The EM problem that solves 
>$$
>\max_{\theta \in \Theta}\max_{q \in \mathscr{P}_{Z}}\mathcal{L}(q, \theta; \mathcal{D})
>$$
>is also called the **variational EM.**

- [[Probabilistic Graphical Models by Koller]] pp 895
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]

## Majorization-Minimization Algorithm

>[!important] Definition
> The *EM algorithm* is a **majorization-minimization (MM)** algorithm as follows
>- Repeat the following steps until convergence:
>	- *Choose* $\hat{\theta}_{k+1}$ by **minimizing** the *negative proposed log-likelihood function* $$\hat{\theta}_{k+1} \in \arg\min_{\theta \in \Theta}\,- Q(\theta; \hat{\theta}_{k})$$ where $Q(\theta; \hat{\theta}_{k}) := \mathbb{E}_{ p }\left[  \ell(\theta; x, z) \;|\; x, \hat{\theta}_{k} \right]$ is computed at **E-Step**.
>	- $k \leftarrow k+1$.
>
>Here $$M(\theta; \hat{\theta}_{k}) = - Q(\theta; \hat{\theta}_{k}) := \mathbb{E}_{ p }\left[  - \ell(\theta; x, z) \;|\; x, \hat{\theta}_{k} \right]$$ is called a **(negative) majorization function** or a **surrogate function** in *MM algorithm* and
>$$
>\begin{align*}
>M(\theta; \hat{\theta}_{k}) &= -\log p_{\theta}(x) + \mathbb{KL}\left( p(\cdot | x, \hat{\theta}_{k}) \left\|\right. p(\cdot | x, \theta) \right)\\
>&:= f(\theta) + D(\theta, \theta_{k}).
\end{align*}
>$$
>We have the following property of the surrogate function
>- If $\theta = \hat{\theta}_{k}$, then $$M(\theta; \hat{\theta}_{k}) = f(\theta) := - \log p_{\theta}(x).$$
>- For any $\theta\in \Theta$, $$M(\theta; \hat{\theta}) \ge f(\hat{\theta}) := -\log p_{\hat{\theta}}(x)$$
>  

- [[Majorization-Minimization Algorithm]]
- [[Cross-Entropy Loss Function]]

## Cross Entropy Method and Evolutionary Computation

>[!info]
>Note that the **majorization function** is proportional to the **cross entropy term**
>$$
>- Q(\theta; \hat{\theta}_{k}) \propto  \mathbb{E}_{ Z \sim p(z|x,\, \hat{\theta}_{k}) }\left[ -\log p(Z\,|\,x, \theta)  \right] := H_{ce}(p(\cdot|x,\, \hat{\theta}_{k})\,,\, p(\cdot\,|\,x, \theta))
>$$


- [[Cross-Entropy Loss Function]]
- Brookes, D., Busia, A., Fannjiang, C., Murphy, K., & Listgarten, J. (2020). A view of estimation of distribution algorithms through the lens of expectation-maximization. _Proceedings of the 2020 Genetic and Evolutionary Computation Conference Companion_, 189–190. [https://doi.org/10.1145/3377929.3389938](https://doi.org/10.1145/3377929.3389938)



## em Algorithm via E-Projection and M-Projection

>[!important] Proposition
>A similar algorithm called **em algorithm** is proposed as a **iterative projection algorithm** that **minimize** the **relative entropy** $\mathbb{KL}\left( q \left\|\right. p(\cdot | x, \theta) \right)$.
>
>In particular,  **the em algorithm** is described as below:
>- Repeat the following steps until convergence:
>	- **E-Step**: choose a *probability density function* $q \in \mathscr{P}_{Z}$ on $\mathcal{Z}$ via **e-projection** $$q_{t+1} \in \arg\min_{q\in \mathscr{P}_{Z}}\left\{ \mathbb{KL}\left( q \left\|\right. p(\cdot | x, \hat{\theta}_{t}) \right) \right\}$$
>	- **M-Step**: choose $\hat{\theta}_{k+1}$ via **m-projection**, i.e. $$\hat{\theta}_{k+1} \in \arg\min_{\theta\in \Theta}\left\{ \mathbb{KL}\left( q_{t+1} \left\|\right. p(\cdot | x, \theta)\right)  \right\}.$$
>	- $k \leftarrow k+1$.

- [[Information Projection and Moment Projection]]
- [[Methods of Information Geometry by Amari]]
- Amari, S. I. (1995). Information geometry of the EM and em algorithms for neural networks. _Neural networks_, _8_(9), 1379-1408. 





## EM Algorithm and Bregmann Divergence Minimization



- [[Expectation-Maximization Algorithm for Exponential Family]]
- [[Bregman Divergence Minimization]]



## Explanation

>[!important]
>In high level, in **E-step** of EM algorithm, we are trying to find the proposed density function $q(z)$ as close to the **true posterior density** $p(z | x, \theta)$  as possible. 
>
>Specifically, the **ELBO** can be represented by two terms
>$$
>\mathcal{L}(q, \theta; x) = \log p_{\theta}(x) - \mathbb{KL}\left( q \left\|\right. p(\cdot | x, \theta) \right).
>$$
>And in **E-step**, we are choosing $$q = p(\cdot | x, \hat{\theta}_{t})$$ so that 
>$$
>\mathbb{KL}\left( q \left\|\right. p(\cdot | x, \theta) \right) \to 0.
>$$
>
>For Gaussian mixture model, it is possible to obtain $p(z | x, \theta)$ in closed form, which achieve this goal.

- [[Kullback-Leibler Divergence]]

## Variational EM

- [[Variational Expectation-Maximization]]

## Monte Carlo EM

- [[Monte Carlo Expectation Maximization]]



-----------
##  Recommended Notes and References

- [[Evidence Lower Bound]]
- [[Variational Inference vs EM Algorithm]]
- [[Gaussian Mixture Models]]

- [[Radon-Nikodym Derivative]]
- [[Parametric Models]]
- [[Information Projection and Moment Projection]]


- [[Elements of Statistical Learning by Hastie]] pp 272 - 279
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 283 - 291
- [[Deep Learning Foundations and Concepts by Bishop]] pp 474 - 490, 518 - 521
- [[Elements of Information Theory by Cover]]
- [[Nonlinear Programming by Bertsekas]] pp 554
- [[Probabilistic Graphical Models by Koller]] pp 868- 892, 907-929
- [[Monte Carlo Statistical Methods by Robert]] pp 176 - 182


- [[Kullback-Leibler Divergence]]

