---
tags:
  - entry_point
  - concept
  - statistics/concentration_inequality
keywords: 
topics:
  - concentration_inequality
name: Basic Inequalities
date of note: 2024-05-11
---

## Concept Definition


### Algebra and Arithmetic Inequalties

>[!important]
>$$
>1 + x \le e^{x}
>$$

>[!important]
>$$
>\log(x)  \le x - 1, \quad x >0.
>$$

>[!important]
>$$
>h(x) = (1+x)\log(1+x) - x \ge \frac{x^2}{2(1+ x/3)}, \quad x>0
>$$

>[!important]
>$$
>- \log(1 - x) - x \le \frac{x^2}{2(1- x)}, \quad x \in (0, 1)
>$$

>[!important]
>$$
>h_{1}(x) = 1+ x - \sqrt{ 1 + 2x } \ge \frac{x^2}{2(1+ x)}, \quad x>0
>$$

>[!important]
>$$
>\sum_{i=0}^{d}{n \choose i} \le \left( \frac{ en}{d}\right)^d , \quad d \in [1, n], \; \text{ and } d, n \in \mathbb{N}
>$$




- [[Young Inequality]]

>[!important] Cauchy-Schwartz Inequality
>For any $x, y \in V$ where $V$ is an inner product space,
>$$
>\lvert \left\langle  x\,,\,y \right\rangle \rvert \le \sqrt{ \left\langle x\,,\,x \right\rangle } \sqrt{ \left\langle  y\,,\,y \right\rangle } 
>$$
>where the **equality** holds if and only if $x$ and $y$ are linearly dependent.

- [[Cauchy-Schwartz Inequality]]

>[!important] Hölder's Inequality
>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a measure space and let $p ,q \in [1, +\infty]$ with $$\frac{1}{p} + \frac{1}{q} = 1.$$
>
>Then for **all measurable real (or complex) functions** $f$ and $g$ on $\mathcal{X}$,
>$$
>\begin{align*}
> \lVert f\,g \rVert_{1} \le \lVert f \rVert_{p}\, \lVert g \rVert_{q}.   
>\end{align*}
>$$
>
>If, in addition, $p, q \in (1, +\infty)$ and $f\in L^p(\mathcal{X}, \mu)$ and $g\in L^q(\mathcal{X}, \mu)$, then the **equality** holds for above *if and only if* $$|f|^p, \; |g|^{q} \text{ are linearly dependent in } L^1(\mathcal{X}, \mu).$$ This means that there exists some real number $\alpha, \beta \ge 0,$ not all zero, such that 
>$$
>\alpha \lvert f \rvert^{p} = \beta \lvert g \rvert^{q}, \quad \mu\text{-almost everywhere.}  
>$$

- [[Hölder Inequality]]

>[!important] Minkowski's Inequality
>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be measure space and let $1 \le p < \infty$.
>
>For any $f, g\in L^p(\mathcal{X}, \mu)$, then $f + g \in L^p(\mathcal{X}, \mu)$ and. we have
>$$
>\lVert f + g \rVert_{p} \le \lVert f \rVert_{p} + \lVert g \rVert_{p},  
>$$
>where the **equality** holds *if and only if* $f$ and $g$ are *linearly dependent*.

- [[Minkowski Inequality]]

### Inequality for Convex Functions


>[!important] Jensen's Inequality (Finite version)
>Let $\varphi: X \to \mathbb{R}$ be **convex function**.  Given a sequence of points $(x_{i})_{i=1}^n$ in the domain $X$ and a sequence of *positive numbers* $(a_{i})_{i}^n$, the Jensen's inequality states that
>$$
>\begin{align*}
>\varphi \left( \frac{\sum_{i=1}^n a_{i}x_{i} }{\sum_{i=1}^n a_{i}}\right) &\le  \frac{\sum_{i=1}^n a_{i} \varphi\left(x_{i}\right)   }{\sum_{i=1}^n a_{i}}
\end{align*}
>$$ 
>Equality holds if and only if $x_{1} = x_{2} \,{=}\ldots{=}\, x_{n},$ or $\varphi$ is *linear* on the domain $X$.

