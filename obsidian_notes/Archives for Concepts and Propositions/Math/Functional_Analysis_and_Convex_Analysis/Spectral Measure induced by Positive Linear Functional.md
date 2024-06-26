---
tags:
  - concept
  - math/functional_analysis
  - math/measure_theory
keywords: 
topics:
  - functional_analysis
  - measure_theory
name: 
date of note: 2024-05-27
---

## Concept Definition

>[!important]
>**Name**: Spectral Measure induced by Positive Linear Functional

>[!info]
>For each $\psi \in \mathcal{H}$, defines a **bounded linear functional** on $\mathcal{L}(\mathcal{H})$ as below:
>$$
> \begin{align*}
> \widetilde{I}_{\psi}: A \mapsto \left\langle A \psi\,,\,    \psi \right\rangle_{\mathcal{H}}.
> \end{align*} 
>$$ 

>[!info]
>Then by **continuous functional calculus**, there exists a *unique map* $$\phi_{A}: \mathcal{C}(\sigma(A)) \to \mathcal{L}(\mathcal{H}), \qquad  f \mapsto \phi_{A}(f) := f(A).$$
>
>We can define a composite map $$I_{\psi} =\widetilde{I}_{\psi} \circ \phi_{A}: \mathcal{C}(\sigma(A)) \rightarrow  \mathbb{R},$$ which is seen as a **positive linear functional** (*not positive operator*) on $\mathcal{C}(\sigma(A))$.
>
>That is $\forall \psi \in \mathcal{H}$,
>$$
> \begin{align*}
> I_{\psi}(f) :=  \left\langle  f(A)\psi\,,\, \psi \right\rangle_{\mathcal{H}} \ge 0 \qquad \text{ whenever }f\ge 0.
> \end{align*}
>$$ 

- [[Positive Linear Functional]]
- [[Continuous Functional Calculus]]

>[!info]
> For a **bounded self-adjoint operator** $A$, the **spectrum** $$\sigma(A) \subset \mathbb{R}$$ is a *__closed bounded__ subset* of $\mathbb{R}$ so it is **compact**. 

- [[Spectral Radius of Linear Operator]]
- [[Spectrum of Self-Adjoint Linear Operator]]


> [!info]
> Thus $\mathcal{C}(\sigma(A))$ is a *space of __continuous functions__* on *__compact domain__*, which, by **Riesz-Markov Representation theorem**, has *dual space* that is *isomorphic* to *the space of complex __positive Radon measures__* on $\sigma(A)$. 

>[!info]
> In other word, for each $\psi \in \mathcal{H}$, there *exists* a **positive Radon measure** on **spectral domain** $$\mu_{\psi} \in \mathcal{M}_{+}(\sigma(A)) \simeq (\mathcal{C}(\sigma(A)))^{*}$$ so that 
> $$
> \begin{align}
> I_{\psi}(f) := \left\langle f(A)\psi\,,\,\psi  \right\rangle_{\mathcal{H}}  &= \int_{\sigma(A)} f\; d\mu_{\psi}.
> \end{align}
>$$
>

- [[Riesz-Markov Representation Theorem]]

>[!important] Definition
>For each $\psi \in \mathcal{H}$, the induced *Radon measure* $\mu_{\psi} \in \mathcal{M}_{+}(\sigma(A))$ defined in
>$$
>\left\langle f(A)\psi\,,\,\psi  \right\rangle_{\mathcal{H}}  = \int_{\sigma(A)} f\; d\mu_{\psi},\quad \forall f \in \mathcal{C}(\sigma(A))
>$$
> is called the **spectral measure** *associated with* the vector $\psi \in \mathcal{H}$. 

- [[Radon Measure]]

## Explanation





## Parseval Identity

>[!info]
> Here  let $$f = \bar{g}g,$$ the equation above becomes
>$$ 
> \begin{align}
> \left\langle \bar{g}g(A) \psi\,,\,\psi \right\rangle_{\mathcal{H}} &= \int_{\sigma(A)} \bar{g}g \;d\mu_{\psi} \\
>&= \int_{\sigma(A)} \lvert g(\lambda) \rvert^2  d\mu_{\psi}(\lambda) \nonumber\\ 
> \implies \lVert g(A)\psi \rVert_{\mathcal{H}}^2  &= \int_{\sigma(A)} \lvert g(\lambda) \rvert^2  d\mu_{\psi}(\lambda),  
> \end{align}
>$$ 
> which confirms the **Parseval's identity** between time and spectral domain. That is, *the total energy* in **time-domain** should match *the total energy* in **spectral domain**. The last equality holds since
> $$
> \lVert g(A)\psi \rVert_{\mathcal{H}}^2  = \left\langle  g(A)\psi\,,\,g(A)\psi \right\rangle = \left\langle \bar{g}(A) g(A)\psi\,,\, \psi \right\rangle =  \left\langle \bar{g}g(A)\psi\,,\,\psi \right\rangle 
> $$

- [[Adjoint of Bounded Operator in Hilbert Space]]
- [[Continuous Functional Calculus]]



-----------
##  Recommended Notes and References

- [[Riesz-Markov Representation Theorem]]
- [[Continuous Functional Calculus]]
- [[Positive Linear Functional]]
- [[Radon Measure]]


- [[Functional Analysis by Reed]]