---
tags:
  - concept
  - math/calculus_of_variations
  - math/functional_analysis
  - math/differential_equation
keywords:
  - fundamental_lemma_calculus_of_variations
  - weak_extremum_functional
topics:
  - variational_calculus
  - functional_analysis
  - differential_equation
name: Fundamental Lemma of the Calculus of Variations
date of note: 2024-10-30
---

## Concept Definition

>[!important]
>**Name**: Fundamental Lemma of the Calculus of Variations

>[!important] Fundamental Lemma of the Calculus of Variations
>Let $f\in \mathcal{C}(\Omega, \mathbb{R})$ be a **continuous real-valued function** on an open set $\Omega \subset \mathbb{R}^{n}$, and 
>- suppose that $$\int_{\Omega}\,f(x)\,\eta(x)\,dx \ge 0,\quad \forall \eta \in \mathcal{C}_{0}^{\infty}(\Omega),\; \eta \ge 0$$ holds. Then we have  $$f(x) \ge 0, \quad \forall x\in \Omega.$$
>  
>- Suppose that  $$\int_{\Omega}\,f(x)\,\eta(x)\,dx = 0, \quad \forall \eta\in \mathcal{C}_{c}^{\infty}(\Omega)$$ holds. Then we have  $$f(x) = 0, \quad \forall x\in \Omega.$$
>
>

^0510db

- [[Continuous Functions that Vanish At Infinity]]
- [[Continuous Functions with Compact Support]]
- [[Smooth Map between Euclidean Spaces]]

### General Form $L^1$ space

>[!important] Fundamental Lemma of the Calculus of Variations (General Form)
>Let $f\in L^{1}(\Omega)$ be a **integrable real-valued function** on an open set $\Omega \subset \mathbb{R}^{n}$, and 
>- suppose that $$\int_{\Omega}\,f(x)\,\eta(x)\,dx \ge 0,\quad \forall \eta \in \mathcal{C}_{c}^{\infty}(\Omega),\; \eta \ge 0$$ holds. Then we have  $$f(x) \ge 0, \quad \text{ a.e. in } \Omega.$$
>  
>- Suppose that  $$\int_{\Omega}\,f(x)\,\eta(x)\,dx = 0, \quad \forall \eta\in \mathcal{C}_{c}^{\infty}(\Omega)$$ holds. Then we have  $$f(x) = 0,\quad \text{ a.e. in } \Omega.$$
>
>

- [[Absolutely Convergent Integration]]
- [[Lp Space]]
- [[Pointwise Almost Everywhere Convergence]]

### Sobolev Space 

>[!important] Fundamental Lemma of the Calculus of Variations (Du Bois-Reymond's Lemma)
>Let $f\in L^{1}(\Omega)$ be a *integrable real-valued function* on an open set $\Omega \subset \mathbb{R}^{n}$, and 
>- suppose that $$\int_{\Omega}\,f(x)\,D^{\alpha}\eta(x)\,dx = 0,\quad \forall \eta \in \mathcal{C}_{c}^{\infty}(\Omega),\;\forall 1 \le \alpha \le n$$ holds. Then we have  $$f(x) = \text{const.}\quad \text{ a.e. in } \Omega.$$
>
>

- [[Sobolev Space]]


### Subsidiary Conditions

>[!important] Fundamental Lemma of the Calculus of Variations (Subsidiary Conditions)
>Let $f\in L^{1}(\Omega)$ be a *integrable real-valued function* on an open set $\Omega \subset \mathbb{R}^{n}$, and suppose that $$\int_{\Omega}\,f(x)\,\eta(x)\,dx = 0$$ holds for all $\eta \in \mathcal{C}_{c}^{\infty}(\Omega)$ subject to the **subsidiary condition** $$\int_{\Omega}\,g(x)\,\eta(x)\,dx = 0$$
>
>Then there exists $\lambda \in \mathbb{R}$ such that   $$f(x) = \lambda\,g(x) \quad \text{ a.e. in } \Omega.$$
>
>In particular, if $f\in L^{1}(\Omega)$ satisfies $$\int_{\Omega}\,f(x)\,\eta(x)\,dx = 0$$ for all $\eta \in \mathcal{C}_{c}^{\infty}(\Omega)$ with **mean value zero** and the mean of $\Omega$ is bounded, then $$f(x) = \text{const.} \quad \text{ a.e. in } \Omega.$$





## Explanation




-----------
##  Recommended Notes and References



- [[First Variation of Functional]]
- [[Gateaux Derivative and Weak Derivative in Banach Space]]
- [[Euler–Lagrange Equations]]
- [[Principle of Least Action]]

- [[Banach Space]]


- [[Calculus of Variations by Gelfand]] pp 9 - 11
- Giaquinta, M. and Hildebrandt, S. (1996) *Calculus of Variations 1. The Lagrangian Formalism*, Grundlehren der Mathematischen Wissenschaften 310. Springer-Verlag, Berlin. pp 16, 32