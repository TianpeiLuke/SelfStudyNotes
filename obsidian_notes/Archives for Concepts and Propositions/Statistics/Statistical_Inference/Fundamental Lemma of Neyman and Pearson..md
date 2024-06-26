---
tags:
  - concept
  - statistics/hypothesis_testing
keywords:
  - neyman_pearson_lemma
topics:
  - statistics
name: Fundamental Lemma of Neyman and Pearson.
date of note: 2024-05-23
---

## Concept Definition

>[!important]
>**Name**: Fundamental Lemma of Neyman and Pearson.

>[!important] Theorem (Fundamental Lemma of Neyman and Pearson)
>Let $\mathcal{P}_{0}$ and $\mathcal{P}_{1}$ be *probability distributions* possessing *densities* $p_{0}$ and $p_{1}$ respectively with respect to a measure $\mu$.
>
>- **Existence**. For testing $H_{0}: p_{0}$ against the alternative $H_{1}: p_{1}$, there *exists a test* $\phi$ and a constant $k$ such that 
>  $$
>  \mathbb{E}_{ 0 }\left[  \Phi(X) \right] = \alpha \qquad (1)
> $$
> and
> $$
> \begin{align*}
> \phi(x) = \left\{ \begin{array}{cc}
> 1 & \text{ when }p_{1}(x) > k\, p_{0}(x),\\ 
> 0 & \text{ when }p_{1}(x) < k\, p_{0}(x).
\end{array}
> \right. \qquad (2)
\end{align*}
> $$
> 
>- **Sufficient condition for a most powerful test.** If a test satisfies the above two conditions (1) and (2) *for some $k$*, then it is the **most powerful** for testing $p_{0}$ against $p_{1}$ at **level $\alpha$.**
>
>- **Necessary condition for a most powerful test.** If $\phi$ is **most powerful at level $\alpha$** for testing $p_{0}$ against $p_{1}$, then 
>	- for some $k$ it *satisfies* (2) almost everywhere $\mu$.  
>	- It also *satisfies* (1) **unless** there *exists* a test of *size* $<\alpha$ and with *power* $1$

- [[Power and Size of Test]]


>[!important] Corollary 
>Let $\beta$ denote the **power** of the **most powerful  level-$\alpha$ test** ($0 < \alpha < 1$) for testing $P_{0}$ against $P_{1}$. 
>
>Then $\alpha < \beta$ unless $P_{0} = P_{1.}$

## Explanation

>[!important]
>The above theorem states that if we *have information on the distribution of two hypotheses*, **the most powerful test** is the **likelihood ratio test**
>$$
> \begin{align*}
> \phi(x) = \left\{ \begin{array}{cc}
> 1 & \text{ when } \dfrac{p_{1}(x)}{p_{0}(x)} > k,\\[15pt] 
> 0 & \text{ otherwise }
\end{array}
> \right. 
\end{align*}
> $$
>
>Note that the true probabilities for null hypothesis and alternative hypothesis are usually **unknown**. Thus the likelihood ratio test is not always available.

- [[Unbiased Most Powerful Test]]
- [[Likelihood Ratio Test]]



-----------
##  Recommended Notes and References

- [[Power and Size of Test]]

- [[All of Statistics A Concise Course by Wasserman]]
- [[Testing Statistical Hypotheses by Lehmann]]