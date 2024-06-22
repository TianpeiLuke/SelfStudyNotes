---
tags:
  - concept
  - math/functional_analysis
  - math/linear_algebra
keywords:
  - riesz_representation_theorem
topics:
  - functional_analysis
  - linear_algebra
name: Riesz Representation Theorem
date of note: 2024-05-15
---

## Theorem

>[!important]
>**Name**: The Riesz Representation Theorem or *Riesz–Fréchet representation theorem*

>[!important] The Riesz Representation Theorem
>Let $(\mathcal{H}, \left\langle \,,\,   \right\rangle)$ be a *Hilbert space* and the inner product is *linear in its first argument* and *conjugate-linear in its second argument*.
>
>For each continuous linear functional $T \in \mathcal{H}^{*}$, there exists a **unique** $f_{T} \in \mathcal{H}$ such that 
>$$
> \begin{align*}
> T(x) &= \left\langle  x\,,\, f_{T}   \right\rangle
> \end{align*}
>$$  
>for all $x \in \mathcal{H}$. 
>
>In addition, the norm of linear functional under dual space $\mathcal{H}^{*}$  is equal to the norm of vector in $\mathcal{H}$
>$$\lVert f_{T} \rVert_{\mathcal{H}} = \lVert T \rVert_{\mathcal{H}^{*}}.$$

^4ad0dc

>[!important]
>Importantly for _complex_ Hilbert spaces, $f_{T}$ is always located in the **_conjugate-linear_ coordinate** of the inner product.

>[!important] Corollary
>The *canonical map* from $\mathcal{H}$ to its dual $\mathcal{H}^{*}$ 
>$$
>\Phi: x \mapsto \left\langle \cdot \,,\, x   \right\rangle
>$$
>is an **isometric isomorphism**.  That is,  a Hilbert space $\mathcal{H}$ is **isometric isomorphic** to its *dual* $\mathcal{H}^{*}$
>$$
>\mathcal{H} \simeq \mathcal{H}^{*}.
>$$

- [[Isometry and Isometric isomorphism]]

>[!info]
>Moreover, $\Phi$ is **conjugate-linear**
>$$
>\begin{align*}
>\Phi(a y + b z) &= \left\langle  \cdot\,,\, ay + bz \right\rangle \\
>&= \bar{a} \left\langle \cdot \,,\, y \right\rangle + \bar{b} \left\langle  \cdot\,,\, z   \right\rangle\\
>&= \bar{a}\Phi(y) +  \bar{b}\Phi(z)
\end{align*}
>$$


## Explanation

>[!info]
>This version assume that the inner product is **linear in its first argument**, and **conjugate-linear in its second argument**:
>$$
>\left\langle ax+by \,,\, z   \right\rangle = a \left\langle  x\,,\,z    \right\rangle + b \left\langle  y\,,\,z    \right\rangle
>$$
>and
>$$
>\left\langle  x\,,\,ay + bz    \right\rangle = \bar{a} \left\langle x \,,\, y \right\rangle + \bar{b} \left\langle  x\,,\, z   \right\rangle
>$$

>[!info]
>*The Riesz Representation Theorem* is also called **The Riesz Lemma**. 

- [[Functional Analysis by Reed]]

>[!important]
>The inner product in $\mathcal{H}$ and its dual space $\mathcal{H}^{*}$ are related
>$$
>\left\langle  \Phi(x)\,,\, \Phi(y)   \right\rangle_{\mathcal{H}^{*}} = \overline{\left\langle  x\,,\, y   \right\rangle_{\mathcal{H}}} = \left\langle y \,,\, x   \right\rangle_{\mathcal{H}}
>$$


>[!info]
>The canonical dual pairing [[Canonical Dual Pairing]] in Hilbert space
>$$
>\left\langle  f\,,\,   x \right\rangle = f(x), \quad \forall f\in X^{*} \text{ and } x\in X
>$$
>is equivalent to
>$$
>\left\langle  f\,,\,   x \right\rangle = \left\langle  x\,,\,   h_{f} \right\rangle_{\mathcal{H}} = \overline{\left\langle  h_{f}\,,\,x    \right\rangle}
>$$
>where $h_{f}$ is the unique vector in $\mathcal{H}$ corresponding to $f$.

## Proof

>[!info]
>Let $\mathcal{N}$ be the **kernel** of linear map $T$, i.e. $$\mathcal{N} := \{ x \in \mathcal{H}: T(x) = 0 \} = T^{-1}(0).$$
>$\mathcal{N}$ is a **closed subspace** of $\mathcal{H}$
 
- [[Range and Kernel of Linear Operator]]

>[!info]
>If $\mathcal{H} = \mathcal{N}$, then we can choose $f_{T}=0 \in \mathcal{H}$ so that 
>$$
>T(x) = 0 = \left\langle  x\,,\, f_{T}   \right\rangle
>$$
>for all $x\in \mathcal{H} = \mathcal{N}.$

>[!important]
>Assume $\mathcal{N} \subsetneq \mathcal{H}$. 
>
>By [[Projection Theorem of Hilbert Spaces]], there exists an *non-zero* $x_{0}\in \mathcal{N}^{\bot}.$
>
>Now define $$f_{T} := \frac{\overline{T(x_{0})}}{\lVert x_{0} \rVert_{2}^2 } x_{0}.$$
>We claim that $f_{T} \in \mathcal{H}$ is what we want. 

