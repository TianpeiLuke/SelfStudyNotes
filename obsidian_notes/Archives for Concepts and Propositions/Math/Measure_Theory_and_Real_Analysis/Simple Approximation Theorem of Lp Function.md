---
tags:
  - concept
  - math/real_analysis
keywords:
  - l1_approximation
topics:
  - real_analysis
name: Lp Approximation of Functions
date of note: 2024-05-28
---

## Concept Definition

>[!important]
>**Name**: Lp Approximation of Functions

>[!important] Theorem
>Let $f \in L^1(\mathbb{R}^d)$ and $\epsilon > 0$.
>
>- There exists an **absolutely integrable simple function** $g$ such that
>$$
> \begin{align*}
> \lVert f - g \rVert_{ L^1(\mathbb{R}^d)} &\le \epsilon; 
> \end{align*}
>$$ 
>- There exists a **step function** $g$, i.e. $g$ is represented as a *finite linear combination of indicator functions* of boxes, such that 
>$$
>  \lVert f - g \rVert_{ L^1(\mathbb{R}^d)}  \le \epsilon;
>$$
>- There exists a **continuous**, **compactly supported** $g$ such that
>$$
>  \lVert f - g \rVert_{ L^1(\mathbb{R}^d)}  \le \epsilon;
>$$

- [[Absolutely Convergent Integration]]
- [[Simple Integral of Simple Functions]]
- [[Convergence in Lp norm]]
- [[Continuous Functions with Compact Support]]
- [[Lp Space]]

>[!important] Simple Approximation Lemma
>Let $(\mathcal{X}, \mathscr{F})$ be a *measurable space* and $f$ a *measurable function* on $\mathcal{X}$ that is **bounded** on $\mathcal{X}$, that is, there is an $M \ge 0$ for which $$|f| \le M$$ on $\mathcal{X}$. 
>
>Then for *each* $\epsilon > 0$, there are **simple functions** $\varphi_{\epsilon}$. and $\psi_{\epsilon}$. defined on $\mathcal{X}$ that have the following **approximation properties**: 
>$$
> \varphi_{\epsilon}  \le f \le  \psi_{\epsilon} \;\; \text{ and }\;\; 0 \le \psi_{\epsilon} - \varphi_{\epsilon} < \epsilon
>$$
>on $\mathcal{X}$.

>[!important] Simple Approximation Thoerem
>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a *measure space* and $f$ a *measurable function* on $\mathcal{X}$.
>
>Then there is a sequence $\{ \psi_{n} \}$ of **simple functions** on $\mathcal{X}$ that **converges pointwise** on $\mathcal{X}$ to $f$ and has the **property** that 
>$$
>\lvert \psi_{n} \rvert \le \lvert f \rvert  
>$$ 
>on $\mathcal{X}$ for all $n$.
>
>- If $\mathcal{X}$ is **$\sigma$-finite**, then we may choose $\{\psi_{n}\}$ such that each $\psi_{n}$ **vanishes outside** a set of **finite measure**. 
>- If $f$ is **non-negative**, then we may choose $\{\psi_{n}\}$ to be **increasing** and each $\psi_{n} \ge 0$ on $\mathcal{X}.$

- [[Real Analysis by Royden]] pp 363


>[!important] Theorem
>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a measure space and $1 \le p <\infty$. 
>
>Then *the subspace* of **simple functions** on $X$ that *vanish* outside *a set of finite measure* is **dense** in $L^p(\mathcal{X}, \mu)$.

^705504

- [[Real Analysis by Royden]] pp 398

## Explanation


>[!important]
>From the theorem, we see that
>$$
>\mathcal{C}_{c}(\mathbb{R}^d) \subset L^{\infty}(\mathbb{R}^d)
>$$
>is a **dense** subset.

- [[Dense Set]]
- [[Continuous Functions with Compact Support]]
- [[Lp Space]]



-----------
##  Recommended Notes and References

- [[Continuous Functions with Compact Support]]

- [[Absolutely Convergent Integration]]
- [[Unsigned Integral of Functions]]
- [[Simple Integral of Simple Functions]]
- [[Convergence in Lp norm]]

- [[Summary of Spaces of Continuous Functions]]

