---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/theory
  - probabilistic_graphical_models/models
  - machine_learning/theory
keywords:
  - log_partition_function
  - score_function
  - probabilistic_graphical_model
topics:
  - probabilistic_graphical_model
name: Log-Partition Function and Score Function of Graphical Models
date of note: 2024-08-03
---

## Concept Definition

>[!important]
>**Name**: Log-Partition Function and Score Function of Graphical Models

![[Gibbs Distribution#^ea2e18]]

>[!important] Definition
>Consider a *Markov network* $(\mathcal{H}, \mathcal{P}_{\Phi})$, where $\mathcal{P}_{\Phi}$ is a *Gibbs distribution* parameterized by factors $\Phi$ i.e. the p.d.f. is of the form
> $$
> \mathcal{P}(x; \Phi) = \frac{1}{Z(\Phi)}\hat{\mathcal{P}}(x; \Phi) = \frac{1}{Z(\Phi)}\prod_{i=1}^{k}\phi(D_{i})
> $$
> where $Z(\Phi)$ is the **partition function** of *Markov network* 
> $$
> Z(\Phi) = \sum_{x}\hat{\mathcal{P}}(x; \Phi) = \sum_{(D_{1} \,{,}\ldots{,}\,D_{k})}\prod_{i=1}^{k}\phi(D_{i})
> $$

- [[Clique Tree Invariant of Sum Product and Reparameterization of PGM]]

![[Exponential Family of Distributions#^c95a01]]


>[!important] Definition
>Given the likelihood function $\ell(\theta; x) := \mathcal{P}_{\theta}(x)$ of Gibbs distribution parameterized by $\theta$, the **score function** or the **log-likelihood gradient** *with respect to* $\theta$ is defined as 
>$$
>\begin{align*}
>\nabla_{\theta}\log \ell(\theta; x) := \nabla_{\theta}\log \mathcal{P}(x; \theta) &= \nabla_{\theta}\log \hat{\mathcal{P}}(x; \theta) - \nabla_{\theta} \log Z(\theta) \\
>&=\nabla_{\theta}\log \hat{\mathcal{P}}(x; \theta) -  \mathbb{E}_{ \mathcal{P}_{\theta} }\left[ \nabla_{\theta} \log \hat{\mathcal{P}}(X; \theta)\right]
>\end{align*}
>$$ 
>Note that 
>- the second term is the *gradient* of the **log-partition function**. It is usually very difficult to estimate this term. 
>- the first term is from the data.
>- The score function is the **difference** between the **sample mean** and the **model mean** of log-likelihood gradient un-normalized term $\nabla_{\theta}\log \hat{\mathcal{P}}(x; \theta)$.
>  

- [[Markov Network on Undirected Graph]]

>[!important] Definition
>The following **identity** holds for the *gradient* of *log-partition function* 
>$$
>\nabla_{\theta} \log Z(\theta) = \mathbb{E}_{ \mathcal{P}_{\theta} }\left[ \nabla_{\theta} \log \hat{\mathcal{P}}(X; \theta)\right]
>$$
>
>- This identity states that the **log-partition gradient**  $\nabla_{\theta} \log Z(\theta)$ can be obtained by the **model expectation** of log-likelihood gradient for unnormalized term.
>- This is the basis of estimation of $\log Z$ via the *Markov Chain Monte Carlo methods*

- [[Markov Chain Monte Carlo Methods]]


>[!info]
>Check 
>$$
>\begin{align*}
> \nabla \log Z &= \frac{1}{Z} \nabla Z\\[5pt]
> &= \frac{1}{Z} \nabla \left(\sum_{x}\hat{\mathcal{P}}_{\theta}\right)\\[5pt]
> &= \frac{1}{Z} \nabla \left(\sum_{x}\exp \left(\log \hat{\mathcal{P}}_{\theta}\right) \right) \\
> &= \frac{1}{Z} \sum_{x}\left(\exp \left(\log \hat{\mathcal{P}}_{\theta}\right) \; \nabla \log \hat{\mathcal{P}}_{\theta}\right) \\[5pt]
> &= \sum_{x}\left(\frac{1}{Z}\hat{\mathcal{P}}_{\theta}\right)\nabla \log \hat{\mathcal{P}}_{\theta} \\[5pt]
> &= \sum_{x}\mathcal{P}(x; \theta)\,\nabla \log \hat{\mathcal{P}}_{\theta} \\[5pt]
> &= \mathbb{E}_{ \mathcal{P} }\left[ \log \hat{\mathcal{P}}(X; \theta)\right]
>\end{align*}
>$$



## Explanation

>[!quote]
>$$
> \nabla_{\theta}\log \mathcal{P}(x; \theta) = \nabla_{\theta}\hat{\mathcal{P}}(x; \theta) - \nabla_{\theta} \log Z(\theta)
>$$ 
>This is a well-known decomposition into the **positive phase** and **negative phase** of learning.
>-- [[Deep Learning by Goodfellow]] pp 598

>[!info]
>For exponential family, $$\nabla A := \nabla_{\theta} \log Z(\theta)$$ is called the **forward mapping**

- [[Exponential Family of Distributions]]
- [[Log-Partition Function of Exponential Family]]







-----------
##  Recommended Notes and References


- [[Log-Partition Function of Exponential Family]]
- [[Gibbs Distribution]]

- [[Exponential Family of Distributions]]
- [[Markov Network on Undirected Graph]]
- [[Partition Function for AdaBoost]]

- [[Markov Chain Monte Carlo Methods]]

- [[Probabilistic Graphical Models by Koller]]  pp 108
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Deep Learning by Goodfellow]] pp 597- 606