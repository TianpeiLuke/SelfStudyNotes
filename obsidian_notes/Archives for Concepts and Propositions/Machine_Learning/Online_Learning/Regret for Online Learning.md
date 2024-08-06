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

![[Online Prediction with Expert Advice#^980822]]


### Regret for Prediction with Expert Advice

![[Online Prediction with Expert Advice#^d0e7f4]]


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





## Explanation





-----------
##  Recommended Notes and References


- [[No-Regret Learning]]
- [[Online Prediction with Expert Advice]]



- [[Markov Decision Process]]
- [[Sequential Decision Process]]
- [[Statistical Decision Problem]]

- [[Prediction Learning and Games by Cesa-Bianchi]] pp 8