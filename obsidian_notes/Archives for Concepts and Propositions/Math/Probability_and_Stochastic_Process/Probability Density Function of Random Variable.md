---
tags:
  - concept
  - math/probability
  - math/measure_theory
keywords:
  - pdf_random_variable
  - probability_density
topics:
  - probability
  - measure_theory
name: Probability Density Function of Random Variable
date of note: 2024-06-28
---

## Concept Definition

>[!important]
>**Name**: Probability Density Function (*p.d.f.*) of Random Variable

>[!important] Definition
>Let $(\Omega, \mathscr{F}, \mathcal{P})$ be a *probability space* and $X: \Omega \to \mathcal{X}$ be a *random variable* taking values in $\mathcal{X}$.  Let $\nu$  be a  *$\sigma$-finite measure* on *measurable space* $(\mathcal{X}, \mathscr{B})$
>
>The **probability density function (p.d.f.)**  of $X$ with respect to $\nu$ on $\mathcal{X}$ is defined by the *Radon-Nikodym derivative*
>$$
>p_{\mathcal{X}}(x) := \frac{d\mathcal{P}_{\mathcal{X}}(x)}{d\nu(x)}
>$$
>where 
>$$
>\mathcal{P}_{\mathcal{X}} = X_{*}\,\mathcal{P} := \mathcal{P} \circ X^{-1}
>$$
>is the **distribution** of $X$.


- [[Probability Distribution of Random Variable]]
- [[Random Element and Random Variable]]
- [[Radon-Nikodym Derivative]]
- [[Push-forward Measure and Push-forward Operator]]
- [[Probability Space]]



## Explanation





-----------
##  Recommended Notes and References


- [[Probability Distribution of Random Variable]]
- [[Lebesgue Density from Radon-Nikodym Derivative]]
- [[Radon-Nikodym Derivative]]
- [[Finite and sigma-Finite Measure]]
- [[Probability Space]]

- [[Measure Space and Countably Additive Measure]]
- [[Lebesgue-Stieltjes Measure]]



- [[A Probability Path by Resnick]]
- [[Probability and Measure by Billingsley]]