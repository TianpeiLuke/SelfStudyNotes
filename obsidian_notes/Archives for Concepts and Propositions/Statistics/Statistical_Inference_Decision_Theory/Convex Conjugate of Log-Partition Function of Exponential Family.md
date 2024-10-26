---
tags:
  - concept
  - statistics/estimation
  - math/convex_analysis
keywords:
  - log_partition_function
  - exponential_family
  - convex_conjugate
topics:
  - statistics/estimation
  - convex_analysis
  - machine_learning_models
name: Convex Conjugate of Log-Partition Function of Exponential Family
date of note: 2024-06-27
---

## Concept Definition

>[!important]
>**Name**: Convex Conjugate of Log-Partition Function of Exponential Family

![[Log-Partition Function of Exponential Family#^88a0c0]]


>[!important] Theorem
>Let $X$ be sample from **exponential family** $\left\{ f_{\eta}: \eta\in \Xi \right\}$ taking values in $\mathcal{X}$, where
>$$
>f_{\eta}(x) = \exp\left( \left\langle  \eta\,,\, T(x)   \right\rangle - A(\eta) \right)\;h(x), \quad x \in \mathcal{X}.
>$$
>and $A$ is the **log-partition function**,
>$$
>A(\eta) = \log \left(\int_{\Omega}\,\exp\left( \left\langle  \eta\,,\, T(\omega) \right\rangle \right)\;h(\omega)\, d\nu(\omega) \right).
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
>- In terms of this dual, the **log-partition function** has the **variational representation** $$A(\eta) = \sup_{\mu \in \mathcal{M}}\left\langle  \eta, \mu \right\rangle - A^{*}(\mu).$$
>- For all $\eta\in \mathcal{D}$, the **supremum** is attained **uniquely** at $\mu \in \text{int}(\mathcal{M})$ specified by the **moment-matching conditions** $$\mu =  \mathbb{E}_{ f_{\eta} }\left[T(X)\right] = \int_{\mathcal{X}}T\,f_{\eta}\,d\mu.$$

^fcfbf5

- [[Legendre Transform]]
- [[Shannon Entropy]]
- [[Log-Partition Function of Exponential Family]]
- [[Interior of Set]]
- [[Exponential Family of Distributions]]
- [[Sufficient Statistics]]
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 67


## Explanation


>[!info]
>The second conclusion states 
>$$
>A^{* *} = A.
>$$

>[!info]
>Recall the **variational formula** for **KL-divergence**
>$$
>\begin{align*}
>\log \mathbb{E}_{\mathcal{Q}}\left[ \exp\left(f\right) \right] &= \sup_{P \ll Q}\left\{ \mathbb{E}_{P}\left[f\right] - \mathbb{KL}\left( P \left\|\right. Q \right)  \right\}
\end{align*}
>$$
>and
>$$
>A(\eta) := \log \mathbb{E}_{\nu}\left[ \exp\left(\left\langle  \eta\,,\,T    \right\rangle\right) \right]
>$$
>Thus
>$$
>\begin{align*}
>\log \mathbb{E}_{\nu}\left[ \exp\left(\left\langle  \eta\,,\,T  \right\rangle\right) \right] &= \sup_{P \ll \nu}\left\{ \mathbb{E}_{P}\left[\left\langle  \eta\,,\,T  \right\rangle\right] - \mathbb{KL}\left( P \left\|\right. \nu \right)  \right\}\\
>&= \sup_{P \ll \nu}\left\{\left\langle  \eta\,,\,\mathbb{E}_{P_{\eta(\mu)}}\left[T\right]  \right\rangle - \mathbb{KL}\left( P_{\eta(\mu)} \left\|\right. \nu \right) \right\}\\
>&= \sup_{\mu \in \mathcal{M}}\left\{\left\langle  \eta\,,\,\mu    \right\rangle + H(f_{\eta(\mu)})\right\}\\
> \implies A(\eta) &=  \sup_{\mu \in \mathcal{M}}\left\{\left\langle  \eta\,,\,\mu    \right\rangle - A^{*}(\mu)\right\}
\end{align*}
>$$

- [[Kullback-Leibler Divergence]]
- [[Variational Formula for Kullback-Leibler Divergence]]

## Properties

>[!important] Proposition
>The dual function $A^{*}$ is always **convex** and **lower semi-continuous**.
>
>Morover, in a **minimal** and *regular* exponential family, 
>- $A^{*}$ is **differentiable** on $\text{int}(\mathcal{M})$, and $$\nabla A^{*}(\mu) = \left(\nabla A\right)^{-1}(\mu).$$
>- $A^{*}$ is **strictly convex** and **essentially smooth**.

^f33ca3

- [[Convex Function]]
- [[Semi-Continuous Function]]
- [[Exponential Family of Distributions#Minimal Representation]]
- [[Smooth Map between Euclidean Spaces]]
- [[Interior of Set]]
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]] pp 273

## Backward Mapping

>[!important] Definition
>The gradient of dual function $A^{*}$, $\nabla A^{*}: \text{int}(\mathcal{M}) \to \mathcal{D}$ is called the **backward mapping**.

^cdf6cd

>[!info]
>For *minimal exponential family*,  the **forward mapping** $\nabla A: \mathcal{D} \to \text{int}(\mathcal{M})$ and the **backward mapping** $\nabla A^{*}: \text{int}(\mathcal{M}) \to \mathcal{D}$  are **inverse** to each other.




-----------
##  Recommended Notes and References

- [[Convex Optimization Problem]]
- [[Fenchel Duality Theorem]]

- [[Exponential Family of Distributions]]
- [[Exponential Family as Probabilistic Graphical Model]]
- [[Exponential Family and Convex Duality]]


- [[Mathematical Statistics by Shao]] pp 96 - 99
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Graphical Models by Koller]]
- [[Convex Analysis by Rockafellar]]
- [[Convex Optimization by Boyd]]