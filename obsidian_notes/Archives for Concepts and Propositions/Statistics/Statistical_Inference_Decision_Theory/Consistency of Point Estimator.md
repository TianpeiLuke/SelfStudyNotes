---
tags:
  - concept
  - statistics/estimation
keywords:
  - point_estimator
  - consistency_estimation
topics:
  - statistics
name: Consistency of Point Estimator
date of note: 2024-05-22
---

## Concept Definition

>[!important]
>**Name**: Consistency of Point Estimator

>[!info] 
>Let $X_{1} \,{,}\ldots{,}\, X_{n}$ be $n$ independent identically distributed (i.i.d.) random variables from distribution $F$. 
>
>A **point estimator** $\hat{\theta}$ of a parameter $\theta$ is some function $g$ of $X_{1} \,{,}\ldots{,}\, X_{n}$:
>$$
>\hat{\theta}_{n} := g\left( X_{1} \,{,}\ldots{,}\, X_{n} \right)
>$$

- [[Point Estimator]]

>[!important] Definition
>A point estimator $\hat{\theta}$ of a *parameter* $\theta$  is **consistent** if
>$$
>\hat{\theta}_{n} \stackrel{\mathcal{P}}{\longrightarrow} \theta
>$$
>with respect to any $\mathcal{P}\in \mathscr{P}.$

- [[Convergence in Measure]]

>[!important] Definition
>A point estimator $\hat{\theta}$ of a *parameter* $\theta$  is **strong consistent** if
>$$
>\hat{\theta}_{n} \stackrel{\text{a.s.}}{\longrightarrow} \theta
>$$
>with respect to any $\mathcal{P}\in \mathscr{P}.$

- [[Pointwise Almost Everywhere Convergence]]

>[!important] Definition
>A point estimator $\hat{\theta}$ of a *parameter* $\theta$  is **$L^p$-consistent** for $1\le p <\infty$  if
>$$
>\hat{\theta}_{n} \stackrel{L^p}{\longrightarrow} \theta
>$$
>with respect to any $\mathcal{P}\in \mathscr{P}.$
>
>For $p=2$, **$L^2$-consistency** is also called **consistency in Mean Squared Error.**

- [[Convergence in Lp norm]]
- [[Minimum Mean Square Estimation]]



## Explanation


>[!info]
>That is, the **probability measure** of *deviation event* is approaching to zero as $n\to \infty$.
>
>That is, for any $\epsilon >0$,  and any $\delta >0$, there exists some $m\in \mathbb{N}$, such that for all $n \ge m$,
>$$
>\mathcal{P}_{\theta}\left\{ \lvert \hat{\theta}_{n}  - \theta \rvert \ge \epsilon   \right\} \le \delta
>$$ 

>[!info]
>If $\hat{\theta}$ is *unbiased*, $\theta =  \mathbb{E}_{\theta}[\hat{\theta} ]$, then we have **the concentration-type inequality**
>$$
>\mathcal{P}_{\theta}\left\{   \lVert\;  \hat{\theta}_{n} -  \mathbb{E}_{\theta}[\hat{\theta} ] \;\rVert \ge t  \right\} \leq \delta(t, n)
>$$

- [[Bias of Point Estimator and Unbiasedness]]
- [[Basic Inequalities and Cramér–Chernoff Method]]

>[!info]
>From [[Summary of Modes of Convergence]], we see that *consistency* (in measure) is **weaker** than *strong consistency* (almost surely consistency) and *$L^p$-consistency*.

>[!important]
>**Consistency** is a very *essential requirement* in the sense that any *inconsistent estimators should not be used*, but a **consistent estimator is not necessarily good**. 
>
>Thus, consistency should be used together with one or a few more criteria.


## Compare Consistency and Unbiasedness

>[!important]
>- It is important to understand that the *concept* of **consistency** concerns the *performance of estimator* under the **large sample regime**, i.e. when the sample size $n\to \infty$.
>	- It concerns about whether or not the *value of estimator* will **eventually** become the **ground truth parameter** $\theta$.
>	- It concerns about the value of a *single estimator* $\hat{\theta}_{n}$ for a large sample size.
>- The concept of **bias** of estimator concerns only the **mean value** of estimator.
>	- It does *not control* the **behavior of estimator** as the data size changes.




-----------
##  Recommended Notes and References

- [[Summary of Modes of Convergence]]
	- [[Convergence in Measure]]
	- [[Pointwise Almost Everywhere Convergence]]
	- [[Convergence in Lp norm]]

- 

- [[Probability Distribution of Random Variable]]
- [[Independent Random Variables]]
- [[Probability Space]]

- [[Point Estimator]]

- [[All of Statistics A Concise Course by Wasserman]]