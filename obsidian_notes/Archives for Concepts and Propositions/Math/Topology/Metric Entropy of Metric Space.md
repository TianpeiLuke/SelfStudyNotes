---
tags:
  - concept
  - math/topology
  - math/functional_analysis
  - math/stochastic_process
  - statistics/concentration_inequality
keywords:
  - metric_entropy
topics:
  - topology
  - functional_analysis
  - stochastic_process
  - concentration_inequality
name: Metric Entropy of Metric Space
date of note: 2024-05-31
---

## Concept Definition

>[!important]
>**Name**: Metric Entropy of Metric Space

![[epsilon-Cover and epsilon-Net of Metric Space#^b37cb4]]

- [[epsilon-Cover and epsilon-Net of Metric Space]]

![[Covering Number of Metric Space#^4e5f78]]

- [[Covering Number of Metric Space]]

>[!important] Definition
>The *logarithm* of the *covering numbers*
>$$ 
> \begin{align*}
> \log \mathcal{N}(K, d, \epsilon)
> \end{align*} 
>$$  
>is often called the **metric entropy of $K$**.

- [[Covering Number of Metric Space]]
- [[Metric Space]]

## Explanation


>[!info]
> Typically, the covering number **diverges** as $\epsilon \to 0_{+}$, and of interest to us is the **growth rate** of **covering number** on a *logarithmic scale*.
>$$
>\log \mathcal{N}(K, d, \epsilon)
>$$


>[!important]
>When discussing metric entropy, we restrict our attention to subset $K$ of metric spaces $K \subset (T, d)$ that are **totally bounded**, meaning that the covering number $\mathcal{N}(K, d, \epsilon)$ is **finite** for *all* $\epsilon > 0$. 
> 
> Note that  a **metric space** that is **compact** *if and only if* it is **totally bounded** and **complete**. 
> 
> So we can instead assume that $K$ of interest is **compact**.
> 

- [[Compactness]]
- [[Total Boundedness]]
- [[Complete Metric Space]]
- [[Compactness in Functional Analysis]]



## Metric Entropy as Shortest Length of Representation in Vector Quantization

>[!important]
>The concept of **$\epsilon$-net**, i.e. a **dense subset** $\mathcal{N} \subset K$ such that *every element* in $K$ is $\epsilon$-close to *at least of one* of element in $\mathcal{N}$, can be seen as a **vector quantization** or **clustering** of the set $K$.  
>
>In particular, assume that $\mathcal{N}$ is a **maximal $\epsilon$-separated set.** By Lemma [[epsilon-Separated Set in Metric Space#^08741a]], it is an $\epsilon$-net. 

>[!important]
>Note that  each element $x \in K$ can be *represented* by its **nearest neighbor** $x_0 \in \mathcal{N}$ within $\epsilon$-neighorhood. The **shortest lengh of repesenation** for $x_0 \in \mathcal{N}$ is $$k =  \log_{2} \mathcal{N}(K, d, \epsilon).$$ 
>
>Since all elements *within* the $\epsilon$-neighorhood of $x_0$ *shares the same representation*, it needs **at least $\log_{2} \mathcal{N}(K, d, \epsilon)$ to encode** every element in $K$ with **at most $\epsilon$ error rate**.

- [[Elements of Information Theory by Cover]]

>[!info]
> Moreover, as $\epsilon \to 0$, *the quantization* becomes **finer** but the **dimension** of **representation** **increases**. 

>[!important]
> This shows the **tradeoff** between the **granularity** of **representation** and the **encoding efficiency**. 
> 
> As we shall show that **the metric entropy** $$\log_{2} \mathcal{N}(K, d, \epsilon)$$ describes the **complexity of set** *quantitatively*.

### Metric Entropy and Coding

![[Error Correcting Code#^9810bb]]

- [[Error Correcting Code]]






-----------
##  Recommended Notes and References

- [[Covering Number of Metric Space]]

- [[epsilon-Cover and epsilon-Net of Metric Space]]
- [[Metric Space]]
- [[Pre-Compactness]]
- [[Covering of Set and Open Covering of Topological Set]]

- [[High Dimensional Probability An Introduction by Vershynin]]
- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Concentration Inequalities by Boucheron]]
- [[Topology Book by Munkres]]
- [[Elements of Information Theory by Cover]]