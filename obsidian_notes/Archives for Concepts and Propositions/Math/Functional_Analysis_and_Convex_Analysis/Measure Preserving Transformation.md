---
tags:
  - concept
  - math/functional_analysis
  - math/probability
  - math/stochastic_process
keywords:
  - measure_preserving_transformation
topics:
  - stochastic_process
  - functional_analysis
  - measure_theory
name: Measure Preserving Transformation
date of note: 2024-06-05
---

## Concept Definition

>[!important]
>**Name**: Measure Preserving Transformation

>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a *measure space*. 
>
>A *measurable  transformation*  $T: \mathcal{X} \to \mathcal{X}$ is called **measure preserving** (or $T$ **preserves** $\mu$ ) if $$\mu\left(T^{-1}A \right) = \mu(A)$$ for any $A \in \mathscr{F}.$
>
>- And the measure $\mu$ is called the **invariant measure** of $T$, or $\mu$ is **$T$-invariant**.
>- The set $A$ satisfies above definition is said to be **invariant under $T$**.

^87b4a3


- [[Vector Space over a Field]]
- [[Measurable Function]]
- [[Measure Space and Countably Additive Measure]]
- [[Space of Bounded Linear Operators]]
- [[Real Analysis by Royden]] pp 489

>[!important] Definition
>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a *measure space* and $T: \mathcal{X} \to \mathcal{X}$ be a *measurable transformation*. 
>
>A measurable set $A \in \mathscr{F}$ is said to be **invariant under $T$** *with respect to* $\mu$ if 
>$$
>\mu \left(A \,\setminus\, T^{-1}(A) \right) = \mu \left(T^{-1}(A) \, \setminus\,A  \right) = 0. 
>$$


## Explanation

>[!info]
>By definition,  **modulo** *sets of $\mu$-measure zero*, 
>$$
>T^{-1}(A) = A
>$$
>if $T$ is measure preseving,


>[!info]
>For measurable transformation $T$, 
>- $A$ is **invariant** under $T$ *if and only if* $$\chi_{A} \circ T = \chi_{A} \quad \text{ a.e. in } \mathcal{X}$$

- [[Characteristic Function of Set]]

>[!info]
>It is common to consider only an **invertible measure preserving** $T$. In this case, the inverse $T^{-1}$ is also *measure preserving*.

- [[Bijective Function and Inverse Function]]
- [[General Linear Group]]




## Pushforward Measure

>[!important]
>The definition can be written *compactly* in terms of **pushforward measure**
>$$
>  T_{*}\,\mu = \mu
>$$

- [[Push-forward Measure and Push-forward Operator]]


## Properties

>[!important] Proposition
>Let $(\mathcal{X}, \mathscr{F}, \mu)$ be a **finite measure space**, and $T: \mathcal{X}\to \mathcal{X}$ be a measurable transformation. 
>
>Then $T$ is **measure preserving** *if and only if* $g \circ T \in L^1(\mathcal{X},\mu)$ is **integrable** *whenever* $g\in L^1(\mathcal{X}, \mu)$ is **integrable**, and $$\int_{\mathcal{X}} g \circ T \;d\mu = \int_{\mathcal{X}} g\; d\mu, \quad \forall g\in L^1(\mathcal{X}, \mu).$$

- [[Real Analysis by Royden]] pp 488

## Criterion of Measure Preserving Transformation

>[!important] Lemma
>If $\mathscr{P}$ is a **$\pi$-system** generating $\mathscr{F}$, and if 
>- $$T^{-1}(A) \in \mathscr{F}$$ and 
>- $$\mathcal{P}(T^{-1}A) = \mathcal{P}(A), \quad A \in \mathscr{P},$$ 
>
>then $T$ is a **measure preserving transformation**.

- [[pi-system and lambda-system and Dynkin Theorem]]
- [[Probability and Measure by Billingsley]] pp 311



## Existence

