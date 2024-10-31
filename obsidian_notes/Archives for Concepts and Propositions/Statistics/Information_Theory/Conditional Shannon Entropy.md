---
tags:
  - concept
keywords: 
topics: 
name: 
date of note: 2024-06-01
---

## Concept Definition

>[!important]
>**Name**: Conditional Shannon Entropy

>[!important] Definition
>Let $X$ and $Y$ be **discrete random variables**,taking values in $\mathcal{X}$ and $\mathcal{Y}$, respectively. Let $p(x, y)$ be the *joint probability mass function* of $(X,Y)$  and $p(x)$ be the *marginal* probability mass function of $X$. 
>
>The **conditional entropy** of $Y$ **given** $X$ is defined as
>$$
>H(Y | X) := - \sum_{(x,y)\in \mathcal{X} \times \mathcal{Y}}p(x,y) \log \left( \frac{p(x,y)}{p(x)}\right)
>$$
 
- [[Shannon Entropy]]
- [[Fubini Theorem]]

## Explanation

>[!info]
>Intuitively, the conditional entropy of $X$ given $Y$ can be written as
>$$
>H(Y | X) = \mathbb{E}_{ (X, Y) }\left[\; - \log p(y | x) \; \right]
>$$
>where 
>$$
>p(y|x) := \frac{p(x,y)}{p(x)}
>$$
>is the **conditional probability mass function**.



-----------
##  Recommended Notes References

- [[Conditional Probability]]
- [[Conditional Expectation]]
- [[Evidence Lower Bound]]


- [[Elements of Information Theory by Cover]]



