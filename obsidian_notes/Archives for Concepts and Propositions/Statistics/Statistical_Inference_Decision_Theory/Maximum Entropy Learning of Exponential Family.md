---
tags:
  - concept
  - math/probability
  - statistics/estimation
  - math/information_theory
  - math/convex_analysis
keywords:
  - maximum_entropy_learning
  - exponential_family
topics:
  - statistics/estimation
  - information_theory
  - convex_analysis
name: Maximum Entropy Learning of Exponential Family
date of note: 2024-06-24
---

## Concept Definition

>[!important]
>**Name**: Maximum Entropy Learning of Exponential Family

### Exponential Family as Solution of Maximum Entropy Learning 

>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F}, \mathcal{P}_{0})$ be a *probability space* and $T_{i}: \mathcal{X} \to \mathbb{R}$ is a *measurable function* for $i=1 \,{,}\ldots{,}\,d$. 
>
>For all $\mathcal{P} \ll \mathcal{P}_{0}$, consider the **maximum entropy learning** problem
>$$
>\begin{align*}
> \min_{\mathcal{P} \ll \mathcal{P}_{0}}&\;\; \mathbb{KL}\left( \mathcal{P} \left\|\right. \mathcal{P}_{0} \right) \\
> \text{s.t. }&\; \mathbb{E}_{ \mathcal{P} }\left[  T_{i}(X) \right] = \mu_{i}, \quad i=1 \,{,}\ldots{,}\,d
>\end{align*}
>$$
>where $\mu_{i} \in \mathbb{R}$ for  $i=1 \,{,}\ldots{,}\,d$.
>
>The **optimal solution** $\mathcal{P}^{*}$ of the above maximum entropy problem is from the **exponential family**, where the *Radon-Nikodym derivative* of $\mathcal{P}$ with respect to $\mathcal{P}_{0}$ is
>$$
> f_{\eta}(x) = \frac{d\mathcal{P}^{*}}{d\mathcal{P}_{0}} = \exp \left(\left\langle  \eta\,,\, T(x) \right\rangle - A(\eta)\right)
>$$
>and $T(x) = (T_{1}(x) \,{,}\ldots{,}\,T_{d}(x))$ and $\eta = (\eta_{1} \,{,}\ldots{,}\,\eta_{i}) \in \mathbb{R}^d$ and 
>$$A(\eta) = \log \int_{\mathcal{X}} \exp \left(\left\langle  \eta\,,\, T(x) \right\rangle \right)d\mathcal{P}_{0}(x)  = \log \mathbb{E}_{ \mathcal{P}_{0} }\left[ \exp \left(\left\langle  \eta\,,\, T(X) \right\rangle\right) \right].$$

^e73c44

- [[Kullback-Leibler Divergence]]
- [[Maximum Entropy Learning]]
- [[Exponential Family of Distributions]]
- [[Gibbs Measure and Energy-based Model]]
- [[Elements of Information Theory by Cover]]
- [[Information Projection and Moment Projection]]

### Proof via Lagrangian Multiplier on Function Space

