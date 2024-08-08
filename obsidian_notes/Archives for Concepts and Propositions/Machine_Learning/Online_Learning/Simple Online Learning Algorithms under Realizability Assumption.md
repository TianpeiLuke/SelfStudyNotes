---
tags:
  - concept
  - online_learning/theory
  - online_learning/algorithms
  - machine_learning/theory
keywords: 
topics: 
name: Simple Online Learning Algorithms under Realizability Assumption
date of note: 2024-08-07
---

## Concept Definition

>[!important]
>**Name**: Simple Online Learning Algorithms under Realizability Assumption

![[Online Learnability and Realizabililty Assumption#^c10d11]]

![[Online Learnability and Realizabililty Assumption#^5e75f3]]

![[Online Learnability and Realizabililty Assumption#^f05186]]


### Consistent Algorithm

>[!important] Definition
>Assume that the *hypothesis class* $\mathcal{H}$ is **finite**, i.e. $|\mathcal{H}| < \infty.$ We also assume **realizability** i.e all labels $y_{t}$ is generated from some hypothesis $h^{*}\in \mathcal{H}$. 
>
>A natural learning rule for *online learning* is to use any *Empirical Risk Minimization (ERM)* hypothesis that is *consistent* with *all past examples.*
>
>The **Consistent Algorithm** is described as follows:
>- *Require*: A finite hypothesis class $\mathcal{H}$
>- *Initialize*: $\mathcal{V}_{1} = \mathcal{H}$
>- For $t=1 \,{,}\ldots{,}\,$:
>	- the learner receives sample $x_{t}\in \mathcal{X}$
>	- *Choose* a hypothesis $h \in \mathcal{V}_{t}$
>	- the hypothesis **predict** $$p_{t} = h(x_{t})$$
>	- the learner receives **true label** $y_{t} = h^{*}(x_{t})$
>	- *Update* the **Version Space** $$V_{t+1} = \left\{ h\in V_{t}: h(x_{t}) = y_{t} \right\}$$

- [[Empirical Risk Minimization]]

>[!important] Definition
>The **Consistent algorithm** maintains a set, $V_{t}$, of all the hypotheses which are **consistent** with all past examples collected until time $(t-1)$, i.e. $$V_{t} = \left\{ h\in \mathcal{H}: h(x_{s}) = y_{s},\, \forall s \le (t-1)\right\}.$$
>
>This set is often called the **version space**.

### Mistake Bound for Consistent Algorithm

>[!important] Proposition
>Let $\mathcal{H}$ be a **finite** hypothesis class. 
>
>The **Consistent Algorithm** enjoys the **mistake bound** $$M_{\text{Consistent}}(\mathcal{H}) \le |\mathcal{H}| - 1.$$

### Halving Algorithm

>[!important] Definition
>The **Halving Algorithm** is described as follows
>- *Require*: A finite hypothesis class $\mathcal{H}$
>- *Initialize*: $\mathcal{V}_{1} = \mathcal{H}$
>- For $t=1 \,{,}\ldots{,}\,$:
>	- the learner receives sample $x_{t}\in \mathcal{X}$
>	- the hypothesis **predict** based on the *number of hypotheses* that agree with the decision  $$p_{t} = \arg\max_{r\in [0,1]}\lvert \left\{ h\in V_{t}:\, h_{t}(x_{t}) = r \right\} \rvert $$
>	- the learner receives **true label** $y_{t} = h^{*}(x_{t})$
>	- *Update* the **Version Space** $$V_{t+1} = \left\{ h\in V_{t}: h(x_{t}) = y_{t} \right\}$$

### Mistake Bound for Halving Algorithm

>[!important] Proposition
>Let $\mathcal{H}$ be a **finite** hypothesis class. 
>
>The **Halving Algorithm** enjoys the **mistake bound** $$M_{\text{Halving}}(\mathcal{H}) \le \log_{2}\left(|\mathcal{H}|\right).$$






## Explanation





-----------
##  Recommended Notes and References


- [[Online Learnability and Realizabililty Assumption]]
- [[Empirical Risk Minimization]]
- [[PAC Learnable and Agnostic PAC Learnable]]

- [[Understanding Machine Learning by Shalev-Shwartz]] pp 247
- [[Online Learning and Online Convex Optimization by Shalev-Shwartz]] pp 113 - 115