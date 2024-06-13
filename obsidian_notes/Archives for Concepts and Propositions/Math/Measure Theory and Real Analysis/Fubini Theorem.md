---
tags:
  - concept
  - math/real_analysis
  - math/measure_theory
  - math/probability
keywords:
  - fubini_theorem
topics:
  - measure_theory
  - real_analysis
  - probability
name: Fubini Theorem
date of note: 2024-05-25
---

## Concept Definition

>[!important]
>**Name**: Fubini's Theorem

>[!info]
>We can extend the conclusion in [[Tonelli Theorem]] to absolutely convergent integral.


>[!important] Fubini's Theorem
>Let $(X, \mathscr{B}_X, \mu_X)$ and $(Y, \mathscr{B}_Y, \mu_Y)$ be **complete $\sigma$-finite measure spaces**, and let $f : X \times Y \to [0, +\infty]$ be **absolutely integrable** with respect to $\mathscr{B}_X \times \mathscr{B}_Y$. 
>
>Then:
> 
>-  For **$\mu_X$-almost every**  $x \in X$,  the function
>$$ 
> \begin{align*}
> y \to f(x,y)
> \end{align*}
>$$  
>is **absolutely integrable with respect to $\mu_Y$** and in particular, $$\int_Y f(x,y) d\mu_Y(y)$$ *exists.* 
>- Furthermore, the **$\mu_X$-almost everywhere defined** *map*
>$$
> \begin{align*}
> x \to \int_Y f(x,y) d\mu_Y(y)
> \end{align*}
>$$  
>is **absolutely integrable with respect to $\mu_X$**.
> 
>-  For **$\mu_Y$-almost every**  $y \in Y$,  the function
>$$ 
> \begin{align*}
> x \to f(x,y)
> \end{align*}
>$$  
>is **absolutely integrable with respect to $\mu_X$** and in particular, $$\int_X f(x,y) d\mu_X(x)$$ *exists*. 
>- Furthermore, the **$\mu_Y$-almost everywhere defined** *map*
>$$
> \begin{align*}
> y \to \int_X f(x,y) d\mu_X(x)
> \end{align*} 
>$$
>is **absolutely integrable with respect to $\mu_Y$**.
> 
>- We have
>$$
> \begin{align}
> &\int_{X \times Y} f(x, y) \;d\left(\overline{\mu_X \times \mu_Y}\right)(x, y) \\
>&= \int_X\left(\int_Y f(x, y) d\mu_Y(y)\right) d\mu_X(x) \nonumber\\
> &=  \int_Y\left(\int_Xf(x, y) d\mu_X(x) \right)d\mu_Y(y) 
> \end{align}
>$$

- [[Absolutely Convergent Integration]]
- [[Product Measure]]
- [[Product sigma-Algebra]]
- [[Finite and sigma-Finite Measure]]



## Explanation

>[!important]
>Informally, **Fubini's theorem** allows one to *always* **interchange the order of two integrals**, as long as the **integrand is absolutely integrable** in the **product space** (or its *completion*). 
>
>In particular, specialising to **Lebesgue measure**, we have
>$$
> \begin{align*}
> \int_{\mathbb{R}^{d+d'}}f(x,y) d(x,y) = \int_{\mathbb{R}^d}\left(\int_{\mathbb{R}^{d'}} f(x, y)dy\right) dx = \int_{\mathbb{R}^{d'}}\left(\int_{\mathbb{R}^{d}} f(x, y)dx\right) dy
> \end{align*}
>$$ 
> whenever $f: \mathbb{R}^{d+d'} \to \mathbb{C}$ is **absolutely integrable**. 
> 
> In view of this, we often *write* $dxdy$ (or $dydx$) for $d(x, y)$.


## Corollary


>[!important] Corollay (Fubini-Tonelli Theorem)
>Let $(X, \mathscr{B}_X, \mu_X)$ and $(Y, \mathscr{B}_Y, \mu_Y)$ be **complete $\sigma$-finite measure spaces**, and let $f: X \times Y \to \mathbb{C}$ be *measurable* *with respect to* $\overline{\mathscr{B}_X \times \mathscr{B}_Y}$.  
>
>If
>$$
> \begin{align*}
>  \int_X \left(\int_Y |f(x, y)| d\mu_Y(y)\right) d\mu_X(x) < \infty
> \end{align*}
>$$ 
> then $f$ is **absolutely integrable** *with respect to* $\overline{\mathscr{B}_X \times \mathscr{B}_Y}$, and in particular the *conclusions* of *Fubini's theorem* hold. 
> 
> Similarly if we use $$\int_Y \left(\int_X |f(x, y)| d\mu_X(x)\right) d\mu_Y(y) $$ 
> instead of $$\int_X \left(\int_Y |f(x, y)| d\mu_Y(y)\right) d\mu_X(x).$$
> 



>[!important] Corollary (Area Interpretation of Integral)
>Let $(X, \mathscr{B}, \mu)$ be a **$\sigma$-finite measure space**, and let $\mathbb{R}$ be equipped with *Lebesgue measure* $m$ and the *Borel* $\sigma$-algebra $\mathcal{B}[\mathbb{R}]$. 
>
>Then $f : X \to [0, +\infty]$ is **measurable** *if and only if* its **subgraph**
>$$
> \begin{align*}
> \set{(x, t)\in X \times \mathbb{R}: 0 \le t\le f(x)}
> \end{align*}
>$$ 
> is **measurable** in $\mathscr{B} \times \mathcal{B}[\mathbb{R}]$, in which case we have
>$$ 
> \begin{align*}
> (\mu \times m)\set{(x, t)\in X \times \mathbb{R}: 0 \le t\le f(x)} &= \int_{X} f(x) d\mu(x).
> \end{align*}
>$$  
>Similarly if we replace $$\set{(x, t)\in X \times \mathbb{R}: 0 \le t\le f(x)}$$ by $$\set{(x, t)\in X \times \mathbb{R}: 0 \le t < f(x)}.$$

- [[Hypograph of Subgraph of Function]]


>[!important] Corollary (Distribution Formula)
>Let $(X, \mathscr{B}, \mu)$ be a **$\sigma$-finite measure space,** and let $f : X \to [0, +\infty]$ be **measurable**. 
>
>Then
>$$
> \begin{align}
>  \int_{X} f(x)\; d\mu(x) &= \int_{[0, \infty]}\mu\set{x\in X: f(x) \ge \lambda}\; d\lambda 
> \end{align}
>$$ 
> 
> (Note that the integrand on the right-hand side is *monotone* and thus *Lebesgue measurable*.) 
> 
> Similarly if we replace $$\set{x\in X: f(x) \ge \lambda}$$ by $$\set{x\in X: f(x) > \lambda}.$$






-----------
##  Recommended Notes and References

- [[Tonelli Theorem]]

- [[Absolutely Convergent Integration]]
- [[Product Measure]]
- [[Product sigma-Algebra]]
- [[Finite and sigma-Finite Measure]]



- [[Introduction to Measure Theory by Tao]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Probability and Measure by Billingsley]]
- [[A Probability Path by Resnick]]
