---
tags:
  - concept
  - math/convex_analysis
  - math/functional_analysis
  - statistics/concentration_inequality
keywords: 
topics:
  - concentration_inequality
  - convex_analysis
name: Convex Distance
date of note: 2024-05-30
---

## Concept Definition

>[!important]
>**Name**: Talagrand's Convex Distance

>[!important] Definition
>For any $x = (x_1 \,{,}\ldots{,}\, x_n) \in \mathcal{X}^n$, the **convex distance** (or *Talagrand's convex distance*) of $x$ from a subset $A$ by
>$$
> \begin{align*}
> d_{T}(x, A) &:=\sup\left\{d_{\alpha}(x, A): \alpha \in \mathbb{R}_{+}^{n},  \lVert \alpha \rVert_{2} = 1 \right\}  
> \end{align*}
>$$ 
>


- [[Weighted Hamming Distance]]

## Explanation

>[!info]
>That is,  $d_{T}(x, A)$ is the **maximal** of *the minimal Hamming distance* from $x$ to $A$ over the **convex polytope** weight
>$$\Delta_{n} := \left\{  \alpha \in \mathbb{R}_{+}^{n}:  \lVert \alpha \rVert_{2} = 1 \right\} $$

- [[Convex Set]]

## Comparison to Distance to Convex Set

>[!important] Lemma
>Let $A \subset [0, 1]^n$ be a **convex set** and let $x = (x_1 \,{,}\ldots{,}\, x_n)  \in [0,1]^n$. 
>
>Then
>$$
> \begin{align}
>  d(x, A):= \inf_{y \in A}\lVert x - y \rVert_{2}  \le d_{T}(x, A).  
> \end{align}
>$$ 

- [[Convex Set]]




-----------
##  Recommended Notes and References


- [[Talagrand Convex Distance Inequality]]


- [[Convex Analysis by Rockafellar]]
- [[Concentration Inequalities by Boucheron]]