>[!info]
>Consider the **Lagrangian** for the maximum entropy learning problem
>$$
>\begin{align*}
> L(\mathcal{P}, \lambda) &=   \mathbb{KL}\left( \mathcal{P} \left\|\right. \mathcal{P}_{0} \right)    + \left\langle  \lambda \,,\, \mathbb{E}_{ \mathcal{P} }\left[  T(X) \right] \right\rangle - \left\langle  \lambda\,,\,\mu \right\rangle + \nu \left(\mathcal{P}(\mathcal{X}) - 1\right)\\[5pt]
>  &= \int_{\mathcal{X}} \left(\frac{d\mathcal{P}}{d\mathcal{P}_{0}}\right)\log \left(\frac{d\mathcal{P}}{d\mathcal{P}_{0}}\right)d\mathcal{P}_{0} + \int_{\mathcal{X}}\left\langle  \lambda\,,\, T \right\rangle\,\left(\frac{d\mathcal{P}}{d\mathcal{P}_{0}}\right) d\mathcal{P}_{0} \\[5pt]
>  &\;\; - \left\langle  \lambda\,,\,\mu \right\rangle + \nu \left(\int_{\mathcal{X}}\left(\frac{d\mathcal{P}}{d\mathcal{P}_{0}}\right) d\mathcal{P}_{0} - 1\right) \\[15pt]
>  \implies L(f, \lambda) &= \int_{\mathcal{X}}f\,\log(f)\,\mathcal{P}_{0} + \int_{\mathcal{X}}\left\langle \lambda\,,\, T \right\rangle\,f\,d\mathcal{P}_{0} - \left\langle  \lambda\,,\,\mu \right\rangle + \nu \left(\int_{\mathcal{X}}f\,d\mathcal{P}_{0} - 1\right)
>\end{align*}
>$$
>where 
>$$f := \frac{d\mathcal{P}}{d\mathcal{P}_{0}}.$$
>
>The **KKT** conditions are 
>$$
>\begin{align*}
> \frac{ \partial L }{ \partial f } &= \int \;\log(f)\; d\mathcal{P}_{0} + 1 + \int_{\mathcal{X}}\left\langle \lambda\,,\, T \right\rangle\,\,d\mathcal{P}_{0} + \nu = 0\\
> &\; \int_{\mathcal{X}}f\,d\mathcal{P}_{0} = 1 \\
> &\; \int_{\mathcal{X}}f\,T\,d\mathcal{P}_{0} = \mu \\[5pt]
> &\; f \ge 0 \\[5pt]
> &\; \nu \in \mathbb{R},\;\; \lambda \in \mathbb{R}^{d}
>\end{align*}
>$$
>Let $A := \nu + 1$ in the first equality, we show that for $\mathcal{P}_{0}$ almost everywhere 
>$$
>\begin{align*}
>\log(f) &= \left\langle -\lambda\,,\, T \right\rangle - A \\[5pt]
> f&= \exp \left( \left\langle -\lambda\,,\, T \right\rangle - A \right) \\
> \text{ where }& A = \log \int_{\mathcal{X}} \exp \left(\left\langle -\lambda\,,\, T \right\rangle \right) d\mathcal{P}_{0}
>\end{align*}
>$$
>Substituting $\eta = - \lambda$, we have the result. Q.E.D.

- [[Entropy Functional]]
- [[Methods of Lagrangian Multipliers]]
- [[Karush-Kuhn-Tucker Optimality Condition]]
- [[Elements of Information Theory by Cover]] pp 409 - 415

### Proof via Variational Representation of KL Divergence

