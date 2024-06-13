---
tags:
  - concept
  - math/real_analysis
  - math/measure_theory
  - math/probability
keywords:
  - tonelli_theorem
topics:
  - measure_theory
  - real_analysis
  - probability
name: Tonelli's Theorem
date of note: 2024-05-25
---

## Concept Definition

>[!important]
>**Name**: Tonelli Theorem

>[!important] Tonelli's Theorem, Incomplete Version
>Let $(X, \mathscr{B}_X, \mu_X)$ and $(Y, \mathscr{B}_Y, \mu_Y)$ be **$\sigma$-finite measure spaces**, and let $f : X \times Y \to [0, +\infty]$ be *measurable* with respect to $\mathscr{B}_X \times \mathscr{B}_Y$. 
>
>Then:
> 
>- The functions 
>$$ 
> \begin{align*}
> x \to \int_Y f(x,y) d\mu_Y(y)\\
> y \to \int_X f(x,y) d\mu_X(x)
> \end{align*}
>$$ 
>(which are well-defined) are **measurable** with **respect to $\mathscr{B}_X$ and $\mathscr{B}_Y$ respectively**.
> 
>- We have
>$$
> \begin{align}
> &\int_{X \times Y} f(x, y) \;d\left(\mu_X \times \mu_Y\right)(x, y) \\
> &= \int_X \left(\int_Y f(x, y) d\mu_Y(y)\right) d\mu_X(x) \nonumber\\
> &=  \int_Y \left(\int_Xf(x, y) d\mu_X(x)\right)d\mu_Y(y)  
> \end{align}
>$$ 
>

- [[Unsigned Integral of Functions]]
- [[Product Measure]]
- [[Product sigma-Algebra]]
- [[Finite and sigma-Finite Measure]]

>[!important] Corollary  (Slice of Null Set)
> Let $(X, \mathscr{B}_X, \mu_X)$ and $(Y, \mathscr{B}_Y, \mu_Y)$ be **$\sigma$-finite measure spaces**, and let $E \in \mathscr{B}_X \times \mathscr{B}_Y$ be a **null set** *with respect to* $\mu_X \times \mu_Y$. 
> 
> Then 
> - for **$\mu_X$-almost every**  $x \in X$, the set $$E_x := \set{y \in Y: (x, y) \in E}$$ is a **$\mu_Y$-null set**; and similarly, 
>- for **$\mu_Y$-almost every** $y \in Y$,  the set $$E^y := \set{x \in X: (x, y) \in E}$$ is a **$\mu_X$-null set**.



>[!important] Tonelli's Theorem, Complete Version
>Let $(X, \mathscr{B}_X, \mu_X)$ and $(Y, \mathscr{B}_Y, \mu_Y)$ be **complete $\sigma$-finite measure spaces**, and let $f : X \times Y \to [0, +\infty]$ be *measurable* with respect to $\mathscr{B}_X \times \mathscr{B}_Y$. 
>
>Then:
> 
>-  For **$\mu_X$-almost every**  $x \in X$,  the function
>$$ 
> \begin{align*}
> y \to f(x,y)
> \end{align*}
>$$  
>is **$\mathscr{B}_Y$-measurable** and *in particular,* $$\int_Y f(x,y) d\mu_Y(y)$$ *exists.* 
>- Furthermore, the **$\mu_X$-almost everywhere defined** *map*
>$$
> \begin{align*}
> x \to \int_Y f(x,y) d\mu_Y(y)
> \end{align*}
>$$  
>is **$\mathscr{B}_X$-measurable**.
> 
>-  For **$\mu_Y$-almost every**  $y \in Y$,  the function
>$$ 
> \begin{align*}
> x \to f(x,y)
> \end{align*}
>$$  
>is **$\mathscr{B}_X$-measurable** and in particular, $$\int_X f(x,y) d\mu_X(x)$$ *exists*. 
>- Furthermore, the **$\mu_Y$-almost everywhere defined** *map*
>$$
> \begin{align*}
> y \to \int_X f(x,y) d\mu_X(x)
> \end{align*} 
>$$
>is **$\mathscr{B}_Y$-measurable**.
> 
>- We have
>$$
> \begin{align}
> &\int_{X \times Y} f(x, y) \;d\left(\overline{\mu_X \times \mu_Y}\right)(x, y) \\
>&= \int_X\left(\int_Y f(x, y) d\mu_Y(y)\right) d\mu_X(x) \nonumber\\
> &=  \int_Y\left(\int_Xf(x, y) d\mu_X(x) \right)d\mu_Y(y) 
> \end{align}
>$$



## Explanation

>[!important]
>Tonelli’s theorem can **fail** if **the $\sigma$-finite hypothesis** is **removed**, and also that **product measure need not be unique**.

>[!info]
>Tonelli's theorem is for the **unsigned integral**, but it leads to an important analogue for the **absolutely integral**, known as **Fubini's theorem**

- [[Fubini Theorem]]

## Corollary


>[!important] Proposition
>Let $(X, \mathscr{B}_X, \mu_X)$ and $(Y, \mathscr{B}_Y, \mu_Y)$ be **complete $\sigma$-finite measure spaces**, and let $$E \in \overline{\mathscr{B}_X \times \mathscr{B}_Y}.$$ 
>
>Then:
>
>- For **$\mu_X$-almost every**  $x \in X$,  the set
>$$
> \begin{align*}
> E_x := \set{y \in Y: (x, y) \in E} \in \mathscr{B}_Y
> \end{align*}
>$$  
>- and the **$\mu_X$-almost everywhere defined** *map*
>$$ 
> \begin{align*}
> x \to \mu_Y(E_x)
> \end{align*}
>$$  
>is **$\mathscr{B}_X$-measurable**.
> 
>-  For **$\mu_Y$-almost every**  $y \in Y$,  the set
>$$ 
> \begin{align*}
> E^y := \set{x \in X: (x, y) \in E} \in \mathscr{B}_X
> \end{align*} 
>$$ 
>- and the **$\mu_Y$-almost everywhere defined** map
>$$
> \begin{align*}
> y \to \mu_X(E^y)
> \end{align*}
>$$  
>is **$\mathscr{B}_Y$-measurable**.
> 
>- We have
>$$
> \begin{align}
> \overline{\mu_X \times \mu_Y}(E) &= \int_X\mu_Y(E_x)\; d\mu_X(x) \nonumber\\
> &=  \int_Y \mu_X(E^y)\;d\mu_Y(y) 
> \end{align}
>$$ 









-----------
##  Recommended Notes and References

- [[Absolutely Convergent Integration]]
- [[Product Measure]]
- [[Product sigma-Algebra]]
- [[Finite and sigma-Finite Measure]]



- [[Introduction to Measure Theory by Tao]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Probability and Measure by Billingsley]]
- [[A Probability Path by Resnick]]
