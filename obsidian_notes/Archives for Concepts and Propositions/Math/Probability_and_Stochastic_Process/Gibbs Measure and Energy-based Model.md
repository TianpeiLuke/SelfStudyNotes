---
tags:
  - concept
  - math/information_theory
  - math/probability
  - machine_learning/models
  - math/information_geometry
  - deep_learning/models
keywords:
  - gibbs_measure
  - energy_based_model
topics:
  - probability
  - information_theory
  - information_geometry
  - machine_learning_models
name: Gibbs measure and Energy-based Model
date of note: 2024-05-14
---

## Concept Definition

>[!important]
>**Name**: Gibbs measure and Energy-based Model

>[!important] Definition
>Let $(\Omega, \mathscr{F})$ be a measurable space. A probability measure $P$ on $\mathscr{F}$ is called **a Gibbs measure** if its density with respect to a base measure $\mu$ is of the form
>$$
>\begin{align*}
>dP(x) = \frac{1}{Z}\exp \left(- \frac{E(x)}{T}  \right)\; d\mu(x)
\end{align*}
>$$
>where $T >0$ is the **temperature** and $E(x)$ is called the **energy** of the system. 
>
>The *normalization factor* $$Z = \int_{\Omega} \exp \left(- \frac{ E(x)}{T}  \right)\; d\mu(x)$$ is called **the partition function**.

^bfb840

>[!important] Definition
>The **energy-based model (EBM)** can be written as a *Gibbs measure*, i.e. the p.d.f.
> $$
>\begin{align*}
>p(x; \theta) = \frac{1}{Z(\theta)}\exp \left(- E_{\theta}(x) \right)\; 
\end{align*}
>$$
>where
>- $E_{\theta}(x)$ is called the **energy** of the system. 
>
>- The *normalization factor* $$Z(\theta) = \int_{\Omega} \exp \left(- E_{\theta}(x) \right)\; d\mu(x)$$ is called **the partition function**.

^c81bcd


- [[Probability Density Function of Random Variable]]


## Explanation

>[!important]
>Gibbs measure is the **optimal solution** for **the maximum entropy optimization**.
>$$
>\begin{align*}
>\inf_{P \ll \mu} \;&\mathbb{KL}\left( P \left\|\right. \mu \right)\\
>\text{s.t. }& \mathbb{E}_{P}\left[ f \right] = const.
\end{align*}
>$$
>where $f(x) := - E(x) / T.$

- [[Maximum Entropy Learning]]
- See proof in [[Variational Formula for Kullback-Leibler Divergence]]

>[!info]
>Note that most of time the energy function is **not factorized**, i.e. it is not represented by the graphical model.  
>
>As a result, the **partition function** for *energy model* is **intractable**.

- [[Gibbs Distribution]]

## Training Energy-based Model

>[!info]
>Since the partition function is intractable, learning the energy-based model need to **approximate the log-likelihood**.

>[!quote]
>Most techniques for estimating models with **intractable partition functions** do not provide an *estimate of the partition function*. **SML** and **CD** estimate only the gradient of the log partition function, rather than the partition function itself. **Score matching** and **pseudolikelihood** avoid computing quantities related to the partition function altogether.

### Maximum Likelihood Estimation

- [[Maximum Likelihood Estimation]]

### Sampling-Based Method and Stochastic Maximum Likelihood

- [[Markov Chain Monte Carlo Methods]]
- [[Gibbs Sampling]]
- [[Langevin Dynamics and Langevin Sampling]]
- [[Hamiltonian Monte Carlo]]
- [[Contrastive Divergence as Approximate Markov Chain Monte Carlo]]

### Score Matching

- [[Score Matching and Denoising Score Matching]]



-----------
##  Recommended Notes and References

- [[Gibbs Distribution]]
- [[Simulated Annealing]]
- [[Restricted Boltzmann Machine or RBM]]
- [[Auto-Encoder and Stochastic Auto-Encoder]]
- [[Score Matching and Denoising Score Matching]]
- [[Langevin Dynamics and Langevin Sampling]]

- [[Gaussian Random Vector]]
- [[Gaussian Measure]]

- Wikipedia [Gibbs measure](https://en.wikipedia.org/wiki/Gibbs_measure)
- [[Probabilistic Graphical Models by Koller]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 839