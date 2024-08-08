---
tags:
  - concept
  - online_learning/theory
  - machine_learning/theory
keywords:
  - regret_online_learning
  - no_regret_learning
topics:
  - online_learning
name: Regret for Online Learning
date of note: 2024-08-05
---

## Concept Definition

>[!important]
>**Name**: Regret for Online Learning

![[Prediction with Expert Advice#^980822]]


### Regret for Prediction with Expert Advice

![[Prediction with Expert Advice#^d0e7f4]]


>[!important] Definition
>The forecaster's **goal** is to keep as small as possible the **cumulative regret** (or simply **regret**) with respect to each expert.
>
>The **regret** of expert  $E\in \mathcal{E}$ over $T$ rounds is defined as
>$$
>R_{E, T} := \sum_{t=1}^{T}\left( \ell(\hat{y}_{t}, y_{t}) - \ell(f_{E}^{(t)}, y_{t}) \right) := \widehat{L}_{T} - L_{E, T}
>$$
>which consists of two parts: 
>1. the *forecaster*'s **cumulative loss**  $$\widehat{L}_{T} := \sum_{t=1}^{T}\ell(\hat{y}_{t}, y_{t}) $$
>2. the *expert* $E$'s **cumulative loss**  $$L_{E, T} := \sum_{t=1}^{T}\ell(f_{E}^{(t)}, y_{t}) $$
>
>Thus, the **cumulative regret**  is the **difference** between *forecaster*'s **total loss** and that of expert $E$ *after* $T$ prediction rounds.

^c8c1f8

>[!important] Definition
>We define the **instantaneous regret** *with respect to expert* $E$ at time $t$ as
>$$
>r_{E, t} := \ell(\hat{y}_{t}, y_{t}) - \ell(f_{E}^{(t)}, y_{t})
>$$
>Thus the **cumulative regret** is $$R_{E, t} = \sum_{t=1}^{T}\,r_{E, t}$$

^7704b4

![[No-Regret Learning#^873808]]

- [[No-Regret Learning]]

### Regret for Online Learning

![[Online Learnability and Realizabililty Assumption#^c10d11]]

![[Online Learnability and Realizabililty Assumption#^5e75f3]]

![[Online Learnability and Realizabililty Assumption#^f05186]]

>[!important] Definition (Non-Realizable Case)
>In general **online learning** setting, we make the following assumptions:
>- There is no stochastic assumption on the outcomes $(y_{1} \,{,}\ldots{,}\,y_{T}) \subset \mathcal{Y}$.
>- $\mathcal{H} \subset \mathcal{Y}^{\mathcal{X}}$ is a *hypothesis class* $\mathcal{X}\to \mathcal{Y}$.
>- At each time $t$, the *learner* predicts $p_{t}\in \mathcal{D}$
>- The loss function is defined as $\ell: \mathcal{D}\times \mathcal{Y} \to \mathbb{R}_{+}$
>  
>After running for $T$ rounds, the **regret** of an *online learning algorithm* relative to some *fixed hypothesis* $h\in \mathcal{H}$ is defined as
>$$
>R_{T}(h) := \sum_{t=1}^{T}\ell(p_{t}, y_{t}) - \sum_{t=1}^{T}\ell(h(x_{t}), y_{t})
>$$
>
>The **regret** of the algorithm relative to a *hypothesis class* $\mathcal{H}$ is defined as the **maximum regret** relative to any hypothesis in $\mathcal{H}$, i.e.
>$$
>R_{T}(\mathcal{H}) = \sup_{h\in \mathcal{H}}R_{T}(h) = \sum_{t=1}^{T}\ell(p_{t}, y_{t}) - \inf_{h\in \mathcal{H}}\sum_{t=1}^{T}\ell(h(x_{t}), y_{t})
>$$

- [[Online Learnability and Realizabililty Assumption]]
- [[Empirical Risk Minimization]]
- [[Realizability Assumption for Empirical Risk Minimization]]
- [[Online Learning and Online Convex Optimization by Shalev-Shwartz]]
- [[Understanding Machine Learning by Shalev-Shwartz]] pp 251


## Explanation

>[!info]
>**Regret** $R_{T}(h)$ measures how “*sorry*” the learner is, in retrospect, *not to have followed* the predictions of some hypothesis $h\in \mathcal{H}$.


>[!quote]
>We restate the learner’s goal as having the lowest possible regret relative to $\mathcal{H}$. We will sometime be satisfied with “**low regret**” algorithms, by which we mean that $R_{T}(\mathcal{H})$ **grows sub-linearly** with the number of rounds, $T$, which implies that the *difference* between the *average loss* of the *learner* and the *average loss* of the *best hypothesis* in $\mathcal{H}$ tends to zero as $T$ goes to infinity.
>
>-- [[Online Learning and Online Convex Optimization by Shalev-Shwartz]] pp 111


>[!info]
>Even if $|\mathcal{H}| =2$, under the **unrealizable asusmption**, **no algorithm** can obtain a **sublinear bound**.

- [[Understanding Machine Learning by Shalev-Shwartz]] pp 251- 252





-----------
##  Recommended Notes and References


- [[No-Regret Learning]]
- [[Prediction with Expert Advice]]
- [[Online Convex Optimization]]


- [[PAC Learnable and Agnostic PAC Learnable]]
- [[Markov Decision Process]]
- [[Sequential Decision Process]]
- [[Statistical Decision Problem]]

- [[Prediction Learning and Games by Cesa-Bianchi]] pp 8
- [[Bandit Algorithms by Lattimore]] 
- [[Understanding Machine Learning by Shalev-Shwartz]] pp 246
- [[Online Learning and Online Convex Optimization by Shalev-Shwartz]]