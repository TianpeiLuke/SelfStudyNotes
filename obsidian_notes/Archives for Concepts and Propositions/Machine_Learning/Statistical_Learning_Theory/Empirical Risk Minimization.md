---
tags:
  - concept
  - machine_learning/theory
  - math/stochastic_process
keywords:
  - empirical_process
  - empirical_risk_minimization
topics:
  - machine_learning_theory
name: Empirical Risk Minimization
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Empirical Risk Minimization

### Non-Agnostic Setting

>[!important] Definition (Non-Agnostic Setting)
>Let $(\mathcal{X}, \mathscr{F}, \mathcal{P})$ be a *probability space* and $(\mathcal{X}^T, \mathscr{F}^T, \mathcal{P}^T)$ be an *infinite dimensional* product space with index set $T$.  
>
>Let $\mathcal{P}_{n}$ be an *empirical measure* of $X_{1} \,{,}\ldots{,}\,X_{n}$, for some $n$, i.e.
>$$\mathcal{P}_{n} = \frac{1}{n}\sum_{i=1}^{n}\delta_{X_{i}}$$
>where $X_{i}\in \mathcal{X}$ be *independent identically distributed* random variables on $\mathcal{X}$. 
>
>Suppose $\mathcal{H} \subset \mathcal{Y}^{\mathcal{X}}$ is a class of *measurable functions* $h: \mathcal{X} \to  \mathcal{Y}$ on domain $\mathcal{X}$. Also there exists a *fixed* unknown measurable function $l \in \mathcal{Y}^{\mathcal{X}}$. Let  $\mathcal{F}_{\mathcal{H}}$ be  the class of *boolean  functions* $f_{h, l}: \mathcal{X} \to \{ 0, 1 \}$ induced by $h \in \mathcal{H}$ such that 
>$$
>f_{h,l}(x) := \mathbb{1}\{ h(x) \neq l(x) \}.
>$$
>
>The **empirical risk** or **empirical error** of a *function* $h\in \mathcal{H}$ is defined by
>$$
>\begin{align*}
> L_{\mathcal{D}}(h) := \mathcal{P}_{n}f_{h,l} =  \frac{1}{n}\sum_{i=1}^{n}\mathbb{1}\{ h(X_{i}) \neq l(X_{i})\}.
>\end{align*}
>$$
>where $\mathcal{D} := \{ X_{1} \,{,}\ldots{,}\,X_{n}\}$.
>
>Moreover, 
>- $\mathcal{H}$ is called a **hypothesis class**, where $h \in \mathcal{H}$ is a **hypothesis** (or a **predictor**, or a **classifier**, or a **learner**, or a **prediction rule**).
>- $l: \mathcal{X} \to \mathcal{Y}$ is called a **labeling function**, (or a **target concept**). The set $\mathcal{C} \ni l$ is called **the concept class**.
>- $\mathcal{D} := \{ X_{1} \,{,}\ldots{,}\,X_{n}\}$  is called the **training sample**, where $n$ is called the **sample size**.
>- $\mathcal{X}$ is called the **sample domain** or **feature domain**.
>- $\mathcal{Y}$ is called the **label domain**.
>- The empirical error $L_{\mathcal{D}}(h)$ is also called the **training error** of predictor $h$.

^a84128

- [[Empirical Process and Empirical Measure]]
- [[Understanding Machine Learning by Shalev-Shwartz]] pp 14 - 15



>[!important] Definition
>The empirical risk defines an **empirical process** *indexed by function class* $\mathcal{H}$:
>$$
> h \mapsto L_{\mathcal{D}}(h) := \mathcal{P}_{n}f_{h,l}.
>$$
>
>The *expectation* of empirical error (with respect to the product probability) is called the **generalization error** or **true error** of $h$, i.e.
>$$
>\begin{align*}
> L_{\mathcal{P}, l}(h) := \mathcal{P}f_{h,l} = \mathbb{E}_{ \mathcal{P} }\left[  L_{\mathcal{D}}(h) \right]  = \mathcal{P}\left[ h(X) \neq l(X) \right] .
>\end{align*}
>$$

^c9ebc0

### Agnostic Setting

>[!important] Definition (Agnostic Setting)
>Let $((\mathcal{X}, \mathcal{Y}), \mathscr{F}, \mathcal{P})$ be a *probability space* and $((\mathcal{X}, \mathcal{Y})^T, \mathscr{F}^T, \mathcal{P}^T)$ be an *infinite dimensional* product space with index set $T$.  
>
>Let $\mathcal{P}_{n}$ be an *empirical measure* of $(X_{1}, Y_{1}) \,{,}\ldots{,}\,(X_{n}, Y_{n})$, for some $n$, i.e.
>$$\mathcal{P}_{n} = \frac{1}{n}\sum_{i=1}^{n}\delta_{(X_{i}, Y_{i})}$$
>where $(X_{i}, Y_{i})\in \mathcal{X} \times \mathcal{Y}$ be *independent identically distributed* random variables on $\mathcal{X}\times \mathcal{Y}$. 
>
>Suppose $\mathcal{H} \subset \mathcal{Y}^{\mathcal{X}}$ is a class of *measurable functions* $h: \mathcal{X} \to  \mathcal{Y}$ on domain $\mathcal{X}$.  Let  $\mathcal{F}_{\mathcal{H}}$ be  the class of *boolean  functions* $f_{h}: \mathcal{X} \times \mathcal{Y} \to \{ 0, 1 \}$ induced by $h \in \mathcal{H}$ such that 
>$$
>f_{h}(x, y) := \mathbb{1}\{ h(x) \neq y \}.
>$$
>
>The **empirical risk** or **empirical error** of a *function* $h\in \mathcal{H}$ is defined by
>$$
>\begin{align*}
> L_{\mathcal{D}}(h) := \mathcal{P}_{n}f_{h} =  \frac{1}{n}\sum_{i=1}^{n}\mathbb{1}\{ h(X_{i}) \neq Y_{i} \}.
>\end{align*}
>$$
>where $\mathcal{D} := \{ (X_{1}, Y_{1}) \,{,}\ldots{,}\,(X_{n}, Y_{n}) \}$.
>

