---
tags:
  - entry_point
  - concept
  - math/functional_analysis
  - math/linear_algebra
  - math/measure_theory
  - math/probability
keywords:
  - uniform_convergence
  - pointwise_convergence
  - uniformly_almost_everywhere_convergence
  - almost_uniform_convergence
  - pointwise_almost_everywhere_convergence
  - convergence_in_mean
  - convergence_in_l1_norm
  - convergence_in_measure
topics:
  - functional_analysis
  - real_analysis
  - measure_theory
  - probability
name: modes of convergence
date of note: 2024-05-05
---

## Modes of Convergence


>[!info]
>The reason there are some many different modes of convergence is due to the **infinite dimensionality** of *the function space.* 
>
>For **finite dimension space**, these modes of convergence are all **equivalent.**

>[!info]
>For Probability, the mode of convergence is for **convergence of random variables**, i.e. $Y^X = \mathbb{R}^{\Omega}$.


### List of Modes of Convergence

>[!info]
>The definition of **convergence** can be stated as follows:
>
>A sequence (net) of functions $f_{n}$ *converges to* a function $f$ if in every *neighborhood* of $f$ in some space, *all but a finitely many* of $f_{n}$ are in that neighborhood. 
>
>


#### Basic Convergence

- [[Pointwise Convergence]]
- [[Uniform Convergence]]
- [[Locally Uniform Convergence]]

#### Convergence in Topology

>[!info]
>$f_{n}$ is *"close"* to $f$ under a certain **definition** of *"closeness".*

- [[Convergence in Norm]]
- [[Convergence in Lp norm]]
- [[Uniformly Almost Everywhere Convergence]]
- [[Uniformly Almost Everywhere Convergence]]
- [[Norm Topology]]
- [[Topology of Pointwise Convergence]]
- [[Uniform Topology on Metric Spaces]]
- [[Topology of Compact Convergence]]
- [[Compact Open Topology]]
- [[Weak Topology of Banach Space]]
- [[Weak-star Topology of Banach Space]]
- [[Weak Convergence in Banach Space]]
- [[Weak Convergence in Hilbert Space]]
- [[Convergence in Distribution]]

#### Approximate Convergence w.r.t. Measure

>[!info]
>$f_{n}$ is *"approximately close"* to $f$ with **some small exceptions**.

- [[Pointwise Almost Everywhere Convergence]]
- [[Uniformly Almost Everywhere Convergence]]
- [[Almost Uniform Convergence]]
- [[Convergence in Measure]]

>[!info]
>We can consider $f = g, a.s.$ as *equivalence relation*, thus the convergence almost everywhere is convergence in **quotient topology.**

- [[Tightness of Integrable Functions]]
- [[Uniform Integrable Family of Functions]]
- [[Vitali Lp Convergence Theorem]]

- [[Tight Family of Integrable Functions]]
- [[Uniform Integrable Family of Functions]]
- [[Vitali Convergence Theorem for Uniformly Integrable Tight Functions]]


#### Convergence of (Bounded) Operators

- [[Uniform Operator Topology]]
- [[Strong Operator Topology]]
- [[Weak Operator Topology]]


#### Convergence within a Function Class




### Comparison on Topological and Analytical Properties

>[!important]
>Mode of convergence concerns on **the convergence of functions** under various **different topological properties** of the function spaces $\mathcal{C}(X, \mathbb{R})$ or $\mathcal{L}^{1}(X, \mathbb{R})$. 
>
>The domain and co-domain of these functions also have various requirements on the *topological* and *analytical properties*.

