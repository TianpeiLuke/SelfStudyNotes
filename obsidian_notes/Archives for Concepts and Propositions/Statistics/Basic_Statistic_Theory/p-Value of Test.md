---
tags:
  - concept
  - statistics/estimation
keywords:
  - pvalue_hypothesis_test
topics:
  - statistics
name: p-Value of Test
date of note: 2024-05-22
---

## Concept Definition

>[!important]
>**Name**: p-Value of Test

>[!info]
>Consider the following *hypothesis testing problem*, 
>$$
>\begin{align*}
>H_{0}: \theta \in \Theta_{0} \text{ versus } H_{1}: \theta \in \Theta_{1} 
\end{align*}
>$$
>where the partition of parameter space $\Theta = \Theta_{0} \cup \Theta_{1}$. 
>
>We call $H_{0}$ the **null hypothesis** and $H_{1}$ the **alternative hypothesis**.

>[!info]
>Suppose a random variable $X$ taking values in $\mathcal{X}$, the **rejection region** of a *test* is a subset $R \subset \mathcal{X}$ within which **the null hypothesis is rejected**: 
>$$
>X \in R \implies H_{0} \text{ is rejected.}
>$$
>
>Usually, a rejection region is defined in terms of some **test statistic** $T$:
>$$
>R := \left\{ x \in \mathcal{X}: T(x) \ge t \right\}
>$$


>[!info]
>**$p$-value** used to strength of the test to reject null hypothesis.
>
>**Given** a $\alpha \in (0,1)$, we would like to ask if the test *rejects null hypothesis __at that level__*. 
>
>Since if a test is at level $\alpha$, for every $\alpha' \ge \alpha$, the test would reject the null hypothesis. Thus we can find an *infimum value* for $\alpha$ so that the test would reject null hypothesis at that level.

>[!important] Definition
>Suppose that $\alpha \in (0,1)$, we have a *size $\alpha$ test* with *rejection region* $R_{\alpha}$.
>
>Then **the $p$-value**  is defined as below
>$$
>p\text{-value} := \inf\left\{ \alpha: X \in R_{\alpha} \right\}. 
>$$
>
>That is,  **the $p$-value** is the *smallest level* *at which* we can *reject the null hypothesis* $H_{0}$. 

- [[Power and Size of Test]]

>[!info]
>The $p$-value will serve as a **test statistic**. 

## Explanation

>[!important]
>Informally, the $p$-value is a **measure of the evidence against $H_0$**: the *smaller* the $p$-value, the *stronger* the evidence against $H_0$.

>[!important]
>Given $p$-value from observed data, we can state that for any $\alpha >$ $p$-value, the test would reject the null hypothesis.

>[!important]
>- Normally, we use **$p$-value** **less than $0.01$** as the strong evidence that the null hypothesis is rejected. 
>- $p$-value **between $0.01$ and $0.05$** can still be used against null hypothesis.


## Interpretation

>[!important] Theorem
>Suppose that the **size $\alpha$ test** is of the form
>$$
>T(X) \ge c_{\alpha} \iff \text{ reject }H_{0}.
>$$
>
>Then the $p$-value  can be **computed** as 
>$$
>p\text{-value}  = \sup\left\{ \mathcal{P}_{\theta}\left[ T(X) \ge T(x)\right]:\;\; \theta \in \Theta_{0}  \right\} 
>$$
>where $x$ is the **observed value** of  random variable $X$.

>[!info]
>For $\Theta_{0} = \left\{ \theta \right\}$, we have
>$$
>p(x) =\mathcal{P}_{\theta_{0}}\left[ T(X) \ge T(x)\right]
>$$

>[!important]
>The $p$-value is the *probability* (under **null hypothesis** $H_{0}$) of *observing* a value of the *test statistic* **the same** as **or more extreme** than what was **actually observed.**

>[!info]
>The procedure is 
>- **observing** the value of test statistic $T(x) = t$  from data.
>- assuming that the *hull hypothesis $H_{0}$ is true*.
>- computing the *probability* that the test statistic $T(X)$ have value *greater than or equal to* $t$ **under the null hypothesis assumption**.

>[!important] Proposition
>If the *test statistic* has a **continuous distribution**, then under $H_0 : \theta = \theta_{0}$, the **$p$-value has a Uniform $(0,1)$ distribution**. 
>
>Therefore, if we *reject* $H_0$ when the $p$-value is less than $\alpha$, the **probability of a type I error** is $\alpha$.

>[!info]
>- if $H_0$ is true, the **$p$-value** is like a **random draw** from a $Unif(0, 1)$ distribution.
>- if $H_{1}$ is true, then the **$p$-value** *concentrate* around $0$.



-----------
##  Recommended Notes and References


- [[Probability Distribution of Random Variable]]
- [[Probability Space]]


- [[All of Statistics A Concise Course by Wasserman]]
- [[Testing Statistical Hypotheses by Lehmann]]