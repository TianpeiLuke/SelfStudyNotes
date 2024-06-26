---
tags:
  - concept
  - math/measure_theory
  - math/real_analysis
keywords:
  - hardy_littlewood_maximal_function
  - hardy_littlewood_maximal_inequality
topics:
  - real_analysis
name: Hardy-Littlewood Maximal Theorem
date of note: 2024-05-28
---

## Theorem

>[!important]
>**Name**: Hardy-Littlewood Maximal Theorem or *Hardy-Littlewood Maximal Inequality*

>[!important] Hardy-Littlewood Maximal Theorem 
>Suppose $f$ is **integrable**, then 
>
>- 
> $$ 
>  \begin{align*}
> H^{*}f(x) &\equiv \sup\left\{  \frac{1}{m(B)}\int_{B}|f(z)|\,dz, \;\, B\text{ is a ball }, x\in B   \right\} .
> \end{align*}
> $$ 
> is **measurable**. 
> 
>-  $$H^{*}f(x) <\infty, \text{ a.e. }.$$
> 
>-  $H^{*}f$ satisfies the **Hardy-Littlewood maximal inequality**:
>$$
> \begin{align*}
> m\left( \left\{ x: \, H^{*}f(x)> \alpha \right\}  \right) &\le \frac{A}{\alpha}\lVert f \rVert_{L^{1}(\mathbb{R}^{d})}
> \end{align*}
>$$ 
> for $\alpha>0$, where $A= 3^{d}$, and $$\lVert f \rVert_{L^{1}(\mathbb{R}^{d})} = \int_{\mathbb{R}^{d}}|f(x)|\,dx.$$
>
> 
>Note that $H^{*}f \ge |f|, \,\text{a.e.}$, but the above expression indicates that $H^{*}f$ is *not much larger than* $|f|$. However, we may *not* be able to assume $H^{*}f$ *integrable* for any $f$.

- [[Hardy-Littlewood Maximal Function]]
- [[Metric Topology and epsilon-ball]]

## Explanation



## Proof

- [[Vitali Covering Lemma]]
- [[Vitali Covering]]



-----------
##  Recommended Notes and References

- [[Covering of Set and Open Covering of Topological Set]]

- 


- [[Introduction to Measure Theory by Tao]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]