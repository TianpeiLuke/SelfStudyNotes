---
tags:
  - concept
  - math/functional_analysis
  - math/linear_algebra
  - math/measure_theory
keywords:
  - uniform_convergence
  - pointwise_convergence
  - uniformly_almost_everywhere_convergence
  - almost_uniform_convergence
  - pointwise_almost_everywhere_convergence
  - convergence_in_mean
  - convergence_in_l1_norm
  - convergence_in_measure
topics:
  - functional_analysis
  - real_analysis
  - measure_theory
name: modes of convergence
date of note: 2024-05-05
---

## Modes of Convergence


### Relations between Modes of Convergence

>[!important]
 >Let $(X, \mathscr{F}, \mu)$ be a *measure space*, and let $f_n : X \rightarrow \mathbb{C}$ and $f : X \rightarrow \mathbb{C}$ be *measurable functions*
> 
> - If $f_n$ converges to $f$ **uniformly**, then $f_n$ converges to $f$ **pointwisely**.
> - If $f_n$ converges to $f$ **uniformly**, then $f_n$ converges to $f$ in **$L^\infty$ norm**. 
> - Conversely, if $f_n$ converges to $f$ **in $L^\infty$ norm**, then $f_n$ converges to $f$ **uniformly outside of a null set** 
> 	- i.e. there exists a null set $E$ such that the restriction $f_n\left|_{X/E}\right.$ of $f_n$ to the *complement* of $E$ converges to the restriction $f\left|_{X/E}\right.$ of $f$.
> - If $f_n$ converges to $f$ in **$L^\infty$ norm**, then $f_n$ converges to $f$ **almost uniformly.**
> - If $f_n$ converges to $f$ **almost uniformly**, then $f_n$ converges to $f$ **pointwise almost everywhere.**
> - If $f_n$ converges to $f$ **pointwise**, then $f_n$ converges to $f$ **pointwise almost everywhere**.
> - If $f_n$ converges to $f$ in **$L^1$ norm**, then $f_n$ converges to $f$ **in measure**.
> 	- If $f_n$ converges to $f$ **in measure** and $f_{n}$ is **uniformly integrable**, then $f_{n}$ converges to $f$ in __$L^1$ norm__
> - If $f_n$ converges to $f$ **almost uniformly**, then $f_n$ converges to $f$ **in measure.**


>[!important]
>- $f_n$ converges to $f$ in **$L^p$ norm**  $\longleftrightarrow$  $f_n$ converges to $f$ **in measure** and $\{|f_{n}|^{p}\}$ is **uniformly integrable** and **tight**.
>- If $f_n$ converges to $f$  **pointwise almost everywhere**, then 
>	- $f_n$ converges to $f$ in **$L^p$ norm**  $\longleftrightarrow$   $\{|f_{n}|^p\}$ is **uniformly integrable** and **tight**.

- [[Vitali Lp Convergence Theorem]]

### Counter Arguments that are Not True

>[!important]
> - $L^{\infty} \not\rightarrow L^{1}$: see the **Escape to Width Infinity** example below.
> - $\text{\emph{\textbf{uniform}} } \not\rightarrow L^{1}$: see the **Escape to Width Infinity** example below.
> - $L^{1}  \not\rightarrow \text{\emph{\textbf{uniform}} }$: see the **Typewriter Sequence** example below.
> - $\text{\emph{\textbf{pointwise}} } \not\rightarrow L^{1}$: see the **Escape to Horizontal Infinity** example below.
> - $\text{\emph{\textbf{pointwise}} } \not\rightarrow \text{\emph{\textbf{uniform}}}$: see the **$f_n = x/n$** example above.
> - For finite measure space, $\text{\emph{\textbf{pointwise a.e.}} } \rightarrow \text{\emph{\textbf{almost uniform}}}$: see the **Egorov's theorem**.
> - $\text{\emph{\textbf{almost uniform}}}  \not\rightarrow L^{1}$: see the **Escape to Vertical Infinity** example below.
> - $\text{\emph{\textbf{almost uniform}}}  \not\rightarrow L^{\infty}$: see the **Escape to Vertical Infinity** example below. 
> 	- The **converse** is true, however.
> - For bounded $f_n \le G, a.e.\; \forall n$, then $\text{\emph{\textbf{pointwise a.e.}} } \rightarrow L^{1}$: see **Dominated Convergence Theorem.** 
> - $L^{1}  \not\rightarrow \text{\emph{\textbf{pointwise a.e.}} }$: see the **Typewriter Sequence** example below.
> - $\text{\emph{\textbf{in measure}}} \not\rightarrow \text{\emph{\textbf{pointwise a.e.}} }$: see the **Typewriter Sequence** example below.
> - $L^{1}  \rightarrow \text{\emph{\textbf{convergence in integral}}}$:  by **triangle inequality**. 
> 	- Note that the other modes of convergence *does not directly lead to convergence in integral*.




-----------
##  Recommended Notes and References

- [[Modes of Convergence in Tail Support and Width]]

- [[Pointwise Convergence]]
- [[Pointwise Almost Everywhere Convergence]]
- [[Uniform Convergence]]
- [[Uniformly Almost Everywhere Convergence]]
- [[Convergence in Lp norm]]
- [[Almost Uniform Convergence]]
- [[Convergence in Measure]]

- [[Uniform Integrable Family of Functions]]
- [[Tightness of Integrable Functions]]
- [[Vitali Lp Convergence Theorem]]

- [[Measure Space and Countably Additive Measure]]