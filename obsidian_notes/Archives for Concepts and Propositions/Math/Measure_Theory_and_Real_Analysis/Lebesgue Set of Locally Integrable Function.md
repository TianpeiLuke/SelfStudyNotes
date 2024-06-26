---
tags:
  - concept
  - math/measure_theory
  - math/real_analysis
keywords:
  - lebesgue_set_locally_integrable_function
topics:
  - real_analysis
name: Lebesgue Set of Locally Integrable Function
date of note: 2024-05-28
---

## Concept Definition

>[!important]
>**Name**: Lebesgue Set of Locally Integrable Function

>[!important] Definition
>If $f\in L_{loc}^{1}(\mathbb{R}^{d})$, the **Lebesgue set** of $f$ consists of *all points* $\overline{x}\in \mathbb{R}^{d}$ for which $f(\overline{x})$ is **finite** and 
>$$
> \begin{align*}
> \lim\limits_{B \ni \overline{x},\; m(B)\rightarrow 0}\frac{1}{m(B)}\int_{B}\lvert f(z)- f(\overline{x}) \rvert  dz &= 0.
> \end{align*}
>$$ 

- [[Locally Integrable Function]]
or equivalent saying, [[Real Analysis Modern Techniques and Their Applications by Folland]]

>[!important] Definition
>Equivalently,
>$$
> \begin{align*}
> Lf &\equiv \left\{  x\in \mathbb{R}^{d}: \lim\limits_{r\rightarrow 0}\frac{1}{m\left( B(r,x) \right) }\int_{B(r,x)}\lvert f(z)- f(x) \rvert  dz = 0  \right\}.
> \end{align*}
>$$ 


## Explanation


## Properties


![[Lebesgue Density from Radon-Nikodym Derivative#^7e0527]]

- [[Lebesgue Density from Radon-Nikodym Derivative]]


>[!important] Proposition
>If $f$ is **locally integrable** on $\mathbb{R}^{d}$, then **almost every** *point* belongs to **the Lebesgue set** of $f$. 

- [[Locally Integrable Function]]




-----------
##  Recommended Notes and References

- [[Locally Integrable Function]]
- [[Set Shrink Regularly and Bounded Eccentricity]]


- [[Introduction to Measure Theory by Tao]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]