---
tags:
  - concept
  - math/information_theory
keywords:
  - f_divergence
topics:
  - information_theory
name: f-Divergence
date of note: 2024-05-07
---

## Concept Definition

>[!important]
>**Name**: $f$-Divergence

>[!important] Definition
>if $P$ and $Q$ are *probability measures* on a measurable space $(\Omega, \mathscr{F})$, and $P$ is *absolutely continuous* with respect to $Q$, 
>$$P \ll Q.$$
>
>Define $f: [0, +\infty) \to (-\infty, +\infty]$ as a *convex* function satisfying the following conditions:
>- $f(x) < +\infty$ for $x >0$;
>- $f(1) = 0$;
>- $f(0)= \lim_{ x \to 0^+ }f(x)$.
>
>Then **$f$-Divergence** *from* $Q$ to $P$ is defined as
> $$
> \begin{align*}
> \mathbb{D}_{f}\left( P \left\|\right. Q \right) &:= \int_{\Omega} f\left( \frac{dP}{dQ} \right) dQ 
> \end{align*}
> $$
> where $\frac{dP}{dQ}$ is the *Radon-Nikodym derivative* of $P$ with respect to $Q$.
> 
> We call $f$ the **generator** of $\mathbb{D}_{f}\left( \cdot \left\|\right. \cdot \right).$

^e7fa76

- [[Convex Function]]
- [[Absolute Continuity for Measures]]
- [[Radon-Nikodym Derivative]]
- [[Divergence Function on Manifold]]
- [[Phi Entropy Functional]]


## Explanation



## Properties

>[!important] Proposition
>Let $P$ and $Q$ be two probability measures on $\mathcal{X}$ and $P \ll Q$. 
>
 Then the $f$-Divergence from $Q$ to $P$ is **non-negative**
>$$
>\mathbb{D}_{f}\left( P \left\|\right. Q \right)  \ge 0.
>$$
>with equality holds  *if and only if* $P = Q$.

>[!info]
>This follows from the *convexity* of the mapping 
>$$(p, q) \mapsto q\,f\left(\frac{p}{q}\right)$$ on $\mathbb{R}^2$

- [[Perspective Function]]

>[!info]
>$f$-divergence is a **convex** function in the joint space of two discrete probability vectors.

>[!important] Proposition
>The $f$-divergence $\mathbb{D}_{f}\left( P \left\|\right.Q \right)$ is **convex** in **the pair of probability measures** $(P, Q)$; 
>
>that is, if $(P_{1}, Q_{1})$ and $(P_{2}, Q_{2})$ are two pair of *probability measures*. Then for all $\lambda \in [0,1]$,
>$$
>\begin{align*}
>\mathbb{D}_{f}\left( P_{1} + (1- \lambda) P_{2} \left\|\right. \lambda Q_{1} + (1- \lambda) Q_{2}  \right) &\le \lambda \mathbb{D}_{f}\left(  P_{1}  \left\|\right. Q_{1}  \right) \\
>&\;\; + (1- \lambda) \mathbb{D}_{f}\left( P_{2} \left\|\right. Q_{2}  \right)
\end{align*}
>$$



## Example

>[!example]
>$$f(x) := x\log(x),$$ we have the [[Kullback-Leibler Divergence]].
>$$
>\mathbb{D}_{f}\left(P\left\|\right.Q\right) = \int \frac{dP}{dQ} \log\left( \frac{dP}{dQ} \right) dQ = \int  \log\left( \frac{dP}{dQ} \right) dP = \mathbb{KL}\left( P \left\|\right. Q \right) .
>$$

>[!example]
>$$f(x) := -\log(x),$$ we have the **reversed** [[Kullback-Leibler Divergence]].
>$$
>\mathbb{D}_{f}\left(P\left\|\right.Q\right) = \int - \log\left( \frac{dP}{dQ} \right) dQ = \int  \log\left( \frac{dQ}{dP} \right) dQ = \mathbb{KL}\left( Q \left\|\right. P \right) .
>$$







-----------
##  Recommended Notes and References

- [[Kullback-Leibler Divergence]]
- [[Entropy Functional]]
- [[Divergence Function on Manifold]]


- [[Elements of Information Theory by Cover]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 55
- Wikipedia [F-divergence](https://en.wikipedia.org/wiki/F-divergence)

