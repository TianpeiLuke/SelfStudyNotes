---
tags:
  - concept
  - math/functional_analysis
  - math/probability
  - math/stochastic_process
keywords: 
topics:
  - functional_analysis
  - stochastic_process
name: Ergodic Transformation
date of note: 2024-06-05
---

## Concept Definition

>[!important]
>**Name**: Ergodic Transformation

![[Measure Preserving Transformation#^87b4a3]]


>[!important] Definition
>Let $\mathcal{X}$ be a vector space, and $(\mathcal{X}, \mathscr{F}, \mu)$ be a *measure space*. 
>
>A *measurable transformation*  $T: \mathcal{X} \to \mathcal{X}$ is called **$\mu$-ergodic** if 
>- **$T$ preserves $\mu$**: i.e. for any $A \in \mathscr{F},$ $$\mu\left(T^{-1}A \right) = \mu(A)$$ 
>- **Metric Transitivity**: There exists **no $T$-invariant subset** *up to null set*. That is, for any $A \in \mathscr{F}$, $$T^{-1}(A) = A \implies \mu(A) = 1 \text{ or }\mu(A) = 0.$$
>
>The corresponding measure $\mu$ is called **ergodic measure**.

^41fb4e

- [[Measure Preserving Transformation]]

>[!important] Definitiion
>A *measure preserving transformation* $T$ is said to be **ergodic** provided any set $A$ that is *invariant* under $T$ *with respect to* $\mu$, has $\mu(A) = 0$ or $\mu(A) = 1$.

- [[Real Analysis by Royden]] pp 489


## Explanation

>[!info]
>The concept of **measure preserving** provides a **sufficient condition** for $T^{-1}(A) = A$, i.e.
>$$
>T \text{ preserves }\mu \implies  T^{-1}(A) = A\, \text{ except for a $\mu$-null set}
>$$
>And **ergodicity** provides **necessary condition**
>$$
> T^{-1}(A) = A\, \implies \mu(A) = 1 \;\text{ or }\;\mu(A) = 0.
>$$
>



## Properties

>[!important] Proposition
>Let $(\Omega, \mathscr{F}, \mathcal{P})$ be a **probability space**, and $T: \mathcal{X} \to \mathcal{X}$ be a **measure preserving transformation**.
>
>Then the following two statements are **equivalent**:
>- $T$ is **ergodic**.
>- For all measurable functions $g: \mathcal{X}\to \mathbb{R}$,   if $$g\circ T = g \quad \text{ a.e.}$$ then $g$ is **constant** *almost everywhere* on $\mathcal{X}.$


- [[Real Analysis by Royden]] pp 489
- [[Probability Space]]
- [[Measurable Function]]
- [[Measure Preserving Transformation]]

## Existence 

![[Measure Preserving Transformation#^cf4b89]]

- [[Measure Preserving Transformation]]

>[!important] Proposition
>Let $f: \mathcal{X} \to \mathcal{X}$ be a **continuous**  mapping on a **compact metric space** $\mathcal{X}$.
>
>Define $\mathcal{M}_{f}$ to be the set of all *probability measures* on *Borel $\sigma$-algebra*  $\mathcal{B}(\mathcal{X})$ with respect to which $f$ is **measure preserving**.
>
>Then a **probability measure** $\mathcal{P}$ in $\mathcal{M}_{f}$ is an **extreme point** of $\mathcal{M}_{f}$ *if and only if* $f$ is **ergodic** with respect to $\mu$.

- [[Real Analysis by Royden]] pp 491
- [[Space of Bounded Signed Measures]]
- [[Extreme Points of Convex Set of Locally Convex Space]]


>[!important] Theorem
>Let $f: \mathcal{X} \to \mathcal{X}$ be a **continuous**  mapping on a **compact metric space** $\mathcal{X}$.
>
>Then there exists a **probability measure** $\mathcal{P}$ on the *Borel $\sigma$-algebra* $\mathcal{B}(\mathcal{X})$ with respect to which $f$ is **ergodic**.

- [[Real Analysis by Royden]] pp 492
- [[Compactness]]
- [[Metric Space]]
- [[Bounded Linear Operator and Norm of Operator]]
- [[Probability Space]]
- [[Borel sigma Field]]

## Ergodic Theorem

- [[Ergodic Theorem]]
- [[Ergodic Theorem for Positive Recurrent Markov Process]]






-----------
##  Recommended Notes and References

- [[Measure Preserving Transformation]]



- [[Invariant Set with respect to Subspace]]
- [[Invariant Measure and Stationary Distribution]]

- [[Ergodic Markov Chain and Asymptotic of Transition Kernel]]



- [[Functional Analysis by Reed]] pp 59
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Real Analysis by Royden]] pp 489
- Halmos, P. R. (1956). *Lectures on Ergodic Theory (First Edition).* Chelsea Pub Co.
- [[Monte Carlo Statistical Methods by Robert]]
- [[Probability and Measure by Billingsley]]