| Modes of Convergence                                                             | **Function Space** $Y^X$                                                                                                   | **Topology** of **Function Space**                                                                           | **Property** of **Domain Space** $X$                                                                                  | **Codomain Space**        | **Topology** of **Codomain** Space $Y$                                                   |
| -------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------- | ------------------------- | ---------------------------------------------------------------------------------------- |
| [[Pointwise Convergence]]                                                        | $Y^X$                                                                                                                      | [[Topology of Pointwise Convergence]]<br><br>**equivalently**,<br><br>[[Weak-star Topology of Banach Space]] | $-$                                                                                                                   | $Y$, usually $\mathbb{R}$ | $Y$ is metric space                                                                      |
| [[Uniform Convergence]]                                                          | $Y^X$                                                                                                                      | [[Uniform Topology on Metric Spaces]]                                                                        | $-$                                                                                                                   | $Y$, usually $\mathbb{R}$ | $Y$ is metric space                                                                      |
| [[Pointwise Almost Everywhere Convergence]]                                      | $M(\mathscr{F}, \mathscr{G}) \subset Y^X$                                                                                  | [[Topology of Pointwise Convergence]] outside a null set                                                     | Measure space $(X, \mathscr{F}, \mu)$                                                                                 | $\mathbb{R}$              | $Y$ is *metric measurable* space <br>$(Y, \mathscr{G})$                                  |
| [[Uniformly Almost Everywhere Convergence]]                                      | $M(\mathscr{F}, \mathscr{G}) \subset Y^X$                                                                                  | [[Uniform Topology on Metric Spaces]] outside a null set                                                     | Measure space $(X, \mathscr{F}, \mu)$                                                                                 | $\mathbb{R}$              | $Y$ is *metric measurable*  space <br>$(Y, \mathscr{G})$                                 |
| [[Almost Uniform Convergence]]                                                   | $M(\mathscr{F}, \mathscr{G}) \subset Y^X$                                                                                  | [[Uniform Topology on Metric Spaces]] outside sets with arbitrary small measure                              | Measure space $(X, \mathscr{F}, \mu)$                                                                                 | $\mathbb{R}$              | $Y$ is *metric measurable*  space <br>$(Y, \mathscr{G})$                                 |
| [[Convergence in Measure]]                                                       | $M(\mathscr{F}, \mathscr{G}) \subset Y^X$                                                                                  | $-$                                                                                                          | Measure space $(X, \mathscr{F}, \mu)$                                                                                 | $\mathbb{R}$              | $Y$ is *metric measurable*  space <br>$(Y, \mathscr{G})$                                 |
| [[Convergence in Lp norm]]                                                       | $\mathcal{L}^{1}(X, Y) \subset Y^X$<br>Banach Space                                                                        | [[Norm Topology]] (Strong Topology)                                                                          | Measure space $(X, \mathscr{F}, \mu)$ <br><br>                                                                        | $\mathbb{R}$              | $Y$ is *metric measurable*  space <br>$(Y, \mathscr{G})$;<br><br>Normed Vector space<br> |
| [[Convergence in Norm]]                                                          | $\mathcal{L}^{1}(X, Y) \subset Y^X$<br>Banach Space                                                                        | [[Norm Topology]]                                                                                            | $-$                                                                                                                   | $-$                       | $Y$ is *measurable*  space <br>$(Y, \mathscr{G})$;<br><br>**normed vector space**        |
| **Uniform Convergence** within **Compact Set**                                   | $Y^X$                                                                                                                      | [[Topology of Compact Convergence]]                                                                          | Topological space $(X, \mathscr{T})$                                                                                  | $Y$                       | $Y$ is *metric* space                                                                    |
| **Convergence** under **compact open topology**                                  | $Y^X$                                                                                                                      | [[Compact Open Topology]]                                                                                    | Topological space $(X, \mathscr{T})$                                                                                  | $Y$                       | *Topological space* $(Y, \mathscr{S})$                                                   |
| [[Convergence in Distribution]]<br><br>or<br><br>__Weak\* Convergence__ <br><br> | The space of Radon measures<br>$\mathcal{M}_{+}(X)$;<br>Banach Space<br><br><br>dual space  $(\mathcal{C}_{0}(X))^{*}$<br> | [[Weak Topology of Banach Space]]<br>                                                                        | Metric measurable space <br>$(X, \mathscr{F},\mu, d)$<br><br><br>$\mathcal{C}_{0}(X)$, with [[Compact Open Topology]] | $\mathbb{R}$              | Borel measure space                                                                      |





>[!info]
> - $M(\mathscr{F}, \mathscr{G})$ is the space of all **$\mathscr{F} /\mathscr{G}$ measurable functions**.
>   $$M(\mathscr{F}, \mathscr{G}) := \left\{ f\in Y^X:  f^{-1}(U) \in \mathscr{F}, \forall U \in \mathscr{G} \right\} $$
> - $\mathcal{L}(X, \mathbb{R})$ is the space of all **absolutely integrable functions**.
>   $$\mathcal{L}^{1}(X, \mathbb{R}) := \left\{ f\in M(\mathscr{F}, \mathcal{B}):   \int_{X} |f| d\mu < \infty  \right\} $$
> - $\mathcal{M}_{+}(X)$ is the space of **positive Radon measures**



### Comparison using Tail Event and Width

- [[Modes of Convergence]]
- [[Modes of Convergence in Tail Support and Width]]
- [[Tail sigma Algebra]]


