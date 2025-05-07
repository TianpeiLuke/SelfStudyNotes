---
tags:
  - concept
  - statistics/estimation
  - math/information_geometry
  - machine_learning/models
keywords:
  - mixture_family_distribution
topics:
  - statistics/estimation
  - machine_learning_models
  - information_geometry
name: Mixture Family of Distributions
date of note: 2024-11-07
---

## Concept Definition

>[!important]
>**Name**: Mixture Family of Distributions

>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a $\sigma$-finite measure space. 
>
>A family of distributions $$\mathcal{M}_{\pi} := \left\{ p(x; \pi):\; \pi\in \Delta_{K}, \;\exists K \in \mathbb{N} \right\}$$ is called a **finite mixture family of distributions** if and only if its probability density function is of the form
>$$
>p(x; \pi) := \frac{d\mathcal{P}}{d\mu} = \sum_{i=1}^{K}\pi^{i}p_{i}(x) + h(x)
>$$
>where 
>- $p_{i}(x), i=1\,{,}\ldots{,}\,K$ is called a **mixture component**, which is a *probability density function* as well. $$p_{i} := \frac{d\mathcal{P}_{i}}{d\mu}$$
>- and the **normalized weights**  $$(\pi^1 \,{,}\ldots{,}\,\pi^{K}) \in \Delta_{K} := \left\{ (\pi^1 \,{,}\ldots{,}\,\pi^{K}):\; \pi^{i} \ge 0, \;\; \sum_{i=1}^{K}\pi^{i} = 1 \right\}  $$
>- Each $p(x; \pi)$ is called a **mixture distribution.**

- [[Probability Space]]
- [[Measure Space and Countably Additive Measure]]
- [[Probability Density Function of Random Variable]]
- [[Generalized Simplex]]

### General Mixture Distribution

>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F})$ be a measurable space. Denote $\mathcal{P}(\mathcal{X})$ be the space of all probability measures on $\mathscr{F}$.
>
>A family of distributions $$\mathcal{M}_{\pi}:= \left\{ p(x; \pi) :\; \pi \in \mathcal{P}(\mathcal{X}) \right\} $$ is called a **general mixture family of distributions** if and only if its probability density function is of the form
>$$
>p(x; \pi) := \frac{d\mathcal{P}}{d\pi} = \int_{y} \left[  \frac{d}{d\pi}  K(y, x) \right]  \,d\pi(y) := \int_{y} f(y, x)\,d\pi(y)
>$$
>where 
>- the $\pi \in \mathcal{P}(\mathcal{X})$ is any *probability measure* on $\mathscr{F}$, 
>- $$K: \mathcal{X} \times \mathcal{F} \to \mathbb{R}_{+}$$ is a *transition kernel* such that 
>	- for each $y\in \mathcal{X}$,  $K(y,\cdot)$ is a *probability measure* on $\mathcal{F}$, which is called a **mixture component**, and $$K(y, \cdot) \ll \pi \implies f(y, \cdot) := \frac{dK(y,\cdot)}{d\pi}$$
>	- and, for any $A\in \mathscr{F}$,  $K(\cdot, A)$ is a *$\pi$-measurable* function. 
>	- In other word, $f(y, x)$ is a *joint p.d.f.* over $\pi \times \pi.$
>- Each $p(x; \pi)$ is called a **mixture distribution**.

- [[Markov Transition Kernel and Transition Function]]
- [[Invariant Measure and Stationary Distribution]]
- [[Product Measure]]
- [[Statistical Manifold as Parametric Family]]
- [[Space of Bounded Signed Measures]]


## Explanation


## Maximum Entropy Learning

- [[Maximum Entropy Learning]]



## Log-Concave Distribution

- [[Log-Concave and Log-Convex Function]]



-----------
##  Recommended Notes and References


- [[Gaussian Mixture Models or GMM]]
- [[Gaussian Scale Mixtures]]

- [[Exponential Family of Distributions]]
- [[Parametric Models]]


- [[Mixture Embedding and Representation of Tangent Space of Statistical Manifold]]
- [[Exponential Connection and Mixture Connection on Statistical Manifold]]
- Wikipedia [Mixture_distribution](https://en.wikipedia.org/wiki/Mixture_distribution)
- [[Mathematical Statistics by Shao]] pp 278, 353