---
tags:
  - concept
  - math/information_theory
keywords:
  - kl_divergence
  - relative_entropy
topics:
  - information_theory
  - information_theory
name: Kullback-Leibler Divergence
date of note: 2024-05-07
---

## Concept Definition

>[!important]
>**Name**: Kullback-Leibler Divergence or *Relative Entropy*

>[!important] Definition
>if $P$ and $Q$ are *probability measures* on a measurable space $(\Omega, \mathscr{F})$, and $P$ is *absolutely continuous* with respect to $Q$, 
>$$P \ll Q,$$
>then **the relative entropy** or **Kullback-Leibler Divergence** *from* $Q$ to $P$ is defined as
> $$
> \begin{align*}
> \mathbb{KL}\left( P \left\|\right. Q \right) &:= \int_{\Omega} \log \left( \frac{dP}{dQ} \right) dP = \int_{\Omega} \frac{dP}{dQ} \log \left( \frac{dP}{dQ} \right) dQ 
> \end{align*}
> $$
> where $\frac{dP}{dQ}$ is the *Radon-Nikodym derivative* of $P$ with respect to $Q$.

^4f1ef4

- [[Absolute Continuity for Measures]]
- [[Divergence on Manifold]]

>[!info]
>We call **KL divergence** for short.


>[!info]
>The *Radon-Nikodym derivative* of $P$ with respect to $Q$ is a *$Q$-measurable function*
> $$
> r(\omega) := \frac{dP}{dQ}(\omega), \qquad Q\text{-a.e}. 
> $$
>such that
>$$
>dP = r\, dQ
>$$

- [[Measurable Function]]
- [[Radon-Nikodym Derivative]]


>[!important] Definition (Discrete Probability Case)
>For discrete *probability distributions* $P$, $Q$ defined on the same sample space $\mathcal{X}$, **the Kullback-Leibler divergence** from $Q$ to $P$ is defined as 
>$$
>\begin{align*}
>\mathbb{KL}\left( P \left\|\right. Q \right) := \sum_{x \in \mathcal{X}}P(x)\log \left( \frac{P(x)}{Q(x)} \right).
>\end{align*}
>$$

>[!info]
>Let $\boldsymbol{p} = [p_{1} \,{,}\ldots{,}\,p_{n}]$ and $\boldsymbol{q} = [q_{1} \,{,}\ldots{,}\,q_{n}]$ be two **probability mass functions**, i.e. $p_{i} \ge 0$, and $q_{i} \ge 0$ and 
>$$
>\sum_{i=1}^{n}p_{i} = 1, \quad \sum_{i=1}^{n}q_{i} = 1.
>$$
>
>*The Kullback-Leibler divergence* from $\boldsymbol{q}$ to $\boldsymbol{p}$ is
>$$
>\mathbb{KL}\left( \boldsymbol{p} \left\|\right. \boldsymbol{q} \right) = \sum_{i=1}^{n}p_{i}\log\left(\frac{p_{i}}{q_{i}}\right)
>$$  

## Explanation


## Relation with Entropy

>[!important]
>$$
>\mathbb{KL}\left( P \left\|\right. Q \right) = H(P, Q) - H(P)
>$$



## Chain Rule

- [[Conditional Kullback-Leibler Divegence]]
- [[Chain Rule of Kullback-Leibler Divergence]]

>[!important] Thereom
>The **Kullback-Leibler divergence** is the **only divergence** that is both a *$f$-divergence* and a *Bregman divergence*.

- [[f-Divergence]]
- [[Bregman Divergence]]

>[!info]
>Chain rule *do not holds* for general $f$-divergence and it is the uniqueness of relative entropy.


## $f$-divergence

- [[f-Divergence]]

>[!info]
>KL divergence is a $f$-divergence. In fact, 
>$$f(x) := x\log(x),$$ we have the [[Kullback-Leibler Divergence]].
>$$
>\mathbb{D}_{f}\left(P\left\|\right.Q\right) = \int \frac{dP}{dQ} \log\left( \frac{dP}{dQ} \right) dQ = \int  \log\left( \frac{dP}{dQ} \right) dP = \mathbb{KL}\left( P \left\|\right. Q \right) .
>$$

### Non-negativity


