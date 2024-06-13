---
tags:
  - concept
  - statistics/concentration_inequality
  - math/convex_analysis
keywords:
  - quasi_convex_function
  - lipschitz_continuous_function
  - concentration
topics:
  - concentration_inequality
  - convex_analysis
name: Concentration of Separately Convex Lipschitz Functions
date of note: 2024-05-30
---

## Concept Definition

>[!important]
>**Name**: Concentration of Separately Convex Lipschitz Functions

>[!important] Concentration of Separately Convex Lipschitz Functions
>Let  $Z:= (Z_1 \,{,}\ldots{,}\, Z_{n})$ be **independent** random variables taking values in the **interval** $[0, 1]$.
>
>Let $f : [0, 1]^n \to \mathbb{R}$ be 
>- a **separately convex function**; that is $f$ is *convex* in *each coordinate* while the others are fixed:
>- Moreover, $f$ is **Lipschitz function** satisfying
>$$
> \begin{align*}
> |f(x) - f(y)| &\le \lVert x- y \rVert \quad \text{for all }x, y \in [0, 1]^n.
> \end{align*}
>$$
>
> 
> Then $X = f(Z_1 \,{,}\ldots{,}\, Z_{n})$ satisfies, for all $t > 0$,
>$$ 
> \begin{align}
> \mathcal{P}\set{f(Z) - \mathbb{E}\left[ f(Z) \right]   \ge   t } &\le \exp\left( - \frac{t^2}{2} \right)
> \end{align}
>$$ 

^ced8d1

- [[Convex Function]]
- [[Lipschitz Continuous Function]]
- [[Logarithmic Sobolev Inequality for Gaussian Random Variables]]
- [[Herbst Argument]]

## Explanation

>[!important] Proposition
>For $Z_i \in [a_i, b_i]$, and $f$ being *$L$-Lipschitz function*, we have
>$$
> \begin{align*}
> \mathcal{P}\set{f(Z) -  \mathbb{E}\left[ f(Z) \right] \ge t } &\le \exp \left( - \frac{t^2}{2L^2\sum_{i=1}^n(b_i - a_i)^2} \right)
> \end{align*}
>$$ 

^8b2d89

- [[Hoeffding Inequality]]


>[!info]
>This result can be generalized to **convex Lipschitz function** of **sub-Gaussian random variables**. 
>
>Note that in above theorems, $Z_i \in [0, 1]$ is *sub-Gaussian* as well. 

- [[Sub-Gaussian Norm]]
- [[Sub-Gaussian Random Variable]]


## Proof













-----------
##  Recommended Notes and References


- [[Logarithmic Sobolev Inequality for Gaussian Random Variables]]
- [[Herbst Argument]]

- [[Hoeffding Inequality]]


- [[Convex Function]]
- [[Lipschitz Continuous Function]]

- [[Concentration of Quasi-Convex Lipschitz Functions]]

- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Concentration Inequalities by Boucheron]]