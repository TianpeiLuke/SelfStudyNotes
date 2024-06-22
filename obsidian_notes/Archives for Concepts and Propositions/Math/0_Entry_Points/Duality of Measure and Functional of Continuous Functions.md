---
tags:
  - entry_point
  - concept
  - math/topology
  - math/functional_analysis
  - math/measure_theory
keywords: 
topics:
  - topology
  - functional_analysis
  - measure_theory
name: 
date of note: 2024-05-08
---

##  List of Concepts

### Measure Theory

- [[Borel sigma Field]]
- [[Borel Measure]]
- [[Gdelta set and Fsigma set]]
- [[Finite and sigma-Finite Measure]]
- [[Baire Measure]]
- [[Inner Regularity]]
- [[Outer Regularity]]
- [[Radon Measure]]
- [[Signed Measure]]
- [[Jordan Decomposition Theorem and total variation measure]]

### Topology

- [[Locally Compactness]]
- [[Locally Compact Hausdorff Space]]
- [[sigma-Compactness]]

### Functional Analysis

- [[Banach Space]]
- [[Dual Normed Space and Dual Banach Space]]
- [[Continuous Functions with Compact Support]]
- [[Continuous Functions that Vanish At Infinity]]
- [[Positive Linear Functional]]
- [[lp Sequence Space]]
- [[Convergent Sequence Space]]

### The Riesz-Markov Representation

- [[Riesz-Markov Representation Theorem]]

### $L^p$ space

- [[Lp Space]]
- [[Hölder Inequality]]
- [[Space of Bounded Signed Measures]]
- [[L-infinite Space]]
- [[Dual Normed Space of Lp Space]]
- [[Dual Normed Space of L-infinity Space]]

### Kantorovitch Representation Theorem

- [[Kantorovitch Representation Theorem for Dual of L-infinity]]


## Explanation

>[!important]
>For *locally compact Hausdorff space* $X$, the above theorem shows the **duality** between
>- the space of *continuous functions* *vanishing at infinity*  $\mathcal{C}_{0}(X)$ and 
>- the space of *bounded signed Radon measures* $\mathcal{M}(X)$.
>$$\mathcal{M}(X) \simeq (\mathcal{C}_{0}(X))^{*} $$


>[!important]
 >The Riesz-Markov Representation Theorem provides an **integral representation** of a *bounded linear functional* on $\mathcal{C}_{0}(X)$.
 >$$
 >I(\cdot) := \int_{X} \; \cdot \; d\mu_{I}
 >$$

>[!important]
>$$
>\begin{CD}
> \mathcal{M}(\mathcal{X}) @>\subset>> \mathcal{BA}(\mathcal{X})\\ 
>@VV*V  @VV* V\\ 
> \mathcal{C}_{0}(\mathcal{X}) @>\subset>> L^{\infty}(\mathcal{X}, \mu)
>\end{CD}
>$$ 

- [[Space of Bounded Signed Measures]]
- [[Continuous Functions that Vanish At Infinity]]
- [[L-infinite Space]]



-----------
##  Recommended Notes and References

- [[Topology Book by Munkres]]

- [[Real Analysis by Royden]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Functional Analysis by Reed]]