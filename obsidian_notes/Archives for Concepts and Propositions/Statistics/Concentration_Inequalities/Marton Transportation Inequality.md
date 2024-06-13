---
tags:
  - concept
  - math/information_theory
  - statistics/concentration_inequality
  - math/optimal_transport
keywords:
  - transportation_inequality_marton
topics:
  - information_theory
  - optimal_transport
  - concentration_inequality
name: Marton Transportation Inequality
date of note: 2024-05-30
---

## Concept Definition

>[!important]
>**Name**: Marton Transportation Inequality

>[!important] Marton's Transportation Inequality
>Let $$\mathcal{P} = \otimes_{k=1}^n \mathcal{P}_k$$ be a **product probability measure** on $\mathcal{X}^n$, and let $\mathcal{Q}$ be a probability measure *absolutely continuous* with respect to $\mathcal{P}$. 
>
>Define two random vectors as below:
>- $X = (X_1 \,{,}\ldots{,}\, X_n) \sim \mathcal{P}$, which are all **independent**, and
>- $Y = (Y_1 \,{,}\ldots{,}\, Y_n) \sim \mathcal{Q}$
>
>Then
>$$
> \begin{align}
>  \min_{\pi \in \Pi(\mathcal{Q}, \mathcal{P})}\sum_{i=1}^n \pi^2\set{Y_i \neq X_i} &\le \frac{1}{2}\mathbb{KL}\left( \mathcal{Q} \left\|\right. \mathcal{P}  \right)
> \end{align}
>$$ 
>where $$\Pi(\mathcal{Q}, \mathcal{P}) := \left\{ \pi \in \mathcal{M}(\mathcal{X}^n \times \mathcal{X}^n): \; Y_{*}\pi = \mathcal{Q},\, X_{*}\pi = \mathcal{P} \right\} $$

^35d313

- [[Wasserstein Distance]]
- [[Weighted Hamming Distance]]
- [[Pinsker Inequality]]


## Explanation

>[!important]
>The above inequality corresponding to **$2$-Wasserstein distance** induced by Hamming distance on $\mathcal{X}$
>$$
>\mathcal{W}_{2, d_{H}} := \sqrt{ \min_{\pi \in \Pi(\mathcal{Q}, \mathcal{P})}\sum_{i=1}^n \pi^2\set{Y_i \neq X_i} } \le \sqrt{ \frac{1}{2}\mathbb{KL}\left( \mathcal{Q} \left\|\right. \mathcal{P}  \right) }
>$$
>we can compared to Pinsker's inequality
>![[Pinsker Inequality#^c30a68]]
>which is the **$1$-Wasserstein distance**
>$$
> \mathcal{W}_{1, d_{H}}  :=  \min_{\pi \in \Pi(\mathcal{Q}, \mathcal{P})}\sum_{i=1}^n \pi\set{Y_i \neq X_i}  \le \sqrt{ \frac{1}{2}\mathbb{KL}\left( \mathcal{Q} \left\|\right. \mathcal{P}  \right) }
>$$
>





-----------
##  Recommended Notes and References

- [[Concepts and Theorems of Optimal Transport]]
- [[Pinsker Inequality]]

- [[Weighted Hamming Distance]]

- [[Sub-Additivity for Transportation Cost Inequality]]

- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]