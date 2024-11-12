---
tags:
  - concept
  - math/information_theory
  - math/information_geometry
  - math/functional_analysis
  - deep_learning/generative_models
  - machine_learning/kernel_methods
keywords:
  - mmd_measure
  - maximum_mean_discrepancy
  - kernel_mean_embedding_distribution
topics:
  - information_theory
  - information_geometry
  - machine_learning/kernel_methods
  - machine_learning_theory
  - deep_learning/generative_models
name: Maximum Mean Discrepancy in RKHS
date of note: 2024-11-07
---

## Concept Definition

>[!important]
>**Name**: Maximum Mean Discrepancy in RKHS

>[!important] Definition
>if $P$ and $Q$ are *probability measures* on a measurable space $(\Omega, \mathscr{F})$, and $P$ is *absolutely continuous* with respect to $Q$, 
>$$P \ll Q.$$
>
>The **maximum mean discrepancy (MMD)** is defined as 
>$$
>\begin{align*}
> \text{MMD}(P,Q; \mathcal{F}) &:= D_{\mathcal{F}}(P, Q) \\[8pt]
> &:= \sup_{f\in \mathcal{F}}\lvert \mathbb{E}_{ P }\left[  f(X) \right] - \mathbb{E}_{ Q }\left[  f(X) \right] \rvert \\[8pt]
>&=  \sup_{f\in \mathcal{F}} \left\lvert \int f\,dP - \int f\,dQ \right\rvert
>\end{align*}
>$$
>where 
>- $\mathcal{F}$ is a bounded subspace of a *reproducing Kernel Hilbert space* $\mathcal{H}$ of functions on $\Omega$ where $$\mathcal{F} := \left\{ f\in \mathcal{H}\;:\; \lVert f \rVert_{\mathcal{H}} \le 1  \right\} $$ 
>- Let $\phi : x\to K(x, \cdot)$  be the canonical feature map for kernel $K$ in $\mathcal{H}$, $$f(x) = \left\langle f , \phi(x) \right\rangle_{\mathcal{H}}.$$ 
>- We see that $$\int f\,dP := \int \left\langle f , \phi \right\rangle_{\mathcal{H}}dP := \left\langle f ,  \mathbb{E}_{ P }\left[ \phi \right] \right\rangle_{\mathcal{H}}$$
>- Define the **kernel mean embedding** of *distribution* $P$ as $$\mu_{P} := \mathbb{E}_{ P }\left[  K(X, \cdot) \right] $$
>- The **maximum mean discrepancy (MMD)** can be reformulated as 
>$$D_{\mathcal{F}}(P, Q) := \sup_{\lVert f \rVert_{\mathcal{H}} \le 1 }\left\lvert \left\langle f , \mu_{P} - \mu_{Q}  \right\rangle_{\mathcal{H}} \right\rvert = \lVert \mu_{P} - \mu_{Q}  \rVert_{\mathcal{H}}.$$

^345e1a

- [[Reproducing Kernel of RKHS]]
- [[Reproducing Kernel Hilbert Space]]
- [[Complete Orthonormal Basis of Hilbert Space]]
- [[Kernel Mean Embedding of Distribution]]

### Kernel Trick Computation

