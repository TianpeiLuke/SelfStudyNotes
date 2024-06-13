---
tags:
  - concept
  - statistics/concentration_inequality
  - math/optimal_transport
  - math/information_theory
keywords:
  - transportation_inequality_talagrand
topics:
  - concentration_inequality
  - optimal_transport
  - information_theory
name: Talagrand Gaussian Transportation Inequality
date of note: 2024-05-30
---

## Concept Definition

>[!important]
>**Name**: Talagrand's Gaussian Transportation Inequality

>[!important]  Talagrand's Gaussian Transportation Inequality
>Let $\mathcal{N}$ be be the **standard Gaussian probability measure** on $\mathbb{R}^n$, and let $\mathcal{Q}$ be a probability measure *absolutely continuous* with respect to $\mathcal{N}$, $$\mathcal{Q} \ll \mathcal{N}.$$
>
>Define two random vectors as below:
>-  $X = (X_1 \,{,}\ldots{,}\, X_n) \sim \mathcal{N}$
>- $Y = (Y_1 \,{,}\ldots{,}\, Y_n) \sim \mathcal{Q}$  
>  
>Then
>$$
> \begin{align}
> \mathcal{W}_{2, d}(\mathcal{Q}, \mathcal{N}) := \sqrt{\min_{\pi \in \Pi(\mathcal{Q}, \mathcal{N})}\sum_{i=1}^n  \mathbb{E}_{\pi}\left[ (Y_i - X_i)^2 \right]} &\le \sqrt{2 \mathbb{KL}\left( \mathcal{Q} \left\|\right. \mathcal{N} \right)}
> \end{align}
>$$ 
>equivalently, 
> $$
> \begin{align} 
> \min_{\pi \in \Pi(\mathcal{Q}, \mathcal{N})}\sum_{i=1}^n  \mathbb{E}_{ \pi }\left[ (Y_i - X_i)^2 \right] &\le 2 \mathbb{KL}\left( \mathcal{Q} \left\|\right. \mathcal{N} \right)
> \end{align}
>$$ 
>where $$\Pi(\mathcal{Q}, \mathcal{N}) := \left\{ \pi \in \mathcal{M}(\mathcal{X}^n \times \mathcal{X}^n): \; Y_{*}\pi = \mathcal{Q},\, X_{*}\pi = \mathcal{N} \right\}. $$

^dafd3d


- [[Marton Transportation Inequality]]
- [[Wasserstein Distance]]
- [[Gaussian Measure]]

## Explanation



## Gaussian Concentration Theorem

>[!important]
>Talagrand's **Gaussian transportation inequality** implies the **Tsirelson-Ibragimov-Sudakov inequality** (i.e. the *dimension-free concentration* of *Lipschitz function* of Gaussian vectors)  
>
 >We proved based on the **Gaussian logarithmic Sobolev inequality** and **Herbst's argument.**


- [[Concentration of Lipschitz Function of Gaussian Vector#^275d78]]
- [[Herbst Argument]]
- [[Logarithmic Sobolev Inequality for Gaussian Random Variables]]



>[!info] 
> Assume that $f: \mathbb{R}^n \to \mathbb{R}$ is a **Lipschitz function** with respect to *Euclidean distance*, that is, for all $x, y \in \mathbb{R}^n$,
> $$
> \begin{align*}
> f(y) - f(x) \le L \sqrt{\sum_{i=1}^n (x_i - y_i)^2}
> \end{align*}
>$$ 
> 
>Then, by *Jensen's inequality*, for every **coupling** $\pi \in \Pi(\mathcal{Q}, \mathcal{P})$, one has
>$$
> \begin{align*}
>  \mathbb{E}_{ \mathcal{Q} }\left[ f(Y) \right] -  \mathbb{E}_{ \mathcal{P} }\left[ f(X) \right] &=   \mathbb{E}_{ \pi }\left[  f(Y) - f(X)\right]  \\
> &\le L  \mathbb{E}_{ \pi }\left[\left( \sum_{i=1}^n (X_i - Y_i)^2 \right)^{1/2}  \right]  \\
> &\le L \left( \sum_{i=1}^n  \mathbb{E}_{ \pi }\left[(X_i - Y_i)^2  \right]  \right)^{1/2}
> \end{align*}
>$$
>the last inequality is due to Jenson's inequality.
>
>Now, taking infimum over $\pi \in \Pi(\mathcal{Q}, \mathcal{P})$ on both sides, we have 
>$$
> \begin{align*}
>\mathbb{E}_{ \mathcal{Q} }\left[ f(Y) \right] -  \mathbb{E}_{ \mathcal{P} }\left[ f(X) \right] \le L\; \mathcal{W}_{2}(\mathcal{Q}, \mathcal{P}) &\le \sqrt{2 L^2  \mathbb{KL}\left( \mathcal{Q} \left\|\right. \mathcal{P} \right)}
> \end{align*}
>$$  
>where the last inequality is due to Talagrand's Gaussian Transportation Inequality. 
>
>By transportation lemma, we show that $$f(X) -  \mathbb{E}_{ \mathcal{P} }\left[f(X)  \right]$$ is **sub-Gaussian distributed** with *parameter* $L^2$. This implies the **Gaussian concentration inequality**.
> 

- [[Gaussian Concentration Theorem]]



-----------
##  Recommended Notes and References

- [[Talagrand Convex Distance Inequality]]
- [[Gaussian Concentration Theorem]]
- [[Gaussian Isoperimetric Theorem]]

- [[Gaussian Isoperimetric Function]]

- [[Marton Transportation Inequality]]
- [[Wasserstein Distance]]

- [[Gaussian Measure]]
- [[Concepts and Theorems of Optimal Transport]]

- [[Concentration Inequalities by Boucheron]]