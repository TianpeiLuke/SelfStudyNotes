---
tags:
  - entry_point
  - concept
  - math/topology
  - math/functional_analysis
keywords: 
topics:
  - topology
  - functional_analysis
name: 
date of note: 2024-05-08
---

##  List of Concepts

- $\mathcal{C}(X)$ i.e. [[Space of all Continuous Functions]]
- $\mathcal{BC}(X)$ i.e. [[Space of Bounded Continuous Function]]
- $\mathcal{C}_{0}(X)$ i.e. [[Continuous Functions that Vanish At Infinity]]
- $\mathcal{C}_{c}(X)$ i.e. [[Continuous Functions with Compact Support]]

### Other Continuity

- [[Space of Continuous Differentiable Functions]]
- [[Lipschitz Continuous Function]]
- [[Absolutely Continuous Function]]
- [[Hölder Condition and Hölder Continuous Function]]
- [[Space of Functions with Bounded Variation]]
- [[Locally Bounded Variation Function]]
- [[Convex Function]]


![[continuous_function_relations.png]]

>[!important]
>Relationship between other continuity conditions
>$$
>\text{continuouly differentiable }\subset \text{ Lipschitz continuous }\subset \text{ Hölder continuous } \subset \text{ uniformly continuous } \subset \text{ continuous }
>$$
## Explanation

>[!important]
>$$
> \begin{align*}
> \mathcal{C}_{c}(X)  \subseteq \mathcal{C}_{0}(X) \subseteq \mathcal{BC}(X) \subseteq \mathcal{C}(X)
> \end{align*}
>$$ 

>[!important]
>$$
> \begin{align*}
> \mathcal{C}_{c}(X)  \subseteq L^1(X)
> \end{align*}
>$$ 
>and it is a **dense** subset.

- [[Simple Approximation Theorem of Lp Function]]
- [[Dense Set]]


## Dual Space 

- [[Duality of Measure and Functional of Continuous Functions]]
- [[Locally Compact Hausdorff Space]]
- [[Development of Signed Measures Decomposition and Density]]

>[!important]
>For *locally compact Hausdorff space* $X$,
>$$\mathcal{M}(X) \simeq   (\mathcal{C}_{0}(X))^{*}$$

>[!important]
>For open subset $\Omega \subset \mathbb{R}^n$,
>$$\left\{ \phi \mapsto \int_{\Omega}u\,\text{div}(\phi)\,dx: u \in BV(\Omega) \right\}  \simeq   (\mathcal{C}_{0}(\Omega, \mathbb{R}^n))^{*}$$

- [[Space of Functions with Bounded Variation]]


-----------
##  Recommended Notes and References


- [[Topology Book by Munkres]]
- [[Real Analysis Modern Techniques and Their Applications by Folland]]
- [[Real Analysis by Royden]]
- [[Functional Analysis by Reed]]