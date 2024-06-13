---
tags:
  - concept
  - math/functional_analysis
  - math/measure_theory
keywords:
  - riesz_markov_representation
topics:
  - functional_analysis
  - measure_theory
name: The Riesz-Markov Representation Theorem
date of note: 2024-05-08
---

## Theorem

>[!important]
>**Name**: The Riesz-Markov Representation Theorem


>[!important] Theorem
>Let $X$ be a *locally compact Hausdorff (LCH)* space, if $I$ is a **positive linear functional** on $\mathcal{C}_{c}(X)$,  there is a **unique Radon measure** $\mu$ on $X$ such that
> $$
> \begin{align*}
> I(f) &= \int f d\mu 
> \end{align*}
> $$
>for all $f \in \mathcal{C}_{c}(X)$. Moreover, $\mu$ satisfies the following conditions:
>
> 1. for all *open sets* $U \subseteq X$,
> $$
> \begin{align*}
> \mu(U) &= \sup\set{I(f): f \in \mathcal{C}_c(X), \text{supp}(f) \subseteq U, \; 0 \le f \le 1}. 
> \end{align*} 
> $$
> 2. for all *compact sets* $K \subseteq X$
> $$
> \begin{align*}
> \mu(K) &= \inf\set{I(f): f \in \mathcal{C}_c(X), f \ge \mathbb{1}_{K}}. 
> \end{align*}
> $$

- [[Locally Compact Hausdorff Space]]
- $\mathcal{C}_{c}(X, \mathbb{R})$ see  [[Continuous Functions with Compact Support]]
- [[Locally Compactness]]
- [[Positive Linear Functional]]
- [[Radon Measure]]


>[!info]
>The Riesz-Markov theorem is the usual way that **measures** arise in **functional analysis.**

## Explanation

>[!info]
>The domain of positive linear functional in the above theorem is the space of *continuous functions with compact support.* The **compact support** is critical.


>[!important]
>The Riesz-Markov Representation Theorem shows that there is a **duality** between a **Radon measure** and a **positive linear functional** on continuous function space $\mathcal{C}_{c}(X)$.  
>
>The significance of this theorem is that it *bridges two branches* of mathematical fields: the **functional analysis** field and the **measure theory** field.

>[!important]
>Following *the Riesz-Markov Theorem*, a Radon measure can be *represented* by *integral form of linear functional*.
>$$
> \begin{align*}
> \mu(X) &= \sup\left\{\int_X f d\mu: f \in \mathcal{C}_c(X),  \; 0 \le f \le 1 \right\}.
> \end{align*}
>$$ 

- [[Real Analysis Modern Techniques and Their Applications by Folland]]

## Generalization, the Duality


>[!info]
>The Riesz-Markov Representation Theorem 
>- can be generalized to $\mathcal{C}_{0}(X)$ for LCH $X$. 
>- can be extended to signed measures. 
>  
>This would result in the following **duality** statement. 

>[!important] Theorem
>Let $X$ be a *locally compact Hausdorff (LCH)* space,  $\mathcal{M}(X)$ be the space of **signed Radon measure** on $X$ and $\mathcal{C}_{0}(X)$ be the space of all continuous functions that *vanishes at infinity.* 
>
>For every signed Radon measure $\mu$, define a bounded linear functional on $\mathcal{C}_{0}(X)$, $I_{\mu}: \mathcal{C}_{0}(X) \to \mathbb{R}$ as
> $$
> \begin{align*}
> I_{\mu}(f) &= \int f d\mu. 
> \end{align*}
> $$
>
>Then the map 
>$$
>\mu \rightarrow I_{\mu}
>$$ 
>is an **isometric isomorphism** from $\mathcal{M}(X)$ to $(\mathcal{C}_{0}(X))^{*}$, i.e.
>$$\mathcal{M}(X) \simeq (\mathcal{C}_{0}(X))^{*} $$

- [[Continuous Functions that Vanish At Infinity]]
- [[Bounded Linear Functional]]


>[!important]
>The above theorem shows the **duality** between
>- the space of *continuous functions* *vanishing at infinity*  $\mathcal{C}_{0}(X)$ and 
>- the space of *signed Radon measures* $\mathcal{M}(X)$.


>[!info]
>The space of **signed Radon measure** on $X$, $\mathcal{M}(X)$, is a *complete normed space* (i.e. **Banach space**) with norm
> $$
> \begin{align*}
> \lVert \mu \rVert &:= |\mu|(X).
> \end{align*}
> $$
> where $\lvert \mu \rvert$ is the total variation of the signed Radon measure.

- [[Signed Measure]]
- [[Jordan Decomposition Theorem and total variation measure]]
- [[Banach Space]]
- [[Lp Space]]


>[!info]
>Every **bounded linear functional** on some continuous function space can be represented as an **integral operation** with respect to some *regular measure.*


>[!important]
 >The Riesz-Markov Representation Theorem provides an **integral representation** of a *bounded linear functional* on $\mathcal{C}_{0}(X)$.
 >$$
 >I(\cdot) := \int_{X} \; \cdot \; d\mu_{I}
 >$$






-----------
##  Recommended Notes and References


- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Functional Analysis by Reed]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)