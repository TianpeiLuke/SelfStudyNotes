---
tags:
  - concept
  - math/information_theory
keywords:
  - kraft_inequality
topics:
  - information_theory
name: Kraft Inequality
date of note: 2024-08-30
---

## Concept Definition

>[!important]
>**Name**: Kraft Inequality

>[!important] Definition
>Fix some *finite set* $\Sigma$ of **symbols** (or "characters"), which we call the **alphabet**. For concreteness, we let $\Sigma = \{0,1\}$.  
>
>A **string** is a *finite sequence of symbols* from $\Sigma$; for example,  $\sigma = (0,1,1,1,0)$ is a string of *length* $5$. 
>- We denote by $|\sigma|$ **the length** of a string. 
>- The set of all *finite length strings* is denoted $\Sigma^{*}$. 


>[!important] Kraft's inequality
>If $S \subseteq \set{0,1}^{*}$ is a **prefix-free** set of *strings*, then
>$$
> \begin{align*}
> \sum_{\sigma \in S}\frac{1}{2^{|\sigma|}} \le 1
> \end{align*}
>$$ 

^9e266e

- [[Prefix-Free String]]

## Explanation





-----------
##  Recommended Notes and References


- [[Prefix-Free String]]
- [[Shannon Entropy]]
- [[Minimum Description Length]]

- [[Elements of Information Theory by Cover]] 