---
tags:
  - concept
  - math/real_analysis
  - math/functional_analysis
  - math/measure_theory
keywords:
  - vitali_convergence_theorem
topics:
  - real_analysis
  - functional_analysis
  - measure_theory
name: Vitali Convergence Theorem for Uniformly Integrable Tight Functions
date of note: 2024-06-20
---

## Concept Definition

>[!important]
>**Name**: Vitali Convergence Theorem for Uniformly Integrable Tight Functions

>[!important] Vitali Convergence Theorem
>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a measure space and $\{ f_{n} \} \subset L^1(\mathcal{X},\mu)$ be a *sequence of functions* on $\mathcal{X}$ that is both
>-  **uniformly integrable** and **tight** over $\mathcal{X}$. 
>
>Assume that 
>- $f_{n} \to f$ **pointwise almost everywhere** on $\mathcal{X}$, and the function $f \in L^1(\mathcal{X}, \mu)$.
>
>Then  
>$$
>\begin{align*}
> \lim_{ n \to \infty } \int_{\mathcal{X}}\,f_{n}\,d\mu = \int_{\mathcal{X}}\,f\,d\mu.
>\end{align*}
>$$
 
- [[Tight Family of Integrable Functions]]
- [[Uniform Integrable Family of Functions]]
- [[Dominated Convergence Theorem]]
- [[Absolutely Convergent Integration]]
- [[Real Analysis by Royden]]  pp 377

>[!important] Vitali Convergence Theorem ($L^p$ space)
>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a measure space. Let $$\{ f_{n} \} \subset L^p(\mathcal{X}, \mu)$$ for $1 \le p < \infty$ and $f \in L^p(\mathcal{X}, \mu)$.
>
>Then the following two statements are **equivalent**:
>- $\{ f_{n} \}$ converges to $f$ **in $L^p$ norm**, i.e. $$f_{n} \stackrel{L^p}{\longrightarrow} f;$$
>- $\{ f_{n} \}$ is **uniformly integrable** and **tight** over $\mathcal{X}$, and $\{ f_{n} \}$ converges to $f$ **$\mu$-pointwise almost everywhere**, i.e. $$f_{n} \to f; \quad \mu\text{-a.e.}$$

- [[Convergence in Norm]]
- [[Convergence in Lp norm]]
- [[Pointwise Almost Everywhere Convergence]]
- [[Lp Space]]


## Explanation

>[!info] 
>**Vitali Convergence Theorem** is a *generalization* of [[Dominated Convergence Theorem]] to $L^p$ norm.

>[!info] 
>**Vitali Convergence Theorem** provides a characterization of **convergence in $L^p$ norm** for $1 \le p < \infty.$

- [[Convergence in Lp norm]]

>[!info]
>For **finite measure space**, $\mu(\mathcal{X}) < \infty$, we can drop the **tightness condition**

- [[Finite and sigma-Finite Measure]]




-----------
##  Recommended Notes and References

- [[Lp Space]]
- [[Vitali Covering]]

- [[Tight Family of Integrable Functions]]
- [[Uniform Integrable Family of Functions]]
- [[Dominated Convergence Theorem]]


- [[Real Analysis by Royden]]  pp 377