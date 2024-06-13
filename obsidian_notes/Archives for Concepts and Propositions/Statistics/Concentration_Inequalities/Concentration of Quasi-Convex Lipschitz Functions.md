---
tags:
  - concept
  - statistics/concentration_inequality
  - math/convex_analysis
keywords:
  - quasi_convex_function
  - lipschitz_continuous_function
  - concentration
topics:
  - concentration_inequality
  - convex_analysis
name: Concentration of Quasi-Convex Lipschitz Functions
date of note: 2024-05-30
---

## Concept Definition

>[!important]
>**Name**: Concentration of Quasi-Convex Lipschitz Functions

>[!important] Concentration of Quasi-Convex Lipschitz Functions
>Let  $Z:= (Z_1 \,{,}\ldots{,}\, Z_{n})$ be **independent** random variables taking values in the **interval** $[0, 1]$.
>
>Let $f : [0, 1]^n \to \mathbb{R}$ be 
>- a **quasi-convex function**; that is
>$$
> \begin{align*}
> \set{z: f(z) \le s} \text{ is convex set for all }s \in \mathbb{R}. 
> \end{align*}
>$$  
>- Moreover, $f$ is **Lipschitz function** satisfying
>$$
> \begin{align*}
> |f(x) - f(y)| &\le \lVert x- y \rVert \quad \text{for all }x, y \in [0, 1]^n.
> \end{align*}
>$$
>
> 
> Then $X = f(Z_1 \,{,}\ldots{,}\, Z_{n})$ satisfies, for all $t > 0$,
>$$ 
> \begin{align}
> \mathcal{P}\set{f(Z)  \ge  \text{med}(f(Z)) + t } &\le 2\exp\left( - \frac{t^2}{4} \right), \\
> \mathcal{P}\set{f(Z)  \le \text{med}(f(Z)) -t } &\le 2\exp\left( - \frac{t^2}{4} \right). \nonumber
> \end{align}
>$$ 

^35c303

- [[Epigraph or Supergraph of Function]]
- [[Convex Set]]
- [[Lipschitz Continuous Function]]

## Explanation


## Proof

>[!info]
>For some $s \in \mathbb{R}$, define the **epigraph** of $f$ as $$A_s = \set{z : f(z) \le s} \subset [0, 1]^n.$$  
>
>Because of **quasi-convexity**, $A_s$ is *convex*.  

>[!info]
>By the **Lipschitz property** and [[Convex Distance#Comparison to Distance to Convex Set]], for all $z \in [0, 1]^n$,
>$$
> \begin{align*}
> f(z) \le s +  d(z, A) \le s + d_{T}(z, A).
> \end{align*}
>$$  

>[!info]
>For $t$-Blowup set
>$$
>A_{s,t} := \left\{z: d_{T}(z, A_{s}) < t \right\} \subseteq \left\{ z\in A_{s}: f(z) \le s + t \right\}
>$$


>[!info]
>So by **convex distance inequality**,  
>$$
>\mathcal{P}(A_{s})\;\mathcal{P}\left(A_{s,t}^c \right) \le \exp \left( - \frac{t^2}{4} \right)
>$$
>or
>$$
> \begin{align*}
> \mathcal{P}\set{f(Z) \le s}\; \mathcal{P}\set{f(Z) \ge s + t} &\le \exp \left( - \frac{t^2}{4} \right)
> \end{align*}
>$$  

- [[Talagrand Convex Distance Inequality]]

>[!info]
>Take 
>- $$s = \text{med}(f(Z))$$ to get the **upper tail** inequality and 
>- $$s = \text{med}(f(Z)) - t$$ to get the **lower tail** inequality.
>  
>Q.E.D.  




-----------
##  Recommended Notes and References

- [[Epigraph or Supergraph of Function]]
- [[Convex Set]]
- [[Convex Function]]
- [[Lipschitz Continuous Function]]

- [[Talagrand Convex Distance Inequality]]


- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[Concentration Inequalities by Boucheron]]