---
tags:
  - concept
  - math/information_theory
  - math/information_geometry
keywords:
  - f_divergence
topics:
  - information_theory
  - information_geometry
name: f-Divergence
date of note: 2024-05-07
---

## Concept Definition

>[!important]
>**Name**: $f$-Divergence

>[!important] Definition
>if $P$ and $Q$ are *probability measures* on a measurable space $(\Omega, \mathscr{F})$, and $P$ is *absolutely continuous* with respect to $Q$, 
>$$P \ll Q.$$
>
>Define $f: [0, +\infty) \to (-\infty, +\infty]$ as a *convex* function satisfying the following conditions:
>- $f(x) < +\infty$ for $x >0$;
>- $f(1) = 0$;
>- $f(0)= \lim_{ x \to 0^+ }f(x)$.
>
>Then **$f$-Divergence** *from* $Q$ to $P$ is defined as
> $$
> \begin{align*}
> \mathbb{D}_{f}\left( P \left\|\right. Q \right) &:= \int_{\Omega} f\left( \frac{dP}{dQ} \right) dQ 
> \end{align*}
> $$
> where $\frac{dP}{dQ}$ is the *Radon-Nikodym derivative* of $P$ with respect to $Q$.
> 
> We call $f$ the **generator** of $\mathbb{D}_{f}\left( \cdot \left\|\right. \cdot \right).$

^e7fa76

- [[Convex Function]]
- [[Absolute Continuity for Measures]]
- [[Radon-Nikodym Derivative]]
- [[Divergence Function on Manifold]]
- [[Phi Entropy Functional]]

### $f$-Mutual Information


>[!important] Definition
>Let $(\mathcal{X}\times \mathcal{Y}, \mathscr{F},  \mathcal{P})$ be a *probability space* on product space $\mathcal{X} \times \mathcal{Y}$. Let $\mathcal{P}_{\mathcal{X}}$ and  $\mathcal{P}_{\mathcal{Y}}$  be the *marginal measure* of $\mathcal{P}$ onto $\mathcal{X}$ and $\mathcal{Y}$.
>
>Define  $(X, Y)$  as a pair of $\mathcal{P}$-measurable *random variables* on $\mathcal{X} \times \mathcal{Y}$, where $X: \mathcal{X} \to \mathbb{R}$ and $Y: \mathcal{Y} \to \mathbb{R}$  are $\mathcal{P}_{\mathcal{X}}$-measurable and $\mathcal{P}_{\mathcal{Y}}$-measurable, respectively.
>
>Define $f: [0, +\infty) \to (-\infty, +\infty]$ as a *convex* function satisfying the following conditions:
>- $f(x) < +\infty$ for $x >0$;
>- $f(1) = 0$;
>- $f(0)= \lim_{ x \to 0^+ }f(x)$.
>
>The **$f$-mutual information**  between random variables $X$ and $Y$ is defined as 
>$$
>\begin{align*}
>I_{f}(X; Y) &= \mathbb{D}_{f}\left( \mathcal{P} \left\|\right. \mathcal{P}_{\mathcal{X}} \otimes \mathcal{P}_{\mathcal{Y}}   \right) \\
>&= \int_{\mathcal{X} \times \mathcal{Y}} f \left(\frac{d\mathcal{P}}{d \mathcal{P}_{\mathcal{X}} \otimes d\mathcal{P}_{\mathcal{Y}} }\right)\;d \mathcal{P}_{\mathcal{X}} \otimes d\mathcal{P}_{\mathcal{Y}},
\end{align*}
>$$
>where $\mathcal{P}_{\mathcal{X}} \otimes \mathcal{P}_{\mathcal{Y}}$ is **the tensor product** between two marginal measures, i.e.
>$$
>(\mathcal{P}_{\mathcal{X}} \otimes \mathcal{P}_{\mathcal{Y}})(U \times V) :=  \mathcal{P}_{\mathcal{X}}(U)\, \mathcal{P}_{\mathcal{Y}}(V), \quad U\times V \in \mathscr{F}.
>$$

- [[Mutual Information]]

## Explanation



## Properties

### Non-negativity

>[!important] Proposition
>Let $P$ and $Q$ be two probability measures on $\mathcal{X}$ and $P \ll Q$. 
>
 Then the $f$-Divergence from $Q$ to $P$ is **non-negative**
>$$
>\mathbb{D}_{f}\left( P \left\|\right. Q \right)  \ge 0.
>$$
>with equality holds  *if and only if* $P = Q$.

>[!info]
>This follows from the *convexity* of the mapping 
>$$(p, q) \mapsto q\,f\left(\frac{p}{q}\right)$$ on $\mathbb{R}^2$

- [[Perspective Function]]

### Convexity

>[!info]
>$f$-divergence is a **convex** function in the joint space of two discrete probability vectors.

