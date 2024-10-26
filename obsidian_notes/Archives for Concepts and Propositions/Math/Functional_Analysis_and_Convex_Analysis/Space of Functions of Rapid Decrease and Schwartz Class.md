---
tags:
  - concept
  - math/functional_analysis
  - math/topology
keywords:
  - function_rapid_decrease
topics:
  - functional_analysis
  - topology
name: Function of Rapid Decrease
date of note: 2024-05-24
---

## Concept Definition

>[!important]
>**Name**: Function of Rapid Decrease and *Schwartz Class*

>[!important] 
>Let $f$ be a smooth function. $I_{+}^n$ denotes the *set* of all $n$-tuple of *non-negative* integers $\alpha = (\alpha_{1} \,{,}\ldots{,}\, \alpha_{n} )$ and 
>$$
>\alpha_{i} \ge 0, \quad |\alpha| := \sum_{i=1}^n \alpha_{i}
>$$ 
>
>Denote the **partial derivatives** of $f$ as $D^{\alpha}$
>$$
>D^{\alpha} := \frac{ \partial^{|\alpha|} }{ \partial x_{1}^{\alpha_{1}} \, \ldots \, \partial x_{n}^{\alpha_{n}}} 
>$$
>and also denote $x^{\alpha} := x_{1}^{\alpha_{1}} \, \ldots \, x_{n}^{\alpha_{n}}.$

^f10f2e

>[!important] Definition
>The **functions of rapid decrease** (or the **class of Schwartz functions**) $\mathscr{S}(\mathbb{R}^n)$ is the set of *infinitely differentiable* complex-valued functions $f: \mathbb{R}^n \to \mathbb{R}$ for which 
>$$
>\begin{align*}
>\lVert f \rVert_{\alpha, \beta} := \sup_{x \in \mathbb{R}^n} \left\lvert  x_{1}^{\alpha_{1}} \, \ldots \, x_{n}^{\alpha_{n}}\; \frac{ \partial^{|\beta|} }{ \partial x_{1}^{\beta_{1}} \, \ldots \, \partial x_{n}^{\beta_{n}}} f(x) \right\rvert  < \infty
\end{align*}
>$$
>for **all $\alpha, \beta \in I_{+}^n.$**
>
>The semi-norm $\lVert f \rVert_{\alpha, \beta}$  is called the **Schwartz semi-norm**.

>[!important] Definition
>We define for $k, m \in I_{+}$, and $f\in \mathscr{S}(\mathbb{R}^n)$, 
>$$
>\lVert f \rVert_{k, m} := \sum_{|\alpha| \le k,\; |\beta| \le m}  \lVert f \rVert_{\alpha, \beta} 
>$$



>[!important] Definition
>We denote the **semi-norm**
>$$
>\lVert f \rVert_{\alpha, \beta, \infty} := \lVert x^{\alpha} D^{\beta}f \rVert_{\infty} = \sup_{x \in \mathbb{R}^n} \left\lvert  x_{1}^{\alpha_{1}} \, \ldots \, x_{n}^{\alpha_{n}}\; \frac{ \partial^{|\beta|} }{ \partial x_{1}^{\beta_{1}} \, \ldots \, \partial x_{n}^{\beta_{n}}} f(x) \right\rvert   
>$$

- [[Locally Convex Space]]
- [[Norm and Normed Space]]
- [[Semi-Norm that Separating Points]]

>[!important] 
>Similarly, we can define the **semi-norm** 
>$$\lVert f \rVert_{\alpha, \beta, p} = \lVert x^\alpha D^{\beta} f \rVert_{p}$$


## Explanation


>[!info]
>$\lVert \cdot \rVert_{\alpha, \beta}$ is a **semi-norm** but **not a norm**, since the **positiveness**  may not hold. 
>
>That is,  there exists non-zero $f \in \mathcal{C}^{\infty}$ such that 
>$$
>\lVert f \rVert_{\alpha, \beta} =0 \iff \left\lvert  x_{1}^{\alpha_{1}} \, \ldots \, x_{n}^{\alpha_{n}}\; \frac{ \partial^{|\beta|} }{ \partial x_{1}^{\beta_{1}} \, \ldots \, \partial x_{n}^{\beta_{n}}} f(x) \right\rvert = 0.
>$$  
>

>[!info]
>For $\alpha = 0$ and $\beta = 0$, then $$\lVert f \rVert_{0,0, \infty} = \sup_{x} |f(x)| = \lVert f \rVert_{\infty}.$$
>
>Thus $$\mathscr{S}(\mathbb{R}) \subset L^{\infty}(\mathbb{R}).$$
>

## Topology

>[!important]
>Under the *topology* compatible with $\mathscr{S}(\mathbb{R}^n)$,
>- $(f, g) \mapsto f + g$
>- $(c, f) \mapsto c f$, for any $c\in \mathbb{R}$,
>- $f \mapsto D^{\alpha}f$, for any $\alpha\in I_{+}^{n}$
>
>are all *continuous map*. 
 



## Space of Smooth Maps

>[!important]
>Denote $\mathcal{C}_{0}^{\infty}(\mathbb{R}^n)$ as the space of all **smooth functions** on $\mathbb{R}^n$ with **compact support**, and $\mathcal{C}^{\infty}(\mathbb{R}^n)$ as the space of all **smooth functions.**
>
>We have
>$$
>\mathcal{C}_{0}^{\infty}(\mathbb{R}^n) \subseteq \mathscr{S}(\mathbb{R}^n) \subseteq \mathcal{C}^{\infty}(\mathbb{R}^n)
>$$

- [[Smooth Map between Euclidean Spaces]]


## Lp space

>[!important]
>The *space of functions of rapid decrease* is a **dense** subset of a $L^p$ space for any $1\le p \le \infty$.
>$$
>\mathscr{S}(\mathbb{R}^d) \subseteq L^{p}(\mathbb{R}^d)
>$$

- [[Lp Space]]


## Completeness

>[!important] Proposition
>The **vector space** $\mathscr{S}(\mathbb{R}^n)$ with the *natural  topology* given by  the **semi-norms** $\lVert \cdot \rVert_{\alpha, \beta}$ is a **Fréchet space**.

- [[Fréchet Space]]






-----------
##  Recommended Notes and References

- [[Smooth Map between Euclidean Spaces]]
- [[Fréchet Space]]

- [[Space of Tempered Distributions]]

- [[Locally Convex Space]]
- [[Norm and Normed Space]]
- [[Semi-Norm that Separating Points]]
- [[Vector Space over a Field]]



- [[Functional Analysis by Reed]]
- Grafakos, L. (2008). _Classical fourier analysis_ (Vol. 2). New York: Springer.