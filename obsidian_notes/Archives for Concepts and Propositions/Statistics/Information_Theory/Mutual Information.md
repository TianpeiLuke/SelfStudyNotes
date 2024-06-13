---
tags:
  - concept
  - math/information_theory
keywords:
  - mutual_information
topics:
  - information_theory
name: Mutual Information
date of note: 2024-05-13
---

## Concept Definition

>[!important]
>**Name**: Mutual Information

>[!important] Definition
>Let $(\mathcal{X}\times \mathcal{Y}, \mathscr{F},  \mathcal{P})$ be a *probability space* on product space $\mathcal{X} \times \mathcal{Y}$. Let $\mathcal{P}_{\mathcal{X}}$ and  $\mathcal{P}_{\mathcal{Y}}$  be the *marginal measure* of $\mathcal{P}$ onto $\mathcal{X}$ and $\mathcal{Y}$.
>
>Define  $(X, Y)$  as a pair of $\mathcal{P}$-measurable *random variables* on $\mathcal{X} \times \mathcal{Y}$, where $X: \mathcal{X} \to \mathbb{R}$ and $Y: \mathcal{Y} \to \mathbb{R}$  are $\mathcal{P}_{\mathcal{X}}$-measurable and $\mathcal{P}_{\mathcal{Y}}$-measurable, respectively.
>
>The **mutual information**  between random variables $X$ and $Y$ is defined as 
>$$
>\begin{align*}
>I(X; Y) &= \mathbb{KL}\left( \mathcal{P} \left\|\right. \mathcal{P}_{\mathcal{X}} \otimes \mathcal{P}_{\mathcal{Y}}   \right) \\
>&= \int_{\mathcal{X} \times \mathcal{Y}}\log \left(\frac{d\mathcal{P}}{d \mathcal{P}_{\mathcal{X}} \otimes d\mathcal{P}_{\mathcal{Y}} }\right) d\mathcal{P},
\end{align*}
>$$
>where $\mathcal{P}_{\mathcal{X}} \otimes \mathcal{P}_{\mathcal{Y}}$ is **the tensor product** between two marginal measures, i.e.
>$$
>(\mathcal{P}_{\mathcal{X}} \otimes \mathcal{P}_{\mathcal{Y}})(U \times V) :=  \mathcal{P}_{\mathcal{X}}(U)\, \mathcal{P}_{\mathcal{Y}}(V), \quad U\times V \in \mathscr{F}.
>$$

- [[Kullback-Leibler Divergence]]
- [[Tensor Product]]


## Explanation



## Mutual Information and Entropy

>[!info] 
>$$
>\begin{align*}
>I(X; Y) &= H(X) - H(X | Y) \\
>&= H(Y) - H(Y | X)\\
>&= H(X) + H(Y) - H(X, Y)
\end{align*}
>$$

>[!info]
>$$
>I(X; X) = H(X)
>$$

## Properties

>[!important] Proposition
>For any two random variables $X$ and $Y$, the mutual information is **non-negative**
>$$
>I(X; Y) \ge 0
>$$
>with equality holds if and only if $X$ and $Y$ are **independent**.

- [[Jensen Inequality]]

>[!info]
>For any two random variables $X$ and $Y$, the mutual information is **symmetric**
>$$
>I(X; Y) = I(Y; X)
>$$





-----------
##  Recommended Notes and References

- [[Absolute Continuity for Measures]]
- [[Measurable Function]]
- [[Radon-Nikodym Derivative]]
- [[Probability Space]]

- [[Shannon Entropy]]
- [[Kullback-Leibler Divergence]]

- [[Elements of Information Theory by Cover]]


