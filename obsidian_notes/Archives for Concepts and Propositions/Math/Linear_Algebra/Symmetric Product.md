---
tags:
  - concept
  - math/linear_algebra
  - math/differential_geometry
keywords:
  - symmetric_product
topics:
  - differential_geometry
  - linear_algebra
name: Symmetric Tensors
date of note: 2024-05-14
---

## Concept Definition

>[!important]
>**Name**: Symmetric Product

>[!important] Definition
>If $\alpha \in \Sigma^{k}(V^{*})$ and $\beta \in \Sigma^{k}(V^{*})$, we define their **symmetric product** to be the *$(k + l)$-tensor* $\alpha\,\beta$ (denoted by juxtaposition with no intervening product symbol) given by
>$$
> \begin{align*}
> \alpha\,\beta &= \text{Sym }(\alpha \otimes \beta)
> \end{align*}
>$$ 
> More explicitly, the *action* of $\alpha\,\beta$ on vectors $v_1,\ldots,v_{k+l}$ is given by
>$$ 
> \begin{align*}
> \alpha\,\beta(v_1,\ldots,v_{k+l}) &= \frac{1}{(k+l)!}\sum_{\sigma \in S_{k+l}}\alpha(v_{\sigma(1)},\ldots,v_{\sigma(k)})\beta(v_{\sigma(k+1)},\ldots,v_{\sigma(k+l)})
> \end{align*}
>$$ 

- [[Symmetric Tensor]]
- [[Projection of Tensor on Symmetric Tensor Space]]

## Explanation



## Properties

>[!important] Proposition
>- The *symmetric product* is **symmetric** and **bilinear**: for all *symmetric tensors* $\alpha, \beta, \gamma$ and all $a, b \in \mathbb{R}$,
>$$
> \begin{align*}
> \alpha\, \beta &= \beta\, \alpha \\
> (a\,\alpha + b\,\beta)\,\gamma &= a\,\alpha\,\gamma + b\,\beta\,\gamma = \gamma\, (a\,\alpha + b\,\beta)
> \end{align*}
>$$ 
>-  If $\alpha$ and $\beta$ are **covectors**, then
>$$
> \begin{align*}
> \alpha\,\beta &=\frac{1}{2}\left( \alpha \otimes \beta + \beta \otimes \alpha \right).
> \end{align*}
>$$ 

- [[Covector on Vector Space]]



-----------
##  Recommended Notes and References


- [[Symmetric Tensor]]
- [[Projection of Tensor on Symmetric Tensor Space]]


- [[Multilinear Function]]

- [[Introduction to Smooth Manifolds by Lee]]