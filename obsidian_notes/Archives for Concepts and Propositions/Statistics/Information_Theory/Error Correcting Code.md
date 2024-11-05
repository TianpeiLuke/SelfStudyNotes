---
tags:
  - concept
  - math/information_theory
  - statistics/concentration_inequality
keywords:
  - error_correcting_code
topics:
  - information_theory
  - concentration_inequality
name: Error Correcting Code
date of note: 2024-06-01
---

## Concept Definition

>[!important]
>**Name**: Error Correcting Code

>[!important] Definition
>Fix integers $k$, $n$ and $r$. Two maps
>$$
> \begin{align*}
> E : \set{0, 1}^k \to \set{0, 1}^n \quad \text{ and } \quad D: \set{0, 1}^n \to \set{0, 1}^k
> \end{align*}
>$$  
>are called **encoding** and **ecoding maps** that can **correct $r$ errors** if we have
>$$
> \begin{align*}
> D(y) = x
> \end{align*}
>$$  
>for every word $x \in  \set{0, 1}^k$ and every string $y \in  \set{0, 1}^n$ that *differs from* $E(x)$ in *at most $r$ bits*. 
>
>- The *encoding map* $E$ is called an **error correcting code**; 
>- its image $$E(\set{0, 1}^k)$$ is called a **codebook** (and very often the image itself is called **the error correcting code**; 
>- the elements $$E(x)$$ of the image are called **codewords**.

- [[Auto-Encoder and Stochastic Auto-Encoder]]

## Explanation





>[!important] Proposition
>Assume that positive integers $k$, $n$ and $r$ are such that
>$$
> \begin{align}
> \log_2 \mathcal{P}(\set{0, 1}^n, d_H, 2r) \ge k. 
> \end{align}
>$$ 
> where $d_H$ is the **Hamming distance**. 
> 
> Then there exists an **error correcting code** that *encodes* $k$-bit strings *into* $n$-bit
> strings and can **correct $r$ errors**.

- [[Packing Number of Metric Space]]

>[!important] Theorem
>Assume that positive integers $k$, $n$ and $r$ are such that
>$$
> \begin{align}
> n \ge k + 2r\log_2\left(\frac{en}{2r}\right). 
> \end{align}
>$$ 
>
>
> Then there exists an **error correcting code** that *encodes* $k$-bit strings *into* $n$-bit strings and can **correct $r$ errors**.

## Metric Entropy as Error Correct Code 

>[!important] Proposition
>Let $(T,d)$ be a *metric space*, and consider a subset $K \subset T$. 
>
>Let $C(K, d, \epsilon)$ denote the **smallest number of bits** *sufficient* to *specify every point* $x\in K$ with *accuracy* $\epsilon$ in the metric $d$.
>
>Then
>$$
>\begin{align*}
> \log_{2}\mathcal{N}(K, d, \epsilon) \le C(K, d, \epsilon) \le \log_{2}\mathcal{N}(K, d, \epsilon / 2).
\end{align*}
>$$ 

^9810bb

- [[Metric Entropy of Metric Space]]



-----------
##  Recommended Notes and References


- [[Shannon Entropy]]
- [[Mutual Information]]

- [[Metric Entropy of Metric Space]]


- [[Elements of Information Theory by Cover]]
- [[High Dimensional Probability An Introduction by Vershynin]]