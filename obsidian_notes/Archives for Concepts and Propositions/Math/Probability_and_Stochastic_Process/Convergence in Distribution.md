---
tags:
  - concept
  - math/functional_analysis
  - math/probability
keywords:
  - convergence_in_distribution
topics:
  - functional_analysis
  - probability
name: convergence in distribution
date of note: 2024-05-09
---

## Concept Definition

>[!important]
>**Name**:  Convergence in Distribution or **Weak Convergence**


>[!important] Definition
>Let $X_n : \Omega \rightarrow \mathbb{R}$ be a sequence of *random variables* (real-valued *measurable functions*), and $X: \Omega \rightarrow \mathbb{R}$ be another random variable (*measurable function*). 
>
>We say that $X_n$ **converges in distribution** to $X$ if **the cumulative distribution function** $F_n(\lambda)$ of $X_n$ *converges pointwise* to the cumulative distribution function $F(\lambda)$ of $X$ at all $\lambda \in \mathbb{R}$ for which $F$ is *continuous.* 
>
>**Denoted** as $X_{n}\stackrel{F}{\rightarrow} X$ or $X_{n}\stackrel{d}{\rightarrow} X$ or $X_n \rightsquigarrow X$, or $F_{n} \Rightarrow F$ 
>$$
> \begin{align*}
> X_{n}\stackrel{d}{\rightarrow} X \; \Leftrightarrow \; F_n(\lambda) \rightarrow F(\lambda), \text{ for all }\lambda \in \mathbb{R}
> \end{align*}
>$$ 

- [[A Probability Path by Resnick]]
- [[Probability and Measure by Billingsley]]


## Explanation

>[!info]
>Note that the c.d.f of $X$ corresponds to a *push-forward measure* of $\mathcal{P}$ by random variable $X$.
>$$
>F_{n}(\lambda) := ((X_{n})_{*}\mathcal{P})((-\infty , \lambda])
>$$ 

- [[Push-forward Measure and Push-forward Operator]](
- [[Push-forward Measure and Push-forward Operator]]

## General Definition on Metric Measure Space

>[!important] Definition
>Let $(\Omega, d)$ be a *__metric space__*, and $(\Omega, \mathscr{B})$ be *a __measurable space__*, where $\mathscr{B}$ is the *Borel $\sigma$-field* on $\Omega$, the smallest $\sigma$-field containing all the open balls (as the basis of *metric topology* on $\Omega$). Let $\{\mu_n \}$ and $\mu$ be *__Borel probability measures__* on $(\Omega, \mathscr{B})$.
>
>Then the sequence $\mu_n$ **converges in distribution** to $\mu$, which we write as $\mu_n \rightsquigarrow \mu$, *if and only if*
>$$
> \begin{align*}
> \int_{\Omega} f d\mu_n \rightarrow \int_{\Omega} f d\mu, \quad \text{ for all } f \in \mathcal{BC}(\Omega).
> \end{align*}
>$$ 
>Here $\mathcal{BC}(\Omega)$ denotes the set of all *bounded*, *continuous*, real functions on $\Omega$.

- [[Weak-star Topology of Banach Space]]
- [[Summary of Spaces of Continuous Functions]]


### Weak* Convergence

>[!important]
> We can see that **the convergence in distribution** is actually a **weak$^{*}$ convergence**. 
> 
> That is, it is **the weak convergence** of  **bounded linear functionals** 
>$$
> I_{\mu_n} \stackrel{w^{*}}{\rightarrow} I_{\mu}
>$$ 
>on *the space of all probability measures* $\mathcal{M}_{\mu}(\Omega) \simeq (\mathcal{BC}(\Omega))^{*}$ on $(\Omega, \mathscr{B})$ where 
>$$
>\begin{align*}
> I_{\mu}: f \mapsto \int_{\Omega} f d\mu.
>\end{align*} 
>$$ 

- Note that $\mathcal{C}_{0}(\Omega) \subseteq \mathcal{BC}(\Omega)$.
- If we further restrict $\Omega$ to be a *compact Hausdorff space*, then we have  $\mathcal{C}_{0}(\Omega) = \mathcal{BC}(\Omega)$. Then we can use [[Riesz-Markov Representation Theorem]]
- Wikipedia [Weak_convergence_of_measures](https://en.wikipedia.org/wiki/Convergence_of_measures#Weak_convergence_of_measures)- Wikipedia [Weak_convergence_of_measures](https://en.wikipedia.org/wiki/Convergence_of_measures#Weak_convergence_of_measures)


>[!info]
>Note that the $I_{\mu_n} \stackrel{w^{*}}{\rightarrow} I_{\mu}$ is equivalent to $I_{\mu_n}(f) \rightarrow I_{\mu}(f)$ for all $f \in  \mathcal{BC}(\Omega)$.


## Helly Selection Theorem

- [[Helly Selection Theorem]]


## Equivalent Conditions for Convergence in Distribution

![[Portmanteau Theorem#^d01470]]

- [[Portmanteau Theorem]]

![[Continuity Theorem for Convergence in Distribution#^11ddd4]]

- [[Characteristic Function of Random Variable]]
- [[Continuity Theorem for Convergence in Distribution]]


-----------
##  Recommended Notes and References

- [[Probability Distribution of Random Variable]]
- [[Weak Convergence in Banach Space]]
- [[Weak Topology of Banach Space]]

- [[Tightness of Measures]]

- [[Asymptotic Statistics by A W van der Vaart]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)