>[!important] Bogoliubov-Krilov Theorem
>Let $\mathcal{X}$ be a **compact metric space**  and $f: \mathcal{X} \to \mathcal{X}$ be a **continuous**.
>
>Then there exists a **probability measure** $\mathcal{P}$ on the *Borel $\sigma$-algebra* $\mathcal{B}(\mathcal{X})$ with respect to which $f$ is **measure preserving**.

^cf4b89

- [[Real Analysis by Royden]] pp 490
- [[Compactness]]
- [[Metric Space]]
- [[Bounded Linear Operator and Norm of Operator]]
- [[Probability Space]]
- [[Borel sigma Field]]







## Examples

### Finite Dimensional Space

>[!important] Proposition
>A *linear transformation* $T \in \mathcal{L}(V)$ on real **finite dimensional space** $V$ is **measure preserving** *if and only if* $$T\in \text{SL}(n, \mathbb{R}) := \left\{T:\; \det T = 1  \right\} $$ i.e. $T$ is *invertible* with *determinant* $1$.
>
>Note that for every Borel set $A \in \mathcal{B}[V]$, $$m\left(T^{-1}\,A\right) = \frac{1}{|\det T|} m(A).$$

- [[Special Linear Group]]
- [[Automorphism between Groups]]
- Halmos, P. R. (1956). *Lectures on Ergodic Theory (First Edition).* Chelsea Pub Co. pp 7

### Lebesgue Measure and Translation

