---
tags:
  - concept
  - math/functional_analysis
  - math/topology
keywords:
  - function_rapid_decrease
  - dual_space
  - tempered_distribution
topics:
  - functional_analysis
  - topology
name: Space of Tempered Distributions
date of note: 2024-05-24
---

## Concept Definition

>[!important]
>**Name**: Space of Tempered Distributions


>[!important] Definition
>Let $\mathscr{S}(\mathbb{R}^n)$  be the *functions of rapid decrease* on $\mathbb{R}^n$. 
>
>The (topological) dual  space of $\mathscr{S}(\mathbb{R}^n)$ , denoted by $\mathscr{S}^{'}(\mathbb{R}^n)$, is called **the space of tempered distributions** or **Schwartz distributions**.

- [[Space of Functions of Rapid Decrease and Schwartz Class]]
- [[Topological Dual of Locally Convex Space]]


## Explanation

>[!important]
>$\mathscr{S}'(\mathbb{R}^n)$ is a **Fréchet space**.

- [[Fréchet Space]]

## Examples

>[!example]
>Let $g\in \mathscr{S}(\mathbb{R}^n)$ and define a **functional** $g(\cdot)$ on $\mathscr{S}$ by 
>$$
>\begin{align*}
>g(\varphi) := \int_{-\infty}^{\infty}g(x)\varphi(x)\,dx.
>\end{align*}
>$$
>The functional $g(\cdot): \mathscr{S}(\mathbb{R}^n) \to \mathbb{R}$ is **linear** and $g$ is **bounded**
>$$
>\begin{align*}
> \lvert g(\varphi) \rvert \le \lVert g \rVert_{L^1(\mathbb{R})}\,\lVert \varphi \rVert_{\infty}.   
>\end{align*}
>$$
>- Since $\varphi \in \mathscr{S}(\mathbb{R}^n)$, $\lVert \varphi \rVert_{\infty}$ is a **continuous semi-norm**.
>- Thus $g(\cdot) \in \mathscr{S}'(\mathbb{R}^n)$.
>- If $g_{1} \neq g_{2}$ in $\mathscr{S}$, then $$g_{1}(\cdot) \neq g_{2}(\cdot)$$ as function in $\mathscr{S}'(\mathbb{R}^n)$. That is, the linear functional is **injective**.
>	- This is due to $\mathscr{S}(\mathbb{R}^n) \subset L^2(\mathbb{R}^n)$ is **dense**. Then $g_{1} \neq g_{2}$ in  $\mathscr{S}$ leads to $g_{1} \neq g_{2}$ in  $L^2.$ By isomorphism of $L^2$ and $(L^2)^{*}$, we have  $g_{1} \neq g_{2}$ in  $(L^2)^{*}.$ Thus $g_{1} \neq g_{2}$ in  $\mathscr{S}'.$
>- Thus, we show that $\iota: \mathscr{S}(\mathbb{R}^n) \to \mathscr{S}'(\mathbb{R}^n)$  is an **embedding**. $$g \mapsto \int_{-\infty}^{\infty}g(x)\,[\cdot(x)]\,dx.$$
>- This embedding is *continuous* if $\sigma(\mathscr{S}', \mathscr{S})$ *topology*.


- [[Space of Functions of Rapid Decrease and Schwartz Class]]
- [[Smooth Embedding]]
- [[Smooth Immersion]]

>[!important] Proposition
>The space of **functions of rapid decrease** $\mathscr{S}$ is **dense** in $\mathscr{S}'$ in the $\sigma(\mathscr{S}', \mathscr{S})$ *topology*

- [[Dense Set]]
- [[Space of Functions of Rapid Decrease and Schwartz Class]]
- [[Space of Tempered Distributions]]

>[!important]
>A **tempered distribution** $T\in \mathscr{S}'(\mathbb{R})$ has the form
>$$
> T(\varphi) = \int_{-\infty}^{+\infty}\,T(x)\,\varphi(x)\; dx.
>$$




-----------
##  Recommended Notes and References

- [[Delta Function]]
- [[Space of Functions of Rapid Decrease and Schwartz Class]]
- [[Topological Dual of Locally Convex Space]]

- [[Lp Space]]

- [[Smooth Map]]
- [[Norm and Normed Space]]
- [[Fréchet Space]]
- [[Vector Space over a Field]]

- [[Functional Analysis by Reed]]
- Grafakos, L. (2008). _Classical fourier analysis_ (Vol. 2). New York: Springer.