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

![[Hypothesis Testing Problem#^14f68d]]

![[Power and Size of Test#^ddfeff]]

![[Power and Size of Test#^7c70c2]]

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
>p\text{-value}(X) := \inf\left\{ \alpha \in (0,1): T_{\alpha}(X) = 1\right\} = \inf\left\{ \alpha \in (0,1): X \in C_{\alpha}\right\}. 
>$$
>
>That is,  **the $p$-value** is the *smallest level* *at which* we can *reject the null hypothesis* $H_{0}$. 

- [[Hypothesis Testing Problem]]
- [[Power and Size of Test]]
- [[Statistics]]



## Explanation

![[Power and Size of Test#^ce7424]]


>[!info]
>- The $p$-value is a function of sample $X$, i.e. it is a **statistic**. 
>- The $p$-value depends on both **data** $x$ and the **test** $T$.


>[!info]
>Given $p$-value from observed data, we can state that for any $\alpha >$ $p$-value, the test would reject the null hypothesis.

>[!important]
>- Normally, we use **$p$-value** **less than $0.01$** as the strong evidence that the null hypothesis is rejected. 
>- $p$-value **between $0.01$ and $0.05$** can still be used against null hypothesis.


## Equivalent Definition

>[!important] Theorem
>Suppose that the **size $\alpha$ test** is of the form
>$$
>T(X) \ge c_{\alpha} \iff \text{ reject }H_{0}.
>$$
>
>Then the $p$-value  can be **computed** as 
>$$
>p\text{-value}(x)  = \sup\left\{ \mathcal{P}_{\theta}\left[ T(X) \ge T(x)\right]:\;\; \theta \in \Theta_{0}  \right\} 
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

## Distribution of p-Value

>[!important] Proposition
>If the *test statistic* has a **continuous distribution**, then under $H_0 : \theta = \theta_{0}$, the **$p$-value has a Uniform $(0,1)$ distribution**. 
>
>Therefore, if we *reject* $H_0$ when the $p$-value is less than $\alpha$, the **probability of a type I error** is $\alpha$.

- [[All of Statistics A Concise Course by Wasserman]]

>[!important]
>We can see that 
>$$
>  \mathcal{P}\left[\,p\text{-value}(X) \le \alpha\right] = \mathcal{P}\left(X \in C_{\alpha}\right)  = \alpha, \quad \mathcal{P}\in \mathscr{P}_{0}
>$$


>[!info]
>- if $H_0$ is true, the **$p$-value** is like a **random draw** from a $Unif(0, 1)$ distribution.
>- if $H_{1}$ is true, then the **$p$-value** *concentrate* around $0$.
>  
>  
>In other word,  if the **null hypothesis is true**,  $\mathcal{P} \in \mathscr{P}_{0}$,  the $p$-value is completely **non-informative** as it has the **maximum entropy** (uniform distribution). 
>
>This shows that the distribution of $p$-value can helps us to understand if the underlying population fits the null hypothesis.



-----------
##  Recommended Notes and References

- [[Randomized Controlled Trial or RCT]]
- [[Probability Distribution of Random Variable]]
- [[Probability Space]]


- [[All of Statistics A Concise Course by Wasserman]]
- [[Testing Statistical Hypotheses by Lehmann]]
- [[Mathematical Statistics by Shao]]