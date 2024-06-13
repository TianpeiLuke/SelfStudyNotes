---
tags:
  - concept
  - machine_learning/pac
keywords:
  - Probably_Approximately_Correct
topics:
  - machine_learning_theory
name: PAC Learnable
date of note: 2024-04-18
---

## Concept Definition

>[!important]
>**Name**: Probably Approximately Correct (PAC) Learning

>[!important] **Probably Approximately Correct (PAC) Learning, Realizable Case**
> - Assume that **the realizability assumption** holds. 
>   
>A *hypothesis class* $\mathcal H$  is said to be **Probably Approximately Correct**-*learnable* i.e. **PAC-learable**,  if there exists an *algorithm* $\mathcal A$ and a **polynomial function** $\text{poly}(\cdot, \cdot, \cdot, \cdot)$  such that 
> - for any $\epsilon > 0$ and $\delta > 0$, for **all distributions** $\mathcal{P}$ on $\mathcal{X}$ and for **any target concept** $c \in \mathcal{C}$,  the following holds when the **sample size** $n \ge \text{poly}(1/\epsilon, 1/\delta, d, \text{size}(c)):$
> $$
> \mathcal{P}\set{L_{\mathcal{P}, c}(\mathcal{A}(\mathcal{D}_n))  \le \epsilon} \ge  1 - \delta. 
> $$
> 
>If $\mathcal{A}$ further runs in $\text{poly}(1/\epsilon, 1/\delta, d, \text{size}(c))$, then $\mathcal{H}$ is said to be **efficiently PAC-learnable**. When such an algorithm $\mathcal{A}$ exists, it is called a *PAC-learning algorithm* *for* $\mathcal{H}$.

- $L_{\mathcal{P}, c}(\cdot): \mathcal{H} \mapsto \mathbb R$ is the **generalization error**. It depends on the underlying distribution $\mathcal P(X)$ and the **concept class** $c \in \mathcal{C}$


>[!important] **Realizability Assumption**
> There exists a hypothesis $h \in \mathcal{H}$ such that **the generalization error is zero**.
> $$
> \exists h\in \mathcal{H}, \quad  L_{\mathcal{P}, c}(h) = 0
> $$


- That is, every ERM hypothesis has zero training error. 
- In the definition of **Probably Approximately Correct (PAC) Learning**, we assume the realizability assumption holds.




## Explanation

- A *hypothesis class* $\mathcal H$ is *PAC Learnable* means that there exists an algorithm with **sample complexity** in polynomial with respect to the reciprocal of *accuracy* $1/\epsilon$, the reciprocal of *error rate* $1/\delta$, *dimension* $d$, and *size* of concept set



-----------
##  Recommended Notes and References

- [[Hoeffding Inequality]]
- [[Bounded Difference Inequality]]

- [[Empirical Risk Minimization]]

- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Boosting Foundations and Algorithms by Schapire]]

- Github Note [link](https://github.com/TianpeiLuke/SelfStudyNotes/tree/master/self-study/statistical_learning_theory)