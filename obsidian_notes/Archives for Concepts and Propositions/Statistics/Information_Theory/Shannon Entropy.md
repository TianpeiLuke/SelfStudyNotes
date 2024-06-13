---
tags:
  - concept
  - math/information_theory
keywords:
  - shannon_entropy
topics:
  - information_theory
name: Shannon Entropy
date of note: 2024-05-22
---

## Concept Definition

>[!important]
>**Name**: Shannon Entropy

>[!important] Definition
>Let $X$ be *discrete random variable*, taking values in $\mathcal{X}$. The *probability mass function* of $X$ is denoted as $p(x) \in [0,1]$ for $x\in \mathcal{X}$.
>
>The **Shannon entropy** (or, simply, the **entropy**) of $X$ is defined as 
>$$
>H(X) := - \sum_{x \in \mathcal{X}}p(x) \log(p(x)).
>$$

- [[Random Element and Random Variable]]

>[!important] Definition
>Let $(\Omega, \mathscr{F}, \mathcal{P})$ be a probability space. 
>
>Consider a **$\mathcal{P}$-almost partition** $\mathscr{S}$ of $\Omega$, which is a collection of subset in $\Omega$ such that
>- 
>  $$
>  \mathcal{P}\left( \bigcup_{A \in \mathscr{S}}A \right) = 1
> $$
> - for any $A, B \in \mathscr{S}$, 
>  $$
>  \mathcal{P}(A \cap B) = 0.
> $$ 
> 
> Then the **Shannon entropy of partition** $\mathscr{S}$ is
>$$
>H_{\mathcal{P}}(\mathscr{S}) = - \sum_{A \in \mathscr{S}}\mathcal{P}(A) \log \left( \mathcal{P}(A) \right)
>$$
>
>For the whole $\sigma$-algebra  $\mathscr{F}$, we define the **Shannon entropy of** $\mathscr{F}$ as 
>$$
>H_{\mathcal{P}}(\mathscr{F}) = \sup_{\mathscr{S} \subset \mathscr{F}}H_{\mathcal{P}}(\mathscr{S}).
>$$ 



## Explanation

>[!important]
>Entropy measures the *average* level of **uncertainty** inherent to random variable $X$'s possible outcome.



## Relation to KL divergence

>[!important]
>For a discrete random variable $X$ taking **finite possible values**, that is $|\mathcal{X}| < +\infty$, we can define the uniform distribution $$u(x) \sim \text{Unifom}(\mathcal{X}) = \frac{1}{|\mathcal{X}|}$$
>
>Thus the **KL-divergence (relative entropy)** is proportional to the **negative entropy** $-H(X)$: 
>$$
>\begin{align*}
>\mathbb{KL}\left( p \left\|\right. u \right)&= \sum_{x \in \mathcal{X}}p(x)\log \left( \frac{p(x)}{u(x)} \right)\\
>&= \sum_{x \in \mathcal{X}}p(x)\log(p(x)) - \sum_{x \in \mathcal{X}}p(x)\log \left(u(x)\right)\\
>&= \log(\left\lvert \mathcal{X} \right\rvert) - H(X)
\end{align*}
>$$ 

- [[Kullback-Leibler Divergence]]

>[!info]
>Shannon entropy is not convenient for *arbitrary measure*. Thus, we usually use **the KL-divergence** in replace of Shannon entropy of arbitrary measures.

## Conditional Entropy

- [[Conditional Shannon Entropy]]





-----------
##  Recommended Notes and References

- [[Kullback-Leibler Divergence]]


- [[Elements of Information Theory by Cover]]