---
tags:
  - concept
  - math/information_theory
keywords:
  - kl_divergence
topics:
  - information_theory
name: Chain Rule of Kullback-Leibler Divergence
date of note: 2024-06-01
---

## Concept Definition

>[!important]
>**Name**: Chain Rule of Kullback-Leibler Divergence

 ![[Kullback-Leibler Divergence#^4f1ef4]]

- [[Kullback-Leibler Divergence]]


>[!info]
>One of the most important properties in relative entropy is **the chain rule**.

>[!important] Theorem
>Let $P$ and $Q$ be the **joint probability distributoin** of $(X, Y)$ on product $\sigma$-algebra $\mathscr{F}_{X} \times \mathcal{F}_{Y}$ such that $P \ll Q$. 
>
>- Let $P_{X}$ and $Q_{X}$ be the corresponding *marginal distribution* of $X$ and 
>- $P[Y | \mathscr{F}_{\mathcal{X}}]$ and $Q[Y | \mathscr{F}_{\mathcal{X}}]$ be the *conditional distribution* of $Y$ given $X$.
>
>The following **chain rule** holds
>$$
>\begin{align*}
>\mathbb{KL}\left( P \left\|\right. Q \right) &= \mathbb{KL}\left( P_{X} \left\|\right. Q_{X}  \right) + \mathbb{KL}\left( P[Y | \mathscr{F}_{\mathcal{X}}] \left\|\right. Q[Y | \mathscr{F}_{\mathcal{X}}] \right)
\end{align*}
>$$

- [[Conditional Kullback-Leibler Divegence]]



>[!info]
>For continuous random variable $X$ and $Y$. Let  $p(x,y)$ and $q(x, y)$ be the joint probability density functions , the chain rule for KL divergence:
>$$
>\mathbb{KL}\left( p(x,y) \left\|\right. q(x, y)\right) = \mathbb{KL}\left( p(x) \left\|\right. q(x) \right) + \mathbb{KL}\left( p(x | y)  \left\|\right. q(x | y) \right)
>$$
>where $p(x)$ is the marginal density, and $p(x|y)$ is the conditional density function. 

- [[Conditional Probability]]
- [[Fubini Theorem]]

### Additivity of KL Divergence

>[!important]
>If $X$ and $Y$ are statistically independent, then the chain rule becomes the **additivity of KL divergence** as 
>$$
>\mathbb{KL}\left( P \left\|\right. Q \right) = \mathbb{KL}\left( P_{X} \left\|\right. Q_{X}  \right) +  \mathbb{KL}\left( P_{Y} \left\|\right. Q_{Y}  \right)
>$$


## Explanation





-----------
##  Recommended Notes and References

- [[Kullback-Leibler Divergence]]
- [[Conditional Probability]]
- [[Fubini Theorem]]


- [[Elements of Information Theory by Cover]]