>[!info]
>If $x\in \mathcal{N}$, then $T(x) = 0$ and $$\left\langle  x\,,\,f_{T}    \right\rangle = \left\langle  x\,,\,   \frac{\overline{T(x_{0})}}{\lVert x_{0} \rVert_{2}^2 } x_{0}  \right\rangle = \frac{T(x_{0})}{\lVert x_{0} \rVert_{2}^2 }\left\langle  x\,,\,x_{0}    \right\rangle = 0$$ since $x_{0}\in \mathcal{N}^{\bot}.$

>[!info]
>If $x = \alpha x_{0}$, then
>$$
>T(x) = T(\alpha x_{0}) = \alpha\,T(x_{0})
>$$
>And
>$$
>\left\langle  \alpha x_{0}\,,\,   \frac{\overline{T(x_{0})}}{\lVert x_{0} \rVert_{2}^2 } x_{0}  \right\rangle = \alpha \frac{T(x_{0})}{\lVert x_{0} \rVert_{2}^2 }\left\langle  x_{0}\,,\,x_{0}    \right\rangle =  \alpha \frac{T(x_{0})}{\lVert x_{0} \rVert_{2}^2 }\lVert x_{0} \rVert_{2}^2 = \alpha\,T(x_{0})
>$$
>Thus
>$$
>T(x) = \left\langle  x\,,\,f_{T}    \right\rangle
>$$

>[!info]
>Note that $T$ and $\left\langle  \cdot\,,\,f_{T}    \right\rangle$ agree on $\mathcal{N}$ and $\{\alpha x_{0}\}$. It follows that 
>$$
>T(x) = \left\langle  x\,,\,f_{T} \right\rangle
>$$
>for all  $x \in \text{span}\{ \mathcal{N}, x_{0} \}.$

>[!info]
>We show that $\mathcal{H} = \text{span}\{ \mathcal{N}, x_{0} \}$.
>
>This is because every vector $x\in \mathcal{H}$ can be **uniquely represented** as
>$$
>x = \left(x - \frac{T(x)}{T(x_{0}) } x_{0} \right) + \frac{T(x)}{T(x_{0}) } x_{0}
>$$ 
>where the second term is in $\{ \alpha\,x_{0} \}$ and the first term $$x - \frac{T(x)}{T(x_{0}) } x_{0}  \in \mathcal{N}$$ since
>$$
>  T\left(x - \frac{T(x)}{T(x_{0}) } x_{0} \right) = T(x) - \frac{T(x)}{T(x_{0}) } T(x_{0}) = 0.
>$$
>Q.E.D.


## Generalization

>[!important]  The Riesz Representation for Sesquilinear Form
>Let $B(\cdot, \cdot)$ be a function from $\mathcal{H} \times \mathcal{H}$ to $\mathbb{C}$ which satisfies: for all $x, y, z \in \mathcal{H}$, $\alpha, \beta \in \mathbb{C}$. 
> 
> 1. **Linearity** $$B(\alpha x + \beta y, z) = \alpha B(x, z) + \beta B(y, z)$$
> 2. **Conjugate Linearity** $$B(x, \alpha y + \beta z) = \overline{\alpha} B(x, y) + \overline{\beta} B(x, z)$$
> 3. **Boundedness** $$|B(x, y)| \le C\, \lVert x \rVert_{\mathcal{H}}\; \lVert y \rVert_{\mathcal{H}}$$
> 
> 
> Then there is a **unique** *bounded linear transformation* $A: \mathcal{H} \rightarrow \mathcal{H}$ so that
>$$ 
> \begin{align*}
> B(x, y) = \left\langle  Ax\,,\,y \right\rangle, \quad \forall x, y \in \mathcal{H}. 
> \end{align*}
>$$  
>
>The **norm** of $A$ is the *smallest constant* $C$ such that 3. holds.

^8d0eaf

- [[Sesquilinear Form]]
- [[Lax-Milgram Lemma]]

>[!important]
>Note that the linear map $A$ must be applied in the **linear coordinate** of the sesquilinear form.


>[!info] Proof
>Fixed $x$, we have a bounded linear functional in $y$ as
>$$
>f_{x} := \overline{B(x, \cdot)} \in \mathcal{L}(\mathcal{H})
>$$
>
>By *Riesz representation theorem*, there exists a *unique vector* $b_{f} \in \mathcal{H}$ such that
>$$
>f_{x}(y) = \overline{B(x, y)} = \left\langle  y, b_{f} \right\rangle.
>$$
>or
>$$
> B(x, y) = \left\langle  b_{f} , y \right\rangle
>$$
>Note that $b_{f}$ is a *linear map* of $x$ since $B(x,y)$ is *linear* in $x$ for fixed $y$ and the inner product is *linear in its first coordinate*. That is, there exists a unique $A$ such that
>$$
>b_{f} = A\,x 
>$$
>
>Given that $B$ is bounded, we see that $A$ is *bounded* as well. Q.E.D.





-----------
##  Recommended Notes and References

- [[Dual Space of Hilbert Space]]
- [[Dual Normed Space and Dual Banach Space]]
- [[Bounded Linear Functional]]
- [[Hilbert Space]]


- [[Functional Analysis by Reed]]
- [[Optimization by Vector Space Methods by Luenberger]]
- [[Introductory Functional Analysis with Applications by Kreyszig]]
- [[Real Analysis by Royden]]