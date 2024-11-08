---
tags:
  - concept
  - math/probability
  - math/stochastic_process
keywords:
  - gaussian_function
  - karhunen_loeve_expansion
topics:
  - probability
  - stochastic_process
name: RKHS of Gaussian Random Function in Hilbert Space
date of note: 2024-05-10
---

## Concept Definition

>[!important]
>**Name**:  Reproducing Kernel Hilbert Space of Gaussian Random Function in Hilbert Space

### Karhunen-Loève expansion

>[!info]
>Let $\mathcal{H}$ be a **separable Hilbert space** whose inner product will be denoted by $\left\langle \cdot , \cdot \right\rangle_{\mathcal{H}}$. 
>
>Consider
>- a **complete orthonormal basis** $\{\varphi_n\}_{n=1}^{\infty}$ on $\mathcal{H}$, 
>- a  sequence of *independent* $\mathcal{N}(0, 1)$-distributed random variables $\{\xi_n\}_{n=1}^{\infty}$, and 
>- a sequence of *non-negative numbers* $\{\sigma_n\}_{n=1}^{\infty}$ satisfying assumption $$\sum_{n=1}^{\infty}\sigma_n^2 < \infty$$ 

^5db3d8

- [[Separable Space]]
- [[Hilbert Space]]

![[Representation of Gaussian Random Function in Hilbert Space#^3e7bb2]]

- [[Representation of Gaussian Random Function in Hilbert Space]]

### Construction Reproducing Kernel Hilbert Space

- [[Reproducing Kernel Hilbert Space]]
- [[RKHS of Gaussian Random Function]]

>[!important] 
>Denote the **space of all measurable linear functionals** as$\mathcal{H}_{\mathcal{N}}^{*} \subset \mathcal{H}^{*}$. 
>
>By the Karhunen-Loève expansion, for any $z\in \mathcal{H}_{\mathcal{N}}^{*}$,
>$$
>\left\langle  z\,,\, X(\omega)   \right\rangle = \sum_{n=1}^{\infty}z_{n}\left(\sigma_n\, \xi_n(\omega) \,\varphi_n\right) = \sum_{n=1}^{\infty}\left(z_{n}\sigma_n \right)\, \xi_n(\omega)\, \varphi_n
>$$
>where $(z_{1},z_{2} \,{,}\ldots{,}\,) \in \ell_{2}$.

>[!important] Space of Measurable Linear Functional
>- For any $f, g \in \mathcal{H}^{*} =\mathcal{H}$, we have the inner product defined in the **space of all measurable linear functionals** $\mathcal{H}_{\mathcal{N}}^{*}$
>$$
>\begin{align*}
>\left\langle I^{*}f  \,,\, I^{*}g  \right\rangle_{\mathcal{H}_{\mathcal{N}}^{*}} &= \mathbb{E}_{ \mathcal{N} }\left[\left(\sum_{i=1}^{\infty}\sigma_{i}\,f_{i}\xi_{i}\right)\, \left(\sum_{i=1}^{\infty}\sigma_{i}\,g_{i}\,\xi_{i}\right)\right] \\
>&= \sum_{i=1}^{\infty}\sigma_{i}^2\,f_{i}g_{i}
>\end{align*}
>$$
>
>- A **$\mathcal{N}$-measurable linear functional** $z\in \mathcal{X}_{\mathcal{N}}^{*}$ has the following coordinate representation
>$$
>z(x) = \sum_{j=1}^{\infty}z_{j}\,x_{j}
>$$
>where $$\sum_{j=1}^{\infty}\sigma_{j}^2\,z_{j}^2 < \infty.$$
>- The **norm** in $\mathcal{X}_{\mathcal{N}}^{*}$ is $$\lVert z \rVert_{\mathcal{X}_{\mathcal{N}}^{*}}^2 = \sum_{j=1}^{\infty}\sigma_{j}^2\,z_{j}^2 $$

>[!important] RKHS of Gaussian process 
>- Then the *function* in RKHS of Gaussian process has the form
>$$
>\begin{align*}
>(Iz)(k) &= \left\langle  \varphi_{k}\,,\,I\,z \right\rangle \\
>&= \left\langle  I^{*}\varphi_{k}\,,\,z  \right\rangle_{\mathcal{X}_{\mathcal{N}}^{*}} \\
>&= \mathbb{E}_{ \mathcal{N} }\left[\left(\sum_{j=1}^{\infty}z_{j}\,\sigma_{j}\,\xi_{j}\right)\,\sigma_k\, \xi_k  \right] \\
>&= \sigma_{k}^2\,z_{k}
>\end{align*}
>$$
>- The function $h\in \mathcal{H}_{\mathcal{N}}$ in RKHS has the **coordinate representation**  $$h = Iz := \sum_{j=1}^{\infty}\sigma_{j}^2\,z_{j}\,\varphi_{j}.$$
>- The **norm** in  *RKHS* of Gaussian process $$\lVert h \rVert_{\mathcal{H}_{\mathcal{N}}^{*}}^2 = \lVert z \rVert_{\mathcal{X}_{\mathcal{N}}^{*}}^2 = \sum_{j=1}^{\infty}\sigma_{j}^2\,z_{j}^2 = \sum_{j=1}^{\infty}\frac{h_{j}^2}{\sigma_{j}^2}.$$ 
>- Thus the **RKHS** of Gaussian process $$\mathcal{H}_{\mathcal{N}} = \left\{ h = \sum_{i=1}^{\infty}h_{i} \varphi_i \in \mathcal{X}:  \; \sum_{j=1}^{\infty}\frac{h_{j}^2}{\sigma_{j}^2} < \infty\right\}.$$
>- The **inner product** in $\mathcal{H}_{\mathcal{N}}$ is defined as $$\left\langle  h_{1}\,,\, h_{2}  \right\rangle_{\mathcal{H}_{\mathcal{N}}} = \sum_{j=1}^{\infty}\frac{(h_{1})_{j}\,(h_{2})_{j}}{\sigma_{j}^2}.$$

^7ecefc

>[!info]
>We see that the function in RKHS of Gaussian process in Hilbert space
>$$
>h(t) := \sum_{j=1}^{\infty}\sigma_{j}^2\,z_{j}\,\varphi_{j}
>$$
>where $(\sigma_{j}^2)$ consists of the **variance** of Gaussian process $X: \omega \to \varphi_{j}$ with respect to each basis function $\varphi_{j}$ and $(z_{j})$ satisfies $$\sum_{j=1}^{\infty}\sigma_{j}^2\,z_{j}^2 < \infty.$$ 

- [[lp Sequence Space]]


-----------
##  Recommended Notes and References

- [[Gaussian Random Vector]]
- [[Gaussian Random Variable]]
- [[Gaussian Random Function]]