---
tags:
  - concept
  - math/functional_analysis
  - math/real_analysis
keywords:
  - convergent_sequence_space
topics:
  - functional_analysis
  - real_analysis
name: Convergent Sequence Space
date of note: 2024-06-20
---

## Concept Definition

>[!important]
>**Name**: Convergent Sequence Space

>[!important] Definition
>Let $\mathbb{C}^{\omega}$ be the **$\omega$-tuple** of $\mathbb{C}$.
>
>The space of **convergent sequences** $c \subset \mathbb{C}^{\omega}$ is defined as
>$$
>c := \left\{ (x_{0}, x_{1} \,{,}\ldots{,}\,): \lim_{ n \to \infty } x_{n}\text{ exists}  \right\} 
>$$

- [[omega Tuples]]
- [[lp Sequence Space]]

>[!important] Definition
>Let $\mathbb{C}^{\omega}$ be the **$\omega$-tuple** of $\mathbb{C}$.
>
>If $\lim_{ n \to \infty }x_{n}$ exists and $$\lim_{ n \to \infty }x_{n} = 0,$$ we say that the sequence $x = (x_{1} \,{,}\ldots{,}\,)$ is a **null sequence** and it **vanishes** 
>
>The space of **null sequences** (or **vanishing sequences**) $c_{0} \subset \mathbb{C}^{\omega}$ is defined as
>$$
>c_{0} := \left\{ (x_{0}, x_{1} \,{,}\ldots{,}\,): \lim_{ n \to \infty } x_{n} = 0  \right\} 
>$$

>[!important] Definition
>Let $\mathbb{C}^{\omega}$ be the **$\omega$-tuple** of $\mathbb{C}$.
>
>If  
>- $\lim_{ n \to \infty }x_{n} = 0,$  and 
>- there are only **finitely many nonzero elements**, 
>  
>we say that the sequence $x = (x_{1} \,{,}\ldots{,}\,)$ is an **eventually zero sequence**.
>
>The space of **eventually zero sequences** $c_{00} \subset \mathbb{C}^{\omega}$ is defined as
>$$
>c_{00} := \left\{ (x_{0}, x_{1} \,{,}\ldots{,}\,): x_{n} = 0, \;\; \text{ for all but finite number of }n \right\} 
>$$


## Explanation



## Banach Space

>[!important]
>Define the norm as
>$$
>\lVert x \rVert_{\infty} = \sup_{n} |x_{n}|
>$$
>
>Then
>- the space of **convergent sequences** $c$ is a **Banach space** and it is a **closed subspace** of $\ell^{\infty}$
>
>- the space of **null sequence** $c_{0}$ is also a **Banach space** and it is a **closed subspace** of $c$.
>- the space of **eventually zero sequences** $c_{00}$ is **not** Banach space since it is **not** a closed subspace of $c_{0}$. But it is a [[Fréchet Space]]. 
>- $c_{00}$ is **dense** in  $c_{0}$ and $c_{00}$ is **dense** in  $\ell^p$ for $p < \infty$.
>  
>We have 
>$$
> c_{00} \subset \ell^p \subset c_{0} \subset c \subset \ell^{\infty}
>$$  

- [[Banach Space]]
- [[lp Sequence Space]]

## Space of Continuous Function

- [[Space of all Continuous Functions]]
- [[Continuous Functions that Vanish At Infinity]]
- [[Continuous Functions with Compact Support]]



-----------
##  Recommended Notes and References

- [[lp Sequence Space]]


- [[Banach Space]]


- Wikipedia [C_space](https://en.wikipedia.org/wiki/C_space)
- Wikipedia [Sequence_space](https://en.wikipedia.org/wiki/Sequence_space)


- [[Real Analysis by Royden]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Functional Analysis by Reed]] pp 69