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

## Space of Natural Parameters


>[!important] Proposition
>Let $f_{\eta}(x)$ be p.d.f. of sample $X$ from an *exponential family*, i.e.
>$$
>f_{\eta}(x) = \exp\left( \left\langle  \eta\,,\, T(x)   \right\rangle - A(\eta) \right)\;h(x), \quad x \in \mathcal{X}. 
>$$
>where $T: \mathcal{X} \to \mathbb{R}^d$ is *sufficient statistic* for $f_{\eta}$ and $\eta\in \mathbb{R}^d$ is the *natural parameter*.
>
>The **space of natural parameters** $$\mathcal{D} := \left\{ \eta \in \mathbb{R}^n: A(\eta) < \infty \right\} $$ is a **convex set**.

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

- [[Convex Set]]
- [[Convex Hull]]
- [[Marginal Polytope and Local Consistent Polytope]]
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 54


## Variational Representation of Log-Partition Function

>[!important] Theorem
>Let $X$ be sample from **exponential family** $\left\{ f_{\eta}: \eta\in \Xi \right\}$ taking values in $\mathcal{X}$, where
>$$
>f_{\eta}(x) = \exp\left( \left\langle  \eta\,,\, T(x)   \right\rangle - A(\eta) \right)\;h(x), \quad x \in \mathcal{X}.
>$$
>and $A$ is the **log-partition function**,
>$$
>A(\eta) = \log \left(\int_{\Omega}\,\exp\left( \left\langle  \eta\,,\, T(\omega) \right\rangle \right)\;h(\omega)\, d\mu(\omega) \right).
>$$
>
>Let $\mathcal{M}$ be the space of all **realizable mean parameters** associated with sufficient statistic $T: \mathcal{X} \to \mathbb{R}^d$,  i.e.
>$$
>\mathcal{M} := \left\{ \mu \in \mathbb{R}^d:  \exists \mathcal{P} \text{ such that }  \mu = \mathbb{E}_{\mathcal{P}}\left[ T(X) \right] \right\}.
>$$
>
>Then
>- For any $\mu \in \text{int}(\mathcal{M})$, denote by $\eta(\mu)$ the **unique canonical parameter** satisfying the *dual matching condition* $$\nabla A(\eta) = \mu.$$ The **convex conjugate** of $A$,  $$A^{*}(\mu) = \sup_{\eta \in \mathcal{D}}\left\langle  \eta, \mu \right\rangle - A(\eta)$$ takes the form
>$$
>A^{*}(\mu) = \left\{ 
>\begin{array}{cc}  
> -H(f_{\eta(\mu)}) :=\mathbb{E}_{ f_{\eta} }\left[ \log(f_{\eta}) \right] &  \text{ if }\mu \in \text{int}(\mathcal{M}) \\
> +\infty & \text{ if }\mu \not\in \overline{\mathcal{M}}.
>\end{array}
> \right.
>$$
> For any *boundary point* $\mu \in \partial \mathcal{M} = \overline{\mathcal{M}}\setminus \text{int}(\mathcal{M})$, we have $$A^{*}(\mu) = \lim_{ n \to \infty }A^{*}(\mu_{n}) $$ where $\left\{ \mu_{n}: n \ge 1 \right\} \subset \text{int}(\mathcal{M})$ and $\lim_{ n \to \infty }\mu_{n} \to \mu.$ 
>- In terms of this dual, the **log-partition function** has the **variational representation** $$A(\eta) = \sup_{\eta \in \mathcal{D}}\left\langle  \eta, \mu \right\rangle - A^{*}(\mu).$$
>- For all $\eta\in \mathcal{D}$, the **supremum** is attained **uniquely** at $\mu \in \text{int}(\mathcal{M})$ specified by the **moment-matching conditions** $$\mu =  \mathbb{E}_{ f_{\eta} }\left[T(X)\right] = \int_{\mathcal{X}}T\,f_{\eta}\,d\mu.$$

^ed96df

- [[Legendre Transform]]
- [[Shannon Entropy]]
- [[Variational Formula for Kullback-Leibler Divergence]]
- [[Convex Optimization Problem]]
- [[Fenchel Duality Theorem]]
- [[Information Projection and Moment Projection]]
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 67

>[!info]
>The second conclusion states 
>$$
>A^{* *} = A.
>$$
 associated with sufficient statistic $T: \mathcal{X} \to \mathbb{R}^d$,  i.e.
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

- [[Polyhedron and Polytope]]
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

- [[Polyhedron and Polytope]]

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

^9f7aa4

- [[Diffeomorphism]]
- [[Riesz-Markov Representation Theorem]]
- [[Information Projection and Moment Projection]]
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 65

## M-Projection and I-Projection

>[!important] Proposition
>Let $\mathcal{P}$ be a distribution over $\mathcal{X}$, and let $\mathscr{P}_{\Theta}:=\left\{ \mathcal{P}_{\theta}: \theta \in \Theta \right\}$ be an **exponential family** with p.d.f.
>$$
> f_{\theta}(x) := \frac{d\mathcal{P}_{\theta}}{d\nu}(x) = \exp\left( \left\langle  \eta(\theta)\,,\, T(x)   \right\rangle - A(\theta) \right)\;h(x), \quad x \in \mathcal{X}. 
>$$
>
>If there exists a set of *parameters* $\theta^{*} \in \Theta$ such that $$ \mathbb{E}_{\mathcal{P}_{\theta^{*}}}\left[ T(X) \right] = \mathbb{E}_{\mathcal{P}}\left[ T(X) \right]$$ then the **$M$-projection** of $\mathcal{P}$ is $\mathcal{P}_{\theta^{*}}$, i.e. $$\mathcal{P}_{\theta^{*}} =\arg\min_{\mathcal{P}_{\theta} \in \mathscr{P}_{\Theta}}\mathbb{KL}\left( \mathcal{P} \left\|\right. \mathcal{P}_{\theta} \right)$$

^cb178d

- [[Information Projection and Moment Projection]]

>[!info]
>The **optimal parameter** $\theta^{*}$ that attains *the $M$-projection* of $\mathcal{P} := \mathcal{P}_{n}$ onto the exponential family is the **maximum likelihood estimator** of parameter $\theta$.

- [[Maximum Likelihood Estimation of Exponential Family]]



-----------
##  Recommended Notes and References



- [[Exponential Family of Distributions]]
- [[Polyhedron and Polytope]]
- [[Convex Optimization Problem]]



- [[Maximum Likelihood Estimation]]
- [[Maximum Entropy Learning]]

- [[Kullback-Leibler Divergence]]
- [[Variational Formula for Kullback-Leibler Divergence]]
- [[Bregman Divergence]]


- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
