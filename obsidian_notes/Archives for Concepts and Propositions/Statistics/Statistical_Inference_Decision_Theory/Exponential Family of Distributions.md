---
tags:
  - concept
  - statistics/estimation
  - math/probability
  - machine_learning/models
  - math/information_theory
  - math/information_geometry
  - math/convex_analysis
keywords:
  - exponential_family
  - kl_divergence
  - maximum_likelihood_estimation
  - maximum_entropy_learning
  - fisher_information
  - information_geometry
topics:
  - probability
  - machine_learning_models
  - statistics/estimation
  - information_geometry
  - information_theory
  - convex_analysis
name: Exponential Family of Distributions
date of note: 2024-06-24
---

## Concept Definition

>[!important]
>**Name**: Exponential Family of Distributions

![[Parametric Models#^408b6c]]

>[!important] Definition
>A *parametric family* $\left\{ \mathcal{P}_{\theta}: \theta \in \Theta \right\}$ dominated by a *$\sigma$-finite measure* $\mu$ on $(\Omega, \mathscr{F})$ is called an **exponential family** *if and only if* its probability density function has the form
>$$
> f_{\theta}(\omega) := \frac{d\mathcal{P}_{\theta}}{d\mu}(\omega) = \exp\left( \left\langle  \eta(\theta)\,,\, T(\omega)   \right\rangle - A(\theta) \right)\;h(\omega), \quad \omega \in \Omega. 
>$$
>where 
>- $T: \Omega \to \mathbb{R}^d$ is a *random $d$-vector* with a fixed positive integer $d$,  
>- $\eta: \Theta \to \mathbb{R}^d$ is a *function*,  
>- $h: \Omega \to [0,\infty)$ is a *nonnegative Borel function* on $(\Omega, \mathscr{F})$, and 
>- $$
>A(\theta) = \log \left(\int_{\Omega}\,\exp\left( \left\langle  \eta(\theta)\,,\, T(\omega)   \right\rangle \right)\;h(\omega)\, d\mu(\omega) \right).
>$$
>The function $Z(\theta) := \exp \left(A(\theta)\right)$ is called a **partition function** or **normalization factor.**

- [[Parametric Models]]
- [[Radon-Nikodym Derivative]]
- [[Borel Measure]]
- [[Measurable Function]]

## Explanation


## Canonical Form of Exponential Family

>[!important] Definition
>In an exponential family, consider the *reparameterization* $$\eta = \eta(\theta),$$ and the density function
>$$
>f_{\eta}(\omega) = \exp\left( \left\langle  \eta\,,\, T(\omega)   \right\rangle - A(\eta) \right)\;h(\omega), \quad \omega \in \Omega. 
>$$
>where the log-partition function becomes
>$$
>A(\eta) = \log \left(\int_{\Omega}\,\exp\left( \left\langle  \eta\,,\, T(\omega)   \right\rangle \right)\;h(\omega)\, d\mu(\omega) \right).
>$$
>
>This form is called **the canonical form** or **the natural parameterization**  of *exponential form*.
>- The new *parameter* $\eta$ is called the **natural parameter**.
>- The new *parameter space* $$\Xi := \left\{ \eta(\theta): \theta \in \Theta  \right\} \subset \mathbb{R}^d$$ is called the **natural parameter space**.
>- An exponential family in *canonical form* is called a **natural exponential family**.


## Maximum Likelihood Estimation and Convex Optimization

- [[Maximum Likelihood Estimation of Exponential Family]]

## Maximum Entropy Learning as Dual Formulation

- [[Maximum Entropy Learning of Exponential Family]]

## Convex Duality 

- [[Exponential Family and Convex Duality]]

## Graphical Model 

- [[Exponential Family as Probabilistic Graphical Model]]

## Information Geometry of Exponential Family

- [[Exponential Family as Affine Subspace in Statistical Manifold]]





-----------
##  Recommended Notes and References


- [[Likelihood Function]]
- [[Sufficient Statistics]]
- [[Minimal Sufficient Statistics]]
- [[Fisher Information and Fisher Metric]]


- [[Generalized Linear Models]]


- [[Maximum Likelihood Estimation]]




- [[All of Statistics A Concise Course by Wasserman]]
- [[Mathematical Statistics by Shao]] pp 96 - 99
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Methods of Information Geometry by Amari]]
- [[Probabilistic Graphical Models by Koller]]
- [[Convex Analysis by Rockafellar]]
- [[Convex Optimization by Boyd]]