![[Lebesgue Measure#^e5f70d]]

- [[Lebesgue Measure]]

>[!example]
>Any **translation operation** on Euclidean space is **measure preserving transformation** with respect to *Lebesgue measure*.

### Volume-Preserving Flow and Divergence Theorem

![[Divergence Operator of Vector Field on Riemannian Manifold#^380a08]]

![[Divergence Operator of Vector Field on Riemannian Manifold#^d27f04]]

- [[Divergence Operator of Vector Field on Riemannian Manifold]]
- [[Local Flow on Smooth Manifold]]
- [[Global Flow on Smooth Manifold]]


>[!example]
>The **smooth flow** $$\theta_{t}: M \to M $$ of vector field $X$ whose divergence $\text{div}(X) = 0$ is a **measure-preserving transformation**.
>$$
> m\left(\theta_{t}^{-1}(D)\right) = m\left(D\right)
>$$
>where $m(\cdot)$ is a *measure* on *Riemannian manifold*.

- Halmos, P. R. (1956). *Lectures on Ergodic Theory (First Edition).* Chelsea Pub Co. pp 3

### Bernoulli Shift


>[!example]
>Let $S$ be a *finite set*, and consider the space $S^{\infty}$ be *$\omega$-tuple* (i.e. the infinite sequence) of $S$. 
>$$
>S^{\infty} := \left\{ \omega := (Z_{1}(\omega), Z_{2}(\omega) \,{,}\ldots{,}\,): Z_{k}(\omega) \in S, k \ge 1 \right\} 
>$$
>where $Z_{k}: S^{\infty} \to S$ is the *coordinate mapping*. Note that $(Z_{1} \,{,}\ldots{,}\,)$ represents all *i.i.d. random variables* in $S$.
>
>- Define a **shift** $T$ of $\omega := (Z_{1}(\omega), Z_{2}(\omega) \,{,}\ldots{,}\,)$ by $$T\omega := (Z_{2}(\omega), Z_{3}(\omega) \,{,}\ldots{,}\,)$$ That is, $T$ shift remaining elements **to the left**. $$Z_{k}\left(T\omega\right) = Z_{k+1}(\omega), \quad k \ge 1.$$ 
>- Define a **probability mass function** on $S$ as $p: S \to [0,1]$ with $\sum_{x\in S} p_{x} = 1$. Then the *joint probability* on any finite-dimensional cylinder is determined uniquely by $$\mathcal{P}\left\{ \omega: \left(Z_{1}(\omega) \,{,}\ldots{,}\,Z_{n}(\omega)\right) = (u_{1} \,{,}\ldots{,}\,u_{n}) \right\} = \prod_{i=1}^{n}p_{u_{i}}.$$ Thus the probability mass function extends to a **probability measure** $\mathcal{P}$ on *the $\sigma$-algebra $\mathscr{C}$ generated by cylinder sets*.
>
>It can be shown that the shift-transformation $T$ above is **$\mathcal{P}$-measure preserving** called the **Bernoulli shift**.**

- [[omega Tuples]]
- [[Stochastic Process]]
- [[Probability and Measure by Billingsley]] pp 311

### Markov Shift

>[!example]
>Let $S$ be a *finite set*. Let $$\boldsymbol{P} := \left[ p_{i,j} \right]_{i\in S \;,j \in S}$$ be a **stochastic matrix** i.e. $$\sum_{i\in S}p_{i,j} = 1,\, \quad \sum_{j\in S}p_{i,j} = 1.$$
>
>- Let $\pi_{i}$ be a *probability* on $S$. The  *joint probability* on any finite-dimensional cylinder is determined uniquely by $$\mathcal{P}\left\{ \omega: \left(Z_{1}(\omega) \,{,}\ldots{,}\,Z_{n}(\omega)\right) = (u_{1} \,{,}\ldots{,}\,u_{n}) \right\} = \sum_{u_{1}\in H}\pi_{u_{1}}\prod_{i=1}^{n}p_{u_{i},u_{i+1}}.$$ Follow the same argument as above, the probability measure $\mathcal{P}$ extends to a **probability measure** $\mathcal{P}$ on *the $\sigma$-algebra* $\mathscr{C} := \sigma(\mathscr{C}_{0})$.
>
>- This *probability measure* $\mathcal{P}$ is uniquely determined by the condition $$\mathcal{P}\left\{ \omega: \left(Z_{1}(\omega) \,{,}\ldots{,}\, Z_{n}(\omega)\right) = (u_{1} \,{,}\ldots{,}\,u_{n}) \right\} = \pi_{u_{1}}\prod_{i=1}^{n}p_{u_{i},u_{i+1}}$$ In other word, the coordinate functions $(Z_{n})$ are a **Markov chain** with *transition probabilities* $p_{i,j}$.
>- Define a **shift** $T$ of $\omega := (Z_{1}(\omega), Z_{2}(\omega) \,{,}\ldots{,}\,)$ by $$T\omega := (Z_{2}(\omega), Z_{3}(\omega) \,{,}\ldots{,}\,)$$ That is, $T$ shift remaining elements **to the left**. $$Z_{k}\left(T\omega\right) = Z_{k+1}(\omega), \quad k \ge 1.$$ 
>- Suppose that $\pi$ is an **invariant measure** of the Markov chain. $$\sum_{x\in S}\pi(x)\,p_{x, y} = \pi(y)$$
>
>It can be shown that the shift-transformation $T$ above is **$\mathcal{P}$-measure preserving** called the **Markov shift**.


## Ergodic Transformation

![[Ergodic Transformation#^41fb4e]]

- [[Ergodic Transformation]]





-----------
##  Recommended Notes and References

- [[Vector Space over a Field]]
- [[Measurable Function]]
- [[Measure Space and Countably Additive Measure]]
- [[Space of Bounded Linear Operators]]

- [[Topological Group]]
- [[Special Linear Group]]
- [[Unitary Group]]
- [[Orthogonal Group]]


- [[Probability and Measure by Billingsley]] pp 311
- [[Real Analysis by Royden]]
- Halmos, P. R. (1956). *Lectures on Ergodic Theory (First Edition).* Chelsea Pub Co. pp 3
- [[Functional Analysis by Reed]]
- [[Monte Carlo Statistical Methods by Robert]]

