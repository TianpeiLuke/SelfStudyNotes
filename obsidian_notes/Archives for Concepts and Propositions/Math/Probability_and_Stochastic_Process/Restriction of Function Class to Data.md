---
tags:
  - concept
  - math/stochastic_process
  - machine_learning/theory
  - math/functional_analysis
  - statistics/concentration_inequality
keywords:
  - restriction_of_function_class_to_data
topics:
  - stochastic_process
  - machine_learning_theory
name: Restriction of Function Class to Data
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Restriction of Function Class to Data

>[!important] Definition
>Let $\mathcal{F}$ be a class of **Boolean functions** from $\mathcal{X}$ to $\set{0,1}$ and let $$\mathcal{D} = \set{x_1 \,{,}\ldots{,}\, x_n} \subset \mathcal{X}.$$
> 
>The **restriction of $\mathcal{F}$ to $\mathcal{D}$** is the set of *functions* from $\mathcal{D}$ to $\set{0,1}$ that can be **derived from** $\mathcal{F}$. 
>
>That is,
>$$
> \begin{align*}
> \mathcal{F}_{\mathcal{D}} := \set{(f(x_1) \,{,}\ldots{,}\, f(x_n)): f \in \mathcal{F}},
> \end{align*}
>$$ 
> where we *represent* each function from $\mathcal{X}$ to $\set{0,1}$ as a **vector** in $\set{0,1}^{|\mathcal{D}|}$.

^60c89d


## Explanation

### Encoding Perspective

>[!important]
>We can define a **binary encoding** of any function $f$ as
>$$
>E: \mathcal{F} \to \{0, 1\}^k
>$$
>where 
>$$
>f \mapsto E(f).
>$$
>
>Then $\mathcal{F}_{\mathcal{D}}$ is the **a subspace of binary encoding** of **boolean functions** $f$.

- [[Error Correcting Code]]
- [[Minimum Description Length]]


>[!important]
>The idea of VC dimension is to find the *best possible* **dimension** for **encoding representation** of $\mathcal{F}$.




### Functional Perspective

>[!important]
>We can define a **linear operator** $I_{\mathcal{D}}$ by combining $n$ **evaluation functionals** at each point in $\mathcal{D}$
>
>That is,
>$$
> I_{\mathcal{D}}:\; \mathcal{F} \to \{0, 1\}^{|\mathcal{D}|}
>$$
>such that
>$$
> f \mapsto I_{\mathcal{D}}(f) := (f(x_1) \,{,}\ldots{,}\, f(x_n)).
>$$
>
>So the *restriction* of $\mathcal{F}$ to $\mathcal{D}$ is the **range** of a *linear operator*  $I_{\mathcal{D}}$:
>$$
>\mathcal{F}_{\mathcal{D}} := I_{\mathcal{D}}(\mathcal{F})
>$$

- [[Covariant Tensor on Vector Space]]
- [[Range and Kernel of Linear Operator]]

>[!important]
>By *restriction* of $\mathcal{F}$ on a **finite** point set, we convert an **infinite dimensional space** $\mathcal{F}$ into a **$|\mathcal{D}|$-dimensional vector space** . 


>[!important]
>For fixed $\mathcal{D}$, the linear operator $I_{\mathcal{D}}$ **may not be injective** since *different functions* would output the *same binary vector* on a given data.
>
>The key for this formulation is to define an **equivalent relation** *given data* $\mathcal{D}$
>$$
>f \sim_{\mathcal{D}} g  \quad \iff \quad I_{\mathcal{D}}(f) = I_{\mathcal{D}}(g).
>$$
>or
>$$
>f \sim_{\mathcal{D}} g  \quad \iff \quad I_{\mathcal{D}}(f-g) = 0.
>$$
>
>Thus by [[Rank–Nullity Theorem]]
>$$
>\mathcal{F}_{\mathcal{D}} \;\simeq\; \mathcal{F} / \sim_{\mathcal{D}} =  \mathcal{F} \;/\; \text{ker}(I_{\mathcal{D}})
>$$

- [[Injective Function]]
- [[Quotient Space of Vector Space]]
- [[Rank–Nullity Theorem]]



>[!info]
>It is important to know if $I_{\mathcal{D}}$ is **surjective**, which is related to [[Shattering of Data by Function Class]]




-----------
##  Recommended Notes and References

- [[Shattering of Data by Function Class]]
- [[VC Dimension]]

- [[Intersection of Set Family to Set]]


- [[PAC Learnable and Agnostic PAC Learnable]]
- [[Bounded Difference Inequality]]
- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[High Dimensional Statistics A Non-Asymptotic Viewpoint by Wainwright]]

- [[Empirical Process and Empirical Measure]]