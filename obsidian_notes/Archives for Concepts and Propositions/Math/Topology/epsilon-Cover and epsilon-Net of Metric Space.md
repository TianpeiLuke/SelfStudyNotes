---
tags:
  - concept
  - math/topology
  - math/functional_analysis
  - math/stochastic_process
  - statistics/concentration_inequality
keywords:
  - epsilon_cover
  - epsilon_net
topics:
  - topology
  - functional_analysis
  - stochastic_process
  - concentration_inequality
name: epsilon-Cover and epsilon-Net
date of note: 2024-05-31
---

## Concept Definition

>[!important]
>**Name**: $\epsilon$-Cover and $\epsilon$-Net of Metric Space

>[!important] Definition
>Let $(T, d)$ be a *metric space* and  $K \subset T$ is a subset of $T$. Let $\epsilon > 0$.  
>
>An **$\epsilon$-cover ($\epsilon$-net) of a set** $K$ *with respect to a metric* $d$ is a subset $$\mathcal{N} \subset K$$ such that *every point* in $K$ is *within distance* $\epsilon$ of some point of $\mathcal{N}$, i.e.
>$$
> \begin{align*}
> \forall x \in K, \; \exists x_0 \in \mathcal{N}, \text{ s.t. }d(x, x_0) \le \epsilon.
> \end{align*}
>$$  
>
>Equivalently, $\mathcal{N}$ is an **$\epsilon$-cover ($\epsilon$-net)** of $K$ *if and only if* $K$ can be *covered* by balls with centers in $\mathcal{N}$ and radii $\epsilon$.

^b37cb4

- [[Lebesgue Number Lemma in Compact Metric Space]]
- [[Metric Space]]
- [[Metric Topology and epsilon-ball]]
- [[Indexed Family of Sets]]

## Explanation

>[!info]
>Note that $\epsilon$ is fixed for $\mathcal{N}$. $\mathcal{N} \subset T$ is a **dense** subset of $T$.

- [[Dense Set]]

>[!important]
>The collection of $\epsilon$-balls, $$\mathscr{B} := \{ B(x, \epsilon), x\in \mathcal{N} \}$$ forms an **open cover** of $K$, i.e.
>$$
>K \subset \bigcup_{x\in \mathcal{N}}B(x, \epsilon).
>$$ 

- [[Covering of Set and Open Covering of Topological Set]]

>[!important]
>By definition of compactness, for a **compact metric space**, the minimal $\epsilon$-Net is **finite** $|\mathcal{N}| < +\infty$ for every $\epsilon >0$.

- [[Covering Number of Metric Space]]


## Vector Quantization

>[!important]
>The concept of **$\epsilon$-net**, i.e. a **dense subset** $\mathcal{N} \subset K$ such that *every element* in $K$ is $\epsilon$-close to *at least of one* of element in $\mathcal{N}$, can be seen as a **vector quantization** or **clustering** of the set $K$.  
>
>In particular, assume that $\mathcal{N}$ is a **maximal $\epsilon$-separated set.** By Lemma [[epsilon-Separated Set in Metric Space#^08741a]], it is an $\epsilon$-net. 

>[!important]
>Note that  each element $x \in K$ can be *represented* by its **nearest neighbor** $x_0 \in \mathcal{N}$ within $\epsilon$-neighorhood. The **shortest lengh of repesenation** for $x_0 \in \mathcal{N}$ is $$k =  \log_{2} \mathcal{N}(K, d, \epsilon).$$ 
>
>Since all elements *within* the $\epsilon$-neighorhood of $x_0$ *shares the same representation*, it needs **at least $\log_{2} \mathcal{N}(K, d, \epsilon)$ to encode** every element in $K$ with **at most $\epsilon$ error rate**.

>[!info]
> Moreover, as $\epsilon \to 0$, *the quantization* becomes **finer** but the **dimension** of **representation** **increases**. 

>[!important]
> This shows the **tradeoff** between the **granularity** of **representation** and the **encoding efficiency**. 
> 
> As we shall show that **the metric entropy** $$\log_{2} \mathcal{N}(K, d, \epsilon)$$ describes the **complexity of set** *quantitatively*.





-----------
##  Recommended Notes and References



- [[High Dimensional Probability An Introduction by Vershynin]]
- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Concentration Inequalities by Boucheron]]
- [[Topology Book by Munkres]]