>[!important] 
>We apply the **variational representation** of the KL divergence
>$$
>\begin{align*}
>\mathbb{KL}\left( \mathcal{P} \left\|\right. \mathcal{P}_{0} \right) := \sup\left\{\mathbb{E}_{\mathcal{P}}\left[f\right] - \log \mathbb{E}_{\mathcal{P}_{0}}\left[ \exp\left(f\right) \right]: f\text{ such that }\exp(f) \in  L^1(\mathcal{X}, \mathscr{F}, \mathcal{P}_{0})  \right\}
\end{align*}
>$$
>
>Let $$f(x) := \left\langle  \eta\,,\, T(x)   \right\rangle$$   Then for any $\mathcal{P} \ll \mathcal{P}_{0}$, we have 
>$$
>\begin{align*}
>\mathbb{KL}\left( \mathcal{P} \left\|\right. \mathcal{P}_{0} \right) &\ge \mathbb{E}_{\mathcal{P}}\left[\left\langle  \eta\,,\, T(X) \right\rangle\right] - \log \mathbb{E}_{\mathcal{P}_{0}}\left[ \exp\left(\left\langle  \eta\,,\, T(X)   \right\rangle\right) \right]\\[5pt]
>&= \left\langle  \eta\,,\, \mathbb{E}_{\mathcal{P}}\left[T(X)\right] \right\rangle - A(\eta)\\[5pt]
>&= \left\langle  \eta\,,\, \mu \right\rangle - A(\eta)
>\end{align*}
>$$
>By  [[Variational Formula for Kullback-Leibler Divergence#Theorem]], the equality holds if and only if $\mathcal{P}$ is from an **exponential family**
>$$
>f:= \frac{d\mathcal{P}}{d\mathcal{P}_{0}} = \frac{\exp(\left\langle  \eta\,,\, T   \right\rangle)}{\mathbb{E}_{\mathcal{P}_{0}}\left[ \exp\left(\left\langle  \eta\,,\, T   \right\rangle\right) \right]}, \quad \mathcal{P}\text{-a.s.} 
>$$

- [[Variational Formula for Kullback-Leibler Divergence]]



## Explanation




## Maximum Entropy Learning of Exponential Family 

![[Kullback-Leibler Divergence for Exponential Family#^1737d6]]

- [[Kullback-Leibler Divergence for Exponential Family]]

>[!important]
>Let $(\mathcal{X}, \mathscr{F}, \nu)$ be a measure space, and let $\mathscr{P}_{\Theta}$ be an exponential family containing *parametric models* that are dominated by a *common* $\sigma$-finite measure $\nu$. 
>
>Let $P_{1}, P_{2}$ be distributions from the same exponential family $\mathscr{P}$, where 
>- $P_{1} = P_{\mu^1}$ with *mean parameter* $\mu^1\in \mathcal{M}$
>- and $P_{2} = P_{\theta^2}$ with *canonical parameter* $\theta^{2} \in \Theta$
>
>The *KL-divergence* from $P_{2}$ to $P_{1}$ can be formulated as the mixed-form 
>$$
>\mathbb{KL}\left( P_{1} \left\|\right. P_{2} \right) = A(\theta^2) - \left\langle \mu^1 , \theta^2 \right\rangle + A^{*}(\mu^1)
>$$ 
>where
>- $A(\theta^2)$ is the *log-partition function* of distribution $P_{2}$
>- $A^{*}(\mu^1)$ is the *dual of log-partition function*, i.e. the *negative entropy* of distribution $P_{1}$
>  
>The **maximum entropy learning** for $P_{1}$ given prior distribution $P_{2}$ under mean constraint set $\mathcal{M}_{2}$ is formulated as 
>$$
>\begin{align*}
> \min_{\mu^1}\;&\; \mathbb{KL}\left( P_{1} \left\|\right. P_{2} \right) \equiv A(\theta^2) - \left\langle \mu^1 , \theta^2 \right\rangle + A^{*}(\mu^1) \\[5pt]
> \text{s.t. }&\;\; \mu^{1} \in \mathcal{M}_{2} 
>\end{align*}
>$$
>or equivalently,
>$$
>\begin{align*}
> \max_{\mu^1}\;&\; \left\langle \mu^1 , \theta^2 \right\rangle -A^{*}(\mu^1) \\[5pt]
> \text{s.t. }&\;\; \mu^{1} \in \mathcal{M} 
>\end{align*}
>$$
>where the *mean parameter space*
>$$
>\mathcal{M} := \left\{ \mu: \exists\,p,\quad \mathbb{E}_{p}\left[  \phi_{k}\right] = \mu_{k},\; k\in I  \right\} 
>$$

- [[Exponential Family of Distributions]]
- [[Log-Partition Function of Exponential Family]]
- [[Convex Conjugate of Log-Partition Function of Exponential Family]]
- [[Maximum Entropy Learning for Approximate Inference in PGM]]
- [[Mean Field Approximation for Exponential Family]]


-----------
##  Recommended Notes and References

- [[Marginal Polytope and Local Consistent Polytope]]
- [[Polyhedron and Polytope]]




- [[Likelihood Function]]
- [[Sufficient Statistics]]


- [[Maximum Likelihood Estimation]]
- [[Maximum Entropy Learning]]

- [[Kullback-Leibler Divergence]]
- [[Variational Formula for Kullback-Leibler Divergence]]

- [[Convex Optimization Problem]]


- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Elements of Information Theory by Cover]] pp 409 - 415
- [[All of Statistics A Concise Course by Wasserman]]

