---
tags:
  - concept
  - math/real_analysis
  - math/measure_theory
  - math/probability
  - math/topology
keywords:
  - product_measure
topics:
  - measure_theory
  - real_analysis
  - probability
  - topology
name: Product Measure
date of note: 2024-05-25
---

## Concept Definition

>[!important]
>**Name**: Product Measure

>[!important] Proposition (Existence and Uniqueness of Product Measure)
>Let $(X, \mathscr{B}_X, \mu_X)$ and $(Y, \mathscr{B}_Y, \mu_Y)$ be **$\sigma$-finite measure spaces**. 
>
>Then there exists a **unique measure** $$\mu_X \times \mu_Y: \mathscr{B}_X \times \mathscr{B}_Y \to [0, \infty]$$ on **product $\sigma$-algebra** $\mathscr{B}_X \times \mathscr{B}_Y$ that obeys 
>$$
> \begin{align*}
> \mu_X \times \mu_Y(E \times F) &= \mu_X(E)\,\mu_Y(F)
> \end{align*}
>$$  
>whenever $E \in  \mathscr{B}_X$ and $F \in \mathscr{B}_Y$.


- [[Product sigma-Algebra]]
- [[Finite and sigma-Finite Measure]]
- [[Tensor Product]]

## Explanation


>[!info]
>When $X, Y$ are **not both $\sigma$-finite**, then one can *still construct* **at least one product measure**, but it will, in general, **not be unique**. 

>[!important]
>Due to [[Riesz-Markov Representation Theorem]], we can find **one-to-one correspondence** between a *$\sigma$-finite measure* and a *linear functional*, given additional topological assumption on the domain, such as compactness.
>
>Assume $X, Y$ are both compact Hausdorff and $\mu_{X}$ and $\mu_{Y}$ are *both $\sigma$-finite Borel measures* (thus both *regular* Radon measure).
>
>Then we have
>$$
>\mu_{X} \mapsto I_{X} := \int_{X}\, \cdot\, d\mu_{X} ; \quad \mu_{Y} \mapsto I_{Y}:= \int_{Y}\,\cdot \, d\mu_{Y}.
>$$
>
>Therefore, there exists a one-to-one correspondence between **the product measure** and **the tensor product** between **two linear functionals** *(covectors)*
>$$
>\mu_{X} \times \mu_{Y} \mapsto I_{X} \otimes I_{Y} := \left(\int_{X}\, \cdot\, d\mu_{X}\right)\left(\int_{Y}\,\cdot \, d\mu_{Y}\right)
>$$

- [[Covector on Vector Space]]
- [[Tensor Product]]
- [[Radon Measure]]


## Properties


>[!important] Proposition
>Let  $(X, \mathscr{B}_X)$ and $(Y, \mathscr{B}_Y)$ be *measurable spaces.*
>
> 
>- The **product** of two **Dirac measures** on $(X, \mathscr{B}_X)$,  $(Y, \mathscr{B}_Y)$ is a **Dirac measure** on $(X \times Y, \mathscr{B}_X \times \mathscr{B}_Y)$.
> 
>- If $X, Y$ are **at most countable**, the **product** of the two **counting measures** on $(X, \mathscr{B}_X)$,  $(Y, \mathscr{B}_Y)$ is the **counting measure** on $(X \times Y, \mathscr{B}_X \times \mathscr{B}_Y)$..
>



>[!important] Proposition (Associativity of Product)
>Let $(X, \mathscr{B}_X, \mu_X)$, $(Y, \mathscr{B}_Y, \mu_Y)$, $(Z, \mathscr{B}_Z, \mu_Z)$ be **$\sigma$-finite sets**. 
>
>We may identify the **Cartesian products** $(X \times Y) \times Z$ and $X \times (Y \times Z)$ with each other in the obvious manner. 
>
>If we do so, then 
>$$ 
> \begin{align*}
>  (\mathscr{B}_X \times \mathscr{B}_Y) \times \mathscr{B}_Z = \mathscr{B}_X \times (\mathscr{B}_Y \times \mathscr{B}_Z) 
> \end{align*}
>$$ 
> and
>$$ 
> \begin{align*}
> (\mu_X \times \mu_Y ) \times \mu_Z = \mu_X \times (\mu_Y \times \mu_Z).
> \end{align*}
>$$ 



-----------
##  Recommended Notes and References

- [[Covector on Vector Space]]
- [[Tensor Product]]

- [[Product sigma-Algebra]]
- [[Finite and sigma-Finite Measure]]

- [[sigma Algebra]]
- [[Measure Space and Countably Additive Measure]]
- [[Arbitrary Cartestian Products]]
- [[Canonical Projection]]



- [[Introduction to Measure Theory by Tao]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Probability and Measure by Billingsley]]
- [[A Probability Path by Resnick]]