>[!important] Proposition
>Let $P$ and $Q$ be two probability measures on $\mathcal{X}$ and $P \ll Q$. Then the Kullback-Leibler Divergence from $Q$ to $P$ is **non-negative**
>$$
>\mathbb{KL}\left( P \left\|\right. Q \right)  \ge 0.
>$$
>with equality holds  *if and only if* $P = Q$.

- [[Jensen Inequality]]

### Convexity

>[!info]
>KL divergence is a **convex** function in the joint space of two discrete probability vectors.

>[!important] Proposition
>$\mathbb{KL}\left( P \left\|\right.Q \right)$ is **convex** in **the pair of probability measures** $(P, Q)$; that is, if $(P_{1}, Q_{1})$ and $(P_{2}, Q_{2})$ are two pair of *probability measures*.
>
>Then for all $\lambda \in [0,1]$,
>$$
>\begin{align*}
>\mathbb{KL}\left( P_{1} + (1- \lambda) P_{2} \left\|\right. \lambda Q_{1} + (1- \lambda) Q_{2}  \right) &\le \lambda \mathbb{KL}\left(  P_{1}  \left\|\right. Q_{1}  \right) \\
>&\;\; + (1- \lambda) \mathbb{KL}\left( P_{2} \left\|\right. Q_{2}  \right)
\end{align*}
>$$


>[!info] 
>$\mathbb{KL}\left( \boldsymbol{p} \left\|\right. \boldsymbol{q} \right)$ is **convex** in the pair $(\boldsymbol{p}, \boldsymbol{q} )$; that is, if $(\boldsymbol{p}_{1}, \boldsymbol{q}_{1})$ and $(\boldsymbol{p}_{2}, \boldsymbol{q} _{2})$ are two pair of *probability mass functions*.
>
>Then for all $\lambda \in [0,1]$,
>$$
>\begin{align*}
>\mathbb{KL}\left( \lambda \boldsymbol{p}_{1} + (1- \lambda) \boldsymbol{p}_{2} \left\|\right. \lambda \boldsymbol{q}_{1} + (1- \lambda) \boldsymbol{q}_{2}  \right) &\le \lambda \mathbb{KL}\left(  \boldsymbol{p}_{1}  \left\|\right. \boldsymbol{q}_{1}  \right) \\
>&\;\; + (1- \lambda) \mathbb{KL}\left( \boldsymbol{p}_{2} \left\|\right. \boldsymbol{q}_{2}  \right)
\end{align*}
>$$


## Bregman divergence

>[!info]
>KL divergence is also a **Bregman divergence**.

>[!important] Proposition
>$$
>\mathbb{KL}\left( \boldsymbol{p} \left\|\right. \boldsymbol{q} \right) = f(\boldsymbol{p}) - f(\boldsymbol{q}) - \nabla f(\boldsymbol{q})^T (\boldsymbol{p} - \boldsymbol{q})
>$$
>where $$f(\boldsymbol{x}) := \sum_{i=1}^{n}x_{i} \log(x_{i}) = - h(\boldsymbol{x})$$ is the *negative entropy function.*

- [[Bregman Divergence]]

>[!info]
>The *Pythagorean Theorem* is the property of *Bregman divergence*. 


### Pythagorean Theorem

>[!info]
>The other important properties in relative entropy is **Pythagorean Theorem**.

- [[Bregman Divergence]]
- [[Pythagorean Theorem and Parallelogram Law]]


## Variational Formula

>[!important]
>The variational theorem provides *a dual representation* of KL divergence
>$$
>\mathbb{KL}\left( P \left\|\right. Q \right) := \sup\left\{\mathbb{E}_{P}\left[f\right] - \log \mathbb{E}_{\mathcal{Q}}\left[ \exp\left(f\right) \right]: f \in  L^1(\Omega, \mathscr{F}, Q)  \right\}
>$$
>It is called **Donsker–Varadhan representation**.

- [[Variational Formula for Kullback-Leibler Divergence]]
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]


## Divergence on Statistical Manifold

- [[Divergence on Manifold]]


## Information Inequalities


- [[Pinsker Inequality]]
- [[Transportation Cost Inequality]]
- [[Sub-Additivity of Entropy Functional and Tensorization]]
- [[Sub-Additivity of Phi Entropy Functional]]




-----------
##  Recommended Notes and References

- [[Divergence on Manifold]]

- [[Elements of Information Theory by Cover]]


