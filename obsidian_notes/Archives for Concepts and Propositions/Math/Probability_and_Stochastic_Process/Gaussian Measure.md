---
tags:
  - concept
  - math/probability
  - statistics/concentration_inequality
  - math/information_theory
keywords:
  - gaussian_measure
topics:
  - probability
  - concentration_inequality
  - information_theory
name: Gaussian Measure
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**:  Gaussian Measure

>[!important] Definition
>Let $(\mathbb{R}^n, \mathcal{L}(\mathbb{R}^n))$ be a *measurable space*, where $\mathcal{L}(\mathbb{R}^n)$ is the *Lebesgue $\sigma$-algebra* on $\mathbb{R}^n$.  Let $\mu^n: \mathcal{L}(\mathbb{R}^n) \to \mathbb{R}_{+}$ be the *Lebesgue measure* on $\mathbb{R}^n.$
>
>Then the **standard Gaussian measure** $\mathcal{N}: \mathcal{L}(\mathbb{R}^n) \to [0,1]$ is defined as 
>$$
> \begin{align*}
> \mathcal{N}(A) &:= \int_{A} \left(\frac{1}{2\pi}\right)^{n/2}\exp \left( -\frac{1}{2} \lVert x \rVert_{2}^2  \right)\, d\mu^n(x)
> \end{align*} 
>$$ 
>for every $A \in \mathcal{L}(\mathbb{R}^n).$

- [[Lebesgue Measure]]
- [[Measure Space and Countably Additive Measure]]
- [[Radon-Nikodym Derivative]]


>[!info]
>The density function with respect to Lebesgue measure is
>$$
> \frac{d\mathcal{N}}{d\mu^n} = \left(\frac{1}{2\pi}\right)^{n/2}\exp \left( -\frac{1}{2} \lVert x \rVert_{2}^2  \right)
>$$

- [[Probability Distribution of Random Variable]]
- [[Density and Probability Density]]
- [[Radon-Nikodym Derivative]]

>[!important]
>The **Gaussian measure** $\mathcal{N}$ with mean $\mu$  and variance $\sigma^2$ is 
>$$
>d\mathcal{N}(x) := \left(\frac{1}{2\pi\sigma^{2}}\right)^{n / 2}\exp \left( -\frac{\lVert x - \mu \rVert_{2}^{2}}{2\sigma^{2}} \right) d\mu^n
>$$


## Explanation

>[!info]
>By definition, Gaussian measure is a **Borel measure**.

- [[Borel Measure]]

## Compare to Lebesgue Measure

>[!important] Proposition
>Let $(\mathbb{R}^n, \mathcal{L}(\mathbb{R}^n))$ be a *measurable space*, where $\mathcal{L}(\mathbb{R}^n)$ is the *Lebesgue $\sigma$-algebra* on $\mathbb{R}^n$.
>
>Denote  $\mu^n: \mathcal{L}(\mathbb{R}^n) \to \mathbb{R}_{+}$ as the *Lebesgue measure* on $\mathbb{R}^n.$ Also denote $\mathcal{N}$ as the Gaussian measure on $\mathbb{R}^n.$
>
>Then 
>$$
>\mu^n \ll \mathcal{N} \ll \mu^n
>$$
>where $\ll$ means the *absolute continuity of measure*.
>
>That is, the Gaussian measure is **equivalent** to Lebesgue measure.
 
- [[Lebesgue Measure]]
- [[Absolute Continuity for Measures]]

## Properties


>[!important] Inner Regularity
>Let $(\mathbb{R}^n, \mathcal{L}(\mathbb{R}^n))$ be a *measurable space*, where $\mathcal{L}(\mathbb{R}^n)$ is the *Lebesgue $\sigma$-algebra* on $\mathbb{R}^n$.
>
>For all *Borel sets* $A \in \mathcal{L}(\mathbb{R}^n)$,
>$$
>\mathcal{N}(A) = \sup\left\{ \mathcal{N}(K): K \subset A, \; K \text{ is compact} \right\} 
>$$

- [[Inner Regularity]]

