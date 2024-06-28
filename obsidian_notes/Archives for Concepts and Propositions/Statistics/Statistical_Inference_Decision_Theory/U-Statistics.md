---
tags:
  - concept
  - statistics/estimation
  - math/probability
keywords:
  - u_statistics
topics:
  - statistics/estimation
name: U-Statistics
date of note: 2024-06-08
---

## Concept Definition

>[!important]
>**Name**: U-Statistics

>[!important] Definition
>Let $X_{1} \,{,}\ldots{,}\, X_{n}$ be **i.i.d.** from an *unknown population* $\mathcal{P}$ in a *nonparametric family* $\mathscr{P}$.
>
>Consider parameters $\theta$ that are of the form
>$$
>\theta := \mathbb{E}_{ \mathcal{P} }\left[ h\left(X_{1} \,{,}\ldots{,}\, X_{m}\right) \right].
>$$
>where $m \le n$ is a positive integer and  $h$ is a **symmetric Borel function** satisfying $$ \mathbb{E}_{ \mathcal{P} }\left[ h\left(X_{1} \,{,}\ldots{,}\, X_{m}\right) \right] < \infty$$ for all $\mathcal{P} \in \mathscr{P}.$
>
>A *symmetric unbiased estimator* of $\theta$ is of the form
>$$
>U_{n} = {n \choose m}^{-1} \sum_{(i_{1} \,{,}\ldots{,}\,i_{m})\in \mathcal{C} }h\left(X_{i_{1}} \,{,}\ldots{,}\, X_{i_{m}}\right)
>$$
>where $\mathcal{C}$ is all combinations of $m$ indices from $\{ 1 \,{,}\ldots{,}\,n \}$.
>
>The estimator $U_{n}$ is called the **$U$-statistic** *with* **kernel** $h$ of **order** $m$.

- [[Nonparametric Models and Semi-Parametric Models]]
- [[Point Estimator]]
- [[Measurable Function]]
- [[Borel sigma Field]]
- [[Mathematical Statistics by Shao]] pp 174


## Explanation



## Example

- [[Gini Mean Difference]]


- [[Wilcoxon Statistic]]


-----------
##  Recommended Notes and References

- [[Point Estimator]]
- [[Uniformly Minimum Variance Unbiased Estimation]]
- [[Nonparametric Models and Semi-Parametric Models]]


- [[All of Statistics A Concise Course by Wasserman]]

- [[Jackknife Estimator of Variance]]
- [[Han Inequality]]
- [[Sub-Additivity of Entropy Functional and Tensorization]]

