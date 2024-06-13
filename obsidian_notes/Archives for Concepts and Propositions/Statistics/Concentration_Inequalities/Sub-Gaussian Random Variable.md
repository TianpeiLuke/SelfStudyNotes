---
tags:
  - concept
  - statistics/concentration_inequality
keywords:
  - sub-gaussian_distribution
topics:
  - statistics
name: Sub-Gaussian Random Variable
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**: Sub-Gaussian Random Variable

>[!info] Chernoff Bound for Normal distribution
>Let $X$ be a **centered Normal random variable** with variance $\sigma^2$. Then
>$$
> \begin{align*}
> \psi_X(\lambda) = \frac{\lambda^2 \sigma^2}{2},\, \quad \lambda_t = \frac{t}{\sigma^2}
> \end{align*} 
>$$
>and, therefore for every $t > 0$, 
>$$
> \begin{align*}
> \psi_{X}^{*}(t) &= \frac{t^2}{2\sigma^2}.
> \end{align*} 
>$$ 
>Hence, **Chernoff's inequality** implies, for all $t > 0$,
>$$
> \begin{align*}
> \mathcal{P}\{X \ge t\} &\le \exp \left( -\frac{t^2}{2\sigma^2} \right).
> \end{align*}
>$$ 


>[!important] Definition
>A *centered* random variable $X$ is said to be **sub-Gaussian** with **variance factor** $\nu$ if
>$$
> \begin{align}
> \psi_X(\lambda) &\le  \frac{\lambda^2 \nu}{2}, \quad \text{ for every }\lambda \in \mathbb{R}.
> \end{align}
>$$  
>We denote the collection of such random variables by $\mathcal{G}(\nu)$.

## Explanation




## Examples

- [[Sub-Gaussian Norm]]

>[!example]
>Any **bounded random variable** $X$ is **sub-gaussian** with
>$$
> \begin{align*}
> \lVert X \rVert_{\psi_2}\le C \lVert X \rVert_{\infty}
> \end{align*}
>$$
> where $C = 1/\sqrt{\log 2}$.







-----------
##  Recommended Notes and References

- [[Sub-Gaussian Norm]]

- [[Chernoff Bound for Gaussian distribution]]
- [[Cramér–Chernoff Method]]
- [[Concentration Inequalities by Boucheron]]