---
tags:
  - concept
  - math/information_theory
keywords:
  - data_processing_inequality
topics:
  - information_theory
name: Data-Processing Inequality
date of note: 2024-11-04
---

## Concept Definition

>[!important]
>**Name**: Data-Processing Inequality

![[Kullback-Leibler Divergence#^4f1ef4]]

>[!important] Data-processing Inequality
>Let $X, Y. Z$ be random variables that form a **Markov chain in order** $$X \to Y \to Z$$ i.e. $$p(x, y, z) = p(z|y)\,p(y|x)\,p(x).$$
>
>Then
>$$
> I(X; Y) \ge I(X ; Z)
>$$
>- That is, **no processing** of $Y$, deterministic or random, can **increase** the information that $Y$ contains about $X$.

^11ff5a

- [[Mutual Information]]
- [[Markov Chain and Markov Process]]

>[!important] Corollary
>Let $X, Y,Z$ be random variables and $Z = g(Y)$ for some function $g$, then 
>$$I(X; Y) \ge I(X; g(Y))$$


>[!important] Corollary
>Let $X, Y. Z$ be random variables that form a **Markov chain in order** $$X \to Y \to Z$$ i.e. $$p(x, y, z) = p(z|y)\,p(y|x)\,p(x).$$
>
>Then 
>$$
> I(X; Y) \ge I(X ; Y | Z)
>$$
>- That is, the **dependence** of $X$ and $Y$ is **decreased** (or remains unchanged) by the observation of a “**downstream**” random variable $Z$

### Sufficient Statistics

![[Sufficient Statistics#^7c0a9f]]

>[!important] Definition
>A function $T(X)$ is said to be a **sufficient statistic** relative to the parametric family $\mathcal{P}_{\theta}$ if $$\theta \to T(X) \to X$$ form a **Markov chain.**
>
>If $T(X)$ is sufficient statistics, then the **equality** holds in the **data processing inequality** $$I(\theta ; X) = I(\theta ; X \,|\, T(X))$$

^8aa0d2

- [[Sufficient Statistics]]

>[!info]
>For any statistics, $$\theta \to X \to T(X)$$
>
>Thus $$I(\theta; X) \ge I(\theta; X \,|\,T(X))$$

>[!important] Definition
>A statistic $T(X)$ is a **minimal sufficient statistic** relative to $\mathcal{P}_{\theta}$ if it is a *function* of *every other sufficient statistic* $U$. This implies that $$\theta \to T(X) \to U(X) \to X$$
>- $$I(\theta ; X) = I(\theta ; X \,|\,T(X)) = I(\theta ; X \,|\,U(X))$$
>- $$I(\theta ; U(X)) \le I(\theta ; T(X))$$

^638906

- [[Minimal Sufficient Statistics]]


## Explanation

>[!important]
>The data processing inequality states that  **any transformation** will cost **information loss**.

### KL Divergence

![[Kullback-Leibler Divergence#^0c204f]]

- [[Kullback-Leibler Divergence]]

## Extension to Other Divergence

![[Renyi Divergence and Renyi Entropy#^39e8c9]]

- [[Renyi Divergence and Renyi Entropy]]
- [[f-Divergence]]




-----------
##  Recommended Notes and References




- [[Elements of Information Theory by Cover]] pp 34 - 35