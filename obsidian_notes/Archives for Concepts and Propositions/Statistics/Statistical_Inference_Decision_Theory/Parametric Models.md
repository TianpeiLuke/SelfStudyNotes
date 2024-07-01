---
tags:
  - concept
  - statistics/estimation
  - math/probability
keywords:
  - parametric_model
topics:
  - statistics/estimation
  - probability
name: Parametric Models
date of note: 2024-06-08
---

## Concept Definition

>[!important]
>**Name**: Parametric Models

>[!important] Definition
>A set of *probability measures* $\mathcal{P}_{\theta}$ on $(\Omega, \mathscr{F})$ *indexed* by a parameter $\theta\in \Theta$ is said to be a **parametric family** *if and only if* 
>-  $\Theta \subset \mathbb{R}^d$ for some fixed positive integer $d$, and 
>- each $\mathcal{P}_{\theta}$ is a **known** *probability measure* when $\theta$ is fixed.
> 
>$$\mathscr{P} := \left\{ \mathcal{P}_{\theta}: \theta \in \Theta \right\}$$
>
>The set $\Theta$ is called the **parameter space** and $d$ is called its **dimension**.

^408b6c

- [[Space of Bounded Signed Measures]]
- [[Coordinate Chart]]
- [[Mathematical Statistics by Shao]] pp 94

>[!important] Definition
>A **parametric model** refers to the assumption that *the population* $\mathcal{P}$ is in a given parametric family.
>
>A parametric family $$\mathscr{P} := \left\{ \mathcal{P}_{\theta}: \theta \in \Theta \right\}$$ is said to be **identifiable** *if and only if* $\theta_{1} \neq \theta_{2}$ and $\theta_{i}\in \Theta$ implies that $\mathcal{P}_{\theta_{1}} \neq \mathcal{P}_{\theta_{2}}$

- [[Injective Function]]
- [[Mathematical Statistics by Shao]] pp 94

>[!important] Definition
>A family of probability measures $\mathscr{P}$ is said to **be dominated by** a *$\sigma$-finite measure* $\mu$ if for every $\mathcal{P} \in \mathscr{P}$, $$\mathcal{P} \ll \mu.$$ In this case, the family $\mathscr{P}$ can be *identified* with **the family of probability density functions**
>$$
>\mathcal{F} := \left\{ \frac{d\mathcal{P}}{d\mu}: \mathcal{P} \in \mathscr{P} \right\}. 
>$$

- [[Probability Density Function of Random Variable]]

>[!important] Definition
>In *statistical inference* and *decision theory*, methods designed for parametric models are called **parametric methods**.



## Explanation

>[!info]
>A *parametric family* is a **finite-dimensional statistical manifold** as it defines a smooth coordinate map $$\varphi: \mathcal{P}_{\theta} \mapsto \theta \in \Theta \subset  \mathbb{R}^d.$$

- [[Smooth Manifold]]
- [[Coordinate Chart]]
- [[Statistical Manifold of Parametric Family]]
- [[Fisher Information]]



-----------
##  Recommended Notes and References

- [[Nonparametric Models and Semi-Parametric Models]]


- [[Population and Sample and Statistical Problem]]

- [[All of Statistics A Concise Course by Wasserman]]
- [[Mathematical Statistics by Shao]] pp 94