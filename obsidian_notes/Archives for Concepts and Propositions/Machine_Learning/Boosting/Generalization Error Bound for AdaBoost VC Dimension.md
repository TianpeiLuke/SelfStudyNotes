---
tags:
  - concept
  - machine_learning/theory
  - machine_learning/boosting
keywords:
  - vc_dimension
  - generalization_error
  - adaboost
topics:
  - machine_learning_theory
name: VC-based Generalization Error Bound for AdaBoost
date of note: 2024-07-29
---

## Concept Definition

>[!important]
>**Name**: Generalization Error Bound for AdaBoost VC Dimension

![[AdaBoost Algorithm#^1982f3]]

![[Generalization Error Bound for AdaBoost Finite Case#^49f151]]

### VC Dimension of Space of Linear Thresholding Functions

![[Generalization Error Bound for AdaBoost Finite Case#^81976d]]

### Finite Hypothesis Space

![[Generalization Error Bound for AdaBoost Finite Case#^6ffb11]]


### Infinite Hypothesis Space

>[!important] Lemma
>Assume $\mathcal{H}$ has **finite VC dimension** $d \ge 1$. Let $m \ge \max\left\{ d, T  \right\}.$
>
>For any set $S$ of $m$ points, the **restriction** of $\mathcal{C}_{T}$ on $S$ has cardinality *bounded*  as follows
>$$
>|\mathcal{C}_{T, S}| \le \tau_{\mathcal{C}_{T}}(m) \le \left( \frac{e\, m}{T} \right)^{T}\left( \frac{e\,m}{d} \right)^{d\,T}.
>$$

- [[VC Dimension]]
- [[Restriction of Function Class to Data]]
- [[Growth Function of Function Class]]
- [[Shattering of Data by Function Class]]

![[Generalization Error Bound for AdaBoost Finite Case#^99fbd3]]

>[!important] Theorem
>Suppose that **AdaBoost** is run for $T$ rounds on $m$ random samples, using base classifiers from a space $\mathcal{H}$ with **finite VC dimension** $d\ge 1$.   Let $m \ge \max\left\{ d, T  \right\}.$
>
>Then, *with probability at least* $1 - \delta$, the **generalization error** of the **combined classifier** $H$ satisifies
>$$
>L_{\mathcal{P}}(H) \le L_{\mathcal{D}}(H) + \sqrt{ \frac{32 \left[ T \left(  \log \left( \dfrac{e\, m\,}{T} \right) + d\,\log \left( \dfrac{e\, m\,}{d} \right)  \right) + \log\left(  \dfrac{8}{\delta}  \right)  \right] }{m} }
>$$
>
>Furthermore, with probability at least $1 - \delta$, if $H$ is **consistent** with the training set (i.e. under the **realizability assumption**) $$L_{\mathcal{D}}(H^{*}) = 0,\quad  \mathcal{P}\text{-a.s.},$$ then 
>$$
>L_{\mathcal{P}}(H) \le \frac{2T\,\left(  \log \left( \dfrac{2\,e\,m\,}{T} \right) + d\log \left( \dfrac{2 e\,m}{d} \right) \right) + 2\log \left( \dfrac{2}{\delta} \right)}{m}
>$$

- [[Generalization Error Bound for Binary Classification VC Dimension]]
- [[PAC Learnable and Agnostic PAC Learnable]]
- [[Realizability Assumption for Empirical Risk Minimization]]

>[!important] Corollary
>Suppose that
>- **AdaBoost** is run for $T$ rounds on $m \ge T$ random samples, using base classifiers from a **finite hypothesis space** $\mathcal{H}$;
>- And each base classifier has **weighted error** $$\epsilon_{t} \le \frac{1}{2} - \gamma$$ for some $\gamma >0$.
>- Furthermore, let the number of rounds $$T = \left\lceil  \frac{\log m}{2\gamma^2}  \right\rceil $$
>
>Then, *with probability at least* $1 − \delta$, the **generalization error** of the combined classifier $H$ 
>$$
>L_{\mathcal{P}}(H) \le O\left( \frac{1}{m} \left[ \frac{\log(m)}{\gamma^2} \left( \log (m) + d\log \left( \dfrac{m}{d} \right) \right) + \log \left( \frac{1}{\delta} \right) \right]  \right)
>$$


## Explanation

>[!info]
>The generalization error bound increases as the **number of base classifiers $T$ increases**
>- This is because the **VC-dimension** of hypothesis class $\mathcal{C}_{T}$ **increases** with respect to the *number* of base classifiers $T$, $$\text{VC-Dim}(\mathcal{C}_{T}) \le T\,d$$
>- Note that  $$\text{VC-Dim}(\mathcal{C}_{T}) = \max\left\{ m: \tau_{\mathcal{C}_{T}}(m) = 2^{m} \right\}$$ thus
>  $$
>  \begin{align}
>    m \le T\left( \log_{2}(em) - \log_{2}(T) + \,d\log_{2} \left(  \frac{e\,m}{d}\right)  \right) \\ \\
>    \frac{m}{T} \le \log_{2}\left( \frac{m}{T} \right) + \log_{2}(e) + \,d\log_{2} \left(  \frac{e\,m}{d}\right)
   \end{align}
>$$ 

>[!important]
>The bound suggests that the combined classifier would **overfit** when $T$ is too large.

>[!important]
>The generalization bound for Boosting is **loose**. In practice, the AdaBoost **performs much better** than the bound suggested.




-----------
##  Recommended Notes and References

- [[Generalization Error Bound for AdaBoost Finite Case]]
- [[VC Dimension]]
- [[Restriction of Function Class to Data]]
- [[Shattering of Data by Function Class]]
- [[PAC Learnable and Agnostic PAC Learnable]]
- [[Growth Function of Function Class]]
- [[Sauer-Shelah Lemma for VC Dimension]]


- [[AdaBoost Algorithm]]
- [[Empirical Risk Minimization]]



- [[Foundations of Machine Learning by Mohri]] pp 130 - 131
- [[Boosting Foundations and Algorithms by Schapire]]  pp 77 - 82