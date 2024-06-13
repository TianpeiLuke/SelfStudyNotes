---
tags:
  - concept
  - math/topology
keywords:
  - quotient_map
topics:
  - topology
name: Quotient Map
date of note: 2024-05-17
---

## Concept Definition

>[!important]
>**Name**: Quotient Map

>[!important] Definition
>Let $X$ and $Y$ be *topological spaces*; let $\pi : X \rightarrow Y$ be a *surjective map*. 
>
>The map $\pi$ is said to be a **quotient map** provided a subset $U$ of $Y$ is *open* in $Y$ **if and only if** $\pi^{-1}(U)$ is *open* in $X$.
>
>That is, the followings are equivalent: 
>- $\pi: X\to Y$ is a **quotient map** 
>- For map $\pi: X\to Y$, and any open $U \subset Y$, 
>$$
>U \text{ open subset of } Y  \iff \pi^{-1}(U) \text{ open subset of } X
>$$

- [[Surjective Function]]
- [[Topology of Set]]

## Explanation

>[!info]
>By definition, a quotient map must be **continuous**.

- [[Continuous Function]]

>[!info]
>Being a quotient map is **stronger** than being **continuous**, since not only the preimage of open set is open, **the image of an open** set is also open. That is, a quotient map is an open map. 


>[!important] Proposition
>If $\pi: X \rightarrow Y$ is a **surjective continuous** map that is *either* **open** or **closed**, then $\pi$ is a **quotient** map.

- [[Surjective Function]]
- [[Continuous Function]]
- [[Open Map]]
- [[Closed Map]]

>[!important]
>The converse is **not true**.
>
>There are **quotient maps** that are **neither _open_ nor _closed_**. See Exercise in [[Topology Book by Munkres]].


## Example

>[!example] 
>Let $\pi_1 : \mathbb{R}\times \mathbb{R} \rightarrow \mathbb{R}$ be the **canonical projection** *onto* **the first coordinate**. [[Canonical Projection]]
>$$
>\pi(x, y) = x
>$$
>
>Then $\pi_1$ is **continuous** and **surjective**. 
>
>Furthermore, $\pi_1$ is an **open map**. For if $U \times V$ is a nonempty *basis element* for $\mathbb{R} \times \mathbb{R}$, then $\pi_1(U \times V) = U$ is *open* in $\mathbb{R}$; it follows that $\pi_1$ *carries open sets* of $\mathbb{R} \times \mathbb{R}$ to *open* sets of $\bR$. 
>
>That is, $\pi_1$ is a **quotient map.**

>[!info]
> However, $\pi_1$ is **not a closed map**. 
> 
> The subset
> $$
> \begin{align*}
> C = \set{(x, y): x \cdot y =1}
> \end{align*}
>$$ 
> of $\mathbb{R} \times \mathbb{R}$ is **closed**, but $\pi_1(C) = \mathbb{R} \setminus \{0\}$, which is **not closed** in $\mathbb{R}$.




-----------
##  Recommended Notes and References


- [[Topology of Set]]
- [[Topology Book by Munkres]]