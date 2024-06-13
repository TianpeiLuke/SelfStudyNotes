---
tags:
  - concept
  - math/convex_analysis
keywords:
  - convex_function
topics:
  - convex_analysis
name: Convex Function
date of note: 2024-05-15
---

## Concept Definition

>[!important]
>**Name**: Convex Function

>[!important] Definition
>Let $X$ be a *convex* subset of a real vector space. Let $f: X \to \mathbb{R}$ be a function. 
>
>$f$ is called **convex function** if for all $x, y \in X$, and $\theta$ with $\theta\in [0, 1]$,
>$$
>f(\theta x + (1- \theta) y) \le \theta f(x) + (1- \theta) f(y).
>$$

>[!important] Definition
>The **effective domain** of a convex function is denoted as 
>$$
>\text{dom}(f) := \{ x: f(x) < + \infty \}
>$$


>[!important] Definition
>A function $f$ is **strictly convex** if *strict inequality* holds above whenever $x \neq y$ and $0 < \theta < 1$.

>[!important] Definition
>We say $f$ is **concave** if $−f$ is *convex*, and **strictly concave** if $−f$ is *strictly convex*.

## Alternative Definition


>[!important] Alternative Definition
>Let $X$ be a subset of a real vector space. Let $f: X \to \mathbb{R}$ be a function. 
>
>The function $f$ is a **convex function** if its *epigraph* 
>$$
>\text{epi}(f) = \{(x, t): f(x) \le t, \quad x\in X, t \in \mathbb{R}  \}
>$$ 
>is a **convex set**.


- [[Epigraph or Supergraph of Function]]

>[!info]
>The effective domain of a convex function is the *projection of the epigraph* $\text{epi}(f)$ on $X$.
>$$
>\text{dom}(f) := \{x: \exists t, \; (x, t) \in \text{epi}(f)  \}.
>$$

>[!important] Definition
>The **dimension** of convex function $f$ is defined as the dimensional of the effective domain of the convex function.
>$$
>\text{dim}(f) := \text{dim}(\text{dom}(f))
>$$

>[!important] Definition
>A convex function is said to be **proper** if its epigraph is *non-empty* and contains *no vertical lines*, i.e.
>$$
>\exists x\in \text{dom}(f), \;\;  f(x) < + \infty
>$$ 
>and
>$$
>\forall x \in \text{dom}(f), \;\;  f(x) > - \infty
>$$


>[!info]
>A convex function $f$ is proper if and only if the effective domain $C= \text{dom}(f)$ is *non-empty* and *the restriction* of $f$ to its *effective domain* is *finite*. 



## Explanation


>[!important]
>Geometrically, this inequality means that **the line segment** between $(x, f(x))$ and $(y, f (y))$, which is *the chord* from x to y, **lies above the graph of $f$.**

>[!info]
>The *domain* of convex function $\text{dom}(f)$  must be a **convex set**.

## Extended-value 

