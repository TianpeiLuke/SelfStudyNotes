---
tags:
  - concept
  - statistics/estimation
  - math/probability
  - statistics/inference
keywords:
  - statistical_inference
topics:
  - statistics/estimation
  - statistics
name: Statistical Inference Problem
date of note: 2024-06-08
---

## Concept Definition

>[!important]
>**Name**: Statistical Inference Problem

>[!quote] 
>The **loss function** plays a crucial role in **statistical decision theory**.
>- *Loss functions* can be obtained from a **utility analysis** (Berger, 1985  [[Statistical Decision Theory by Berger]]), but in many problems they have to be determined *subjectively.* 
> 
> In **statistical inference**, we make an inference *about* the **unknown population** based on 
> - the *sample* $X$ and
> - _inference procedures_ **without using any loss function**, 
>
>although any inference procedure can be cast in *decision-theoretic terms* as a decision rule. 
> 
> There are **three main types** of inference procedures: 
> - **point estimators**, [[Statistical Estimation Problem]]
> - **hypothesis tests**, [[Hypothesis Testing Problem]] 
> - **confidence sets**.
> 
>-- [[Mathematical Statistics by Shao]] pp 122

- [[Statistical Decision Problem]]
- [[Concepts and Theorems in Statistical Inference and Decision Theory]]
- [[Concepts and Theorems in Hypothesis Testing]]
- [[Point Estimator]]


>[!quote]
>The problem of **statistical inference** on $f$, broadly speaking, can be divided into **three intimately connected problems** of using the *observation* $Y$ to 
>- **Estimate** the *parameter* $f$ by an estimator $T(Y)$,
>- **Test hypotheses** on $f$ based on test functions $\Psi(Y)$ *and/or* 
>- **Construct confidence sets** $C(Y)$ that *contain* $f$ with *high probability*.
>  
>-- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]] pp 1

## Explanation



## Inference Problem vs. Decision Problem

>[!quote] 
>The problem of estimating an unknown parameter related to the unknown population is introduced in ... and the discussion .. as a **special statistical decision problem**.
>
>In **statistical inference**, however, *estimators of parameters* are derived based on **some principle** (such as the *unbiasedness*, *invariance*, *sufficiency*, *substitution principle*, *likelihood principle*, *Bayesian principle*, etc.), **not based on a loss or risk function**. 
> 
>-- [[Mathematical Statistics by Shao]] pp 122

>[!info]
>*Statistical inference* can be viewed as **query-answering system**:
>- The user provides query about the **properties** of the population $\mathcal{P}$ 
>- The system has an **inference procedure** based on some **principles**
>- The system returns *statistics* $T$ that reveals the property of the population. 






-----------
##  Recommended Notes and References

- [[Three Components of Intelligence System]]

- [[Point Estimator]]


- [[All of Statistics A Concise Course by Wasserman]]
- [[Mathematical Statistics by Shao]] pp 122
- [[Statistical Decision Theory by Berger]]
- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]] pp 1
- [[Probabilistic Graphical Models by Koller]]