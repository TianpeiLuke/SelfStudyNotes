---
tags:
  - concept
  - math/information_theory
  - math/information_geometry
  - math/functional_analysis
  - deep_learning/generative_models
  - machine_learning/kernel_methods
keywords:
  - integral_probability_metric
topics:
  - information_theory
  - information_geometry
  - machine_learning/kernel_methods
  - machine_learning_theory
  - deep_learning/generative_models
name: Integral Probability Metric between Probability Measures
date of note: 2024-11-07
---

## Concept Definition

>[!important]
>**Name**: Integral Probability Metric between Probability Measures

>[!important] Definition
>if $P$ and $Q$ are *probability measures* on a measurable space $(\Omega, \mathscr{F})$, and $P$ is *absolutely continuous* with respect to $Q$, 
>$$P \ll Q.$$
>
>The **integral probability metric (IPM)** is defined as 
>$$
>\begin{align*}
>D_{\mathcal{F}}(P, Q) &:= \sup_{f\in \mathcal{F}}\lvert \mathbb{E}_{ P }\left[  f(X) \right] - \mathbb{E}_{ Q }\left[  f(X) \right] \rvert \\[8pt]
>&=  \sup_{f\in \mathcal{F}} \left\lvert \int f\,dP - \int f\,dQ \right\rvert
>\end{align*}
>$$
>where 
>- $\mathcal{F}$ is a class of real-valued functions on $\Omega$. $f\in \mathcal{F}$ is called a **witness function**.


### Uniform Metric on Functional Space

>[!important] Definition
>The  **integral probability metric (IPM)** between two probability measures can be viewed as a **uniform operator metric** on *space of probability measures*, i.e.
>$$
>D_{\mathcal{F}}(P, Q) := \lVert P - Q \rVert_{\mathcal{F}} := \sup_{f\in \mathcal{F}}\lvert P\,f - Q\,f \rvert  
>$$
>where $P, Q$ are identified with a *bounded linear operator* on $\mathcal{F}$, i.e. $$P\,f := \int f\,dP, \quad Q\,f := \int f\,dQ.$$

- [[Riesz-Markov Representation Theorem]]
- [[Bounded Linear Functional]]
- [[Radon Measure]]
- [[Space of Bounded Signed Measures]]



## Explanation


### Glivenko-Cantelli Class and Weak Convergence of Measures

![[Glivenko-Cantelli Class#^a200eb]]

- [[Glivenko-Cantelli Class]]
- [[Supremum of Empirical Process indexed by VC Class]]


>[!info]
>If the **empirical measure** $\mathcal{P}_{n}$ *converge* to $\mathcal{P}$ under **weak$^{*}$ topology** of dual space of $\mathcal{F}^{*}$
>$$
>\mathcal{P}_{n} \stackrel{w}{\rightarrow} \mathcal{P}
>$$
>then $\mathcal{F}$ is a **strong Glivenko-Cantelli class**

- [[Weak-star Topology of Banach Space]]
- [[Weak Convergence in Banach Space]]
- [[Convergence in Distribution]]


## $f$-Divergence

![[integral_prob_f_diverg.png]]

>[!important]
>The only **integral probability metric** that is also a *$f$-divergence* is the **total variation** of measure.
>
>$$
>\begin{align*}
>V(P, Q) &:= \sup_{A\in \mathscr{F}}\lvert  P(A) - Q(A) \rvert  \\[5pt]
>&= \sup_{\mathbb{1} \in \mathcal{F}}\left\{ \left\lvert \int_{\Omega}\mathbb{1}_{A}\,P - \int_{\Omega}\mathbb{1}_{A}\,Q   \right\rvert   \right\} 
>\end{align*}
>$$
>That is $$\mathcal{F} := \left\{ \mathbb{1}_{A}: \;A\in \mathscr{F} \right\} $$

- [[Total Variation between Measures]]

- [[Variational Formula for f-Divergence]]
- [[f-Divergence]]

## Wasserstein Distance

>[!important]
>**Wasserstein-1 distance** is a *integral probability metric* 
>$$\mathcal{W}_{1}(P, Q) = \sup_{f\in \mathcal{F}}\left\{ \left\lvert \int_{\Omega} f\;dP -  \int_{\Omega}\,f\;dQ  \right\rvert  \right\}$$
 >where the function class $\mathcal{F}$ is the **Lipschitz continuous function** with Lipschitz constant bounded by $1$
>$$
>\mathcal{F} := \left\{f: \Omega \to \mathbb{R}:\; \exists K \le 1,\;\; d_{\mathbb{R}}(f(x), f(y)) \le K\,d(x, y), \forall x, y \in \mathcal{X}\;  \right\}
>$$

- [[Variational Representation of Wasserstein Distance]]
- [[Wasserstein Distance]]
- [[Wasserstein Space]]

## Maximum Mean Discrepancy 

>[!important]
>The **maximum mean descrepancy** is a *integral probability metric* 
>$$\mathcal{W}_{1}(P, Q) = \sup_{f\in \mathcal{F}}\left\{ \left\lvert \int_{\Omega} f\;dP -  \int_{\Omega}\,f\;dQ  \right\rvert  \right\}$$
 >where the function class $\mathcal{F}$ is the **Lipschitz continuous function** with Lipschitz constant bounded by $1$
>$$
>\mathcal{F} := \left\{f: \Omega \to \mathbb{R}:\; \exists K \le 1,\;\; d_{\mathbb{R}}(f(x), f(y)) \le K\,d(x, y), \forall x, y \in \mathcal{X}\;  \right\}
>$$

![[Maximum Mean Discrepancy between Probability Measures via RKHS#^345e1a]]

- [[Maximum Mean Discrepancy between Probability Measures via RKHS]]



-----------
##  Recommended Notes and References



- [[Maximum Mean Discrepancy between Probability Measures via RKHS]]
- [[Principle of Learning by Comparison for Implicit Generative Models]]

- [[Kullback-Leibler Divergence]]
- [[Divergence Function on Manifold]]



- [[Statistical Manifold as Parametric Family]]
- [[Reproducing Kernel of RKHS]]
- [[Reproducing Kernel Hilbert Space]]
- [[RKHS of Gaussian Process]]
- [[Gaussian Process]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 57,  889
- Wikipedia [Integral_probability_metric](https://en.wikipedia.org/wiki/Integral_probability_metric)


