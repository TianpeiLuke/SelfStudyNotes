---
tags:
  - concept
  - math/functional_analysis
  - math/real_analysis
keywords:
  - lp_sequence
topics:
  - functional_analysis
  - real_analysis
name: lp Sequence Space
date of note: 2024-06-20
---

## Concept Definition

>[!important]
>**Name**: $\ell^p$ Sequence Space

![[omega Tuples#^1645cc]]


>[!important] Definition
>Let $\mathbb{C}^{\omega}$ be the **$\omega$-tuple** of $\mathbb{C}$, i.e. for $x\in \mathbb{C}^{\omega}$,  $x = (x_{0}, x_{1} \,{,}\ldots{,}\,)$ where $x_{i} \in \mathbb{C}$.
>
>For $1 \le p < \infty$,  $\ell^p \subset \mathbb{C}^{\omega}$ is defined as the space of **all $p$-summable sequence**, i.e.
>$$
>\ell^p = \left\{ x\in \mathbb{C}^{\omega}: \sum_{n=0}^{\infty}|x_{n}|^{p}  < \infty   \right\} 
>$$
>where the norm
>$$
>\lVert x \rVert_{p} := \left( \sum_{n=0}^{\infty}|x_{n}|^{p}  \right)^{1 / p}. 
>$$

- [[omega Tuples]]
- [[Lp Space]]

>[!important]
>For $p=2$, the space of all **square summable sequences** is defined as
>$$
>\ell^2 = \left\{ x\in \mathbb{C}^{\omega}:\sum_{n=0}^{\infty}|x_{n}|^{2} < \infty   \right\}. 
>$$ 
>The inner product is defined as
>$$
>\left\langle x , y \right\rangle_{\ell^2} := \sum_{n=0}^{\infty}\,x_{n}\bar{y}_{n}.
>$$

- [[Hilbert Space]]

>[!important]
>For $p=\infty$, the space of all **bounded sequences** is defined as
>$$
>\ell^{\infty} = \left\{ x\in \mathbb{C}^{\omega}: \sup_{n}|x_{n}| < \infty   \right\}. 
>$$ 
>The norm is defined as
>$$
>\lVert x \rVert_{\infty} := \sup_{n} |x_{n}|.
>$$


## Explanation

>[!info]
>For  $1 \le p < \infty$,  $\ell^p$ is a **Banach space**





## Hilbert Space

>[!info]
>For  $p = 2$,  $\ell^2$ is a **Hilbert space**

>[!important]
>A Hilbert space $\mathcal{H}$ with *infinite dimension* is **separable** *if and only if* it is isomorphic to $\ell^2$.


- [[Separable Hilbert Space]]

>[!info]
>$$\ell^2 = \left\{  (a_{1},\, a_{2} \,{,}\ldots{,}\,): \sum_{i=1}^{\infty}|a_{i}|^2 < +\infty  \right\}$$ is also called **the canonical Hilbert space**.

## C Space

>[!important]
>$$
>c_{0} \subset c \subset \ell^{\infty}
>$$
>
>$c$ space is the **closed subspace** of $\ell^{\infty}$ and it is also a **Banach space**.

- [[Convergent Sequence Space]]


-----------
##  Recommended Notes and References

- [[Lp Space]]
- [[Banach Space]]
- [[Hilbert Space]]

- Wikipedia [Sequence_space](https://en.wikipedia.org/wiki/Sequence_space)

- [[Representation of Gaussian Random Function in Hilbert Space]]
- [[RKHS of Gaussian Random Function in Hilbert Space]]

- [[Real Analysis by Royden]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Functional Analysis by Reed]]