---
tags:
  - concept
  - machine_learning/theory
keywords:
  - Probably_Approximately_Correct
  - weak_probabily_approximately_correct
  - weak_learnable
topics:
  - machine_learning_theory
name: Weak PAC Learnablity
date of note: 2024-07-29
---

## Concept Definition

>[!important]
>**Name**: Weak PAC Learnablity

![[Empirical Risk Minimization#^a84128]]

![[PAC Learnable and Agnostic PAC Learnable#^500325]]


>[!important] Definition
>A *hypothesis class* $\mathcal H$  is said to be **weakly PAC Learnable**, if there exists an *algorithm* $\mathcal A$ and a **polynomial function** $\text{poly}(\cdot, \cdot, \cdot)$  such that 
> - for **some** $$\epsilon = \frac{1}{2} - \gamma$$ with some small $\gamma >0$ and *any* $\delta > 0$, 
> - for *all distributions* $\mathcal{P}$ on $\mathcal{X}$ and 
> - for *any target concept* $l \in \mathcal{C}$,  
>
>the following holds when the **sample size** $n \ge n_{\mathcal{H}}(\gamma, \delta):$
> $$
> \mathcal{P}\left\{L_{\mathcal{P}, l}(\mathcal{A}(\mathcal{D}_n))  \le \frac{1}{2} - \gamma \right\} \ge  1 - \delta. 
> $$
> 
> - If $\mathcal{A}$ further runs in $$n_{\mathcal{H}} := \text{poly}(1/\gamma, 1/\delta, \text{size}(l)),$$ then $\mathcal{H}$ is said to be **efficiently weakly PAC-learnable**. 
>- When such an algorithm $\mathcal{A}$ exists, it is called a **weak PAC-learning algorithm** *for* $\mathcal{H}$.

^6b4c5c

- [[Empirical Weak Learning Assumption]]
- [[PAC Learnable and Agnostic PAC Learnable]]
- [[Realizability Assumption for Empirical Risk Minimization]]


## Explanation

>[!important] 
>Compare to **(strong) PAC learnable**, our goal is merely to find a hypothesis whose error is just **slightly below the trivial baseline** of $50\%$.


## Boosting

>[!important]
>AdaBoost algorithm implies that the concept of **weak learnability** is **equivalent to strong learnability.** 

- [[AdaBoost Algorithm]]

>[!quote]
>That strong and weak learnability are equivalent implies that learning, as we have defined it, is an “**all or nothing**” phenomenon in the sense that for every class $C$, either $C$ is **learnable** with **nearly perfect accuracy** for **every distribution**, or $C$ **cannot be learned** in even the **most minimal way** on every distribution. There is nothing in between these two extremes.
>
>-- [[Boosting Foundations and Algorithms by Schapire]] pp 47





-----------
##  Recommended Notes and References


- [[PAC Learnable and Agnostic PAC Learnable]]
- [[Empirical Risk Minimization]]
- [[Rademacher Complexity]]
- [[VC Dimension]]

- [[Cramér–Chernoff Method]]


- [[Boosting Foundations and Algorithms by Schapire]]  pp 46