>[!important] Jensen's Inequality (Integration version)
>Let $(X, \mathscr{F}, \mu)$ be a *measure space.* Let $f:X \to \mathbb{R}$ be a $\mu$-measurable function and  $\varphi: \mathbb{R} \to \mathbb{R}$ be **convex function**. Then
>$$
> \begin{align*}
> \varphi \left(\int_{X} f d\mu \right) &\le \int_{X} \varphi \circ f\, d\mu. 
> \end{align*}
>$$ 

>[!important] Jensen's Inequality (Probability version)
>Let $(\Omega, \mathscr{F}, \mathcal{P})$ be a *probability space.* Let $X:\Omega \to \mathbb{R}$ be a random variable ($\mathcal{P}$-measurable function) and  $\varphi: \mathbb{R} \to \mathbb{R}$ be **convex function**. Then
>$$
> \begin{align}
> \varphi \left( \mathbb{E}_{\mathcal{P}}\left[ X \right] \right) &\le  \mathbb{E}_{\mathcal{P}}\left[ \varphi(X) \right]. 
> \end{align}
>$$ 

- [[Jensen Inequality]]

>[!important]
>Let $X$ be a real *topological vector space*, and $X^{*}$ be the *dual space* of $X$. 
>
>Define a function $f: X \to \mathbb{R}$ and $f^{*}$ is its *convex conjugate* function $f^{*}: X^{*} \to \mathbb{R}$. 
>$$
>f^{*}(p) := \sup_{x \in X}\left\{ \left\langle p,x\right\rangle - f(x) \right\}, 
>$$
>where $\left\langle  \cdot\,,\, \cdot   \right\rangle: X^{*} \times X \to \mathbb{R}$ is the *canonical dual pairing*:
>$$
>\left\langle  p\,,\, x   \right\rangle := p(x).
>$$
>
>The **Fenchel's inequality** (also known as the **Fenchel–Young inequality**) states that
>$$
>f(x) + f^{*}(p) \ge \left\langle p\,,\, x   \right\rangle, \quad \forall x\in X, \; p \in X^{*}
>$$
>
>Furthermore, the *equality* holds only when $p \in \partial f(x).$

- [[Fenchel Inequality]]
### Fundamental Inequality in Probability

>[!important] Markov's Inequality
>Let $(\Omega, \mathscr{F}, \mathcal{P})$ be a probability space. $X \in L^1(\Omega, \mathcal{P})$ is an *non-negative integrable random variable*, i.e. $X \ge 0, a.s.$. Then for all $t > 0$,
> $$
> \begin{align*}
> \mathcal{P}\left[X \ge t\right] &\le  \frac{\mathbb{E}\left[X \right]}{t}
> \end{align*}
> $$

>[!important]
>Let $\phi: I \subseteq \mathbb{R} \to \mathbb{R}$ be any *nondecreasing and nonnegative* function, and if $X$ denotes a random variable taking values in $I$,  then *Markov’s inequality* implies that for every $t \in I$ with $\phi(t) > 0,$
> $$
> \begin{align*}
> \mathcal{P}\left[X \ge t\right] \le \mathcal{P}\left[\phi(X) \ge \phi(t)\right] &\le  \frac{\mathbb{E}\left[\phi(X)  \right]}{\phi(t)}.
> \end{align*}
> $$

- [[Markov Inequality]]
- [[Chebyshev Inequality]]

### Cramér–Chernoff Method