![[Kernel Mean Embedding of Distribution#^6e1506]]

>[!important] Definition
>Let $\{ X_{i} \}_{i=1}^{n}$ be i.i.d. samples in $\mathcal{X}$ from $P$ and  $\{ X_{i}' \}_{i=1}^{m}$ be i.i.d. samples in $\mathcal{X}$ from $Q$. Let  $\mathcal{H}$ be a *reproducing Kernel Hilbert space (RKHS)* of functions with kernel $K$, indexed by $\mathcal{X}$. 
>
>The *empirical kernel mean embedding* for $P$ and $Q$ are given by 
>$$
>\mu \left(P_{n}\right) := \frac{1}{n} \sum_{i=1}^{n}\, K(X_{i}, \cdot)
>$$
>and
>$$
>\mu \left(Q_{m}\right) := \frac{1}{m} \sum_{i=1}^{m}\, K(X_{i}', \cdot)
>$$
>
>Thus we can compute the **squared maximum mean discrepancy** as 
>$$
>\begin{align*}
> \text{MMD}^2(P, Q; \mathcal{F}) &= \left\lVert \frac{1}{n} \sum_{i=1}^{n}\, K(X_{i}, \cdot) - \frac{1}{m} \sum_{i=1}^{m}\, K(X_{i}', \cdot) \right\rVert_{\mathcal{H}}^2 \\[8pt]
> &=  \frac{1}{n^2}\,\sum_{i=1}^{n}\sum_{j=1}^{n}K(X_{i}, X_{j}) - \frac{2}{n\,m}\,\sum_{i=1}^{n}\sum_{j=1}^{m}K(X_{i}, X_{j}') \\[5pt]
> &\quad + \frac{1}{m^2}\,\sum_{i=1}^{m}\sum_{j=1}^{m}K(X_{i}', X_{j}')
>\end{align*}
>$$

- [[Kernel Mean Embedding of Distribution]]

### Linear Time Computation with Unnormalized Mean Embedding

>[!important]
>Instead of computing all samples with $O(n^2)$ complexity, we can *reduce the number of samples* involved in evaluation of kernel mean embedding.
>
>Define the **squared witness score** as $$\text{witness}^2(v) := \left(\mu_{Q}(v) - \mu_{P}(v)\right)^2$$
>- Thus for empirical mean embedding, the evaluation  $$\text{witness}^2(v) := \left(\frac{1}{n}\sum_{i=1}^{n}K(X_{i}, v) - \frac{1}{m}\sum_{j=1}^{m}K(X_{j}', v)\right)^2$$ takes $O(n)$ time complexity (assuming that $m \approx n$)
>
>The key for **unnormalized mean embedding (UME)** is to select a set of *test locations* $v_{1}\,{,}\ldots{,}\,v_{M}$ that is *sufficent* to evaluate $P, Q$. Then
>$$
>\text{UME}^2(P, Q) = \frac{1}{M}\sum_{j=1}^{M}\left(\mu_{P}(v_{j}) - \mu_{Q}(v_{j})\right)^2
>$$
>- This process takes about $O(n)$ complexity.
>- We can *maximize UME* with respect to $\{ v_{i} \}$ to find the optimal location. 

- [[Gaussian Process Latent Variable Model]]


## Explanation

### Compare with $f$-divergence and Wasserstein Distance

>[!important]
>- **Wasserstein distance** $$\mathcal{W}_{1}(\alpha, \beta) = \sup\left\{ \int_{\mathcal{X}}\phi\;d\alpha -  \int_{\mathcal{X}}\phi\;d\beta:  \;\forall \phi \in \mathcal{C}(\mathcal{X}) \text{ with } \text{Lip}(\phi) \le 1 \right\}$$
>- **$f$-divergence** $$\mathbb{D}_{f}\left( \alpha \left\|\right. \beta \right) = \sup\left\{ \int_{\mathcal{X}}\,\phi\;d\alpha - \int_{\mathcal{X}}\,f^{*}(\phi)\,d\beta:\; \forall \phi \in \mathcal{B}(\mathcal{X}) \text{ and measureable}  \right\} $$


- [[Variational Representation of Wasserstein Distance]]
- [[Wasserstein Distance]]
- [[Wasserstein Space]]
- [[Variational Formula for f-Divergence]]
- [[f-Divergence]]





## Gaussian Process

![[RKHS of Gaussian Random Function in Hilbert Space#^5db3d8]]

![[RKHS of Gaussian Random Function in Hilbert Space#^7ecefc]]

- [[RKHS of Gaussian Random Function in Hilbert Space]]
- [[RKHS of Gaussian Process]]
- [[Gaussian Process]]



-----------
##  Recommended Notes and References



- [[Integral Probability Metric between Probability Measures]]
- [[Principle of Learning by Comparison for Implicit Generative Models]]

- [[Kullback-Leibler Divergence]]
- [[Divergence Function on Manifold]]


- [[Hilbert Space]]
- [[Statistical Manifold as Parametric Family]]



- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 58 - 59,  891
- [[Kernel Mean Embedding of Distributions by Muandet]] pp 44 - 51


