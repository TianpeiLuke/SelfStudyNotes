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
name: No-Regret Learning for Online Prediction with Expert Advices
date of note: 2024-08-05
---

## Concept Definition

>[!important]
>**Name**: No-Regret Learning for Online Prediction with Expert Advices

![[Online Prediction with Expert Advice#^980822]]

![[Online Prediction with Expert Advice#^d0e7f4]]

![[Regret for Online Learning#^c8c1f8]]


>[!important] Definition
>The goal of **no-regret learning** is to *predict* so that the **regret** is as small as possible for *all sequences of outcomes*. 
>
>For online prediction with $\mathcal{E}$ experts, 
>$$
> \max_{E\in \mathcal{E}}R_{E, T} = o(T)
>$$
>or
>$$
>\frac{1}{T}\left( \widehat{L}_{T} - \min_{E\in \mathcal{E}}L_{E, T} \right) \stackrel{T\to \infty}{\longrightarrow} 0
>$$
>- Assume that $\mathcal{E} \subset \mathbb{N}$ and $\mathcal{E}$ is **finite**.
>- The *convergence* is **uniform** over the *choice of outcome sequences* $(y_{1}\,{,}\ldots{,}\,y_{T})$ and the *expert advices* $(f_{E}^{(t)}: t=1\,{,}\ldots{,}\,T,\, E\in \mathcal{E})$, i.e. $$\lim_{ T \to \infty }\max_{y_{t}, t\le T}\max_{f_{E}^{(t)}, t\le T, E\in \mathcal{E}} \frac{1}{T}\sum_{t=1}^{T}\left( \ell(\hat{p}_{t}, y_{t}) - \min_{E\in \mathcal{E}}\ell(f_{E}^{(t)}, y_{t}) \right) = 0$$

^873808

- [[Uniform Convergence]]

## Explanation

>[!important]
>In **no-regret learning**, we need to find algorithm that achieves the **sub-linear regret**. 
>- The learning is *effective* if the algorithm is able to "*predict and act one step ahead*" as compared to the underlying *environment*.
>
>It is trivial to achieve **linear regret** without proper learning.







-----------
##  Recommended Notes and References


- [[Regret for Online Learning]]
- [[Online Prediction with Expert Advice]]



- [[Markov Decision Process]]
- [[Sequential Decision Process]]
- [[Statistical Decision Problem]]

- [[Prediction Learning and Games by Cesa-Bianchi]]