---
tags:
  - concept
  - machine_learning/theory
  - math/stochastic_process
  - statistics/concentration_inequality
keywords: 
topics: 
name: Sauer-Shelah Lemma for VC Dimension
date of note: 2024-06-02
---

## Concept Definition

>[!important]
>**Name**: Sauer-Shelah Lemma for VC Dimension

>[!important] Sauer-Shelah Lemma
>Let $\mathcal{F}$ be a class of **Boolean functions** with **finite VC dimension** $$\text{VC-dim}(\mathcal{F}) \le d < \infty.$$ 
>
>Then, for all $n > d+1$, 
>$$
> \begin{align}
> \tau_{\mathcal{F}}(n) &\le \sum_{i=0}^{d}{{n}\choose{i}}\le \left(\frac{en}{d}\right)^{d} 
> \end{align}
>$$ 

- [[VC Dimension]]
- [[Growth Function of Function Class]]
- [[Vapnik-Chervonenkis Class]]

## Explanation

>[!important]
>The **Sauer-Shelah lemma** shows that the **growth rate** of **VC class** of functions is 
>- either **exponential** when the *VC dimension* is **infinite** 
>- or **polynomial** up to the **degree** of **VC dimension**.




-----------
##  Recommended Notes and References

- [[VC Dimension]]
- [[Growth Function of Function Class]]
- [[Vapnik-Chervonenkis Class]]

- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Boosting Foundations and Algorithms by Schapire]]
- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]