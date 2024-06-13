---
tags:
  - concept
  - math/probability
keywords:
  - zero_one_law
topics:
  - probability
name: Komogorov Zero-One Law
date of note: 2024-05-22
---

## Concept Definition

>[!important]
>**Name**: Komogorov Zero-One Law

>[!important] Theorem (Komogorov Zero-One Law)
>Let $\set{X_{n}}$ be **independent** *random variables* with **tail $\sigma$-algebra** $\mathscr{T}$.
>
>Then $\Lambda \in \mathscr{T}$ *implies* 
>$$\mathcal{P}(\Lambda)=0$$ or 
>$$\mathcal{P}(\Lambda)=1$$ 
>so that $\sigma$-algebra $\mathscr{T}$ is **almost trivial**. 

- [[Tail sigma Algebra]]
- [[Almost Trivial sigma Algebra]]

>[!important] Corollary
>Let $\set{X_{n}}$ be **independent** *random variables*. Then 
>
>- The event 
>$$ 
> \begin{align*}
> \left\{\omega: \sum_{n=1}^{\infty}X_{n}(\omega) \text{ converges} \right\} \in \mathscr{T}
> \end{align*}
>$$  
>has probability $0$ or $1$.
>
>- The **tail random variables** $$\limsup\limits_{n\rightarrow \infty} X_{n}$$ and $$\liminf\limits_{n\rightarrow \infty} X_{n}$$ are **constant** with *probability* $0$ or $1$.
>  
>- The event 
> $$ 
> \begin{align*}
> \left\{\omega: \lim\limits_{n\rightarrow \infty}\frac{S_n(\omega)}{n} = 0 \right\} = \left\{\omega: \lim\limits_{n\rightarrow \infty}\frac{\sum_{k=1}^{n}X_{k}(\omega)}{n} = 0 \right\} \in \mathscr{T},
> \end{align*}
>$$  
>has *probability* $0$ or $1$.
> 

- [[Tail sigma Algebra]]

## Explanation

>[!important]
>From the Komogorov Zero-One Law, the **tail event** associated with a set of  **independent** random variables is either 
>- **happening** *almost surely*
>- **not happening** *almost surely*
>  
>That is, we have great **certainty** on the occurrence of the tail event.


>[!important]
> The *Komogorov Zero-One Law* shows that the tail $\sigma$-algebra for a set of **independent random variables** is quite **almost trivial**, which is quite simple:
>$$
>\mathscr{T} = \left\langle \emptyset, \Omega  \right\rangle \cup \text{ some null sets}.
>$$

>[!info]
>This theorem is the basis for the **Strong Law of Large Numbers**.
>$$
>\mathcal{P}\left\{\omega\in \Omega: \lim_{ n \to \infty } \frac{1}{n}\sum_{i=1}^{n} X_{i}(\omega) =  \mathbb{E}_{\mathcal{P}}\left[X\right] \right\} = 1
>$$

## Preference on Independence Assumption

>[!important]
>The **Komogorov zero-one law** reveals the reason why the **independence assumption is preferred** in a lot of *statistical analysis* esp. concerning the **consistency** of *statistics*.

>[!important]
>The theorem reveals that the tail $\sigma$-algebra $$\mathscr{T} = \bigcap_{n \ge 1}\sigma(X_{n+1}, \ldots)$$ 
>for **independent variables** are *almost trivial*, thus the **test** run on the $\mathscr{T}$ is **almost deterministic**. 
>
>This is because *all* **tail events** *either* form a *null set* or occupy  **the entire space** *outside a null set*.

- [[Markov Inequality]]



-----------
##  Recommended Notes and References

- [[Probability Space]]
- [[Measure Space and Countably Additive Measure]]
- [[Independence of Events]]


- [[A Probability Path by Resnick]]
- [[Introduction to Measure Theory by Tao]]
- [[Probability and Measure by Billingsley]]