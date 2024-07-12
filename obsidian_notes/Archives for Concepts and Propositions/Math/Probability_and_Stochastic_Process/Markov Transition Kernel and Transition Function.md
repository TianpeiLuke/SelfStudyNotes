---
tags:
  - concept
  - math/stochastic_process
  - math/functional_analysis
  - machine_learning_models/mc
keywords:
  - Markov_Chain
  - Transition_Kernel
  - transition_function
topics:
  - stochastic_process
  - functional_analysis
  - machine_learning_models
name: Markov Chain
date of note: 2024-04-18
---

## Concept Definition

>[!important]
>**Name**:  Markov Chain Transition Kernel

### Transition Kernel

>[!important] Definition: 
> A **transition kernel** (or **probability kernel**) is a function $K$ defined on $\mathcal{X} \times \mathcal{B}(\mathcal{X})$ such that 
> 1. $\forall x \in \mathcal{X}$,    $K(x, \cdot)$  is a **probability measure**;
> 2. $\forall A \in \mathcal{B}(\mathcal{X})$,    $K(\cdot, A)$ is a **measurable** function.

^3d05e1

- $\mathcal{B}(\mathcal{X})$ is the Borel $\sigma$-Algebra. [[Borel sigma Field]]
- [[Probability Space]]
- [[Measurable Function]]
- [[Conditional Probability]]
- [[Monte Carlo Statistical Methods by Robert]]

### Transition Function

>[!important] Definition
>Let $p(s, x, t, A)$ be a *non-negative function* defined for $0 \le s < t < \infty$, $x\in \mathcal{X}$, $A\in \mathcal{B}(\mathcal{X})$, and satisfying:
>1. $p(s, x, t, A)$ is **Borel measurable** in $x$, for fixed $s, t, A$;
>2. $p(s, x, t, A)$ is a **probability measure** in $A$, for fixed  $s, x, t$;
>3. $p$ satisfies the **Chapman-Kolmogorov equation** $$p(s, x, t, A) = \int_{\mathcal{X}}p(u, y, t, A)p(s, x, u, dy)$$ for any $s < u < t.$
>   
>Then we call $p(s, x, t, A)$ a **Markov transition function** (a **transition probability function**, or a **transition probability**).   

- Friedman, A. (1975). *Stochastic differential equations and applications*. pp 18
- [[Chapman-Kolmogorov Equation]]

## Understanding

>[!info]
>The definition of **transition kernel** fits better for *discrete-time Markov chain*.
>
>The definition of **transition function** fits better for *continuous-time Markov process*.



>[!info] **Conditional Density Function**
The above definition of Transition Kernel can be used to define the **conditional density function** $K(x, y) = P(y | x)$:
> - Given a point $x \in \mathcal{X}$, $P(A|x)$ is a probability measure of set $A \in \mathcal{B}(\mathcal{X})$
> - Given a Borel set $A \in \mathcal{B}(\mathcal{X})$, $P(A | x)$ is a measurable function of $x$

- [[Conditional Probability]]


>[!info]
>There is no consensus on the ordering of these arguments. 
>
>For example, in [[Introduction to Stochastic Calculus by Klebaner]]
>$$
>p\left( \text{ next state }, \text{ next time },  \text{ current state },  \text{ current time }  \right)
>$$
>in  Friedman, A. (1975). Stochastic differential equations and applications. In _Stochastic differential equations_
>$$
>p\left( \text{ current time }, \text{ current state },  \text{ next time },  \text{ next state }  \right)
>$$


>[!info]
>The **transition function** $p$ and **transition kernel** $K$ are equivalent
>$$
>\begin{align*}
>p(s, x, t, A) := K(x,  A) = \mathcal{P}\left( X_{t} \in A | X_{s} = x \right)
>\end{align*}
>$$
>where $A\in \mathcal{B}(\mathcal{X}).$

- [[Markov Chain and Markov Process]]
- [[Stochastic Process]]

>[!info] 
>For discrete-state Markov chain $X_{t}$, the **transition kernel** of Markov Chain can be simplified as the *time-invariant conditional probability mass function*
> $$
> K(x, y) := p(x, t, y, t+1)  := \mathcal{P}(X_{t+1} = y | X_t = x).
> $$ 

>[!info] **$m$-Step Transition Probability**
> Then the **$m$-step transition probability** is defined as
> $$
> K^{m}(x, y) = \mathcal{P}(X_{t+m} = y | X_t = x)
> $$
> 

## Chapman-Kolmogorov Equation

- [[Chapman-Kolmogorov Equation]]

>[!info]
>In general, we can consider $K: L^1(\mu) \to L^1(\mu)$ as an **operator** on $L^1(\mu)$. 
>
>That is, we can define
>$$
>K\,h(x) := \int_{\mathcal{X}} h(y)\,K(x, dy)
>$$


## Stochastic Process from Transition Function

>[!important] Theorem
>Let $p$ be a **transition probability function**. 
>
>Then, for any $s \ge 0$, and for **any probability distribution** $\pi$ on $(\mathcal{X}, \mathscr{F})$, there exists a *stochastic process* $(X_{t}, s \le t < \infty)$ such that 
>- $$\mathcal{P}\left\{ X(s, \omega) \in A \right\} = \pi(A)$$
>- $$\mathcal{P}\left\{ X(t, \omega) \in A \,|\, \sigma\left(X_{u}, u \in [s, \bar{s}]  \right) \right\} = p(\bar{s}, X(\bar{s}), t, A), \quad \text{ a.s. } $$ for  $s \le \bar{s} <t.$

^b6b406

- Friedman, A. (1975). Stochastic differential equations and applications. In _Stochastic differential equations_ (pp. 75-148). Berlin, Heidelberg: Springer Berlin Heidelberg. pp 30

- [[Markov Chain and Markov Process]]

## Semigroup 

- [[Semigroup associated with Transition Function]]

## Integral Operator

- [[Integral Operator associated with Transition Kernel]]

## Functional Analysis

>[!important]
>If $\mu$ is a *positive measure*, by [[Riesz-Markov Representation Theorem]], we can represent
>$$
>\mu\,f := \int_{\mathcal{X}}f(x)d\mu(x).
>$$
>By the definition of transition kernel [[Markov Transition Kernel and Transition Function]],   
>- $\mu\,K$ is a **positive measure** on $\mathcal{B}(\mathcal{X})$ defined as $$\mu\,K (A) := \mu\,K(\cdot, A) = \int_{\mathcal{X}}K(x, A)\,d\mu(x), \quad \forall A\in \mathcal{B}(\mathcal{X}).$$
>- $K\,f$ is a **function** on $\mathcal{X}$ defined as $$K\,f(x) := \int_{\mathcal{X}}\,f(y)\,K(x, dy), \quad \forall x\in \mathcal{X}.$$

- [Lecture note](https://www.randomservices.org/random/expect/Kernels.html)
- [[Invariant Measure and Stationary Distribution]]

## Forward and Backward Equation of SDE


- [[Infinitesimal Generator of Stochastic Differential Equation]]
- [[Fokker–Planck and Kolmogorov Forward-Backward Equation]]
- [[Introduction to Stochastic Calculus by Klebaner]] pp 135



-----------
##  Recommended Notes and References

- [[Markov Chain and Markov Process]]

- [[Probability Space]]
- [[Measure Space and Countably Additive Measure]]
- [[Conditional Probability]]
- [[Conditional Expectation]]

- [[Monte Carlo Statistical Methods by Robert]]
- [[Introduction to Stochastic Calculus by Klebaner]]
- Wikipedia [Transition_kernel](https://en.wikipedia.org/wiki/Transition_kernel)