>[!important] Proposition
>The $f$-divergence $\mathbb{D}_{f}\left( P \left\|\right.Q \right)$ is **convex** in **the pair of probability measures** $(P, Q)$; 
>- that is, if $(P_{1}, Q_{1})$ and $(P_{2}, Q_{2})$ are two pair of *probability measures*. Then for all $\lambda \in [0,1]$,
>$$
>\begin{align*}
>\mathbb{D}_{f}\left( P_{1} + (1- \lambda) P_{2} \left\|\right. \lambda Q_{1} + (1- \lambda) Q_{2}  \right) &\le \lambda \mathbb{D}_{f}\left(  P_{1}  \left\|\right. Q_{1}  \right) \\
>&\;\; + (1- \lambda) \mathbb{D}_{f}\left( P_{2} \left\|\right. Q_{2}  \right)
\end{align*}
>$$

### Dual Divergence



### Data Processing Inequality

>[!important] Proposition (Monotonicity)
>Let $P, Q$ be probability measures on *product measureable space* $(\mathcal{X}\times \mathcal{Y}, \mathscr{F})$.  Define  $(X, Y)$  as a pair of  *random variables* on $\mathcal{X} \times \mathcal{Y}$ whose joint distribution can be $P$ or $Q$. 
>- Denote $P_{X}$ and $Q_{X}$ as the *marginal distribution* whose *joint distribution* is $P$ and $Q$, respectively.
>
>Then the $f$-divergence of **joint distribution** is *no less* than the $f$-divergence of **marginals**
>$$\mathbb{D}_{f}\left( P_{X,Y} \left\|\right. Q_{X, Y} \right) \ge \mathbb{D}_{f}\left( P_{X} \left\|\right. Q_{X} \right) $$


>[!important] Proposition
>Let $P, Q$ be probability measures on *product measureable space* $(\mathcal{X}\times \mathcal{Y}, \mathscr{F})$.  Define  $(X, Y)$  as a pair of  *random variables* on $\mathcal{X} \times \mathcal{Y}$ whose joint distribution can be $P$ or $Q$. 
>- Assume that the *marginal distribution* on $X$ is the same  $$P_{X} = Q_{X}.$$ 
>- Denote $P_{Y|X}$ and $Q_{Y|X}$ as conditional probability of $Y$ given $X$ if the joint distribution is $P$ and $Q$ respectively.
>- Note that $$P_{X, Y} = P_{X}\,P_{Y|X}, \quad Q_{X, Y} = P_{X}\,Q_{Y|X}$$
>
>
>Define the **conditional $f$-divergence** as $$\mathbb{E}_{ X }\left[  \mathbb{D}_{f}\left( P_{Y|X} \left\|\right. Q_{Y|X} \right) \right]$$
>
>Then the **conditional $f$-divergence** is *no less than* the *$f$-divergence* between **marginals**
>$$
>\mathbb{E}_{ X }\left[  \mathbb{D}_{f}\left( P_{Y|X} \left\|\right. Q_{Y|X} \right) \right] \ge \mathbb{D}_{f}\left( P_{Y} \left\|\right. Q_{Y} \right)
>$$

^7d4f1b


>[!important] Data Processing Inequality
>Let $P, Q$ be probability measures on *product measureable space* $(\mathcal{X}\times \mathcal{Y}, \mathscr{F})$.  Define  $(X, Y)$  as a pair of  *random variables* on $\mathcal{X} \times \mathcal{Y}$ whose joint distribution can be $P$ or $Q$. 
>- Assume that the *conditional distribution* is same $$P_{Y|X} = Q_{Y|X}$$ That is, the same transformation on both input distributions.
>- Note that $$P_{X, Y} = P_{X}\,P_{Y|X}, \quad Q_{X, Y} = Q_{X}\,P_{Y|X}$$
>
>
>Then the $f$-divergence of **processed distributoin** is *no greater than* the *$f$-divergence* between **originals**
>$$
> \mathbb{D}_{f}\left( P_{X} \left\|\right. Q_{X} \right)  \ge \mathbb{D}_{f}\left( P_{Y} \left\|\right. Q_{Y} \right)
>$$

^186a5e


>[!important] Data-processing Inequality
>Let $X, Y. Z$ be random variables that form a **Markov chain in order** $$X \to Y \to Z$$ i.e. $$p(x, y, z) = p(z|y)\,p(y|x)\,p(x).$$
>
>Then
>$$
> I_{f}(X; Y) \ge I_{f}(X ; Z)
>$$
>- That is, **no processing** of $Y$, deterministic or random, can **increase** the information that $Y$ contains about $X$.

^45f066


- [[Data-Processing Inequality]]


### Invariant to Sufficient Statistics

>[!important] Definition
>A function $T(X)$ is said to be a **sufficient statistic** relative to the parametric family $\mathcal{P}_{\theta}$ if $$\theta \to T(X) \to X$$ form a **Markov chain.**
>
>If $T(X)$ is sufficient statistics, then the **equality** holds in the **data processing inequality** $$I_{f}(\theta \,;\, X) = I_{f}(\theta \,;\, X \,|\, T(X))$$

