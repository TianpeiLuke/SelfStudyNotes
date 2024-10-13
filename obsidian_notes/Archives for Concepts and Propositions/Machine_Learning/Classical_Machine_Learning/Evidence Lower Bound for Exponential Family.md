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
>**Name**: Evidence Lower Bound for Exponential Family

![[Evidence Lower Bound#^c74005]]


>[!important] Definition
>Let $(X, Z) \in \mathcal{X} \times \mathcal{Z}$ be a sample pair from *an exponential family* $\{p_{\theta}(x, z), \theta\in \Theta\}$, i.e.
>$$\log p_{\theta}(x, z)   = \left\langle  \theta\,,\, T(x, z) \right\rangle - A(\theta).$$ The *marginal p.d.f.* of $Z$ is denoted as $p(z)$, and the *conditional p.d.f.* of $X$ given $Z$ is $p_{\theta}(x|z)$. Assume that $X$ is *observed* and $Z$ is *unobserved*.
>
>By Bayes theorem, the *posterior density* of $Z$ given $x$ is 
>$$
>\begin{align*}
> p_{\theta}(z | x) &=  \frac{p_{\theta}(x, z)}{\int_{\mathcal{Z}}\,p_{\theta}(x, z)\, d\nu(z)} \\[10pt]
> &:= \exp \left(\left\langle  \theta\,,\, T(x, z) \right\rangle - A(\theta\,; x)\right),
>\end{align*}
>$$
>where for each fixed $x$, the *log-partition function* for the posterior is $$A(\theta; x) := \log \int_{\mathcal{Z}}\,\exp \left(\left\langle  \theta\,,\, T(x, z) \right\rangle\right)\, d\nu(z).$$
>
>Consider the class of all density function $q_{\eta}(z | x)$ of $Z$ from the same *exponential family* that contains $p_{\theta}(z | x)$. That is, the *variational density* $q$ is of the same form
>$$
>\log q_{\eta}(z|x) := \left\langle  \eta\,,\, T(x, z) \right\rangle - A(\eta\,; x),
>$$
>
>The **evidence lower bound (ELBO)** or the **variational lower bound** for the *exponential family*, is given by
>$$
>\begin{align*}
>\mathcal{L}(\eta, \theta; x) &:= \mathbb{E}_{ \eta }\left[ \log \left(\frac{p_{\theta}(x, Z)}{q_{\eta}(Z|x)}\right) \right] \\[5pt]
>&=  \mathbb{E}_{ \eta }\left[ \log p_{\theta}(x, Z) - \log q_{\eta}(Z | x) \right] \\[10pt]
>&=   \mathbb{E}_{ \eta }\left[ \left\langle  \theta\,,\, T(x, Z) \right\rangle - A(\theta) -  \left\langle  \eta\,,\, T(x, Z) \right\rangle + A(\eta\,; x) \right] \\[5pt]
>&= \mathbb{E}_{ \eta }\left[ \left\langle  \theta - \eta\,,\, T(x, Z) \right\rangle - A(\theta) + A(\eta\,; x) \right] \\[5pt]
>&= \left\langle  \theta - \eta\,,\, \mathbb{E}_{ \eta }\left[T(x, Z)\right]  \right\rangle - A(\theta) + A(\eta\,; x) \\[5pt]
>&:= \left\langle  \theta - \eta\,,\, \mu_{x} \right\rangle - A(\theta) + A(\eta\,; x)
\end{align*}
>$$
>where $\mu_{x}$ is the *mean parameters* of the variational density,  $$\mu_{x} := \mathbb{E}_{ \eta }\left[T(x, Z)\right] .$$
>
>The **primal representation** of the **ELBO** for **exponential family** has the form
>$$
>\mathcal{L}(\eta, \theta; x) = \left\langle  \theta - \eta\,,\, \mu_{x} \right\rangle - A(\theta) + A(\eta\,; x)
>$$

^5475ea


- [[Exponential Family of Distributions]]
- [[Log-Partition Function of Exponential Family]]
- [[Bregman Divergence]]
- [[Evidence Lower Bound]]

### Primal-Dual Representation of ELBO

>[!important]
>By definition, the **convex conjugate** of log-partition function of variational density, $A_{x}(\eta) := A(\eta\,;x)$, is defined as
>$$
> A_{x}^{*}(\mu_{x}) := \sup_{\eta \in \Theta}\left\{ \left\langle  \eta\,,\,\mu_{x} \right\rangle - A_{x}(\eta) \right\} 
>$$
>Substituting the above definition, we have the **primal-dual representation** of the **ELBO** for **exponential family** 
>$$
>\begin{align*}
>\mathcal{L}(\mu_{x}, \theta; x) &=\left\langle  \theta\,,\, \mu_{x} \right\rangle - A_{x}^{*}(\mu_{x})  - A(\theta). 
>\end{align*}
>$$
>where $$\mu_{x} := \mathbb{E}_{ \eta }\left[T(x, Z)\right]$$ is the **mean parameter** of the **variational density.**

^d69640

- [[Kullback-Leibler Divergence for Exponential Family#Mixed Form]]
- [[Convex Conjugate Function]]
- [[Legendre Transform]]


## Explanation

![[Kullback-Leibler Divergence for Exponential Family#^1737d6]]




## KL Divergence

![[Kullback-Leibler Divergence for Exponential Family#^a7c80d]]

- [[Kullback-Leibler Divergence for Exponential Family]]


## EM Algorithm

- [[Expectation-Maximization Algorithm for Exponential Family]]




-----------
##  Recommended Notes and References


- [[Expectation-Maximization Algorithm]]
- [[Log-Partition Function of Exponential Family]]
- [[Exponential Family of Distributions]]
- [[Energy Functional for Probabilistic Graphical Model]]



- [[Bregman Divergence]]
- [[Bregman Projection]]
- [[Kullback-Leibler Divergence]]

- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 154 - 156
