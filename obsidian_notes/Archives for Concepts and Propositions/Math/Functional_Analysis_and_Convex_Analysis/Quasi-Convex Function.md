---
tags:
  - concept
  - math/convex_analysis
keywords:
  - quasi_convex_function
topics:
  - convex_analysis
name: Quasi-Convex Function
date of note: 2024-06-18
---

## Concept Definition

>[!important]
>**Name**: Quasi-Convex Function

>[!important] Definition
>A function $f: \mathbb{R}^{n} \to \mathbb{R}$ is called **quasi-convex** if 
>- the domain of $f$, $\text{dom}(f)$, is a *convex set*; and
>- the *sub-level* set $$S_{\alpha} := \left\{ x: f(x) \le \alpha \right\}$$ is *convex* for each $\alpha >0.$

- [[Convex Function]]
- [[Convex Set]]

>[!important] Definition
>A function $f: \mathbb{R}^{n} \to \mathbb{R}$ is called **quasi-concave** if 
>- $-f$ is *quasi-convex.*

### Direct Definition


>[!important] Definition
>A function $f: \mathbb{R}^{n} \to \mathbb{R}$ is called **quasi-convex** if 
>- the domain of $f$, $\text{dom}(f)$, is a *convex set*; and
>- for $x, y \in \text{dom}(f)$, $0 \le \alpha \le 1$,  $$f(\alpha x + (1- \alpha) y) \le \max\left\{ f(x), f(y) \right\} $$

>[!important] Definition
>A function $f: \mathbb{R}^{n} \to \mathbb{R}$ is called **strictly quasi-convex** if 
>- for $x \neq y \in \text{dom}(f)$, $0 < \alpha < 1$,  $$f(\alpha x + (1- \alpha) y) < \max\left\{ f(x), f(y) \right\}.$$

>[!important] Definition
>A function $f: \mathbb{R}^{n} \to \mathbb{R}$ is called **quasi-concave** if 
>- the domain of $f$, $\text{dom}(f)$, is a *convex set*; and
>- for $x, y \in \text{dom}(f)$, $0 \le \alpha \le 1$,  $$f(\alpha x + (1- \alpha) y) \ge \min\left\{ f(x), f(y) \right\} $$

>[!important] Definition
>A function $f: \mathbb{R}^{n} \to \mathbb{R}$ is called **strictly quasi-concave** if 
>- for $x \neq y \in \text{dom}(f)$, $0 < \alpha < 1$,  $$f(\alpha x + (1- \alpha) y) > \min\left\{ f(x), f(y) \right\}.$$



## Explanation

>[!info]
>Every **convex** function is **quasi-convex**.



>[!info]
>$$
>\text{convex function } \implies \text{log-convex function } \implies \text{quasi-convex function } 
>$$

- [[Convex Function]]
- [[Log-Concave and Log-Convex Function]]



-----------
##  Recommended Notes and References


- [[Epigraph or Supergraph of Function]]
- [[Convex Function]]
- [[Log-Concave and Log-Convex Function]]