>[!important] Chernoff's inequality
>Let $(\Omega, \mathscr{F}, \mathcal{P})$ be a probability space. $X$ is a *random variable* whose *moment generating function* 
>$$
>M_{X}(\lambda) := \mathbb{E}\left[ e^{\lambda X} \right] < \infty.
>$$
> Then for all $t > 0$, 
> $$
> \begin{align*}
> \mathcal{P}\left[ X \ge t\right] &\le \exp\left( - \psi_{X}^{*}(t)  \right)
> \end{align*}
> $$
> where $\psi_{X}^{*}(t)$ is **the Legendre transform** of $\psi_{X}(\lambda) := \log M_{X}(\lambda)$, the *logarithm* of *the moment-generating function*.

- [[Cramér–Chernoff Method]]
	- [[Chernoff Bound for Gaussian distribution]]
	- [[Chernoff Bound for Bernoulli distribution]]
	- [[Chernoff Bound for Poisson distribution]]

- [[Sub-Gaussian Random Variable]]
	- [[Sub-Gaussian Norm]]
	- [[Orlicz Space]]

>[!important] Hoeffding's Inequality
>Let $X_1 \,{,}\ldots{,}\, X_n$ be **independent** random variables such that $X_i$ **takes its values in $[a_i, b_i]$** *almost surely* for all $i \le n$. Let
>$$
> \begin{align*}
> S &= \sum_{i=1}^{n} \left( X_i - \mathbb{E}_{}\left[ X_{i} \right] \right).
> \end{align*}
>$$ 
>Then for every $t > 0$,
>$$
>\begin{align}
> \mathcal{P}\{S \ge  t\} \le \exp \left( - \frac{2t^2}{\sum_{i=1}^{n}(b_i - a_i)^2}\right). 
>\end{align}
>$$ 

- [[Hoeffding Inequality]]

>[!important] Bennett's Inequality
>Let $X_{1} \,{,}\ldots{,}\, X_{n}$ be *independent* random variable with **finite variance** such that $X_{i} \le b$ for some $b > 0$ *almost surely* for all $i\le n$. 
>
>Let $S = \sum_{i=1}^n (X_{i} - \mathbb{E}\left[ X_{i} \right])$ be the sum of *centered* random variables and $\nu = \sum_{i=1}^n \mathbb{E}\left[ X_{i}^2 \right]$ be proportional to the *sample estimate of the second moment*. 
>
>Then, for any $t > 0$,
>$$
> \begin{align}
> \mathcal{P} \{ S \ge t \} \le \exp \left(-\frac{\nu}{b^2}h\left(\frac{b\,t}{\nu}\right)\right)
> \end{align}
>$$ 
>where $h(u) = (1 + u) \log(1 + u) - u$ for $u > 0$.

- [[Bennett Inequality]]

>[!important] Bernstein's Inequality (Simple Form)
>Let $X_{1} \,{,}\ldots{,}\, X_{n}$ be *independent* random variable. Assume that there exist *positive numbers* $\nu$ and $c$ such that
>$$
> \begin{align*}
> \mathbb{E}\left[ \left(X\right)_{+}^q \right] \le \frac{q!}{2}\nu c^{q-2}, \quad \forall q\in \mathbb{N},\; q\ge 2,
> \end{align*}
>$$ 
>where $(x)_{+}= \max(x, 0)$ be the positive part of $x$.
>
>Let $S = \sum_{i=1}^n (X_{i} - \mathbb{E}\left[ X_{i} \right])$, then,  for any $t > 0$,
>$$
> \begin{align}
> \mathcal{P} \{ S \ge t \} \le \exp \left(- \frac{t^2}{2(\nu + c\,t)} \right).
> \end{align}
>$$ 

- [[Bernstein Inequality]]

### Johnson-Lindenstrauss Lemma


- [[Gaussian Random Projections]]
- [[epsilon Isometry]]
- [[Johnson-Lindenstrauss Lemma for Dimensionality Reduction]]









-----------
##  Recommended Notes and References

- [[Concentration Inequalities by Boucheron]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]
- [[High Dimensional Probability An Introduction by Vershynin]]