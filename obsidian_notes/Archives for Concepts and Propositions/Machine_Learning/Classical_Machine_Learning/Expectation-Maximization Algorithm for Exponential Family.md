---
tags:
  - concept
  - statistics/estimation
  - machine_learning/models
  - machine_learning/algorithms
keywords:
  - expectation_maximization
  - exponential_family
  - bregman_divergence
topics:
  - machine_learning_models
  - machine_learning_algorithm
name: Expectation-Maximization Algorithm for Exponential Family
date of note: 2024-07-06
---

## Concept Definition

>[!important]
>**Name**: Expectation-Maximization Algorithm for Exponential Family

![[Expectation-Maximization Algorithm#^b34608]]

>[!important] Definition
>Let $(X, Z) \in \mathcal{X} \times \mathcal{Z}$ be a sample pair from *an exponential family* $\{p_{\theta}(x, z), \theta\in \Theta\}$, i.e.
>$$\log p_{\theta}(x, z)   = \left\langle  \theta\,,\, T(x, z) \right\rangle - A(\theta).$$ The *marginal p.d.f.* of $Z$ is denoted as $p(z)$, and the *conditional p.d.f.* of $X$ given $Z$ is $p_{\theta}(x|z)$. Assume that $X$ is *observed* and $Z$ is *unobserved*.
>
>Consider the class of all density function $q_{\eta}(z | x)$ of $Z$ from the same *exponential family* that contains $p_{\theta}(z | x)$. That is, the *variational density* $q$ is of the same form
>$$
>\log q_{\eta}(z|x) := \left\langle  \eta\,,\, T(x, z) \right\rangle - A_{x}(\eta),
>$$
>where for each fixed $x$, the *log-partition function* for the posterior is $$A_{x}(\eta) := \log \int_{\mathcal{Z}}\,\exp \left(\left\langle  \eta\,,\, T(x, z) \right\rangle\right)\, d\nu(z).$$
>
>For $q_{\eta}(z | x)$, the **primal-dual representation** for **evidence lower bound (ELBO)** is given by
>$$
>\begin{align*}
>\mathcal{L}(\mu_{x}, \theta\,; x) &:= \left\langle  \theta\,,\, \mu_{x} \right\rangle - A_{x}^{*}(\mu_{x})  - A(\theta). 
\end{align*}
>$$
>where $\mu_{x}$ is the *mean parameters* of the variational density,  $$\mu_{x} := \mathbb{E}_{ \eta }\left[T(x, Z)\right],$$ and $$A_{x}^{*}(\mu_{x}) := \sup_{\eta \in \Theta}\left\{ \left\langle  \eta\,,\,\mu_{x} \right\rangle - A_{x}(\eta) \right\}.$$

>[!important] Definition
>The **expectation-maximization (EM) algorithm** for exponential family works as below:
>- Repeat the following steps until convergence:
>	- **E-Step**: *Estimate* the **mean parameter** of the *variational density* based on previous *estimated parameters* $\hat{\theta}^{k}$ and observed data $x$ $$\hat{\mu}_{x}^{k+1} = \arg\max_{\mu_{x}\in \mathcal{M}_{x}} \mathcal{L}(\mu_{x}, \hat{\theta}^{k}\,; x) $$ where $$\mathcal{M}_{x} := \{ \mu_{x}\in \mathbb{R}^{d}:\, \mu_{x} := \mathbb{E}_{p}\left[T(x, Z)\right] \text{ for some }p \}$$
>	- **M-Step**: *Estimate* $\hat{\theta}^{k+1}$ of complete likelihood by **maximizing** the *proposed log-likelihood function* $$\hat{\theta}^{k+1} = \arg\max_{\theta \in \Theta}\,\mathcal{L}(\mu_{x}^{k+1}, \theta\,; x) $$
>	- $k \leftarrow k+1$.


- [[Evidence Lower Bound for Exponential Family]]
- [[Exponential Family of Distributions]]
- [[Expectation-Maximization Algorithm]]
- [[Evidence Lower Bound]]
## Explanation


## Variational EM for Exponential Family

>[!important] Definition
>The **variational expectation-maximization (EM) algorithm** for exponential family works as below:
>- Repeat the following steps until convergence:
>	- **Mean-Field E-Step**: *Estimate* the **mean parameter** of the *mean field variational density* based on previous *estimated parameters* $\hat{\theta}^{k}$ and observed data $x$. For  $$\hat{\mu}_{x}^{k+1} = \arg\max_{\mu_{x}\in \mathcal{M}(\phi)} \mathcal{L}(\mu_{x}, \hat{\theta}^{k}\,; x) $$ where the optimization is over a **marginal polytope** via **mean field approximation** $$\mathcal{M}(\phi):= \{ \mu\in \mathbb{R}^{d}:\, \mu := \mathbb{E}_{p}\left[\phi(Z)\right] \text{ for some }p \}.$$
>	- **M-Step**: *Estimate* the **natural parameter** by $$\hat{\theta}^{k+1} = \arg\max_{\theta \in \Theta}\,\mathcal{L}(\hat{\mu}_{x}^{k+1}, \theta\,; x) $$
>	- $k \leftarrow k+1$.

- [[Mean Field Approximation]]



-----------
##  Recommended Notes and References



- [[Expectation-Maximization Algorithm]]
- [[Evidence Lower Bound]]

- [[Log-Partition Function of Exponential Family]]

- [[Bregman Divergence]]
- [[Bregman Projection]]
- [[Bregman Distance Minimization]]
- [[Kullback-Leibler Divergence]]

- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