>[!important] Definition
>We can extend the definition of $f$ beyond its effective domain as
>$$
>\begin{align}
>\widetilde{f}(x) = \left\{ \begin{array}[cc]
>f(x) & x \in \text{dom}(f)\\
>+\infty & x \not\in \text{dom}(f)
\end{array}  \right. 
\end{align}
>$$

## Examples

>[!example] Convex or Concave Functions
>- exponential function is **convex** function
>  $$f(x)  = e^{\alpha x}$$
>-   power function is **concave** function, for $\alpha \ge 1$ or $\alpha  \le 0$
>  $$f(x) = x^{\alpha}$$
>    it is **concave** for $\alpha \in [0, 1]$
>- power of absolute value is **concave** function, for $p \ge 1$,
>  $$f(x) = |x|^p$$    
>- logarithm is **concave** function for $x > 0$, 
>  $$f(x) = \log(x)$$  
>- *negative entropy* is **convex** function for $x >0$
>  $$f(x) = x \log(x)$$
>- every *norm* is **convex** function [[Norm and Normed Space]]
>  $$f(x) = \lVert x \rVert $$
>- max function is **convex** function
>  $$f(x) = \max_{i=1 \,{,}\ldots{,}\,n}\{ x_{i} \}$$
>- *log-sum-exp* function is **convex** function: [[Variational Formula for Kullback-Leibler Divergence]]
>  $$f(x) = \log \left(\sum_{i=1}^n \exp(x_{i})\right)$$
>  This function is also called **the soft-max function**
>  $$ \max_{i=1 \,{,}\ldots{,}\,n}\{ x_{i} \} \le \log \left(\sum_{i=1}^n \exp(x_{i})\right) \le \max_{i=1 \,{,}\ldots{,}\,n}\{ x_{i} \} + \log(n)$$
>- *quadratic over linear function* is **convex** function over $\mathbb{R} \times \mathbb{R}_{+}$
>  $$f(x, y) = \frac{x^2}{y}$$
>- *geometric mean* is **concave** function on $\mathbb{R}_{+}^n$  
>  $$f(x) = \left(\prod_{i=1}^n x_{i}\right)^{1/n}$$
>- *log-determinant* function is **concave** function on $\mathcal{S}_{+}^n$ the space of *positive definite matrices* of dimension $\frac{n(n+1)}{2}$. 
>$$f(\boldsymbol{X}) = \log\det(\boldsymbol{X})$$   

>[!example]
>For symmetric matrix $\boldsymbol{X} \in \mathcal{S}^{n}$, the **largest eigen-value** is **convex** function of $\boldsymbol{X}$, i.e.
>$$
>\lambda_{max}(\boldsymbol{X}) = \sup\left\{\boldsymbol{z}^T\boldsymbol{X}\boldsymbol{z}: \lVert \boldsymbol{z} \rVert_{2} = 1    \right\}
>$$

>[!important] Proposition
>Let $C$ be a nonempty *convex set* and $f$ is *convex* in $(x, y)$, then the function 
>$$
>g(x) = \inf_{y \in C}f(x, y)
>$$
>is a **convex** function in $x$.

>[!example] Projection on Convex Set
>Let $C$ be a nonempty *convex set* and $f(x, y) = \lVert x - y \rVert$, then the function 
>$$
>g(x) = \inf_{y \in C}\lVert x - y \rVert
>$$
>is a **convex** function in $x$.

>[!example] 
>Given a positive semi-definite matrix
>$$
>\left[\begin{array}[cc]  \\
>\boldsymbol{A} & \boldsymbol{B} \\ 
>\boldsymbol{B}^T & \boldsymbol{C}
\end{array}\right] \in \mathcal{S}_{+}^n,
>$$
>we can expressed it in terms of the *quadratic form*
>$$
>f(\boldsymbol{x}, \boldsymbol{y}) := \boldsymbol{x}^T\boldsymbol{A}\boldsymbol{x} + 2 \boldsymbol{x}^T\boldsymbol{B}\boldsymbol{y} + \boldsymbol{y}^T\boldsymbol{C}\boldsymbol{y}
>$$
>being a **convex** function in $(\boldsymbol{x}, \boldsymbol{y})$.
>
>Then 
>$$
>g(\boldsymbol{x}) := \inf_{\boldsymbol{y}}f(\boldsymbol{x}, \boldsymbol{y}) = \boldsymbol{x}^T \left(\boldsymbol{A} - \boldsymbol{B}\boldsymbol{C}^{\dagger}\boldsymbol{B}^T\right) \boldsymbol{x}
>$$
>where $\boldsymbol{C}^{\dagger}$ is the *pseudo-inverse* of $\boldsymbol{C}.$
>
>$g(\boldsymbol{x})$ is **convex** according to above proposition. By second-order condition of convexity, 
>$$
>\boldsymbol{A} - \boldsymbol{B}\boldsymbol{C}^{\dagger}\boldsymbol{B}^T \succeq \boldsymbol{0}
>$$
>is a *positive semi-definite matrix*.  For $\boldsymbol{C}$ invertible, the term is called **the Schur complement** of $\boldsymbol{C}$ in joint matrix
>$$
>\left[\begin{array}[cc]  \\
>\boldsymbol{A} & \boldsymbol{B} \\ 
>\boldsymbol{B}^T & \boldsymbol{C}
\end{array}\right].
>$$



-----------
##  Recommended Notes and References

- [[Operations that Preserve Convexity]]
- [[Jensen Inequality]]

- [[Convex Optimization by Boyd]]
- [[Convex Analysis by Rockafellar]]