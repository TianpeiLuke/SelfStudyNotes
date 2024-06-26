---
tags:
  - concept
  - math/functional_analysis
  - math/real_analysis
keywords:
  - l_infinite_space
topics:
  - functional_analysis
  - real_analysis
name: L-infinite Space
date of note: 2024-06-20
---

## Concept Definition

>[!important]
>**Name**: $L^{\infty}$ Space

>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a measure space. Suppose that $\mu(\mathcal{X}) > 0.$
>
>The space of all *measurable functions* on $\mathcal{X}$ that are **bounded almost everywhere** is denoted as $L^{\infty}(\mathcal{X}, \mathscr{F}, \mu)$. That is
>$$
> L^{\infty}(\mathcal{X}, \mathscr{F}, \mu) := \left\{ f \in \mathbb{R}^{\mathcal{X}} \text{ measurable}:  \text{ess }\sup_{\mathcal{X}}|f|  <\infty  \right\} 
>$$

- [[Essential Supremum and Essential Infimum]]
- [[Lp Space]]
- [[Absolutely Convergent Integration]]
- [[Measurable Function]]

## Explanation


>[!important]
>$$
>L^{\infty}(\mathcal{X}, \mathscr{F}, \mu)  \subseteq B(\mathcal{X}, \mathbb{R})
>$$

- [[Bounded Function and Space of Bounded Functions]]

## Banach Space

>[!important]
>$L^{\infty}(\mathcal{X}, \mathscr{F}, \mu)$ is **Banach space** with norm
>$$
>\begin{align*}
>\lVert f \rVert_{\infty} &:= \text{ess }\sup_{\mathcal{X}}|f| \\
>&\equiv \inf\left\{  a\in \mathbb{R}: \mu\left\{x:  |f(x)| > a \right\} = 0 \right\}\\
>&\equiv  \inf_{E:\,\mu(E) = 0}\sup_{x \in \mathcal{X} \setminus E }\;|f(x)| 
>\end{align*}
>$$

- [[Banach Space]]

## Mode of Convergence

![[Uniformly Almost Everywhere Convergence#^4f10f6]]

- [[Uniformly Almost Everywhere Convergence]]

## Hölder Inequality

>[!important]
>If $$p = 1, \quad q = \infty,$$ we have the
>$$
>\begin{align*}
> \lVert f\,g \rVert_{1} \le \lVert f \rVert_{1}\, \lVert g \rVert_{\infty}.   
>\end{align*}
>$$

- [[Hölder Inequality]]

## Space of Continuous Function

>[!important] 
>Let $X$ be  a **compact Hausdorff** space. Denote $\mathcal{C}(X, \mathbb{C})$ as the space of *all continuous* (complex-valued) functions on $X$, endowed with the norm
>$$
>\lVert f \rVert_{\infty} := \sup_{x \in X}\lvert f(x) \rvert.  
>$$ 
>
>Let $\mathcal{C}(X, \mathbb{R})$ be the space of all real-valued continuous functions on $X$.
>
>Then $\mathcal{C}(X, \mathbb{C})$ is a complex **Banach space** and $\mathcal{C}(X, \mathbb{R})$ is a real **Banach space**. Also $$\mathcal{C}(X, \mathbb{C}) \subset L^{\infty}(X, \mu)$$ is a **closed subspace**.

- [[Space of all Continuous Functions]]



-----------
##  Recommended Notes and References

- [[Essential Supremum and Essential Infimum]]


- [[Measurable Function]]
- [[Bounded Function and Space of Bounded Functions]]

- [[Banach Space]]


- [[Real Analysis by Royden]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Functional Analysis by Reed]]