^0c98ce



>[!important] Definition
>The empirical risk defines an **empirical process** *indexed by function class* $\mathcal{H}$:
>$$
> h \mapsto L_{\mathcal{D}}(h) := \mathcal{P}_{n}f_{h}.
>$$
>
>The *expectation* of empirical error (with respect to the product probability) is called the **generalization error** or **true error** of $h$, i.e.
>$$
>\begin{align*}
> L_{\mathcal{P}}(h) := \mathcal{P}f_{h} = \mathbb{E}_{ \mathcal{P} }\left[  L_{\mathcal{D}}(h) \right]  = \mathcal{P}\left[ h(X) \neq Y \right] .
>\end{align*}
>$$

^cf1946

### Empirical Risk Minimization

>[!important] Definition
>The task of **empirical risk minimization (ERM)** is to find $h^{*}\in \mathcal{H}$ such that the *empirical error* is *minimized*, i.e.
>$$
>\begin{align*}
> h^{*} \in \arg \min_{h \in \mathcal{H}}L_{\mathcal{D}}(h).
>\end{align*}
>$$
>We denote $h \in \text{ERM}_{\mathcal{H}}(\mathcal{D}).$


## Explanation


>[!info]
>Note that 
>$$
>\mathcal{H} \to \mathcal{F}_{\mathcal{H}}:  h \mapsto f_{h}:= \mathbb{1}\{ h(\cdot) \neq \cdot \} 
>$$
>is *surjective* but *not injective*.

>[!info]
>We sometimes use $$\widehat{L}_{n}(h) := \frac{1}{n}\sum_{i=1}^{n}\mathbb{1}\{ h(X_{i}) \neq Y_{i} \}$$ for training error when we want to emphasize the dependency on the sample size $n$

>[!important]
>- Under **agnostic** setting,  the **label** is generated by an *unknown* **deterministic function** $l$ which may or may not inside the hypothesis class $\mathcal{H}$. 
>	- In this setting, there exists some "**deterministic ground truth**" function $l$
>- Under **non-agnostic** setting, both the **features** *and* the **label** is generated by a *unknown* **joint distribution** $\mathcal{P}(X, Y)$. 
>	- In this setting, there does not exists *deterministic* ground truth. The label is *randomly* generated by a *conditional probability measure* $\mathcal{P}[Y | X].$


>[!info]
> The **generalization error** $L_{\mathcal{P}, l}(\cdot): \mathcal{H} \mapsto \mathbb R$ depends on the underlying distribution $\mathcal{P}$ and the **concept class** $l \in \mathcal{C}$

## Goal of ERM and PAC Learnability

>[!important]
>Although the **task** of ERM is to **minimize the empirical error**, the **ultimate goal** is to show that $h^{*}\in \text{ERM}_{\mathcal{H}}(\mathcal{D})$ also lead to the *minimization* of **generation error**
>$$
>\begin{align*}
> h^{*} \in \arg \min_{h \in \mathcal{H}}L_{\mathcal{D}}(h) \implies h^{*} \in \arg \min_{h \in \mathcal{H}}L_{\mathcal{P}}(h)
>\end{align*}
>$$
>
>In particular, we are interested in the **uniform bound** *the generalization error* with *empirical error*
>$$
>L_{\mathcal{P},l}(h) \le L_{\mathcal{D}}(h) + \epsilon
>$$
>over all $h \in \mathcal{H}$.
>
>This depends on the **structure of hypothesis class $\mathcal{H}$**. In particular, we are interested in **concentration inequality**
>$$
>\mathcal{P}\left( \sup_{h \in \mathcal{H}} \;\lvert L_{\mathcal{D}}(h)  -  L_{\mathcal{P},l}(h) \rvert \ge \epsilon \right) \le \delta
>$$
>for some $n = |\mathcal{D}| \ge \text{poly}(1/\epsilon, 1/\delta).$

- [[PAC Learnable and Agnostic PAC Learnable]]

>[!info]
>We want to show that $$\mathcal{F}_{\mathcal{H}} = \{\mathbb{1}\{ h(x) \neq l(x) \}, \;\; h\in \mathcal{H}  \}$$ is a **Glivenko-Cantelli class** for $\mathcal{P}$. 

- [[Glivenko-Cantelli Class]]
- [[Concepts and Inequalities for Empirical Process]]


## Realizability Assumption

- [[Realizability Assumption for Empirical Risk Minimization]]





-----------
##  Recommended Notes and References

- [[PAC Learnable and Agnostic PAC Learnable]]
- [[Bounded Difference Inequality]]

- [[Empirical Process and Empirical Measure]]


- [[Foundations of Machine Learning by Mohri]]
- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Boosting Foundations and Algorithms by Schapire]] pp 43 - 45
- [[Probabilistic Graphical Models by Koller]]

