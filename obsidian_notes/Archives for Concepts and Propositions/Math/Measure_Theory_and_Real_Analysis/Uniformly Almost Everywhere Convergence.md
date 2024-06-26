---
tags:
  - concept
  - math/functional_analysis
  - math/measure_theory
keywords:
  - uniformly_almost_everywhere_convergence
topics:
  - functional_analysis
  - real_analysis
  - measure_theory
name: uniformly almost everywhere convergence
date of note: 2024-05-05
---

## Concept Definition

>[!important]
>**Name**:  Uniformly Almost Everywhere Convergence


>[!important] Definition
>We say $f_n$ *converges* to $f$ **uniformly almost everywhere**, or **essentially uniformly**, or **in $L^{\infty}$ norm** if, for every $\epsilon> 0$, there exists $N$ such that for every $n\ge  N$,  
>$$| f_n(x) - f(x) | \leq \epsilon$$
>for *$\mu$-almost every * $x \in X$. 
>
>That is, $f_n \rightarrow f$ **uniformly** in $x \in X \setminus E$,  for *some* $E$ with **$\mu(E) = 0$**.


>[!important] Definition
>We can also formulate the *uniformly almost everywhere convergence* in terms of **$L^{\infty}$ norm** as 
> $$
> \left\|f_n(x) - f(x)\right\|_{L^{\infty}(X)} \stackrel{n\rightarrow \infty}{\longrightarrow} 0,
> $$
where
> $$
> \|f\|_{L^{\infty}(X)} = \text{ess}\sup_{x}|f(x)| \equiv\inf\limits_{\{E:\mu(E)=0\}}\sup\limits_{x\in X \setminus E}|f(x)|
> $$
> is the **essential bound**. It is denoted as $f_{n}\stackrel{L^{\infty}}{\rightarrow}f$.

^4f10f6

- [[L-infinite Space]]
- [[Essential Supremum and Essential Infimum]]



## Explanation





-----------
##  Recommended Notes and References

- [[Uniform Convergence]]
- [[Measure Space and Countably Additive Measure]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)