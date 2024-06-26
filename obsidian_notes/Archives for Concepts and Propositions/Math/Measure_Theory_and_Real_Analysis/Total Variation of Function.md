---
tags:
  - concept
  - math/real_analysis
keywords:
  - total_variation_norm
topics:
  - real_analysis
name: Total Variation as Function Norm
date of note: 2024-05-28
---

## Concept Definition

>[!important]
>**Name**: Total Variation as Function Norm

>[!important] Definition
>Let $F : \mathbb{R} \rightarrow \mathbb{R}$  be a function. 
>
>**The total variation** $\lVert F \rVert_{TV(\mathbb{R})}$ (or $\lVert F \rVert_{TV}$ for short) of $F$ is defined to be the *supremum*
>$$
> \begin{align*}
> \lVert F \rVert_{TV(\mathbb{R})} := \sup\limits_{x_0 \,{<}\ldots{<}\, x_n}\sum_{i=1}^{n}\left\lvert F(x_i) - F (x_{i-1}) \right\rvert
> \end{align*}
>$$  
>where the supremum ranges over *all finite increasing sequences* $x_0  \,{,}\ldots{,}\, x_n$ of real numbers with $n \ge 0$; this is a quantity in $[0, +\infty]$. 
>

^a2e91f

- [[Norm and Normed Space]]
- [[Lp Space]]

## Explanation


## Total Variation Norm

>[!important] Proposition
>For any functions $F, G: \mathbb{R} \rightarrow \mathbb{R}$, the total variation $\lVert \cdot \rVert_{TV(\mathbb{R})}$ satisfies the following property:
>- **Non-Negativity**: $$\lVert F \rVert_{TV(\mathbb{R})} \ge 0;$$
>- **Positive Definiteness**: $$\lVert F \rVert_{TV(\mathbb{R})} = 0$$ if and only if $F$ is *constant*.
>- **Homogeneity**: $$\lVert c\,F \rVert_{TV(\mathbb{R})} =|c|\,\lVert F \rVert_{TV(\mathbb{R})}$$ for any $c \in \mathbb{R}$.
>- **Triangle Inequality**: $$\lVert F + G\rVert_{TV(\mathbb{R})} \le \lVert F \rVert_{TV(\mathbb{R})} + \lVert G \rVert_{TV(\mathbb{R})}$$
>
>Thus $\lVert \cdot \rVert_{TV(\mathbb{R})}$ is a **norm**.

- [[Norm and Normed Space]]

## Generalization

>[!important] Definition
>Let $\Omega$ be an open subset of $\mathbb{R}^n$. Assume that $f \in L^1(\Omega)$. 
>
>The **total variation** of $f$ in $\Omega$ is defined as 
>$$
>\begin{align*}
> V(f, \Omega) := \sup\left\{ \int_{\Omega}f \;\text{div}(\phi)\, dx: \;\; \phi \in \mathcal{C}_{c}(\Omega, \mathbb{R}^n), \; \lVert \phi \rVert_{L^{\infty}(\Omega)} \le 1  \right\} 
\end{align*}
>$$
>where $\text{div}$ is the **divergence operator**, $\mathcal{C}_{c}(\Omega, \mathbb{R}^d)$ is the continuous function from $\Omega \to \mathbb{R}^d$ with *compact support*, $\lVert \cdot \rVert_{\infty}$ is the **essential supremum norm**.

- [[Divergence Operator of Vector Field on Riemannian Manifold]]
- [[Continuous Functions with Compact Support]]
- [[L-infinite Space]]

>[!important]
>If $f \in \mathcal{C}^1(\Omega)$, i.e. it is continuous differentiable, then 
>$$
>V(f, \Omega)  = \int_{\Omega}\,\lVert \nabla f \rVert dx
>$$ 



>[!info]
>The **total variation** of $f$ can be formulated as
>$$
>\int_{\Omega} \lvert Df \rvert := V(f, \Omega) 
>$$
>where $Df$ is the **weak derivative** of $f$ and it is a **finite vector-valued signed Radon measure** on $\mathscr{F}$ of $\Omega$ with 
>$$
>\int_{\Omega}f \;\text{div}(\phi)\, dx = - \int_{\Omega}\,\left\langle \phi , Df \right\rangle
>$$

- [[Weak Derivative via Tempered Distribution]]
- [[Radon Measure]]






-----------
##  Recommended Notes and References

- [[Norm and Normed Space]]
- [[Norm Topology]]
- [[Banach Space]]
- [[Lp Space]]

- [[Space of Functions with Bounded Variation]]

- [[Total Variation between Measures]]
- [[Space of Bounded Signed Measures]]

- Wikipedia [Total variation](https://en.wikipedia.org/wiki/Total_variation)