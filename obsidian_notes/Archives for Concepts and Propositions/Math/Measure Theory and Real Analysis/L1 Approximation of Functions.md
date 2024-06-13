---
tags:
  - concept
  - math/real_analysis
keywords:
  - l1_approximation
topics:
  - real_analysis
name: L1 Approximation of Functions
date of note: 2024-05-28
---

## Concept Definition

>[!important]
>**Name**: L1 Approximation of Functions

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
- [[Convergence in L1 norm]]
- [[Continuous Functions with Compact Support]]

## Explanation


>[!important]
>From the theorem, we see that
>$$
>\mathcal{C}_{c}(\mathbb{R}^d) \subset L^1(\mathbb{R}^d)
>$$
>is a **dense** subset.

- [[Dense Set]]
- [[Continuous Functions with Compact Support]]
- [[Lp Space]]



-----------
##  Recommended Notes and References

- [[Continuous Functions with Compact Support]]

- [[Absolutely Convergent Integration]]
- [[Simple Integral of Simple Functions]]
- [[Convergence in L1 norm]]

- [[Summary of Spaces of Continuous Functions]]