---
tags:
  - concept
  - math/measure_theory
  - math/real_analysis
keywords:
  - hardy_littlewood_maximal_function
topics:
  - real_analysis
name: Hardy-Littlewood Maximal Function
date of note: 2024-05-28
---

## Concept Definition

>[!important]
>**Name**: Hardy-Littlewood Maximal Function

>[!important] Definition
>If $f\in L_{loc}^{1}(\mathbb{R}^{d})$, the **Hardy-Littlewood maximal function** $Hf(x)$ is defined as
>$$
> \begin{align*}
> Hf(x)&\equiv \sup_{r>0}\frac{1}{m(B(r,x))}\int_{B(r,x)}|f(z)|dz
> \end{align*}
>$$ 
> where $B(r,x)= \set{y: \lVert y -x \rVert < r}$, and the **average value** of $f$ **on** $B(r,x)$ is 
>$$ 
> \begin{align*}
> A_{r}f(x)&=\frac{1}{m(B(r,x))}\int_{B(r,x)}f(z)dz.
> \end{align*}
>$$ 

- [[Differentiation of Locally Integrable Function]]
- [[Metric Topology and epsilon-ball]]


## Explanation

>[!info]
>The *Hardy-Littlewood maximal function* is an important function in the field of **(real-variable) harmonic analysis**.


## Properties

>[!important] Proposition
>The Hardy-Littlewood maximal function has the following properties:
> 
>- $$(Hf)^{-1}(a, \infty) = \bigcup_{r>0}(A_{r}f)^{-1}(a,\infty)$$ is **open** for any $a\in \mathbb{R}$, so the *Hardy-Littlewood maximal function* is **measurable**. 
>-  Moreover, $$Hf(x)<\infty, \,\text{ a.e.}$$ is **essentially bounded**.  
>- $$Hf \le H^{*}f \le 2^{d}Hf$$
>

- [[Hardy-Littlewood Maximal Theorem]]




-----------
##  Recommended Notes and References

- [[Covering of Set and Open Covering of Topological Set]]
- [[Hardy-Littlewood Maximal Theorem]]


- [[Introduction to Measure Theory by Tao]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]