>[!important] Proposition (Pushforward or Translation)
>Let $(\mathbb{R}^n, \mathcal{L}(\mathbb{R}^n))$ be a *measurable space*, where $\mathcal{L}(\mathbb{R}^n)$ is the *Lebesgue $\sigma$-algebra* on $\mathbb{R}^n$.
>
>Given $h\in \mathbb{R}^n$, define **the translation map** $T_{h}: \mathbb{R}^n \to \mathbb{R}^N$ as a *Borel measurable function* by 
>$$
>T_{h}(x) = x + h 
>$$ 
>
>Then the **pushforward** of **Gaussian measure** by $T_{h}$ is 
>$$
>\begin{align*}
>T_{h, \#}(d\mathcal{N}) = d\mathcal{N} \circ T_{h}^{-1} = \exp \left( \left\langle h\,,\, x \right\rangle -\frac{1}{2} \lVert h \rVert_{2}^2  \right)\,   d\mathcal{N}
\end{align*}
>$$

- [[Push-forward Measure and Push-forward Operator]]
- [[Cameron–Martin Theorem and Admissible Shift of Gaussian Measure]]


>[!info]
>Unlike Lebesgue measure, Gaussian measure is **not translation invariant.** 

## Extension to Infinite Product Space

>[!important]
>Based on [[Kolmogorov Extension Theorem in Infinite Product Space]], there exists Gaussian measure $\mathcal{N}$ on **arbitrary product space** $\prod_{t\in T}\mathcal{X}_{t}$ of **locally compact, second countable** space $\mathcal{X}_{t}$. 

- [[Locally Compactness]]
- [[Second Countablity]]
- [[Product Measure on Infinite Product Space]]

## Concentration of Gaussian Measure

### Concentration of Lipschitz Function of Gaussian Vector

![[Concentration of Lipschitz Function of Gaussian Vector#^275d78]]



![[Concentration of Lipschitz Function of Gaussian Vector#^5bdfe6]]

- [[Concentration of Lipschitz Function of Gaussian Vector]]

>[!important] Dimension-Free Concentration
>An **important feature** of the *Gaussian concentration inequalities* is that the upper bound **does not depend on the dimension $n$**. 
>
>This inequality has served as a benchmark for the development of *concentration inequalities* during the last three decades.

### Logarithmic Sobolev Inequality


![[Logarithmic Sobolev Inequality for Gaussian Random Variables#^928b56]]

- [[Logarithmic Sobolev Inequality for Gaussian Random Variables]]

>[!important] 
>The **Gaussian logarithmic Sobolev inequality** has a *constant* $C = 2$ that is **independent of dimension** $n$:
>$$
>\text{Ent}_{\mathcal{N}}(f^2) \le C\,\int_{\mathbb{R}^n} \lvert \nabla f \rvert^2 \,d\mathcal{N}  
>$$
>
>This **dimension-free property** is related to the **concentration of Gaussian measure** $\mathcal{N}.$
>
>As a consequence, this inequality can be extended to **functions** of *Gaussian measure* on **infinite dimensional space**, such as Gibbs measure, *Gaussian process* etc.


![[Bobkov Inequality#^74be32]]


- [[Bobkov Inequality]]

### Isoperimetry Problem

![[Gaussian Isoperimetric Function#^fcd238]]

- [[Gaussian Isoperimetric Function]]

![[Gaussian Isoperimetric Theorem#^66aeb2]]

- [[Gaussian Isoperimetric Theorem]]


![[Gaussian Concentration Theorem#^e48f3e]]


- [[Gaussian Concentration Theorem]]

### Gaussian Transportation Cost Inequality

![[Talagrand Gaussian Transportation Inequality#^dafd3d]]

- [[Talagrand Gaussian Transportation Inequality]]
- [[Wasserstein Distance]]






-----------
##  Recommended Notes and References


- [[Borel sigma Field]]
- [[Lebesgue Measure]]
- [[Absolute Continuity for Measures]]
- [[Radon-Nikodym Derivative]]
- [[Push-forward Measure and Push-forward Operator]]

- [[Gaussian Random Variable]]
- [[Gaussian Random Vector]]
- [[Gaussian Random Function]]

- [[Log-Concave and Log-Convex Function]]
- [[Logarithmic Sobolev Inequality for Gaussian Random Variables]]

- [[Borel Measure]]
- [[Inner Regularity]]
- [[Kolmogorov Extension Theorem in Infinite Product Space]]