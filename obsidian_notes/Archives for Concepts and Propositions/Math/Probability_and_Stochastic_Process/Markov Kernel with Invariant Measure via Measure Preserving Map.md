---
tags:
  - concept
  - math/stochastic_process
  - math/functional_analysis
  - statistics/monte_carlo_simulation
keywords:
  - measure_preserving_transformation
  - Transition_Kernel
topics:
  - stochastic_process
  - functional_analysis
  - monte_carlo
name: Markov Kernel via Measure Preserving Map
date of note: 2024-07-08
---

## Concept Definition

>[!important]
>**Name**: Markov Kernel via Measure Preserving Map

![[Markov Transition Kernel and Transition Function#^3d05e1]]


>[!important] Goal
>Let $(\mathcal{X}, \mathcal{B}(\mathcal{X}), \pi)$ be a *probability space*, where $\mathcal{B}(\mathcal{X})$ be Borel $\sigma$-algebra, and $\pi$ be a probability measure.  
>
>The **goal** is to **construct** a *Markov transition kernel* $K: \mathcal{X} \times \mathcal{B}(\mathcal{X}) \to \mathbb{R}_{+}$ so that $\pi$ is an **invariant measure** under $K$
>$$
>\pi(A) = \int K(x, A)\pi(dx), \quad \forall A\in \mathcal{B}(\mathcal{X}).
>$$
>or in *functional representation*
>$$
>\pi\, \mathcal{K} = \pi
>$$
>where $\mathcal{K}: \mathcal{P}(\mathcal{X}) \to \mathcal{P}(\mathcal{X})$ is defined as
$$\pi\,\mathcal{K} (A) := \pi\,\mathcal{K}(\cdot, A) = \int_{\mathcal{X}}K(x, A)\,d\pi(x), \quad \forall A\in \mathcal{B}(\mathcal{X}).$$

- [[Invariant Measure and Stationary Distribution]]
- [[Probability Space]]
- [[Borel sigma Field]]

>[!important] Definition
>Let $\Gamma$ be a space of *continuous, bijective* maps from $\mathcal{X}$ to itself,
>$$
>T: \mathcal{X} \to \mathcal{X}, \quad \forall T \in \Gamma
>$$
>that each $T \in \Gamma$ **preserves the target measure** $\pi \in \mathcal{P}(\mathcal{X})$
>$$
>T_{*}\,\pi = \pi
>$$
>where $T_{*}\pi = \pi \circ T^{-1}$ is the *push-forward measure*.
>
>Define a *probability space* on $\Gamma$, $(\Gamma, \mathscr{F}, \nu)$, where $\mathscr{F}$ is a $\sigma$-algebra over $\Gamma$, and $\nu$ is a probability measure over $\mathscr{F}$. 
>
>A **Markov kernel** can be induced by an iterated random function
>$$
>K(x, A) := \int_{\Gamma}\, \mathbb{1}_{A}(T(x))\; \nu \left(dT\right).
>$$
>In other word, the kernel assigns a probability to a set $A \in \mathcal{B}(\mathcal{X})$, by computing the *measure of the preimage* $T^{-1}(A)$, averaged over all *isomorphisms* in $\Gamma$.
>
>We see that by *Fubini's Theorem*,
>$$
>\begin{align*}
> \int_{\mathcal{X}}K(x, A)\pi(dx) &= \int_{\mathcal{X}}\int_{\Gamma}\, \mathbb{1}_{A}(T(x))\, \nu \left(dT\right)\,\pi(dx)\\
> &= \int_{\Gamma}\,\int_{\mathcal{X}}\mathbb{1}(T(x) \in A))\,\pi(dx)\, \nu \left(dT\right)\\
> &= \int_{\Gamma}\,\int_{\mathcal{X}}\mathbb{1}(x \in T^{-1}(A))\,\pi(dx)\, \nu \left(dT\right)\\
> &= \int_{\Gamma}\,T_{*}\pi(A)\, \nu \left(dT\right)\\
> &= \int_{\Gamma}\,\pi(A)\,\nu \left(dT\right)\\
> &= \pi(A)
>\end{align*}
>$$
>where the second last equality is due to the *measure-preserving property* of $T$. 
>
>This shows that the measure $\pi$ is the  **invariant measure** for the constructed Markov kernel $K$.
 

- [[Bijective Function and Inverse Function]]
- [[Isomorphism between Groups]]
- [[Measure Preserving Transformation]]
- [[Push-forward Measure and Push-forward Operator]]
- [[Characteristic Function of Set]]
- [[Preimage and Range of Function]]
- [[Fubini Theorem]]
- [[Invariant Measure and Stationary Distribution]]
- Betancourt, M., Byrne, S., Livingstone, S., & Girolami, M. (2017). The geometric foundations of Hamiltonian Monte Carlo. _Bernoulli_, _23_(4A), 2257–2298.  pp 4

## Explanation

>[!info]
>The function $K$ defined above fits the definition of Markov transition kernel
>- For fixed $x\in \mathcal{X}$, $$K(x, \cdot) = \int_{\Gamma} \mathbb{1}\left\{  x \in T^{-1}(\cdot) \right\}  d\nu(T)$$ is a probability measure on $\mathcal{B}(\mathcal{X})$
>  
>This is true.
>- $$K(x, A) = \int_{\Gamma} \mathbb{1}\left\{  x \in T^{-1}(A) \right\}  d\nu(T) \ge 0$$
>- For the whole set $\mathcal{X}$
>$$
>\begin{align*}
>K(x, \mathcal{X}) = \int_{\Gamma} \mathbb{1}\left\{  x \in T^{-1}(\mathcal{X}) \right\}  d\nu(T) = \int_{\Gamma} d\nu(T) = 1
>\end{align*}
>$$
>- For disjoint $A_{i} \in \mathcal{B}(\mathcal{X}), i=1\,{,}\ldots\,$
>
>$$\begin{align*}
>  K\left( x\,, \,\bigcup_{i=1}^{\infty}A_{i} \right) &= \int_{\Gamma} \mathbb{1}\left\{  x \in T^{-1}\left( \bigcup_{i=1}^{\infty}A_{i} \right) \right\}  d\nu(T)\\
>  &=\int_{\Gamma} \sum_{i=1}^{\infty} \mathbb{1}\left\{  x \in T^{-1}\left( A_{i} \right) \right\}  d\nu(T)\\
>  &= \sum_{i=1}^{\infty}\int_{\Gamma}\mathbb{1}\left\{  x \in T^{-1}\left( A_{i} \right) \right\}  d\nu(T) \\
>  &= \sum_{i=1}^{\infty}K(x, A_{i})
\end{align*}
$$

- [[Markov Transition Kernel and Transition Function]]
- [[Probability Space]]

>[!important]
>The definition of the Markov kernel
>$$
>K(x, A) := \int_{\Gamma}\, \mathbb{1}_{A}(T(x))\; \nu \left(dT\right).
>$$
>identifies a **rejection sampling process**. That is, we will reject samples from a region $A$ that does not contain $T(x)$ from any $T \in \Gamma$.
>
>To see this, for given set of states $A$, $$x \not\in T^{-1}(A), \;\forall T \in \Gamma \implies K(x, A) = 0.$$  
>
>In other word, if the next state region $A$ **cannot be reached** *from* $x$ by a *measure preserving bijection* $T \in \Gamma$, then the corresponding *Markov chain* will **not visit that region** from $x$ as well.

- [[Accept-Reject Sampling]]

>[!info]
>The function 
>$$
>\widehat{K}(x, A) := \mathbb{1}_{A}(T(x))
>$$
>is also a kernel. The corresponding *"Markov chain"* is defined by a **deterministic process** $T$. 
>
>Thus the *randomness* of Markov chain with 
>$$
>K(x, A) := \int_{\Gamma}\, \mathbb{1}_{A}(T(x))\; \nu \left(dT\right).
>$$
>comes from the **randomness** of the **measure preserving map.**



>[!info] 
>Given an **$T$-invariant measure** $\pi$,  this construction allows us to define a **positive stationary chain** that takes $\pi$ has its **invariant (stationary) measure** as well.

- [[Positive Recurrent Markov Chain]]




-----------
##  Recommended Notes and References


- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]






- Betancourt, M., Byrne, S., Livingstone, S., & Girolami, M. (2017). The geometric foundations of Hamiltonian Monte Carlo. _Bernoulli_, _23_(4A), 2257–2298. [https://doi.org/10.3150/16-BEJ810](https://doi.org/10.3150/16-BEJ810)