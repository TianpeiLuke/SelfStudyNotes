---
tags:
  - concept
  - math/real_analysis
keywords:
  - riemann_stieltjes_integration
topics:
  - real_analysis
name: Riemann–Stieltjes Integration
date of note: 2024-06-06
---

## Concept Definition

>[!important]
>**Name**: Riemann–Stieltjes Integration

>[!important] Definition
>Let $F: [a. b] \to \mathbb{R}$ be a **monotonically increasing** and *right-semicontinuous function* and $P = \left\{ x_{0}, x_{1} \,{,}\ldots{,}\, x_{n} \right\}$ be a *partition* of $[a,b]$. Denote $$\Delta F_{i} := F(x_{i}) - F(x_{i-1}).$$ It is clear that $\Delta F_{i} > 0.$
>
>For any *bounded function* $f: [a,b] \to \mathbb{R}$, define
>$$
>\begin{align*}
>L(f, P, F) := \sum_{k=1}^{n}m_{k}\,\Delta F_{k} 
>\end{align*}
>$$
>where 
>$$
>m_{k} = \inf\left\{ f(x): x \in [x_{k-1}, x_{k}] \right\}.
>$$
>
>Similarly,  define 
>$$
>\begin{align*}
>U(f, P, F) := \sum_{k=1}^{n}M_{k}\Delta F_{k} 
>\end{align*}
>$$
>where
>$$
>M_{k} = \sup\left\{ f(x): x \in [x_{k-1}, x_{k}] \right\}.
>$$

- [[Darboux Lower Sum and Darboux Upper Sum]]

>[!important] Definition
>Let $\mathcal{P}$ be the set of all possible partitions of $[a,b]$.
>
>The **Riemann–Stieltjes lower integral** is defined as 
>$$
>\begin{align*}
>L(f, F) := \sup\left\{L(f, P, F): P\in \mathcal{P}  \right\}
>\end{align*}
>$$
>and the **Riemann–Stieltjes upper integral** is defined as 
>$$
>\begin{align*}
>U(f, F) := \inf\left\{U(f, P, F): P\in \mathcal{P}  \right\}
>\end{align*}
>$$

>[!important] Definition 
>Let $f: [a,b] \to \mathbb{R}$ be a *bounded function* and $F: [a. b] \to \mathbb{R}$ be a **monotonically increasing** and *right-semicontinuous function* 
>
>We say that $f$ is **Riemann-Stieltjes-integrable** *with respect to* $F$ if $$L(f, F) = U(f, F).$$ We denote it as $f\in \mathcal{R}(F)$, and 
>$$
>\int_{a}^{b}f(x)\,dF(x) = U(f, F) = L(f, F)
>$$

- [[Riemann Integration]]

## Explanation

>[!important]
>We denote the **Riemann–Stieltjes lower integral** and the **Riemann–Stieltjes upper integral**  with respect to $F$ as
>$$
>U(f, F) := \overline{\int_{a}^{b}}f(x)\,dF(x), \quad L(f) := \underline{\int_{a}^{b}}f(x)\,dF(x).
>$$


## Relaxation

>[!important]
>The condition on function $F: [a,b] \to \mathbb{R}$ for the existence of *Riemann-Stieltjes integration* can be *generalized* to be all *function* of **bounded variation.**
>$$
> \begin{align*}
> \lVert F \rVert_{TV(\mathbb{R})} := \sup\limits_{x_0 \,{<}\ldots{<}\, x_n}\sum_{i=1}^{n}\left\lvert \Delta F_{i} \right\rvert < \infty
> \end{align*}
>$$  

- [[Space of Functions with Bounded Variation]]

## Riemann Integration

>[!info]
>If $F: [a,b] \to \mathbb{R}$ is **identity function**, i.e. $F(x)= x$, then $$\int_{a}^{b}f(x)\,dF(x) = \int_{a}^{b}f(x)\,dx$$

- [[Riemann Integration]]
## Criterion of Riemann Integrability

- [[Criterion of Riemann-Stieltjes Integrability]]

## Differential Function

>[!important] Proposition
>Assume $F: [a,b] \to \mathbb{R}$ is **monotonically increasing** and $F'$ is **Riemann integrable** on $[a,b]$. Suppose $f$ is **bounded** on $[a,b]$.
>
>Then $f\in \mathcal{R}(F)$ *if and only if* $f\,F' \in \mathcal{R}$. In that case, 
>$$\int_{a}^{b} f(x)\,dF(x) =  \int_{a}^{b} f(x)\,F'(x)\,dx$$


## Properties

>[!important] Proposition
>Suppose $f, g\in \mathcal{R}(F)$ on $[a,b]$ and $\alpha, \beta\in \mathbb{R}$.
>
>Then 
>- **Linearity**: $$\int_{a}^b (\alpha\,f + \beta\,g)\,dF = \alpha\,\int_{a}^b f\,dF + \beta \int_{a}^b g\,dF $$
>- **Monotonicity**: if $f \le g$ on $[a,b]$, then $$\int_{a}^b f\,dF \le \int_{a}^b g\,dF.$$
>- **Partition on Integral Region**: if $f\in \mathcal{R}(F)$ on $[a,b]$, and $c\in [a,b]$, then $f\in \mathcal{R}(F)$ on $[a,c]$ and  $f\in \mathcal{R}(F)$ on $[c,b]$. And $$\int_{a}^b f\,dF  = \int_{a}^{c} f\,dF + \int_{c}^b f\,dF.$$
>- **Boundedness**: If $f\in \mathcal{R}(F)$ on $[a,b]$ and $|f(x)| \le M$ for $x\in [a,b]$, then $$\left\lvert \int_{a}^b f\,dF  \right\rvert \le M\,(F(b) - F(a)).$$
>- **Linearity with respect to $F$**: if   $f\in \mathcal{R}(F_{1})$ and $f\in \mathcal{R}(F_{2})$, then $f\in \mathcal{R}(\alpha F_{1} + \beta F_{2})$. And $$\int_{a}^b f\,d(\alpha\,F_{1} + \beta\,F_{2}) = \alpha\,\int_{a}^b f\,dF_{1} + \beta \int_{a}^b f\,dF_{2}.$$
 

>[!important] Proposition
>Suppose $f, g\in \mathcal{R}(F)$ on $[a,b]$ and $\alpha, \beta\in \mathbb{R}$.
>
>Then 
>- **Product**: $f\,g\in \mathcal{R}(F)$.
>- **Norm**:  $|f| \in \mathcal{R}(F)$ on $[a,b]$, and $$\left|\int_{a}^b f\,dF\right| \le \int_{a}^b |f|\,dF.$$



## Integral by Parts

- [[Integration by Parts]]


-----------
##  Recommended Notes and References

- [[Introduction to Measure Theory by Tao]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]

- [[Principles of Mathematical Analysis by Rudin]] pp 122
- Abbott, S. (2015). _Understanding analysis_. Springer.