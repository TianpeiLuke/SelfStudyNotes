---
tags:
  - concept
  - math/convex_analysis
keywords:
  - jensen_inequality
topics:
  - convex_analysis
name: Jensen Inequality
date of note: 2024-05-08
---

## Concept Definition

>[!important]
>**Name**:  Jensen's Inequality


>[!important] Jensen's Inequality (Finite version)
>Let $\varphi: X \to \mathbb{R}$ be **convex function**.  Given a sequence of points $(x_{i})_{i=1}^n$ in the domain $X$ and a sequence of *positive numbers* $(a_{i})_{i}^n$, the Jensen's inequality states that
>$$
>\begin{align*}
>\varphi \left( \frac{\sum_{i=1}^n a_{i}x_{i} }{\sum_{i=1}^n a_{i}}\right) &\le  \frac{\sum_{i=1}^n a_{i} \varphi\left(x_{i}\right)   }{\sum_{i=1}^n a_{i}}
\end{align*}
>$$ 
>Equality holds if and only if $x_{1} = x_{2} \,{=}\ldots{=}\, x_{n},$ or $\varphi$ is *linear* on the domain $X.$

- [[Convex Function]]

>[!important] Jensen's Inequality (Integration version)
>Let $(X, \mathscr{F}, \mu)$ be a *measure space.* Let $f:X \to \mathbb{R}$ be a $\mu$-measurable function and  $\varphi: \mathbb{R} \to \mathbb{R}$ be **convex function**. Then
>$$
> \begin{align*}
> \varphi \left(\int_{X} f d\mu \right) &\le \int_{X} \varphi \circ f\, d\mu. 
> \end{align*}
>$$ 

- [[Measurable Function]]


>[!important] Jensen's Inequality (Probability version)
>Let $(\Omega, \mathscr{F}, \mathcal{P})$ be a *probability space.* Let $X:\Omega \to \mathbb{R}$ be a random variable ($\mathcal{P}$-measurable function) and  $\varphi: \mathbb{R} \to \mathbb{R}$ be **convex function**. Then
>$$
> \begin{align}
> \varphi \left( \mathbb{E}_{\mathcal{P}}\left[ X \right] \right) := \varphi \left(\int_{\Omega} X d\mathcal{P} \right) &\le \int_{\Omega} \varphi \circ X\, d\mathcal{P} := \mathbb{E}_{\mathcal{P}}\left[ \varphi(X) \right]. 
> \end{align}
>$$ 

^df6fae

- [[Random Element and Random Variable]]



## Explanation




- [[Hölder Inequality]]


-----------
##  Recommended Notes and References

- Wikipedia [Jensen's_inequality](https://en.wikipedia.org/wiki/Jensen%27s_inequality)
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)