- [[Sufficient Statistics]]


## Fisher metric and $\alpha$-Connection and Information Geometry

![[alpha-Connection on Statistical Manifold#^ec8eb2]]

>[!important] 
>Since *$f$-divergence*  is **invariant** with respect to **sufficient statistics**, so 
>- the *induced metric* $g^{(f)}$
>- and the *induced connection* $\nabla^{(f)}$
>
>are **invariant** with respect to **sufficient statistics**.
>
>This implies that there exists $c, \alpha$ such that
>$$g^{(f)} = c\,g, \quad \nabla^{(f)} = \nabla^{(\alpha)}$$
>where 
>- $g$ is the **Fisher metric**, and $\nabla^{(\alpha)}$ is an **$\alpha$-connection**.
>-  We can find that $$c= f^{(2)}(1), \quad \alpha = 3 + 2 \frac{f^{(3)}(1)}{f^{(2)}(1)} $$

- [[alpha-Connection on Statistical Manifold]]


## Example

>[!example]
>$$f(x) := x\log(x),$$ we have the **KL divergence** i.e. [[Kullback-Leibler Divergence]].
>$$
>\mathbb{D}_{f}\left(P\left\|\right.Q\right) = \int \frac{dP}{dQ} \log\left( \frac{dP}{dQ} \right) dQ = \int  \log\left( \frac{dP}{dQ} \right) dP = \mathbb{KL}\left( P \left\|\right. Q \right) .
>$$

>[!example]
>$$f(x) := -\log(x),$$ we have the **reversed KL divergence**, i.e. [[Kullback-Leibler Divergence]].
>$$
>\mathbb{D}_{f}\left(P\left\|\right.Q\right) = \int - \log\left( \frac{dP}{dQ} \right) dQ = \int  \log\left( \frac{dQ}{dP} \right) dQ = \mathbb{KL}\left( Q \left\|\right. P \right) .
>$$

>[!example]
>$$
>f^{(\alpha)}(x) = \left\{\begin{array}{cl} \dfrac{4}{1- \alpha^2}\left[ 1 - x^{(1+\alpha)/2} \right] & \alpha \not\in \{ -1, 1 \} \\[5pt] x \log x & \alpha = 1 \\[5pt] -\log x & \alpha = -1  \end{array}  \right. 
>$$
>we have the **$\alpha$-divergence** [[alpha-Divergence]]
>$$
>\mathbb{D}^{(\alpha)}\left(P\left\|\right.Q\right) = \frac{4}{1- \alpha^2} \int \left[ 1 - \left(\frac{dP}{dQ}\right)^{(1+\alpha)/2} \right] dQ =  \frac{4}{1- \alpha^2} \left\{ 1 - \int p(x)^{(1- \alpha)/2} q(x)^{(1 + \alpha)/2}dx \right\}  .
>$$

>[!example]
>$$f(x) := \frac{1}{2}\lvert x - 1 \rvert ,$$ we have the **total variation** [[Total Variation between Measures]]
>$$
>\mathbb{D}_{f}\left(P\left\|\right.Q\right) = \frac{1}{2}\int \left\lvert \left( \frac{dP}{dQ} \right) - 1 \right\rvert  dQ = \frac{1}{2} \int |dP - dQ| = \frac{1}{2} \int |p - q|\,d\mu
>$$

>[!example]
>$$f(x) := \frac{1}{2}(\sqrt{ x } - 1)^2,$$ we have the **squared Hellinger distance** [[Hellinger Distance between Distributions]]
>$$
>\mathbb{D}_{f}\left(P\left\|\right.Q\right) = \frac{1}{2}\int \left( \sqrt{\frac{dP}{dQ} }  - 1 \right)^2  dQ = \frac{1}{2} \int (\sqrt{ p } - \sqrt{ q })^2d\mu
>$$

>[!example]
>$$f(x) := (x - 1)^2,$$ we have the **$\chi^2$-divergence** [[Pearson Chi-square Divergence]]
>$$
>\mathbb{D}_{f}\left(P\left\|\right.Q\right) = \int \left(\frac{dP}{dQ}  - 1 \right)^2  dQ  = \int \frac{\left(dP - dQ\right)^2}{dQ}  = \chi^2\left(P\left\|\right.Q\right)
>$$


>[!example]

- [[Jensen-Shannon Divergence]]




-----------
##  Recommended Notes and References

- [[Kullback-Leibler Divergence]]
- [[Entropy Functional]]
- [[Divergence Function on Manifold]]


- [[Elements of Information Theory by Cover]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 55
- [[Methods of Information Geometry by Amari]] pp 56
- Wikipedia [F-divergence](https://en.wikipedia.org/wiki/F-divergence)
- Lecture notes [7.1 Definition and basic properties of f-divergences - People](https://people.lids.mit.edu/yp/homepage/data/LN_fdiv.pdf)