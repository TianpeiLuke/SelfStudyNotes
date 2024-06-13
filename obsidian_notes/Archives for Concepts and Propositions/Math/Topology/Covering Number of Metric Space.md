---
tags:
  - concept
  - math/topology
  - math/functional_analysis
  - math/stochastic_process
  - statistics/concentration_inequality
keywords:
  - covering_number
  - epsilon_cover
topics:
  - topology
  - functional_analysis
  - stochastic_process
  - concentration_inequality
name: Covering Number of Metric Space
date of note: 2024-05-31
---

## Concept Definition

>[!important]
>**Name**: Covering Number of Metric Space

![[epsilon-Cover and epsilon-Net of Metric Space#^b37cb4]]


>[!important] Definition
>The **smallest possible cardinality** of an *$\epsilon$-net* of $K$ is called  **the covering number of $K$** and is denoted $$\mathcal{N}(K, d, \epsilon).$$ 
>
>Equivalently, $\mathcal{N}(K, d, \epsilon)$ is the *smallest number* of *closed balls* with centers in $K$ and radii $\epsilon$ whose *union covers* $K$.

^4e5f78

- [[epsilon-Cover and epsilon-Net of Metric Space]]
- [[Pre-Compactness]]
- [[Lebesgue Number Lemma in Compact Metric Space]]
- [[Metric Space]]

## Explanation


>[!important] Proposition
>Let  $(T, d)$ be a **complete metric space** and $K \subset T$ be a subset. 
>
>$K$ is **precompact** (i.e. the *closure of* $K$ is *compact*) *if and only if* for every $\epsilon >0$,
>$$
> \begin{align*}
> \mathcal{N}(K, d, \epsilon) < \infty.
> \end{align*}
>$$ 

- [[Pre-Compactness]]

>[!important]
> Thus we can think about the **magnitude** $\mathcal{N}(K, d, \epsilon)$ as a  **quantitative measure** of **compactness** of $K$.

- [[Compactness]]

## Properties

>[!important] Proposition
>Let  $(T, d)$ be a **complete metric space** and $K \subset T$ be a subset. 
>
>The **covering number** is **non-increasing** in $\epsilon$. That is, for any $\epsilon' > \epsilon$
>$$ 
> \begin{align*}
> \mathcal{N}(K, d, \epsilon) \ge \mathcal{N}(K, d, \epsilon').
> \end{align*}
>$$  

>[!info]
> Typically, the covering number **diverges** as $\epsilon \to 0_{+}$, and of interest to us is the **growth rate** of **covering number** on a *logarithmic scale*.
>$$
>\log \mathcal{N}(K, d, \epsilon)
>$$

- [[Metric Entropy of Metric Space]]

## Equivalence of Covering Number and Packing Number

>[!important] Theorem 
>Let  $(T, d)$ be a **complete metric space** and $K \subset T$ be any subset. 
>
>For any  $\epsilon > 0$, we have
>$$
> \begin{align}
> \mathcal{P}(K, d,  2\epsilon) \le \mathcal{N}(K, d, \epsilon) \le \mathcal{P}(K, d,  \epsilon)
> \end{align}
>$$ 

- [[Packing Number of Metric Space]]

## Examples

>[!example] Covering Number in Euclidean space
>Let $K$ be a **subset of $\mathbb{R}^n$** and  $\epsilon > 0$. 
>
>Then
>$$
> \begin{align}
> \frac{m(K)}{m(\epsilon B_2^n)} \le \mathcal{N}(K, \epsilon) \le \mathcal{P}(K, \epsilon) \le \frac{m(K + (\epsilon/2) B_2^n)}{m((\epsilon/2) B_2^n)}  
> \end{align}
>$$
> 
> Here $m(\cdot)$ denotes the **Lebesgue measure** on $\mathbb{R}^n$ (i.e. the **volume**), $B_2^n$ denotes the unit *Euclidean ball* $$B_{2}^n := \set{x \in \mathbb{R}^n:  \lVert x \rVert_{2} \le 1}$$ in $\mathbb{R}^n$, so $\epsilon B_2^n$  is a Euclidean ball with *radius* $\epsilon$.

- [[Isoperimetry Theorem Classical]]

>[!example] Covering Number of Unit Ball and Sphere
>The covering numbers of the **unit Euclidean ball** $B_2^n$ satisfy the following for any $\epsilon > 0$:
>$$
> \begin{align}
> \left(\frac{1}{\epsilon}\right)^n \le \mathcal{N}(B_2^n, \lVert \cdot \rVert_{2}, \epsilon)  \le \left(1+ \frac{2}{\epsilon}\right)^n  
> \end{align}
>$$
> 
> The same upper bound is true for the **unit Euclidean sphere** $\mathbb{S}^{n-1}$.
> 

- [[Concentration Function for Lebesgue Measure on Sphere]]

>[!example] Covering Number for Hamming Cube
>Let $K = \set{0, 1}^n$ be a **$n$-dimensional cube** in **Hamming metric space**. 
>
>Prove that for every integer $m \in [0, n]$, we have
>$$
> \begin{align}
> \frac{2^n}{\sum_{k=0}^m{n \choose k}}  \le \mathcal{N}(K, d_{H}, m) \le \mathcal{P}(K, d_H, m) \le \frac{2^n}{\sum_{k=0}^{\lfloor{m/2}\rfloor  }{n \choose k}}
> \end{align}
>$$ 

>[!important] Proposition
>Let  $\mathcal{F}_{L}([0,1])$ be the class of *real-valued* **$L$-Lipschitz homogeneous functions** on **unit interval $[0, 1]$**;  that is, for any $f \in \mathcal{F}_{L}$, 
>- there exists constant $L$
>  $$
>  |f(x) - f(y) | \le L \lvert x - y \rvert, \quad x, y \in [0,1], 
> $$
>- and $f(0) = 0$.
>  
>Then the **covering number** of $\mathcal{F}_L$ with respect to **supremum norm**  satisfies the following inequalities:
>$$
>  \begin{align}
>  c \exp \left(\frac{L}{\epsilon}\right) \le  \mathcal{N}(\mathcal{F}_L,  \lVert \cdot \rVert_{\infty} , \epsilon)  \le C \exp \left(\frac{L}{\epsilon}\right), 
>  \end{align}
>$$   
>for some constant $c$ and $C$ and suitably small $\epsilon >0$. 
>
>In other word, the **metric entropy** $$\log \mathcal{N}(\mathcal{F}_L,  \lVert \cdot \rVert_{\infty} , \epsilon) \asymp \left( \frac{L}{\epsilon} \right).$$

>[!info]
>The preceding example can be extended to *Lipschitz functions* on the **unit cube** in **higher dimensions**, meaning real-valued functions on $[0, 1]^n$ such that 
>$$
>  \begin{align*}
>  \lvert f(x) - f(y) \rvert  \le L \lVert x - y \rVert_{\infty} .
>  \end{align*}
>$$   
>Denote this class as $\mathcal{F}_{L}([0,1]^n)$. 
>
>The **metric entropy** of $\mathcal{F}_{L}([0,1]^n)$ 
>$$
>  \begin{align}
> \log \mathcal{N}(\mathcal{F}_L([0,1]^n)\,, \, \lVert \cdot \rVert_{\infty} \,,\, \epsilon) \asymp \left(\frac{L}{\epsilon}\right)^n 
>  \end{align}
>$$   
>
>It is worth contrasting the **exponential dependence** of *metric entropy* on the **dimension $n$**, as opposed to  *the linear dependence* that we saw earlier for simpler sets (e.g., such as **$n$-dimensional unit balls**).
>
 This is a dramatic manifestation of **the curse of dimensionality**.
> 

- [[High Dimensional Probability An Introduction by Vershynin]]





-----------
##  Recommended Notes and References

- [[Covering of Set and Open Covering of Topological Set]]
- [[epsilon-Cover and epsilon-Net of Metric Space]]
- [[Pre-Compactness]]
- [[Lebesgue Number Lemma in Compact Metric Space]]
- [[Metric Space]]


- [[High Dimensional Probability An Introduction by Vershynin]]
- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Concentration Inequalities by Boucheron]]
- [[Topology Book by Munkres]]