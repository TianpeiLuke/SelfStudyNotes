---
tags:
  - concept
  - math/probability
keywords:
  - law_iterated_logarithm
topics:
  - probability
name: Law of the Iterated Logarithm
date of note: 2024-06-04
---

## Concept Definition

>[!important]
>**Name**: Law of the Iterated Logarithm

>[!important] The Law of the Iterated Logarithm
>Let $(X_{1} \,{,}\ldots{,}\,X_{n})$ be a sequence of **independent identically distributed** random variables. Let $$S_{n} =  \sum_{i=1}^nX_{i}$$ be the sum of these variables.
>
>Then
>$$
>\mathcal{P}\left[ \lim\sup_{ n \to \infty } \frac{S_{n}}{\sqrt{ 2 n \log\log(n) }} = 1\right]  = 1.
>$$

- [[Pointwise Almost Everywhere Convergence]]
- [[Independent Random Variables]]

>[!important]
>In other word,
>$$
>\mathcal{P}\left[ \left\{ S_{n} \ge (1+\epsilon)\,\sqrt{ 2 n \log\log(n) } \right\} \text{ infinitely often} \right] = 0
>$$
>and
>$$
>\mathcal{P}\left[ \left\{ S_{n} \ge (1-\epsilon)\,\sqrt{ 2 n \log\log(n) }\right\} \text{ infinitely often} \right] = 1
>$$

- [[Limits of Sets]]

## Explanation


## Proof

- [[Cramér–Chernoff Method]]
- [[Borel-Cantelli Lemma]]



-----------
##  Recommended Notes and References

- [[Independent Random Variables]]

- [[Cramér–Chernoff Method]]
- [[Borel-Cantelli Lemma]]

- [[Kolmogorov Strong Law of Large Numbers]]


- [[A Probability Path by Resnick]]
- [[Probability and Measure by Billingsley]]