>[!info]
>- **Event**: $$E_{n,\epsilon} := \set{x \in X: | f_n(x) - f(x) | \ge \epsilon}.$$ 
>- **N-th Tail support**: statistically independent from a finite number $N$ of events  $$T_{N,\epsilon} := \bigcup_{n \ge N}E_{n,\epsilon} := \sup_{n \ge N}E_{n, \epsilon}.$$
>- **Limit of Tail support**: statistically independent from *any* finite number of events  
> $$\bigcap_{N=1}^{\infty}T_{N,\epsilon} := \bigcap_{N=1}^{\infty}\bigcup_{n \ge N}E_{n,\epsilon} := \limsup_{n \to \infty}E_{n,\epsilon}.$$
>- **Width**:  $$\mu(E_{n,\epsilon})$$
>- **Maximum Variation**:  $$\sup_{x \in X}\{ \lvert f_n(x) - f(x) \rvert \}$$
>- **Subgraph**: $$\Gamma(f_{n}) := \{(x,t): 0\leq t \leq f_n(x)\}$$
>	- **Area**: $$\text{area of }\Gamma(f_n) := \mathcal{A}(\Gamma(f_n))$$

- [[Tail Support and Width]]
- [[Supremum and Infimum of Sets]]
- [[Limits of Sets]]
- [[Epigraph or Supergraph of Function]]


|                                                                                                               | **tail event**                                                                                                                         | **width**                                                                                                            | **maximum variation**                                     | **subgraph**                                                                                                                                   |
| ------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------- |
| [[Pointwise Convergence]]                                                                                     | The **common interior** of **all** tail supports is a **empty set**<br><br><br>$\bigcap_{N=1}^{\infty}T_{N,\epsilon} = \emptyset$;     |                                                                                                                      | or,<br> $\rightarrow 0$ on $X$                            |                                                                                                                                                |
| [[Pointwise Almost Everywhere Convergence]]                                                                   | The **common interior** of all tail events is a **null set**<br><br><br>$\mu \left( \bigcap_{N=1}^{\infty}T_{N,\epsilon} \right)  = 0$ |                                                                                                                      | or,<br> $\rightarrow 0$ on $X \setminus E$                |                                                                                                                                                |
| [[Uniform Convergence]]                                                                                       | **Every** tail event is **empty.**<br><br><br>$T_{N,\epsilon} = \emptyset$                                                             |                                                                                                                      | **equivalently**,<br> $\rightarrow 0$ on $X$              |                                                                                                                                                |
| [[Uniformly Almost Everywhere Convergence]]                                                                   | **Every** tail event is **a null set.**<br><br><br>$\mu\left( T_{N,\epsilon} \right) =0$                                               |                                                                                                                      | **equivalently**,<br> $\rightarrow 0$ on $X \setminus E$  |                                                                                                                                                |
| Convergence in $L^{\infty}$ norm; <br><br>*equivalent to*<br><br> [[Uniformly Almost Everywhere Convergence]] | $\mu\left( T_{N,\epsilon} \right) =0$                                                                                                  |                                                                                                                      | equivalently,<br> $\rightarrow 0$ on $X \setminus E$      |                                                                                                                                                |
| [[Almost Uniform Convergence]]                                                                                | A sequence of tail events **shrinks to a null set.**<br><br>$\lim\limits_{N \rightarrow \infty}\mu\left( T_{N,\epsilon} \right) = 0$   |                                                                                                                      | or, <br>$\rightarrow 0$ on $X \setminus E$                |                                                                                                                                                |
| [[Convergence in Measure]]                                                                                    |                                                                                                                                        | The width **shrinks to a null set.**<br><br>$\lim\limits_{n \rightarrow \infty}\mu\left( E_{n,\epsilon} \right) = 0$ | or,<br> $\rightarrow 0$ on $X \setminus E$                |                                                                                                                                                |
| [[Convergence in Lp norm]]                                                                                    |                                                                                                                                        |                                                                                                                      | $\rightarrow 0$ and *support fixed* or **non-increasing** | The **graph area** of variations **shrinks to zero.**<br><br>$\lim\limits_{n \rightarrow \infty}\mathcal{A}(\Gamma(\lvert f_n- f \rvert)) = 0$ |



### Strength Comparison

![[mode_of_convergence_math.png]]

- $\to$: the *left* mode of convergence is **stronger** than the *right* mode of convergence;
	- i.e. **if** the left mode of convergence holds, **then** the right mode of convergence holds
	- if **red color**, then the above logic holds with **additional conditions** on space










-----------
##  Recommended Notes and References

- [[Absolutely Convergent Integration]]
- [[Development of Integrations]]

- [[Banach Space]]
- [[Lp Space]]
- [[Measure Space and Countably Additive Measure]]