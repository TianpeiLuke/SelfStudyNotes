---
tags:
  - concept
  - machine_learning/theory
  - statistics/decision_theory
keywords:
  - empirical_risk_minimization
  - statistical_decision_theory
topics:
  - machine_learning_theory
  - statistics/decision_theory
name: Empirical Risk Minimization via Statistical Decision Theory
date of note: 2024-06-26
---

## Concept Definition

>[!important]
>**Name**: Empirical Risk Minimization via Statistical Decision Theory

![[Statistical Decision Problem#^1e4cc1]]

![[Statistical Decision Problem#^e4b559]]

![[Statistical Decision Problem#^36cede]]


>[!important] Definition
>Let $X$ be a sample taking values in $\mathcal{X}$ from *nonparametric model* $\mathcal{P} \in \mathscr{P}$. Suppose that there exists some *unknown* Borel measurable function $f\in \mathcal{F}$ such that $$Y = f(X) \in \mathcal{Y}, \quad \forall X\in \mathcal{X}.$$ Let $\mathcal{H}$ be a family of *Borel measurable functions* from $\mathcal{X}$ to $\mathcal{Y}$. 
>
>A **statistical learning problem** can be formulated as that of *deciding which function* $h \in \mathcal{H}$ based on sample $(X, Y)$ where $X$ is from $\mathcal{P}$.
>- Consider the **action space** $(\mathcal{H}, \mathcal{B}(\mathcal{H}))$ be the Borel measurable space of $\mathcal{H}$. The space $\mathcal{H}$ is called a **hypothesis class**.
>- $f\in \mathcal{F}$ is called a **concept** and $\mathcal{F}$ is called a **concept class.**
>-  A **classification  rule (learning rule)** is $$T: (\mathcal{X}, \mathscr{F}_{\mathcal{X}}) \to (\mathcal{H}, \mathcal{B}(\mathcal{H}))$$  Denote $h:=T(X)$.
>- Define the **loss function** $$L(f, h)$$
>- Define the **risk function** as $$R(f, T) := \mathbb{E}_{ \mathcal{P}}\left[ L(f, T(X)) \right] := L_{\mathcal{P}, f}(h)$$ The risk function is called the **generalization error** of $h.$
>

- [[Statistical Decision Problem]]
- [[PAC Learnable and Agnostic PAC Learnable]]

>[!important]
>A statistical learning problem is an **empirical risk minimization problem** when
>- Define the **loss function** is defined as $$L(f, h) := d_{H}(f, h; \mathcal{D}_{n}) = \frac{1}{n}\sum_{i=1}^{n}\mathbb{1}\{ h(x_{i}) \neq f(x_{i})\}$$
>- Define the **risk function** as $$R(f, T):= \mathbb{E}_{ \mathcal{P} }\left[  L(f, T(X)) \right]  = \mathcal{P}\left[ h(X) \neq f(X) \right] $$ where $h := T(X).$

>[!important] Definition
>A statistical learning problem is a **convex learning problem** if
>- The hypothesis class $\mathcal{H}$ is a **convex set**
>- For each $x\in \mathcal{X}$, the **loss function** $$L_{f}(x, \cdot): \mathcal{H} \to [0, \infty)$$ is a **convex function**
>- Define the **risk function** as $$R_{f}(\mathcal{P}, h):= \mathbb{E}_{ \mathcal{P} }\left[  L_{f}(X, h) \right]$$

- [[Convex Set]]
- [[Convex Function]]



## Explanation





-----------
##  Recommended Notes and References


- [[Statistical Decision Problem]]

- [[Empirical Risk Minimization]]
- [[PAC Learnable and Agnostic PAC Learnable]]



- [[Understanding Machine Learning by Shalev-Shwartz]]  pp 26 - 27
- [[Mathematical Statistics by Shao]] 