---
tags:
  - concept
  - statistics/decision_theory
  - math/convex_analysis
keywords: 
topics: 
name: 
date of note: 2024-06-26
---

## Concept Definition

>[!important]
>**Name**: Convex Decision Problem

![[Statistical Decision Problem#^1e4cc1]]

>[!important] Definition
>Let $X$ be a *sample* from a *population* $\mathcal{P} \in \mathscr{P}$. 
>
>A **convex decision problem** is a statistical decision problem where 
>- the set of allowable actions $\mathcal{A}$ is a *convex subset* of $\mathbb{R}^k$, and
>- the loss function $L: \mathscr{P} \times \mathcal{A} \to [0, \infty)$ is a *convex function* in the second argument, i.e. $L(\mathcal{P}, \cdot): \mathcal{A} \to [0, \infty)$ is *convex*.

- [[Statistical Decision Problem]]
- [[Convex Set]]
- [[Convex Function]]


## Explanation


## Randomized Action

>[!important] Proposition
>Let $X$ be a *sample* from a *population* $\mathcal{P} \in \mathscr{P}$. 
>
>Consider a convex decision problem where $\mathcal{A}$ is a *convex subset* of $\mathbb{R}^k$ and $L(\mathcal{P}, \cdot): \mathcal{A} \to [0, \infty)$ is a *convex function*.
>
>Let $\delta$ be a **randomized rule** satisfying $$\int_{\mathcal{A}}\lVert a \rVert\, \delta(x, da) < \infty, \quad \forall x\in \mathcal{X}$$ and let an *averaged decision* $$T_{1}(x) := \int_{\mathcal{A}}\,a\,\delta(x, da).$$
>
>Then 
>- $T_{1}$ is **as good as** $\delta$, i.e. $$L(\mathcal{P}, T_{1}(x)) \le L(\mathcal{P}, \delta, x),\quad \forall x\in \mathcal{X}, \, \forall \mathcal{P}\in \mathscr{P}.$$
>-  $T_{1}$ is **better than** $\delta$ i.e. $$L(\mathcal{P}, T_{1}(x)) < L(\mathcal{P}, \delta, x),\quad \forall x\in \mathcal{X}, \, \forall \mathcal{P}\in \mathscr{P},$$  if $L(\mathcal{P}, \cdot)$ is **strictly convex**.

^34756f

- [[Statistical Decision Problem#^a44cc3]]
- [[Jensen Inequality]]

## Rao-Blackwell Theorem

- [[Rao-Blackwell Theorem]]



-----------
##  Recommended Notes and References





- [[Mathematical Statistics by Shao]] pp 117