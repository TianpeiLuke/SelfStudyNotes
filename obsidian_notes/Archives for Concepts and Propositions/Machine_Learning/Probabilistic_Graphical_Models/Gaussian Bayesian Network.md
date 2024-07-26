---
tags:
  - concept
  - probabilistic_graphical_models/models
keywords:
  - gaussian_bayesian_network
  - bayesian_network
  - gaussian _graphical_model
topics:
  - probabilistic_graphical_model
name: Gaussian Bayesian Network
date of note: 2024-07-25
---

## Concept Definition

>[!important]
>**Name**: Gaussian Bayesian Network

![[Local Probabilistic Models#^5561cb]]

>[!important] Definition
>A **Gaussian Bayesian network** is a *Bayesian network* $\mathcal{B} := (G, \mathcal{P})$  
>- where all of random variables $(X_{1} \,{,}\ldots{,}\,X_{|V|})$ are *continuous*, and 
>- where all of the *CPDs* are *linear Gaussians*. 
>  
>That is, the joint distribution of  $(X_{1} \,{,}\ldots{,}\,X_{|V|})$ is *factorized* according to $G$ and it can be computed via
>$$
>\mathcal{P}(X_{v},\, v\in V) = \prod_{v\in V}\mathcal{N}(X_{v};\, f_{\beta, \beta_{0}}(X_{Pa(v)})\,,\, \sigma^2)
>$$
>where 
>$$
>f_{\beta, \beta_{0}}(X_{Pa(v)}) = \left\langle \beta , X_{Pa(v)} \right\rangle + \beta_{0}.
>$$


- [[Bayesian Network on Directed Acyclic Graph]]
- [[Local Probabilistic Models]]
- [[Generalized Linear Models]]

## Explanation

>[!important]
>if $\mathcal{B}$ is a **linear Gaussian Bayesian network**, then it defines a joint distribution that is **jointly Gaussian**.

## Joint Distribution

>[!important] Theorem
>Let $Y$ be a **linear Gaussian** given all of its parents $X := (X_{1} \,{,}\ldots{,}\,X_{k})$ $$p(Y\,|\, x) = \mathcal{N}(\beta_{0} + \left\langle \beta , x \right\rangle, \sigma^2).$$
>
>Assume that $X := (X_{1} \,{,}\ldots{,}\,X_{k})$  are **jointly Gaussian** with distribution $\mathcal{N}(\mu, \Sigma)$.
>
>Then:
>- The distribution of $Y$ is a **normal distribution** $\mathcal{N}(y; \,\mu_{Y}, \sigma_{Y}^2)$ where $$\mu_{Y} = \beta_{0} + \left\langle \beta , \mu \right\rangle, \quad \sigma_{Y}^2 = \sigma^2 + \left\langle \Sigma \beta , \beta \right\rangle$$
>- The *joint distribution* over $(X, Y)$ is a **normal distribution** where $$\text{Cov}(X_{i}; Y) = \sum_{j=1}^{k}\beta_{j}\,\text{Cov}(X_{i}; X_{j}) = \sum_{j=1}^{k}\beta_{j}\,\Sigma_{i,j}.$$

## I-Map

>[!important] Theorem
>Let $X := (X_{1} \,{,}\ldots{,}\,X_{n})$, and let $p$ be a **joint Gaussian** distribution over $X$. 
>
>Given any **ordering** $X_{i} \preceq X_{j}, \; i\le j$ over $X$, we can construct a **Bayesian network graph** $G$ and a **Bayesian network** $\mathcal{B}$ over $G$ such that: 
>- $$X_{\text{Pa}_{G}(i)} \subseteq \left\{ X_{1} \,{,}\ldots{,}\, X_{i-1}\right\};$$ 
>- the *CPD* of $X_{i}$ in $\mathcal{B}$ is a **linear Gaussian** of its *parents*; 
>- $G$ is a **minimal $I$-map** for $p$.

- [[Minimal I-Map]]
- [[Bayesian Network on Directed Acyclic Graph]]
- [[Local Probabilistic Models]]



-----------
##  Recommended Notes and References



- [[Inverse Covariance Estimation]]
- [[Independence in Gaussian Distribution]]
- [[Gaussian Graphical Model and Gaussian Markov Random Field]]
- [[Gaussian Random Vector]]


- [[Generalized Linear Models]]


- [[Bayesian Network on Directed Acyclic Graph]]
- [[Graph]]


- [[Probabilistic Graphical Models by Koller]] pp 251 - 254