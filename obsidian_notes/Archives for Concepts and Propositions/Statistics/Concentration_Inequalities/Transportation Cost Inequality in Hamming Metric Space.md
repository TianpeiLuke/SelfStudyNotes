---
tags:
  - concept
  - statistics/concentration_inequality
  - math/information_theory
  - math/optimal_transport
keywords:
  - transportation_cost_inequality
  - weighted_hamming_distance
topics:
  - information_theory
  - optimal_transport
name: Transportation Cost Inequality in Hamming Metric Space
date of note: 2024-05-22
---

## Concept Definition

>[!important]
>**Name**: Transportation Cost Inequality

![[Transportation Cost Inequality#^8653e5]]

- [[Transportation Cost Inequality]]

>[!info]
>To prove concentration inequality with respect to $\mathcal{P}$, we just need to bound
>$$  
> \begin{align}
>  \mathbb{E}_{\mathcal{Q}}\left[X\right] - \mathbb{E}_{\mathcal{P}}\left[X\right] &\le \phi^{*-1}\left(\mathbb{KL}\left( \mathcal{Q} \left\|\right. \mathcal{P}  \right)\right). 
> \end{align} 
>$$ 
>for all $\mathcal{Q} \ll \mathcal{P}$

>[!important] Transportation Cost Inequality in Hamming Metric Space
>- Let $\mathcal{X}^n$ be a *metric measure space* with **weighted Hamming distance**
>$$
> \begin{align*}
> d_{\alpha}(x, y) &= \sum_{i=1}^{n}\alpha_i \,\mathbb{1}\left\{ x_i \neq y_i \right\}
> \end{align*}.
>$$
>
>- Let $$\mathcal{P} = \otimes_{k=1}^n \mathcal{P}_k$$ be a **product probability measure** on $\mathcal{X}^n$, and let $\mathcal{Q}$ be a probability measure *absolutely continuous* with respect to $\mathcal{P}$, $$\mathcal{Q} \ll \mathcal{P}.$$ 
>
>- Define two random vectors as below:
>	- $X = (X_1 \,{,}\ldots{,}\, X_n) \sim \mathcal{P}$, which are all **independent**, and
>	- $Y = (Y_1 \,{,}\ldots{,}\, Y_n) \sim \mathcal{Q}$
>
>- Let $$\Pi(\mathcal{Q}, \mathcal{P}) := \left\{ \pi \in \mathcal{M}(\mathcal{X}^n \times \mathcal{X}^n): \; Y_{*}\pi = \mathcal{Q},\, X_{*}\pi = \mathcal{P} \right\} $$ be the **coupling set** between $\mathcal{Q}$ and $\mathcal{P}$.
>
>Then according to [[Variational Representation of Wasserstein Distance]], for any **Lipschitz function** $f: \mathcal{X}^n \to \mathbb{R}$, and any coupling $\pi \in \Pi(\mathcal{Q}, \mathcal{P})$, 
>$$
>\begin{align*}
>\mathbb{E}_{\mathcal{Q}}\left[f(Y)\right] - \mathbb{E}_{\mathcal{P}}\left[f(X)\right] &\le \sum_{i=1}^{n}\alpha_{i}  \mathbb{E}_{\pi}\left[ \mathbb{1}\left\{ Y_i \neq X_i \right\} \right]\\
>&\le \lVert \alpha \rVert_{2}\,\sqrt{ \sum_{i=1}^{n} \left( \mathbb{E}_{\pi}\left[ \mathbb{1}\left\{ Y_i \neq X_i \right\} \right] \right)^2  }
\end{align*}
>$$ 
>The last inequality follows the [[Cauchy-Schwartz Inequality]].
>
>Thus in order to prove a *sub-Gaussian concentration inequality* for $$Z = f(X_1 \,{,}\ldots{,}\, X_n),$$  it suffice to upper-bound the **2-Wasserstein distance** between $\mathcal{Q}$ and $\mathcal{P}$, for any $\mathcal{Q} \ll \mathcal{P}$, i.e.
>$$
>\mathcal{W}_{2, d_{H}}(\mathcal{Q}, \mathcal{P}) = \min_{\pi \in \Pi(\mathcal{Q}, \mathcal{P}) }\left( \sum_{i=1}^{n} \left( \mathbb{E}_{\pi}\left[ \mathbb{1}\left\{ Y_i \neq X_i \right\} \right] \right)^2  \right)^{1/2}
>$$
>
>In particular, we would like to provide an information inequality in the form of
>$$
>\mathcal{W}_{2, d_{H}}(\mathcal{Q}, \mathcal{P})^2 \le 2\nu\, \mathbb{KL}\left( \mathcal{Q} \left\|\right. \mathcal{P} \right).
>$$
>for some constant $\nu$.
>
>Then it follows from [[Transportation Cost Inequality]], that we can upper-bound the **rate function**
>$$
>\psi_{Z -  \mathbb{E}_{\mathcal{P}}\left[ Z \right]}(\lambda) \le \frac{\nu\, \lVert \alpha \rVert_{2}^2\;\lambda^2}{2}
>$$

^96f8a7

- [[Transportation Cost Inequality]]
- [[Variational Representation of Wasserstein Distance]]
- [[Sub-Additivity for Transportation Cost Inequality]]
- [[Weighted Hamming Distance]]


## Explanation

>[!info]
>We can obtain the upper bound for $\mathcal{W}_{2,d}$ in [[Marton Transportation Inequality]]

>[!info]
>For Gaussian measure $\mathcal{P}$, we have an improved upper bound in [[Talagrand Gaussian Transportation Inequality]].

## Bounded Difference Inequality

>[!important]
>Note that any  function with **bounded difference property** is **Lipschitz function** with respect to **weighted Hamming distance**.
>
>We can apply the [[Marton Transportation Inequality]] to prove the **Bounded Difference Inequality**

- [[Concentration of Measure on Hamming Metric Space]]
- [[Bounded Difference Inequality]]



-----------
##  Recommended Notes and References


- [[Sub-Additivity for Transportation Cost Inequality]]
- [[Weighted Hamming Distance]]

- [[Variational Representation of Wasserstein Distance]]
- [[Wasserstein Distance]]


- [[Transportation Cost Inequality]]

- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Elements of Information Theory by Cover]]