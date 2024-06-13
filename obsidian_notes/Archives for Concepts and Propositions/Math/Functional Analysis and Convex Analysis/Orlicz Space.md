---
tags:
  - concept
  - math/functional_analysis
  - math/real_analysis
  - math/convex_analysis
keywords:
  - orlicz_space
topics:
  - functional_analysis
  - real_analysis
  - convex_analysis
name: Orlicz Space
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**:  Orlicz Space

>[!important] Definition
>A function : $\psi: [0, \infty) \to [0, \infty)$ is called an **Orlicz function** if $\psi$ is **convex**, **increasing**, and satisfies:
>$$
> \begin{align*}
> \psi(0) = 0, \quad \psi(x) \to \infty, \;\text{ as }x\to \infty.
> \end{align*}
>$$ 


>[!important] Definition
>Let $(X, \mathscr{F}, \mu)$ be a measure space. 
>
>For a given *Orlicz function* $\psi$,  **the Orlicz norm** of a measurable function $f: X\to \mathbb{R}$ is defined as
>$$
> \begin{align*}
> \lVert f \rVert_{\psi} := \inf\left\{t>0: \int_{X} \psi \left( \frac{\lvert f \rvert }{t}\right) d\mu  \le 1 \right\}.
> \end{align*}
>$$ 

- [[Minkowski Functional]]


>[!important] Definition
>**The Orlicz space** $L_{\psi} = L_{\psi}(X, \mathscr{F}, \mu)$ consists of all measurable functions $f$ on the measure space $(X, \mathscr{F}, \mu)$ with **finite Orlicz norm**, i.e.
>$$
> \begin{align*}
> L_{\psi} := \set{f \in \mathscr{F}/\mathcal{B}_{\mathbb{R}}: \lVert f \rVert_{\psi}  < \infty}.
> \end{align*}
>$$ 


- [[Measure Space and Countably Additive Measure]]
- [[Measurable Function]]



## Explanation

>[!important]
>*The Orlicz space* $L_{\psi} = L_{\psi}(\Omega, \mathscr{F}, \mu)$ is a **Banach space.**

- [[Banach Space]]





-----------
##  Recommended Notes and References

- [[Vector Space over a Field]]

- [[Minkowski Functional]]
- [[Norm Topology]]
- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)