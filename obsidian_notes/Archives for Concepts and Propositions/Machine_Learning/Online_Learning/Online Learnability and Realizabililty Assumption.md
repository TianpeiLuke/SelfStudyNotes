---
tags:
  - concept
  - online_learning/theory
  - online_learning/algorithms
  - machine_learning/theory
keywords:
  - online_learnability
  - realizability_assumption
topics:
  - online_learning
  - machine_learning_theory
name: Online Learnability and Realizabililty Assumption
date of note: 2024-08-06
---

## Concept Definition

>[!important]
>**Name**: Online Learnability and Realizabililty Assumption

>[!important] Definition
>**Online learning** is performed in *a sequence of rounds*:
>- For $t= 1\,{,}\ldots{,}\,T$:
>	- the **learner** is given an instance $x_{t} \in \mathcal{X}$
>	- the *learner* **predicts** the *label* of $x$, denoted as $p_{t}$
>	- the true **outcome** $y_{t} \in \mathcal{Y}$ is revealed to the learner
>	- the learner suffers a **loss** $\ell(p_{t}, y_{t})$
>
>The **goal** of learner is to **minimize the regret.** 

^c10d11

>[!important] Definition
>Under the **realizability assumption**, we assume that
>- all the labels $(y_{1} \,{,}\ldots{,}\,y_{T})$ are generated by some **fixed hypothesis** $h^{*}: \mathcal{X} \to \mathcal{Y}$
>- $h^{*}\in \mathcal{H}$, where $\mathcal{H}$ is a **hypothesis class**, and $\mathcal{H}$ is *known* to the learner.

^5e75f3

 

- [[Realizability Assumption for Empirical Risk Minimization]]


>[!important] Definition
>Let $\mathcal{H} \subset \mathcal{Y}^{\mathcal{X}}$ be a *hypothesis class*, and let $\mathcal{A}$ be an **online learning algorithm**. Assume the *realizability case*.
>
>Given any sequence $$S = ((x_{1}, h(x_{1})) \,{,}\ldots{,}\, (x_{T}, h(x_{T})))$$ where $T\in \mathbb{N}$ be any integer and $h\in \mathcal{H}$, let $M_{\mathcal{A}}(S)$ be the **number of mistakes** $\mathcal{A}$ makes on the sequence $S$
>$$
>M_{\mathcal{A}}(S) = \sum_{t=1}^{T}\mathbb{1}\{ p_{t} \neq h(x_{t})  \}.
>$$
>- We denote by $M_{\mathcal{A}}(\mathcal{H})$ the **supremum of** $M_{\mathcal{A}}(S)$ over all possible sequences $S$.
>$$
>M_{\mathcal{A}}(\mathcal{H}) = \sup_{h\in \mathcal{H}}\sum_{t=1}^{T}\mathbb{1}\{ p_{t} \neq h(x_{t})  \}.
>$$
>- A bound $B$ on $M_{\mathcal{A}}(\mathcal{H})$ is called a **mistake-bound**
>$$
> M_{\mathcal{A}}(\mathcal{H}) \le B < \infty.
>$$
>- We say a hypothesis class $\mathcal{H}$ is **online learnable** if there exists an algorithm $\mathcal{A}$ for which $$M_{\mathcal{A}}(\mathcal{H}) \le B < \infty$$

^f05186

- [[Characteristic Function of Set]]
- [[Algorithm Big-O Notations and Dominance Relation]]


## Explanation

>[!quote]
>Clearly, learning is hopeless if there is no correlation between past and present rounds. Previously in the book, we studied the **PAC model** in which we assume that past and present examples are sampled **i.i.d.** from the same distribution source. In the **online learning** model we make **no statistical assumptions** regarding the origin of the sequence of examples. The sequence is allowed to be *deterministic*, *stochastic*, or even *adversarially adaptive* to the learner’s own behavior (as in the case of spam e-mail filtering). Naturally, an *adversary* can make the number of prediction mistakes of our online learning algorithm arbitrarily large. For example, the adversary can present the same instance on each online round, wait for the learner’s prediction, and provide the opposite label as the correct label.
>
>
>--  [[Understanding Machine Learning by Shalev-Shwartz]] pp  246

- [[PAC Learnable and Agnostic PAC Learnable]]


## Consistent Algorithm 


- [[Simple Online Learning Algorithms under Realizability Assumption]]


## Halving Algorithm


- [[Simple Online Learning Algorithms under Realizability Assumption]]


-----------
##  Recommended Notes and References


- [[Regret for Online Learning]]
- [[Weighted Majority Algorithm for Binary Loss]]

- [[PAC Learnable and Agnostic PAC Learnable]]
- [[Realizability Assumption for Empirical Risk Minimization]]
- [[Empirical Risk Minimization]]


- [[Understanding Machine Learning by Shalev-Shwartz]] pp  245 - 248
- [[Online Learning and Online Convex Optimization by Shalev-Shwartz]] pp 111 - 112
- [[Prediction Learning and Games by Cesa-Bianchi]]
- [[Foundations of Machine Learning by Mohri]]