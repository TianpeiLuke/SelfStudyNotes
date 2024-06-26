---
tags:
  - concept
  - math/stochastic_process
  - math/functional_analysis
  - machine_learning/theory
keywords:
  - reproducing_kernel_hilbert_space
  - gaussian_process
topics:
  - stochastic_process
  - functional_analysis
  - machine_learning_theory
name: Reproducing Kernel Hilbert Space of Gaussian Random Function
date of note: 2024-06-03
---

## Development of RKHS of Gaussian Process

>[!important]
>**Name**: Development of RKHS of Gaussian Random Function


>[!info] Development of Reproducing Kernel Hilbert Space of Gaussian Process
>Let $(\Omega, \mathscr{F}, \mathcal{P})$ be a probability space and $\mathcal{X} \subset \mathbb{C}^T$ be a *Banach space* on index set $T$. Let $\mathscr{B}(\mathcal{X})$ be the Borel $\sigma$-algebra on $\mathcal{X}$.

- [[Banach Space]]

### Gaussian Measure on Banach Space

>[!info]
>Consider a *zero-mean* Gaussian process $(X_{t}, t\in T)$ as a *Gaussian random function* $$X: \Omega \to \mathcal{X} \implies \omega \to X(\omega, \cdot) \in \mathcal{X}.$$ Let $K: \mathcal{X}^{*} \to \mathcal{X}$ be the *covariance operator* of $X$ in $\mathcal{X}$.  Denote $$ \mathcal{N} = X_{\#}\mathcal{P} := \mathcal{P} \circ X^{-1} $$ as the *distribution* of $X$ on $\mathcal{X}$.
>
 >That is, $\mathcal{N}$ is *pushforward measure* on $\mathscr{B}(\mathcal{X})$ of $\mathcal{P}$ by $X$.

- [[Gaussian Random Function]]
- [[Covariance Operator]]
- [[Push-forward Measure and Push-forward Operator]]
- [[Product Measure on Infinite Product Space]]

### Space of Gaussian Measurable Linear Functionals

>[!info]
>For any *linear functional* $f\in \mathcal{\mathcal{X}}^{*}$, by definition of Gaussian random function, $$\left\langle f , X \right\rangle \sim \mathcal{N}(0, \,f(Kf)\,),$$ where $\left\langle  ,  \right\rangle$ is the canonical dual pairing. 
>
>The *variance* of this random variable $$ \mathbb{E}_{ \mathcal{N} }\left[\left\langle f , X \right\rangle^2  \right] = f(Kf) = \int_{\mathcal{X}}\lVert f \rVert_{\mathcal{H}}^2\; d\mathcal{N} < \infty.$$ This means that $f\in L^2(\mathcal{X}, \mathcal{N}).$

- [[Gaussian Random Function]]
- [[Canonical Dual Pairing]]

>[!important]
> In other word, we can define the **canonical embedding** on dual space $\mathcal{X}^{*}$ $$I^{*}: \mathcal{X}^{*} \to L^2(\mathcal{X}, \mathcal{N}).$$ 

- [[Canonical Inclusion]]
- [[Smooth Embedding]]

>[!important] Definition
>The *closure* of image $\overline{I^{*}(\mathcal{X}^{*})}$ in  $L^2(\mathcal{X}, \mathcal{N})$  is called **the space of all measurable linear functionals** on $\mathcal{X}$, which is denoted as $\mathcal{X}_{\mathcal{N}}^{*}$. 
>
>That is, $$\mathcal{X}_{\mathcal{N}}^{*} := \overline{I^{*}(\mathcal{X}^{*})} \subset L^2(\mathcal{X}, \mathcal{N}).$$

- [[Range and Kernel of Linear Operator]]

>[!info]
>*The space of all measurable linear functionals* $\mathcal{X}_{\mathcal{N}}^{*}$ is a *Hilbert space* since it is a *closed subspace* of a Hilbert space. 
>- The *inner product* is defined as $$\left\langle f , g \right\rangle_{\mathcal{X}_{\mathcal{N}}^{*}} := \int_{\mathcal{H}}f\,g\;d\mathcal{N} = f(Kg),\;\; \forall f, g\in \mathcal{X}_{\mathcal{N}}^{*},$$ where $K$ is the covariance operator.
>- Also the variance $$\lVert f \rVert_{\mathcal{X}_{\mathcal{N}}^{*}}^2 =  \mathbb{E}_{ \mathcal{N} }\left[ f(X)^2 \right]$$

- [[Hilbert Space]]

>[!info]
>We can consider  $I^{*}$ by restricting the embedding onto its image $$I^{*}: \mathcal{X}^{*} \to  \overline{I^{*}(\mathcal{X}^{*})}  = \mathcal{X}_{\mathcal{N}}^{*}.$$ 

### Dual Functional of Gaussian Measurable Linear Functionals

>[!info]
>Define $$I: \mathcal{X}_{\mathcal{N}}^{*} \to \mathcal{X}$$ as the *Banach adjoint of embedding map* $I^{*}: \mathcal{X}^{*} \to \mathcal{X}_{\mathcal{N}}^{*}$ by the following equation $$\left\langle f , I\,g \right\rangle = \left\langle I^{*}f , g \right\rangle_{\mathcal{X}_{\mathcal{N}}^{*} } =  \mathbb{E}_{ \mathcal{N} }\left[\left\langle  f\,,\, X   \right\rangle\, \left\langle  g\,,\,X    \right\rangle \right]\, \quad \forall f\in \mathcal{X}^{*}, g\in \mathcal{X}_{\mathcal{N}}^{*} $$  Note that the first term on the left the *canonical dual pairing* and the term on the right is the *inner product*.

- [[Adjoint of Bounded Operator in Banach Space]]

>[!info]
>We can show that $I$ is **linear** and **injective**. 
>
>To prove it, assume that for some $g \in \mathcal{X}_{\mathcal{N}}^{*}$, $$Ig = 0 \implies \left\langle I^{*}f , g \right\rangle = \left\langle f , Ig \right\rangle = 0, \quad \forall f\in \mathcal{X}.$$ By considering a sequence $I^{*}f_{n} \to g$, we have $$\lVert g \rVert_{\mathcal{X}_{\mathcal{N}}^{*}} = 0 $$ which means $g =0,$ *$\mathcal{N}$-almost surely*.

- [[Injective Function]]


>[!info]
>The **kernel** of linear map $I$
>$$
>\text{ker}(I) = \left\{ g\in \mathcal{X}_{\mathcal{N}}^{*}: Ig = 0 \right\} = \{ c: c\in \mathbb{R} \}
>$$
>is a *$1$-dimensional* space of **constant functions**.
>$$
>\mathbb{E}_{ \mathcal{N} }\left[ c X \right] = c\mathbb{E}_{ \mathcal{N} }\left[ X \right] = 0
>$$



>[!important]
>The concrete definition of $I: \mathcal{X}_{\mathcal{N}}^{*} \to \mathcal{X}$ is as follows
>$$
>I: g \mapsto   \mathbb{E}_{ \mathcal{N} }\left[  g(X)\,X \right]  := \mathbb{E}_{ \mathcal{N} }\left[\left\langle g , X  \right\rangle\,X\right]  \in \mathcal{X}
>$$
>for any $g\in \mathcal{X}_{\mathcal{N}}^{*}.$
>
>$I$ is defined as the **projection** of $\mathcal{X}_{\mathcal{N}}^{*}$ onto $\mathcal{X}$ with the  **evaluation functional** at $X$.
>
>We can identify $I$ with the Banach adjoint map $\hat{I}: \mathcal{X}_{\mathcal{N}}^{**} \to \mathcal{X}$.

- [[Adjoint of Bounded Operator in Banach Space]]
- [[Evaluation Functional]]
- [[Canonical Dual Pairing]]


### Reproducing Hilbert Space as Space of Dual Functions of Gaussian Measurable Linear Functionals


>[!important] Definition
>The range of map $I$ is called the **kernel of distribution** $\mathcal{N}$. $$\mathcal{H}_{\mathcal{N}} := I(\mathcal{X}_{\mathcal{N}}^{*}) \subset \mathcal{X}.$$ 
>
>- $\mathcal{H}_{\mathcal{N}}$ is the **reproducing kernel Hilbert space** of *Gaussian Process* $X$.
>-  inner product defined as
>$$
>\left\langle h_{1} , h_{2} \right\rangle_{\mathcal{H}_{\mathcal{N}}} := \left\langle I^{-1}h_{1} ,  I^{-1}h_{2}\right\rangle_{\mathcal{X}_{\mathcal{N}}^{*}}, \quad \forall h_{1}, h_{2} \in \mathcal{H}_{\mathcal{N}}.
>$$

- [[Gaussian Process]]
- [[Gaussian Random Function]]
- [[Hilbert Space]]
- [[Reproducing Kernel Hilbert Space]]
- [[Reproducing Kernel of RKHS]]

>[!info]
>The function in this RKHS of Gaussian process is
>$$
>f(t) := \mathbb{E}_{ \mathcal{N} }\left[ h\,X(t) \right]
>$$ 
>where $h \in \overline{\left\{ f(X): f \in \mathcal{X}_{\mathcal{N}}^{*} \right\}}$ and
>$$
>\left\langle \; \mathbb{E}_{ \mathcal{N} }\left[ f\,X \right] \;,\;  \mathbb{E}_{ \mathcal{N} }\left[ g\,X(t) \right] \;\right\rangle_{\mathcal{H}_{\mathcal{N}}} := \left\langle\, f \,,\,  g\, \right\rangle_{\mathcal{X}_{\mathcal{N}}^{*}}
>$$

- [[RKHS of Gaussian Process]]
### Factorization of Covariance Operator

>[!important] Factorization of Covariance Operator
>The **covariance operator** $K: \mathcal{X}^{*} \to \mathcal{X}$ admits the following **factorization**: $$K = I\,I^{*}.$$ In fact for any $f, g\in \mathcal{X}^{*}$ $$\left\langle f , I\,I^{*}g \right\rangle = \left\langle I^{*}f  , I^{*}g  \right\rangle_{\mathcal{X}_{\mathcal{N}}^{*}} = \mathbb{E}_{ \mathcal{N} }\left[  \left\langle f\,,\, X \right\rangle\,\left\langle g\,,\, X \right\rangle \right] := \left\langle f , Kg \right\rangle$$

- [[Covariance Operator]]


### Dispersion Ellipsoid of Gaussian Measure

>[!important] Definition
>The unit ball
>$$
>\{ h\in \mathcal{H}_{\mathcal{N}}: \lVert h \rVert _{\mathcal{H}_{\mathcal{N}}} \le 1 \}
>$$
>is sometimes called **dispersion ellipsoid** of **measure** $\mathcal{N}$.


## Explanation

>[!info]
>The construction of the map
>$$
> \Omega \stackrel{X}{\to} \mathcal{X} \dashrightarrow \mathcal{X}^{*} \stackrel{I^{*}}{\to}  \mathcal{X}_{\mathcal{N}}^{*} \stackrel{\Phi}{\to}\mathcal{X}_{\mathcal{N}}^{* *} \stackrel{(I^{*})^{*}}{\longrightarrow} \mathcal{H}_{\mathcal{N}}
>$$
>where 
>- $I^{*}: \mathcal{X}^{*} \to  \mathcal{X}_{\mathcal{N}}^{*} \subset L^2(\mathcal{X}, \mathcal{N})$ is an **embedding map,** where $$\mathcal{X}_{\mathcal{N}}^{*} := \overline{I^{*}(\mathcal{X}^{*})} .$$ 
>- $\Phi: \mathcal{X}_{\mathcal{N}}^{*} \to \mathcal{X}_{\mathcal{N}}^{**}$ is the Hilbert space *dual isomorphism*. [[Riesz Representation Theorem]];
>- $I^{**}: \mathcal{X}_{\mathcal{N}}^{* *} \to  \mathcal{H}_{\mathcal{N}} \subset \mathcal{X}$ is the **adjoint of embedding map** $I^{*}$;
>- $I =I^{**} \circ \Phi: \mathcal{X}_{\mathcal{N}}^{*} \to \mathcal{H}_{\mathcal{N}}$ where $$\mathcal{H}_{\mathcal{N}} = I(\mathcal{X}_{\mathcal{N}}^{*}).$$
>


>[!info]
>- $\mathcal{X}$ is a *Banach space*
>	- the *RKHS* $H_{\mathcal{N}}$ of Gaussian process is a **Hilbert subspace**  of $\mathcal{X}$
>- $\mathcal{X}^{*}$ is a *Banach space*
>	- the *space of $\mathcal{N}$-measurable linear functionals* $\mathcal{X}_{\mathcal{N}}^{*}$ is a **Hilbert subspace** of $\mathcal{X}^{*}$

## Properties 

>[!important] Proposition
>The space of all measurable linear functionals $\mathcal{X}_{\mathcal{N}}^{*}$ is **separable**.

- [[Separable Space]]

>[!important] Proposition
>Let $\mathcal{X} \subset \mathbb{C}^T$ be a Banach space on index set $T$ and $X: \Omega \to \mathcal{X}$ be a *zero-mean* *Gaussian random function* in space $\mathcal{X}$, with distribution $\mathcal{N}$. Denote $K: \mathcal{X}^{*} \to \mathcal{X}$ as the *covariance operator*.
>
>Denote $\mathcal{H}_{\mathcal{N}}$ as the *kernel* of distribution $\mathcal{N}$.
>
>Then
>$$
>K(\mathcal{X}^{*}) \subseteq \mathcal{H}_{\mathcal{N}} \subseteq \mathcal{X}
>$$
>The equality holds only when $\mathcal{X}$ is **finite-dimensional.**


>[!important] Proposition
>Denote $\mathcal{H}_{\mathcal{N}}$ as the *kernel* of distribution $\mathcal{N}$.
>
>Then 
>-  $$\mathcal{N}(\mathcal{H}_{\mathcal{N}}) = 0$$
>- **topological support of measure** $\mathcal{N}$ coincides with the **closure** of $\mathcal{H}_{\mathcal{P}}$ in $\mathcal{X}$. $$\text{supp}(\mathcal{N})  = \overline{\mathcal{H}_{\mathcal{N}}}.$$
>- the Hilbert space $\mathcal{H}_{\mathcal{N}}$ is **separable**.
>- the ball $$\{ h\in \mathcal{H}_{\mathcal{N}}: \lVert h \rVert_{\mathcal{H}_{\mathcal{N}}} \le \epsilon  \}$$ is **compact** in $\mathcal{H}_{\mathcal{N}}$


## Examples

>[!example]
>Consider a **standard Gaussian random vector** $X: \Omega \to \mathcal{X}$, where $\mathcal{X} = \mathbb{R}^{\infty}.$
>- For any $f, g \in c_{0} = \mathcal{X}^{*}$, we have
>$$
>\begin{align*}
>\left\langle I^{*}f  \,,\, I^{*}g  \right\rangle_{\mathcal{X}_{\mathcal{N}}^{*}} &= \mathbb{E}_{ \mathcal{N} }\left[\left(\sum_{i=1}^{\infty}f_{i}X_{i}\right)\, \left(\sum_{i=1}^{\infty}g_{i}X_{i}\right)\right] \\
>&= \sum_{i=1}^{\infty}f_{i}g_{i} \\
>&= \left\langle  f\,,\,g    \right\rangle_{\ell_{2}}
>\end{align*}
>$$
>
>- A **$\mathcal{N}$-measurable linear functional** $z\in \mathcal{X}_{\mathcal{N}}^{*}$ has the following representation
>$$
>z(x) = \sum_{j=1}^{\infty}z_{j}\,x_{j}
>$$
>where $(z_{j})\in \ell_{2}$, i.e. $$\sum_{j=1}^{\infty}z_{j}^2 < \infty.$$
>- Then the *function* in RKHS of Gaussian process has the form
>$$
>\begin{align*}
>(Iz)(k) &= \left\langle  \delta_{k}\,,\,I\,z \right\rangle \\
>&= \left\langle  I^{*}\delta_{k}\,,\,z  \right\rangle_{\mathcal{X}_{\mathcal{N}}^{*}} \\
>&= \mathbb{E}_{ \mathcal{N} }\left[\left(\sum_{j=1}^{\infty}z_{j}\,X_{j}\right)X_{k} \right] \\
>&= z_{k}
>\end{align*}
>$$
>- Thus the **RKHS** of Gaussian Process $$\mathcal{H}_{\mathcal{N}} = \ell_{2}$$

- [[RKHS of Gaussian Process]]

>[!example]
>Consider a **Gaussian random function in Hilbert space** $X: \Omega \to \mathcal{X}$, where $\mathcal{X}$ is a *Hilbert space*. 
>- By **Karhunen-Loève expansion**, 
>$$ 
> \begin{align}
> X =   \sum_{i=1}^{\infty}\sigma_i \xi_i \varphi_i
> \end{align} 
>$$ 
>where $\{ \varphi_i \}_{i=1}^{\infty}$ forms a *complete orthonormal basis* in $\mathcal{X}$,  $\{ \sigma_i \}$ is a sequence of *non-negative* real numbers, and $\xi_{i}$ are *independent $\mathcal{N}(0,1)$-distributed*  random variables.
>- For any $f, g \in \mathcal{X}^{*} =\mathcal{X}$, we have
>$$
>\begin{align*}
>\left\langle I^{*}f  \,,\, I^{*}g  \right\rangle_{\mathcal{X}_{\mathcal{N}}^{*}} &= \mathbb{E}_{ \mathcal{N} }\left[\left(\sum_{i=1}^{\infty}\sigma_{i}\,f_{i}\xi_{i}\right)\, \left(\sum_{i=1}^{\infty}\sigma_{i}\,g_{i}\,\xi_{i}\right)\right] \\
>&= \sum_{i=1}^{\infty}\sigma_{i}^2\,f_{i}g_{i}
>\end{align*}
>$$
>
>- A **$\mathcal{N}$-measurable linear functional** $z\in \mathcal{X}_{\mathcal{N}}^{*}$ has the following representation
>$$
>z(x) = \sum_{j=1}^{\infty}z_{j}\,x_{j}
>$$
>where $$\sum_{j=1}^{\infty}\sigma_{j}^2\,z_{j}^2 < \infty.$$
>- The **norm** in $\mathcal{X}_{\mathcal{N}}^{*}$ is $$\lVert z \rVert_{\mathcal{X}_{\mathcal{N}}^{*}}^2 = \sum_{j=1}^{\infty}\sigma_{j}^2\,z_{j}^2 $$
>- Then the *function* in RKHS of Gaussian process has the form
>$$
>\begin{align*}
>(Iz)(k) &= \left\langle  \varphi_{k}\,,\,I\,z \right\rangle \\
>&= \left\langle  I^{*}\varphi_{k}\,,\,z  \right\rangle_{\mathcal{X}_{\mathcal{N}}^{*}} \\
>&= \mathbb{E}_{ \mathcal{N} }\left[\left(\sum_{j=1}^{\infty}z_{j}\,\sigma_{j}\,\xi_{j}\right)\,\sigma_k\, \xi_k  \right] \\
>&= \sigma_{k}^2\,z_{k}
>\end{align*}
>$$
>- The function  $$h = Iz := \sum_{j=1}^{\infty}\sigma_{j}^2\,z_{j}\,\varphi_{j} \in \mathcal{H}_{\mathcal{N}}.$$
>- The **norm** in  *RKHS* of Gaussian process $$\lVert h \rVert_{\mathcal{H}_{\mathcal{N}}^{*}}^2 = \lVert z \rVert_{\mathcal{X}_{\mathcal{N}}^{*}}^2 = \sum_{j=1}^{\infty}\sigma_{j}^2\,z_{j}^2 = \sum_{j=1}^{\infty}\frac{h_{j}^2}{\sigma_{j}^2}.$$ 
>- Thus the **RKHS** of Gaussian process $$\mathcal{H}_{\mathcal{N}} = \left\{ h = \sum_{i=1}^{\infty}h_{i} \varphi_i \in \mathcal{X}:  \; \sum_{j=1}^{\infty}\frac{h_{j}^2}{\sigma_{j}^2} < \infty\right\}.$$
>- The **inner product** in $\mathcal{H}_{\mathcal{N}}$ is defined as $$\left\langle  h_{1}\,,\, h_{2}  \right\rangle_{\mathcal{H}_{\mathcal{N}}} = \sum_{j=1}^{\infty}\frac{(h_{1})_{j}\,(h_{2})_{j}}{\sigma_{j}^2}.$$

- [[Representation of Gaussian Random Function in Hilbert Space]]
- [[Complete Orthonormal Basis of Hilbert Space]]


>[!example]
>Consider a **Gaussian random vector in finite-dimensional space** $X: \Omega \to \mathcal{X}$, where $\mathcal{X}:= \mathbb{R}^n$. 
>- Assume that 
>$$ 
> \begin{align}
> X \sim \mathcal{N}(0, K)
> \end{align} 
>$$ 
>where $K: \mathbb{R}^n \to \mathbb{R}^n$ is the **covariance matrix** of $X$.  We have $K\in \mathcal{S}_{+}^n$, and $$K(\mathbb{R}^n) = \mathbb{R}^n.$$ Moreover by *eigen-decomposition*, $$K \sim \text{diag}\left(\sigma_{1}^2 \,{,}\ldots{,}\,\sigma_{n}^2\right).$$
>- Let $(\varphi_{j})_{j=1}^{n}$ be an orthonormal basis of $\mathbb{R}^n$.  $$K\left(\sum_{j=1}^{n}x_{j} \varphi_{j}\right) = \sum_{j=1}^{n}\sigma_{j}^2\,x_{j} \varphi_{j}$$
>- It follows that the Gaussian vector $X$ has expansion
>$$ 
> \begin{align}
> X =   \sum_{i=1}^{n}\sigma_i \xi_i \varphi_i
> \end{align} 
>$$ 
>where $\xi_{i}$ are *independent $\mathcal{N}(0,1)$-distributed* random variables.
>- For any $f, g \in \mathcal{X}^{*} = \mathcal{X}$, we have
>$$
>\begin{align*}
>\left\langle I^{*}f  \,,\, I^{*}g  \right\rangle_{\mathcal{X}_{\mathcal{N}}^{*}} &= \mathbb{E}_{ \mathcal{N} }\left[\left(\sum_{i=1}^{n}\sigma_{i}\,f_{i}\xi_{i}\right)\, \left(\sum_{i=1}^{n}\sigma_{i}\,g_{i}\,\xi_{i}\right)\right] \\
>&= \sum_{i=1}^{n}\sigma_{i}^2\,f_{i}g_{i} \\
>&= f^{T}\,K\,g = \left\langle  f\,,\,K\,g \right\rangle
>\end{align*}
>$$
>
>- A **$\mathcal{N}$-measurable linear functional** $z\in \mathcal{X}_{\mathcal{N}}^{*}$ has the following representation
>$$
>\left\langle z\,,\,x \right\rangle  = \sum_{j=1}^{n}z_{j}\,x_{j} 
>$$
>where $$z^T\,K\,z := \sum_{j=1}^{n}\sigma_{j}^2\,z_{j}^2 < \infty.$$
>- The **norm** in $\mathcal{X}_{\mathcal{N}}^{*}$ is $$\lVert z \rVert_{\mathcal{X}_{\mathcal{N}}^{*}}^2 = z^T\,K\,z = \sum_{j=1}^{n}\sigma_{j}^2\,z_{j}^2 $$
>- Then the *function* in RKHS of Gaussian process has the form
>$$
>\begin{align*}
>(Iz)(k) &= \left\langle  \varphi_{k}\,,\,I\,z \right\rangle \\
>&= \left\langle  I^{*}\varphi_{k}\,,\,z  \right\rangle_{\mathcal{X}_{\mathcal{N}}^{*}} \\
>&= \mathbb{E}_{ \mathcal{N} }\left[\left(\sum_{j=1}^{n}z_{j}\,\sigma_{j}\,\xi_{j}\right)\,\sigma_k\, \xi_k  \right] \\
>&= \sigma_{k}^2\,z_{k}
>\end{align*}
>$$
>- The function  $$h = Iz := \sum_{j=1}^{n}\sigma_{j}^2\,z_{j}\,\varphi_{j} \in \mathcal{H}_{\mathcal{N}}.$$
>- The **norm** in  *RKHS* of Gaussian process $$\lVert h \rVert_{\mathcal{H}_{\mathcal{N}}^{*}}^2 = \lVert z \rVert_{\mathcal{X}_{\mathcal{N}}^{*}}^2 = \sum_{j=1}^{n}\sigma_{j}^2\,z_{j}^2 = \sum_{j=1}^{n}\frac{h_{j}^2}{\sigma_{j}^2} = h^T\,K^{-1}\,h = \lVert K^{-1 / 2}h \rVert_{2}^2.$$ 
>- Thus the **RKHS** of Gaussian process $$\mathcal{H}_{\mathcal{N}} = \left\{ h \in \mathcal{X}:  \; h^T\,K^{-1}\,h < \infty\right\} = \mathbb{R}^n.$$
>- The **inner product** in $\mathcal{H}_{\mathcal{N}}$ is defined as $$\left\langle  h_{1}\,,\, h_{2}  \right\rangle_{\mathcal{H}_{\mathcal{N}}} = \sum_{j=1}^{n}\frac{(h_{1})_{j}\,(h_{2})_{j}}{\sigma_{j}^2}= \left\langle  K^{-1}h_{1}\,,\,h_{2}    \right\rangle.$$
>- Note that for $\mathcal{X}= \mathbb{R}^n$, 
>$$
>\mathcal{X} = \mathcal{X}^{*} = \mathcal{X}_{\mathcal{N}}^{*} = K(\mathcal{X}^{*}) = \mathcal{H}_{\mathcal{N}}.
>$$




## Hilbert Spaces associated with Gaussian Random Function on Banach Space


| base space             | Banach space $\mathcal{X} \subset \mathbb{C}^{T}$                                                                                                                                                                                                                                                                                    | dual space $\mathcal{X}^{*}$                                                                                                                                                                                                                                                                                                                                     |
| ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
|                        | **Gaussian process** $$X: \Omega \to \mathcal{X}$$ such that $X(\omega,\cdot)\in \mathcal{X}$                                                                                                                                                                                                                                        | $f\in \mathcal{X}^{*}: \mathcal{X} \to \mathbb{C}$ so that $$\left\langle  f, X \right\rangle := f(X)\sim \mathcal{N}(0, f(Kf))$$ is $\mathcal{N}$-distributed **random variable**,                                                                                                                                                                              |
| measure space          | $(\mathcal{X}, \mathscr{B}(\mathcal{X}), \mathcal{N})$ where $$\mathcal{N} = \mathcal{P} \circ X^{-1}$$ is the **Gaussian measure**                                                                                                                                                                                                  | **$\mathcal{N}$-measurable linear functional** $f$ such that<br>$$ \mathbb{E}_{ \mathcal{N} }\left[\left\langle  f, X \right\rangle\right] =  \mathbb{E}_{ \mathcal{N} }\left[f(X)  \right] = \int_{\mathcal{X}}f \;d\mathcal{N} < \infty$$<br>                                                                                                                  |
| covariance             | **covariance function** $$K:T \times T \to \mathbb{C}$$ such that <br>$$K(s,t)=  \mathbb{E}_{ \mathcal{N} }\left[X(s)X(t)  \right] = \mathbb{E}_{ \mathcal{N} }\left[\left\langle \delta_{s} , X \right\rangle \left\langle \delta_{t} , X \right\rangle  \right]$$<br>                                                              | **covariance operator** $$K: \mathcal{X}^{*}\to \mathcal{X}$$ such that $$\left\langle  f, Kg \right\rangle := f(Kg) :=\mathbb{E}_{ \mathcal{N} }\left[\left\langle f , X \right\rangle \left\langle g , X \right\rangle \right] =  \mathbb{E}_{ \mathcal{N} }\left[f(X) g(X) \right]$$                                                                          |
| map                    | the **adjoint** $$I: \mathcal{X}_{\mathcal{N}}^{*} \to \mathcal{X}$$                                                                                                                                                                                                                                                                 | **embedding** $$I^{*}: \mathcal{X}^{*} \to \mathcal{X}_{\mathcal{N}}^{*} \subset L^2(\mathcal{X}, \mathcal{N})$$                                                                                                                                                                                                                                                 |
|                        | for any $f\in \mathcal{X}^{*}$ and $g\in \mathcal{X}_{\mathcal{N}}^{*},$ we have $$\left\langle f , I\,g \right\rangle = \left\langle I^{*}f , g \right\rangle_{\mathcal{X}_{\mathcal{N}}^{*}}$$                                                                                                                                     | for any $f\in \mathcal{X}^{*}$ and $g\in \mathcal{X}_{\mathcal{N}}^{*},$ we have $$\left\langle f , I\,I^{*}\,g \right\rangle = \left\langle I^{*}f , I^{*}\,g \right\rangle_{\mathcal{X}_{\mathcal{N}}^{*}} =  \mathbb{E}_{ \mathcal{N} }\left[ \left\langle f , X \right\rangle \left\langle g , X \right\rangle\right] = \left\langle f  , Kg \right\rangle$$ |
| range of map           | the **kernel** of distribution $\mathcal{N},$ $$\mathcal{H}_{\mathcal{N}} := I(\mathcal{X}_{\mathcal{N}}^{*})$$<br>                                                                                                                                                                                                                  | the **space** of **all $\mathcal{N}$-measurable linear functionals** $$\mathcal{X}_{\mathcal{N}}^{*} := \overline{I^{*}(\mathcal{X}^{*})} = \left\{ f \in L^1(\mathcal{X}, \mathcal{N}): \int_{\mathcal{X}}\lVert f \rVert_{\mathcal{X}}^2\;d\mathcal{N}\; < \infty  \right\}$$                                                                                  |
| **Hilbert space**      | $\mathcal{H}_{\mathcal{N}} \subset \mathcal{X}$ is Hilbert space                                                                                                                                                                                                                                                                     | $\mathcal{X}_{\mathcal{N}}^{*} \subset L^2(\mathcal{X}, \mathcal{N})$ is Hilbert space                                                                                                                                                                                                                                                                           |
| inner product          | for any $x, y \in \mathcal{H}_{\mathcal{N}},$$$\left\langle  x, y \right\rangle_{\mathcal{H}_{\mathcal{N}}} = \left\langle I^{-1}\,x \;,\; I^{-1}\,y \right\rangle_{\mathcal{X}_{\mathcal{N}}^{*}} =  \mathbb{E}_{ \mathcal{N} }\left[ \left\langle I^{-1}\,x , X \right\rangle\,\left\langle I^{-1}\,y , X \right\rangle  \right]$$ | for any $f, g\in \mathcal{X}_{\mathcal{N}}^{*},$ $$\left\langle f ,g  \right\rangle_{\mathcal{X}_{\mathcal{N}}^{*}} =  \mathbb{E}_{ \mathcal{N} }\left[\left\langle f , X \right\rangle \left\langle g , X \right\rangle \right]  =\mathbb{E}_{\mathcal{N}}\left[f(X)\, g(X) \right]$$                                                                           |
| **reproducing kernel** | $$K(s,\cdot) = K\,\delta_{s}$$                                                                                                                                                                                                                                                                                                       |                                                                                                                                                                                                                                                                                                                                                                  |
|                        | $$K(s,t) = \left\langle K(s, \cdot) , K(t, \cdot) \right\rangle_{\mathcal{H}_{\mathcal{N}}}$$                                                                                                                                                                                                                                        | $$K = I\,I^{*}$$                                                                                                                                                                                                                                                                                                                                                 |
|                        |                                                                                                                                                                                                                                                                                                                                      |                                                                                                                                                                                                                                                                                                                                                                  |





-----------
##  Recommended Notes and References

- [[Lp Space]]

- [[Lectures on Gaussian Processes by Lifshits]]
- [[Mathematical Foundations of Infinite Dimensional Statistical Models by Gine]]
