---
tags:
  - concept
  - math/topology
  - math/functional_analysis
keywords:
  - point_open_topology
  - topology_pointwise_convergence
topics:
  - topology
name: the topology of pointwise convergence
date of note: 2024-05-05
---

## Concept Definition

>[!important]
>**Name**:  *The Topology of Pointwise Convergence* or *Point-Open Topology*

>[!important] Definition
>Given a point $x$ of the set $X$ and an *open set* $U$ of the space $Y$, let
> $$
> \begin{align*}
> S(x, U) = \set{f:  f \in Y^X\text{ and }f(x) \in U}.
> \end{align*}
> $$
> 
> The sets $S(x, U)$ are a *subbasis* for **topology** on $Y^X$, which is called **the topology of pointwise convergence** (or **the point-open topology**)

- [[Sub-Basis of Topology]]
- Note that this definition *requires $Y$ to be topological space* but $X$ do *not need* to be topological space.
- Y may *not be a metric space*.
- This topology is on *the space of functions* $Y^X$. 
- The definition does not necessarily require $f$ to be a continuous function.

## Alternative Definition via Weak Topology

>[!info]
>We can define a continuous linear functional $I$ on $Y^X$ so that 
>$$
>I_{x}(f) := f(x)
>$$
>$I_{x}$ is called an **evaluation functional**  at $x$.
>
>Then *the topology of pointwise convergence* is a **weak topology** generated by *all evaluation functions* $\mathscr{F} := \{I_{x}, x\in X\} = (Y^X)^{*}$.
>
>The subbasis of this topology is 
>$$
>I_{x}^{-1}(U), \quad x \in X, U \in \mathscr{T}_{Y}.
>$$
 
- [[Weak Topology Generated by Functions]]

## Explanation

>[!info]
>- The general *basis* element for this topology is a **finite intersection** of subbasis elements $S(x, U)$. 
>
>- Thus a typical *basis* element about the function $f$ *consists of all functions* $g$ that are **"close"** to $f$ **at finitely many points**. 
>  
> - The *topology of pointwise convergence* is generated by the **basis**
> $$
> \begin{align*}
> B_{U_1, \ldots, U_n}(x_1 , \ldots, x_n, \epsilon)  &= \bigcap_{i=1}^{n}S(x_i, U_i) \\
> &= \set{f \in Y^X: f(x_1) \in U_1 , \ldots, f(x_n) \in U_n}, \quad \exists n < \infty.
> \end{align*}$$
>It corresponds to **the pointwise convergence** of $f_n$ to $f$ in $Y^X$. 


>[!info]
>- $\mathcal{C}(X, Y)$ is **not closed** in $Y^X$ under the *topology of pointwise convergence*.


>[!info]
>- Assume $Y$ is a *metric space* with metric $d$, then the neighborhood definition of function space $Y^X$ under point-open topology is 
>$$
>\begin{align*}
>\mathcal{N}(f) &:= \left\{g \in Y^{X}: \exists n \in \mathbb{N}, x_i \in X, \text{such that } \; g(x_i) \in B_{\epsilon_i}(f(x_i)), i=1,\ldots, n\right\}\\
>&= \bigcup_{n}\bigcap_{\{(x_i, \epsilon_i)\}_{i=1}^{n}}S(x_i, B_{\epsilon_i}(f(x_i)))
>\end{align*}
>$$
>where $B_{\epsilon}(s):= \{t \in Y: d(s, t) < \epsilon \}$ is an open set in $Y$





-----------
##  Recommended Notes and References

- [[Topology of Set]]
- [[Space of all Continuous Functions]]
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)