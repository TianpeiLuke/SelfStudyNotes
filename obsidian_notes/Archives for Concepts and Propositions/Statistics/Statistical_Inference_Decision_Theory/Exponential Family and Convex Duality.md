---
tags:
  - concept
  - math/probability
  - machine_learning/models
  - math/convex_analysis
  - statistics/estimation
keywords:
  - exponential_family
  - convex_duality
topics:
  - probability
  - machine_learning_models
  - convex_analysis
  - statistics/estimation
name: Exponential Family and Convex Duality
date of note: 2024-06-24
---

## Concept Definition

>[!important]
>**Name**: Exponential Family and Convex Duality

![[Exponential Family of Distributions#^6d86a1]]


- [[Exponential Family of Distributions]]
- [[Convex Function]]
- [[Minimal Sufficient Statistics]]

## Space of Realizable Mean Parameters

>[!important] Proposition
>Let $\mathcal{M}$ be the space of all **realizable mean parameters** associated with sufficient statistic $T: \mathcal{X} \to \mathbb{R}^d$,  i.e.
>$$
>\mathcal{M} := \left\{ \mu \in \mathbb{R}^d:  \exists \mathcal{P} \text{ such that }  \mu = \mathbb{E}_{\mathcal{P}}\left[ T(X) \right] \right\}.
>$$
>
>Then $\mathcal{M}$ is a **convex** subset of $\mathbb{R}^d$.
>
>In particular, if $(X_{1} \,{,}\ldots{,}\,X_{m})$ is *discrete random vector* with *finite state space* $\mathcal{X}^m$, we have representation
>$$
>\begin{align*}
>\mathcal{M} &:= \left\{ \mu \in \mathbb{R}^d: \mu = \sum_{x\in \mathcal{X}^m}T(x)\,p(x) \text{ where }  \exists p \text{ with } \sum_{\mathcal{X}^m}p(x) = 1, \text{ and }p(x) \ge 0   \right\}\\[5pt]
>&= \text{conv}\left\{ T(x): x\in \mathcal{X}^{m} \right\}, 
>\end{align*}
>$$
>where $\text{conv}(A)$ is the **convex hull** of set $A$.

^14b84c

- [[Convex Set]]
- [[Convex Hull]]
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 54

>[!important] Proposition
>Let $\mathcal{M}$ be the space of all **realizable mean parameters** associated with sufficient statistic $T: \mathcal{X} \to \mathbb{R}^d$,  i.e.
>$$
>\mathcal{M} := \left\{ \mu \in \mathbb{R}^d:  \exists \mathcal{P} \text{ such that }  \mu = \mathbb{E}_{\mathcal{P}}\left[ T(X) \right] \right\}.
>$$
>
>Then
>- $\mathcal{M} \subset \mathbb{R}^d$ is **full-dimensional** i.e. it is **affine hull** is equal to $\mathbb{R}^d$ if and only if the exponential family is **minimal.**
>- $\mathcal{M}$ is **bounded** if and only if $\Theta = \mathbb{R}^d$ and the *log-partition function* $A$ is **global Lipschitz** on $\mathbb{R}^d.$


## Convexity of Log-Partition Function

![[Log-Partition Function of Exponential Family#^8780a9]]

- [[Log-Partition Function of Exponential Family]]

## Convex Conjugate of Log-Partition Function

![[Convex Conjugate of Log-Partition Function of Exponential Family#^fcfbf5]]

- [[Convex Conjugate of Log-Partition Function of Exponential Family]]

>[!important] 
>The above theorem shows the **convex duality** between the **log-partition function** $A$ and the **negative entropy** $A^{*}$.
>
>This result also confirms the **convex duality** between the **maximum likelihood estimation** and **maximum entropy learning**. 
>
>This results in the **variational representation** $$A(\eta) = \sup_{\mu \in \mathcal{M}}\left\langle  \eta, \mu \right\rangle - A^{*}(\mu).$$
>where
>$$
>A^{*}(\mu) = \left\{ 
>\begin{array}{cc}  
> -H(f_{\eta(\mu)}) :=\mathbb{E}_{ f_{\eta} }\left[ \log(f_{\eta}) \right] &  \text{ if }\mu \in \text{int}(\mathcal{M}) \\
> +\infty & \text{ if }\mu \not\in \overline{\mathcal{M}}.
>\end{array}
> \right.
>$$

- [[Maximum Likelihood Estimation of Exponential Family]]
- [[Maximum Entropy Learning of Exponential Family]]
- [[Maximum Likelihood Estimation]]
- [[Maximum Entropy Learning]]
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 68


## Forward and Backward Mapping

![[Log-Partition Function of Exponential Family#^e9381e]]

- [[Log-Partition Function of Exponential Family]]

![[Convex Conjugate of Log-Partition Function of Exponential Family#^cdf6cd]]

![[Convex Conjugate of Log-Partition Function of Exponential Family#^f33ca3]]

- [[Convex Conjugate of Log-Partition Function of Exponential Family]]

## Duality between Natural Parameter Space and Mean Parameter Space

>[!important]
>The **forward mapping** and **backward mapping** $$\nabla A: \mathcal{D} \to \text{int}(\mathcal{M}), \quad \nabla A^{*}: \text{int}(\mathcal{M}) \to \mathcal{D}$$  provide a **one-to-one correspondence** between the *natural parameter space* $\mathcal{D}$ and the *interior of mean parameter space* $\text{int}(\mathcal{M})$.
>
>We say that $\eta$ and $\mu$ are **dually coupled** if
>$$
>\mu = \nabla A(\eta)
>$$

- [[Diffeomorphism]]
- [[Riesz-Markov Representation Theorem]]
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 65


## Explanation





-----------
##  Recommended Notes and References



- [[Exponential Family of Distributions]]

- [[Convex Optimization Problem]]



- [[Maximum Likelihood Estimation]]
- [[Maximum Entropy Learning]]

- [[Kullback-Leibler Divergence]]
- [[Variational Formula for Kullback-Leibler Divergence]]
- [[Bregman Divergence]]


- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
