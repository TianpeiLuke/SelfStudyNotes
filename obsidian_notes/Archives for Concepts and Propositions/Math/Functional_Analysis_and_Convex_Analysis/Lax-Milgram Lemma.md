---
tags:
  - concept
  - math/functional_analysis
keywords:
  - lax_milgram_lemma
topics:
  - functional_analysis
name: Lax-Milgram Lemma
date of note: 2024-06-21
---

## Concept Definition

>[!important]
>**Name**: Lax-Milgram Lemma

![[Riesz Representation Theorem#^4ad0dc]]

![[Riesz Representation Theorem#^8d0eaf]]

>[!important] Lax-Milgram Lemma
>Let $\mathcal{H}$ be a *Hilbert space*. Suppose $B(\cdot, \cdot)$ is a function from $\mathcal{H} \times \mathcal{H}$ to $\mathbb{C}$ which satisfies: for all $x, y, z \in \mathcal{H}$, $\alpha, \beta \in \mathbb{C}$. 
> 
> 1. **Linearity** $$B(\alpha x + \beta y, z) = \alpha B(x, z) + \beta B(y, z)$$
> 2. **Conjugate Linearity** $$B(x, \alpha y + \beta z) = \overline{\alpha} B(x, y) + \overline{\beta} B(x, z)$$
> 3. **Boundedness** $$|B(x, y)| \le C_{1}\, \lVert x \rVert_{\mathcal{H}}\; \lVert y \rVert_{\mathcal{H}}$$ for some constant $C_{1} >0$
> 4. **Boundedness** $$B(x, x)\ge C_{2}\, \lVert x \rVert_{\mathcal{H}}^2$$ for some constant $C_{2} >0$
> 
> 
> Then for *each* $f \in \mathcal{H}^{*}$, there is a **unique** $h_{f} \in \mathcal{H}$ such that 
>$$ 
> \begin{align*}
> f(x) = B(x, h_{f}), \quad \forall x \in \mathcal{H}. 
> \end{align*}
>$$  

^d7879a


- [[Riesz Representation Theorem]]
- [[Real Analysis by Royden]] pp 320
- [[Hilbert Space]]


## Explanation





-----------
##  Recommended Notes and References


- [[Hilbert Space]]
- [[Riesz Representation Theorem]]


- [[Functional Analysis by Reed]]
- [[Real Analysis by Royden]] pp 320
- [[Partial Differential Equations by Evans]]