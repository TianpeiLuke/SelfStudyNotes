---
tags:
  - concept
  - math/information_theory
  - statistics/concentration_inequality
keywords:
  - subadditivity
  - transportation_cost_inequality
  - optimal_transport
  - tensorization_optimal_transport
topics:
  - information_theory
  - concentration_inequality
name: Tensorization for Transportation Cost
date of note: 2024-05-30
---

## Concept Definition

>[!important]
>**Name**: Tensorization for Transportation Cost

![[Transportation Cost Inequality#^4642e4]]


>[!important] Proposition
>Suppose that, for each $k = 1, 2 \,{,}\ldots{,}\, n$, the *univariate distribution* $\mathcal{P}_k$ satisfies a **$d_k$-transportation cost inequality** with parameter $\nu_k$. 
>
>Then **the product distribution** $$\mathcal{P} = \otimes_{k=1}^n \mathcal{P}_k$$ satisfies the **$d$-transportation cost inequality**, where $$d(x, y) :=  \sum_{k=1}^{n}d_k(x_k, y_k).$$
>
>That is, $\mathcal{P}$ satisfies the following inequality
>$$
> \begin{align}
> \mathcal{W}_{1, d}(\mathcal{Q}, \mathcal{P}) &\le \sqrt{2 \nu \mathbb{KL}\left( \mathcal{Q} \left\|\right. \mathcal{P} \right)}
> \end{align}
>$$ 
>for all distributions $\mathcal{Q} \ll \mathcal{P}$,  where
>$$
>\nu = \sum_{k=1}^n \nu_k.
>$$

^d0b45c

- [[Sub-Additivity of Entropy Functional and Tensorization]]


## Explanation





-----------
##  Recommended Notes and References



- [[Transportation Cost Inequality]]
- [[Sub-Additivity of Entropy Functional and Tensorization]]
- [[Sub-Additivity of Phi Entropy Functional]]

- [[Concepts and Theorems of Optimal Transport]]


- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Optimal Transport for Applied Mathematicians by Santambrogio]]