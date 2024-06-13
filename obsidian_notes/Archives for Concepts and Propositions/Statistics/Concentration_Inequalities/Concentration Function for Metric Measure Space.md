---
tags:
  - concept
  - statistics/concentration_inequality
keywords:
  - concentration_function
topics:
  - concentration_inequality
name: Concentration Function
date of note: 2024-05-29
---

## Concept Definition

>[!important]
>**Name**: Concentration Function


>[!important] Definition
>The **concentration function** $\alpha: [0, \infty) \to \mathbb{R}_{+}$  associated with *metric probability space* $((\mathcal{X}, d)\,,\, \mathscr{B}(\mathcal{X})\,,\, \mathcal{P})$ is given by
>$$
> \begin{align*}
> \alpha_{\mathcal{P}, (\mathcal{X}, d)}(t) &:= \sup\left\{\mathcal{P}\left\{x: d(x, A) \ge t  \right\}: A \in \mathscr{B}(\mathcal{X}),\, \mathcal{P}(A) \ge \frac{1}{2}  \right\}   \\
>&= \sup \left\{ \mathcal{P}\left( A_{t}^{c} \right):  A \in \mathscr{B}(\mathcal{X}),\,\mathcal{P}(A) \ge \frac{1}{2} \right\} 
> \end{align*}
>$$  
>where $A_t:= A + tB = \set{x \in \mathcal{X}: d(x, A) < t}$ is **the $t$-blowup** of $A \in \mathscr{B}$. 
>
>We simply denote it as $\alpha(t)$.

^e2211a

- [[Isoperimetry Problem in Probability Metric Space]]


>[!info]
> Thus the optimal $A^{*}$ for **isoperimetry problem** is the one that attains the $$\alpha(t) = \mathcal{P}\left( A_{t}^{c}  \right).$$


## Explanation

>[!important]
>The degree of **concentration** is determined by
>- the definition of **metric** $d$
>- the definition of **measure** $\mathcal{P}$
>- the **dimension** of the space

- [[Concentration Function for Lebesgue Measure on Sphere]]



-----------
##  Recommended Notes and References

- [[Isoperimetry Problem in Probability Metric Space]]


- [[Probability Space]]
- [[Borel sigma Field]]
- [[Metric Space]]



- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Concentration Inequalities by Boucheron]]