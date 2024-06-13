---
tags:
  - concept
  - statistics/concentration_inequality
keywords:
  - bounded_difference_inequality
topics:
  - statistics
name: Bounded Difference Inequality
date of note: 2024-05-07
---

## Concept Definition

>[!important]
>**Name**: Bounded Difference Inequality or **McDiarmid's Inequality**

>[!important] Definition
>Given vectors $x, x' \in \mathcal{X}^n$ and an index $k \in \set{1, 2 \,{,}\ldots{,}\, n}$, we define a new vector $x^{(-k)} \in \mathcal{X}^n$ via
>$$
> \begin{align*}
> x_j^{(-k)} &= \left\{\begin{array}{cc}
> x_j & j \neq k\\
> x_k'& j = k
> \end{array}
> \right.
> \end{align*}
>$$ 
> With this notation, we say that $f: \mathcal{X}^n \to \mathbb{R}$ satisfies **the bounded difference property** with parameters $(L_1 \,{,}\ldots{,}\, L_n)$ if, for each index $k = 1, 2 \,{,}\ldots{,}\, n$,
> $$
> \begin{align}
> \lvert f(x) - f(x^{(-k)}) \rvert \le L_k, \quad\text{ for all }x, x' \in \mathcal{X}^n.
> \end{align}
>$$ 


- [[Sub-Gaussian Random Variable]]


>[!important]  Bounded Difference Inequality (McDiarmid's Inequality)
>Suppose that $f$ satisfies **the bounded difference property** with parameters $(L_1 \,{,}\ldots{,}\, L_n)$ and that the random vector $X = (X_1, X_2 \,{,}\ldots{,}\, X_n)$ has **independent components.** 
>
>Then
>$$
> \begin{align}
> \mathcal{P}\left\{ \lvert f(X) - \mathbb{E}\left[ f(X) \right] \rvert \ge t \right\}  &\le  2 \exp \left( - \frac{2 t^2}{ \sum_{k=1}^{n}L_k^2}\right).
> \end{align}
>$$ 

- [[Azuma-Hoeffding Inequality]]
- [[Martingale Differences]]
## Proof

>[!info]
>Consider the associated **martingale difference sequence**
>$$
> \begin{align*}
> D_k :=  \mathbb{E}\left[ f(X) | X_1 \,{,}\ldots{,}\, X_k \right] - \mathbb{E}\left[ f(X) | X_1 \,{,}\ldots{,}\, X_{k-1} \right].
> \end{align*}
>$$
>We claim that $D_k$ lies in **an interval** of **length at most $L_k$** *almost surely*. Then the bounded difference inequality is the result of applying [[Azuma-Hoeffding Inequality]].

>[!info]
>In order to prove this claim, define two *random variables*
>$$
> \begin{align*}
> A_k &:= \inf_x \left\{ \mathbb{E}\left[ f(X) | X_1 \,{,}\ldots{,}\, X_{k-1}, x \right]  \right\} - \mathbb{E}\left[ f(X) | X_1 \,{,}\ldots{,}\, X_{k-1} \right] \\
> B_k &:= \sup_{x} \left\{ \mathbb{E}\left[ f(X) | X_1 \,{,}\ldots{,}\, X_{k-1}, x \right]  \right\} - \mathbb{E}\left[ f(X) | X_1 \,{,}\ldots{,}\, X_{k-1} \right].
> \end{align*}
>$$ 
>On one hand, we have
>$$
> \begin{align*}
> D_k - A_k &=  \mathbb{E}\left[ f(X) | X_1 \,{,}\ldots{,}\, X_k \right] - \inf_x \left\{ \mathbb{E}\left[ f(X) | X_1 \,{,}\ldots{,}\, X_{k-1}, x \right]  \right\},
> \end{align*}
>$$ 
> so that $D_k \ge  A_k$ *almost surely*. 
> 
> A similar argument shows that $D_k \le B_k$ *almost surely.* Thus $D_{k} \in [A_{k}, B_{k}]$, almost surely.
 
>[!info] 
> We now need to show that $B_k - A_k \le L_k$ *almost surely*. Observe that by the **independence** of $\set{X_k}^n_{k=1}$,  $\{\mathbb{E}\left[ f(X) | X_1 \,{,}\ldots{,}\, X_k \right], k \ge 0\}$ forms a *martingale.* Thus, the martingtale equation 
>$$
> \begin{align*}
> \mathbb{E}\left[ f(X) | x_1 \,{,}\ldots{,}\, x_k \right]&= \mathbb{E}_{k+1}\left[ f(X) | x_1 \,{,}\ldots{,}\, x_k, X_{k+1} \,{,}\ldots{,}\, X_{n} \right],\text{ for any }(x_1 \,{,}\ldots{,}\, x_k),
> \end{align*}
>$$  
>where 
> $$\mathbb{E}_{k+1}\left[ \cdot \right] := \mathbb{E}_{X_{k+1} \,{,}\ldots{,}\, X_{n} }\left[\cdot\right]$$ denote the expectation *over* $(X_{k+1} \,{,}\ldots{,}\, X_{n})$.
> 
> Consequently, we have
>$$
> \begin{align*}
> B_k - A_k &=  \sup_{x} \mathbb{E}_{k+1}\left[f(X_1 \,{,}\ldots{,}\, X_{k-1}, x, X_{k+1} \,{,}\ldots{,}\, X_n)\right]  \\
> &\quad - \inf_x  \mathbb{E}_{k+1}\left[f(X_1 \,{,}\ldots{,}\, X_{k-1}, x, X_{k+1} \,{,}\ldots{,}\, X_n)\right] \\
> &\le  \sup_{x,y}\left\{\mathbb{E}_{k+1}\left[f(X_{1 \,{,}\ldots{,}\,k-1}, x, X_{k+1, \,{,}\ldots{,}\,n})\right] - \mathbb{E}_{k+1}\left[f(X_{1 \,{,}\ldots{,}\,k-1}, y, X_{k+1, \,{,}\ldots{,}\,n})\right] \right\}\\
> &\le L_k,
> \end{align*}
>$$ 
> using **the bounded differences assumption**. Thus, the variable $D_k$ lies within an interval of length $L_k$  *almost surely*.  Q.E.D.


## Explanation


## Concentration of Measure on Hamming Metric Space

>[!important] Concentration of Measure on Hamming Metric Space
>For all $t > 0$, we have the **concentration of measure** in **Hamming metric space**:
> $$
> \begin{align}
> \mathcal{P}(A)\;\mathcal{P}\left\{ d_{H}(x, A) \ge t \right\}  \le \min\left\{ \mathcal{P}(A)\,,\, \mathcal{P}\set{d_{H}(x, A) \ge t} \right\}  \le  \exp \left(-\frac{t^2}{2n}\right) 
> \end{align}
>$$ 

- [[Concentration of Measure on Hamming Metric Space]]

>[!important]
>Note that any  function with **bounded difference property** is **Lipschitz function** with respect to **Hamming distance**.

>[!info]
>$$
>f(x^n) - f(y^n) = \sum_{i=1}^{n}(f(x_{(i-1)}) - f(x_{(i)}) )
>$$
>where $F_{i}\,x^n$ as replacing $i$-th component $x_{i}$ with $y_{i}$, and
>$$
>x_{(0)}^n = x^n;  \quad x_{(i)}^n = F_{i}\,x_{(i-1)}^n, \;\; i=1, \ldots, n
>$$
>That is, $x_{(i)}$ is replicate of $x_{(i-1)}$ except for $i$-th component, which is replaced by $y_i$. And  $x_{(n)} = y^n$. 


>[!important]
> Therefore, **the bounded difference inequality** can be seen as an **isoperimetry inequality** for **Lipschitz function** with respect to **Hamming distance**.
> $$
> \begin{align*}
>  \mathcal{P}\left\{ f(Z) - \mathbb{E}_{\mathcal{P}}\left[  f(Z) \right] \ge t \right\}  &\le \exp \left(-\frac{2t^2}{n}\right)
> \end{align*}
>$$ 

- [[Lévy Inequalities]]

## Generalization





-----------
##  Recommended Notes and References

- [[Hoeffding Inequality]]
- [[Martingale Differences]]
- [[Martingale]]

- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Probability An Introduction by Vershynin]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]