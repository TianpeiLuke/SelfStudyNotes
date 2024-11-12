---
tags:
  - concept
  - math/probability
  - math/measure_theory
keywords:
  - pushforward_measure
  - pushforward_operator
topics:
  - probability
name: pushforward measure; pushforward operator
date of note: 2024-05-07
---

## Concept Definition

>[!important]
>**Name**:  Push-forward Operator

>[!important] Definition
>Given two topological measurable spaces $(\mathcal{X}, \mathscr{F})$ and $(\mathcal{Y}, \mathscr{G})$, define the space of all *Radon measures* on $\mathscr{F}$ as $\mathcal{M}(\mathcal{X})$, and the space of all *Radon measures* on $\mathscr{G}$ as $\mathcal{M}(\mathcal{Y})$.
>
>For a *continuous map* $T : \mathcal{X} \rightarrow \mathcal{Y}$,  the **push-forward operator** is defined as $T_{*}: \mathcal{M}(\mathcal{X}) \rightarrow \mathcal{M}(\mathcal{Y})$ that  satisfies 
>$$
> \begin{align*}
> T_{*}\alpha &:= \alpha \circ T^{-1} \in \mathcal{M}(\mathcal{Y}), \quad \forall \alpha \in \mathcal{M}(\mathcal{X}) \\
> \left(T_{*}\alpha \right)(B)&:= \alpha\left(\set{ x: T(x) \in B \subset \mathcal{Y} }\right)  = \alpha(T^{-1}(B)), \quad B \in \mathscr{G}
> \end{align*}
>$$

- [[Radon Measure]]
- [[Preimage and Range of Function]]


>[!important]
>**Name**:  Push-forward Measure

>[!important] Definition
>The **push-forward measure** is defined as $$\beta := T_{*}\alpha \in \mathcal{M}(\mathcal{Y})$$ of some $\alpha \in \mathcal{M}(\mathcal{X})$,  $T^{-1}(\cdot)$ is the *pre-image* of $T$, and $\mathcal{M}(\mathcal{X})$ is the *set of Radon measures* on the space $\mathcal{X}$. 
>- $\beta$ is called the **pushforward** of $\alpha$ by $T$.
>- The pushforward measure is denoted as $$T_{*}\alpha, \quad T_{\#}\alpha.$$

- [[Preimage and Range of Function]]

## Explanation

>[!info]
>The *push-forward measure* is to "push" the *measure* on **domain space** "forward" to *the measure* on **co-domain space**, with the help of a *continuous function* $T$.


## Integration and Change of Variable Formula

>[!important] Proposition
>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a *measure space* and $(\mathcal{Y}, \mathscr{G})$ be a *measurable space*. Define $T: \mathcal{X} \to \mathcal{Y}$ as a  $\mathscr{F}/\mathscr{G}$ *measurable map*.
>
>If $f \circ T\in L^1(\mathcal{X}, \mathscr{F}, \mu)$, then $f \in L^1(\mathcal{Y}, \mathscr{G}, \, T_{*}\mu)$ where $T_{*}\mu$ is the **pushforward measure** of $\mu$ by $T$.
>
> In that case, 
>$$
>\int_{\mathcal{X}} (f\circ T)\, d\mu = \int_{\mathcal{Y}} f \,d(T_{*}\mu).
>$$
>
>The **pushforward measure** corresponds to the change of variable

- [[Absolutely Convergent Integration]]
- [[Jacobian Matrix and Jacobian Determinant]]




-----------
##  Recommended Notes and References

- [[Measure Space and Countably Additive Measure]]
- [[Measurable Function]]
- [[Probability Distribution of Random Variable]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)


- [[Distributional Reinforcement Learning by Bellemare]] pp 36, 65
- [[Optimal Transport Old and New by Villani]]
- [[Computational Optimal Transport by Peyre]]
- [[Optimal Transport for Applied Mathematicians by Santambrogio]]