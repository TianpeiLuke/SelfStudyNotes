---
tags:
  - concept
  - math/probability
keywords:
  - conditional_probability
topics:
  - probability
name: conditional probability
date of note: 2024-05-07
---

## Concept Definition

>[!important]
>**Name**:  Conditional Probability


>[!important] Definition
>Let  $(\Omega, \mathscr{A}, \mathcal{P})$ be a probability space with a *sub-algebra* $\mathscr{F} \subset \mathscr{A}$ and $A \in \mathscr{A}$ is an event.
>
>There exists a *random variable* $\mathcal{P}\left[ A | \mathscr{F} \right]$,  called **the conditional probability** of $A$ *given sub-algebra* $\mathscr{F}$, having these two properties: 
>- $\mathcal{P}\left[ A | \mathscr{F} \right]$  is *$\mathscr{F}$-measurable*, and *integrable*, i.e.
>$$
>\mathcal{P}\left[ A | \mathscr{F} \right] \in L^1(\Omega, \mathcal{P}|_{\mathscr{F}})
>$$
>- $\mathcal{P}\left[ A | \mathscr{F} \right]$ satisfies the following **functional equation**
>$$
>\begin{align*}
> \mathcal{P}(A \cap G) = \int_{G} \mathcal{P}\left[ A | \mathscr{F} \right]\; d\mathcal{P}|_{\mathscr{F}}, \quad \forall G \in \mathscr{F}.
\end{align*}
>$$

>[!info]
>For any two random variables that satisfy the above two conditions, they are equal almost surely.


- See also [[Conditional Expectation]]

- [[Lebesgue-Radon-Nikodym Theorem]]
- [[Probability and Measure by Billingsley]]


## Explanation

>[!info]
>The conditional probability $\mathcal{P}[A | \mathscr{F}]$ can be defined using [[Markov Transition Kernel and Transition Function]]

>[!important] Definition (Kernel Version)
>Consider a *kernel function* $K: \Omega \times \mathscr{F} \to \mathbb{R}$ satisfying the two conditions below:
> 1. $\forall \omega \in \Omega$,    $K(\omega, \cdot)$  is a *probability measure* on $\mathscr{F}$;
> 2. $\forall A \in \mathscr{F}$,    $K(\cdot, A)$ is a *measurable* function.
>    
>Then **the conditional probability** $\mathcal{P}[A | \mathscr{F}]$ is defined as a $\mathscr{F}$-measurable function such that 
>$$
>\mathcal{P}[A | \mathscr{F}](\omega) := K(\omega, A), \quad \omega \in \Omega.
>$$ 


>[!info] Conditional Probability of Random Variables
>Given two random variables $X_{1}, X_{2}$, let $\mathscr{A} := \sigma(X_{1}, X_{2})$ be *the $\sigma$-algebra generated* by two random variables. Also denote $\mathscr{F} := \sigma(X_{1})$ be the $\sigma$-algebra generated by $X_{1}$ only. Then 
>$$
>\sigma(X_{1}) \subset \sigma(X_{1}, X_{2}).
>$$
>
>Thus, the *conditional probability* of $X_{2}$ given $X_{1}$ is defined as
> $$
> \begin{align*}
> \mathcal{P}[X_{2} \in I | X_{1}] &:= \mathcal{P}[X_{2} \in I \;|\; \sigma(X_{1})]\\
> &= \mathcal{P}[ \left\{\omega:  X_{2}(\omega) \in I \right\} \;|\; \sigma(X_{1})]
> \end{align*}
> $$
> 

- [[sigma Algebra Generated by Sets]]
- [[sigma Algebra Generated by Measurable Functions]]



-----------
##  Recommended Notes and References

- [[Probability Space]]
- [[Random Element and Random Variable]]
- [[Conditional Expectation]]
- [[Markov Transition Kernel and Transition Function]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/probability_and_measure_theory)