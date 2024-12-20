---
tags:
  - concept
  - statistics/estimation
keywords:
  - power_hypothesis_test
  - size_hypothesis_test
topics:
  - statistics
name: Power and Size of Test
date of note: 2024-05-22
---

## Concept Definition

>[!important]
>**Name**: Power and Size of Test


![[Hypothesis Testing Problem#^14f68d]]


>[!important] Definition
>The **power function** of a test $T: \mathcal{X} \to \left\{ 0 ,1 \right\}$ is defined as
>$$
>\beta_{T}(\mathcal{P}) := \mathcal{P}\left( T(X) = 1 \right) = \mathcal{P}\left[ X \in C \right]
>$$

^ddfeff

>[!important] Definition
>The **size** of a test $T$ is defined by
>$$
>\alpha := \sup\left\{ \beta_{T}(\mathcal{P}): \mathcal{P} \in \mathscr{P}_{0} \right\} := \sup_{\mathcal{P} \in \mathscr{P}_{0}} \mathcal{P}\left[ X \in C \right] .
>$$
>
>A *test* is said to have **level $\alpha$** if its size is less than or equal to $\alpha$.
>$$
>\sup\left\{ \beta_{T}(\mathcal{P}): \mathcal{P} \in \mathscr{P}_{0}  \right\} \le \alpha
>$$

^7c70c2

- [[Hypothesis Testing Problem]]
- [[Mathematical Statistics by Shao]] pp 125

### Parametric Family

>[!important] Definition
>Suppose that the sample $X$ is from a *parametric model* $\left\{ \mathcal{P}_{\theta}: \theta \in \Theta \right\}$.
>
>The **power function** of a test with *rejection region* $C$ is defined by
>$$
>\beta(\theta) := \mathcal{P}_{\theta}\left[ X \in C  \right] 
>$$

^3354a4

>[!important] Definition
>The **size** of a test is defined by
>$$
>\alpha := \sup\left\{ \beta(\theta): \theta \in \Theta_{0} \right\} := \sup_{\theta \in \Theta_{0}} \mathcal{P}_{\theta}\left[ X \in C \right] .
>$$
>
>A *test* is said to have **level $\alpha$** if its size is less than or equal to $\alpha$.
>$$
>\sup\left\{ \beta(\theta): \theta \in \Theta_{0} \right\} \le \alpha
>$$

- [[Parametric Models]]
- [[All of Statistics A Concise Course by Wasserman]]


>[!info]
>For $\Theta_{0} = \left\{ \theta_{0} \right\}$, the test at $\alpha$ level  with rejection region $C$ has
>$$
>\mathcal{P}_{\theta_{0}}\left[ X \in C \right] \le \alpha
>$$

## Explanation

![[Hypothesis Testing Problem#^1194ca]]


![[Hypothesis Testing Problem#^178dfc]]


>[!info]
>Controlling both *Type-I* and *Type-II error* **simultaneously** is impossible. 
>
>Therefore, a common approach to **finding an “optimal” test** is 
>- to assign a **small bound** $\alpha$ to **one of the error probabilities**, say $$\beta_{T}(\mathcal{P}), \quad \mathcal{P} \in \mathscr{P}_{0},$$  
>- and then to attempt to **minimize the other error probability** $$1 − \beta_{T}(\mathcal{P}), \mathcal{P} \in  \mathscr{P}_{1}.$$
>
>The level $\alpha$ is the *probability* of a test to *reject the null hypothesis* **when the null hypothesis is true**.

- [[Mathematical Statistics by Shao]] pp 126


>[!info]
>Recall that the isometric isomorphism $\mathcal{P} \mapsto \int \cdot d\mathcal{P}$, thus $\mathcal{P}_{\theta}$ is a functional indexed by $\theta$ on $\mathcal{C}(\Omega)$. Thus we can define the **power function** as evaluation functional acts on $\mathcal{P}_{\theta}$:
>$$
>\beta(\theta) = I_{C}( \mathcal{P}_{\theta})  := \mathcal{P}_{\theta}\,\chi_{C}
>$$
>
>
>The **size** of test is the obtained by evaluating a sequence of functionals $\mathcal{P}_{\theta}$ on the function $\chi_{C}$, where $\theta\in \Theta_{0}$.
>$$
>\sup_{\mathcal{P}_{\theta} \in \mathcal{M}(\Theta_{0})}I_{C}(\mathcal{P}_{\theta})
>$$
>where $\mathcal{M}(\Theta_{0}) = \left\{ \mathcal{P}_{\theta} \in \mathcal{M}(\Omega): \theta \in \Theta_{0} \right\}$

- [[Characteristic Function of Set]]
- [[Evaluation Functional]]
- [[Expectation of Random Variable]]

>[!important]
>The choice of a **level of significance** $\alpha$ is usually somewhat ***subjective***. In most applications there is no precise limit to the size of $T$ that can be tolerated. 
>
>Standard values, such as $0.10$, $0.05$, or $0.01$, are often used for *convenience*.

## P-value

>[!important]
>For most tests satisfying $$\sup\left\{ \beta_{T}(\mathcal{P}): \mathcal{P} \in \mathscr{P}_{0}  \right\} \le \alpha,$$ a *small* $\alpha$ leads to a *“small” rejection region*. 
>
>It is good practice to determine *not only whether $H_{0}$ is rejected* or accepted for a *given* $\alpha$ and a *chosen test* $T_{\alpha}$, but also the **smallest possible level of significance** at which $H_{0}$ would be **rejected** for the **computed** $T_{\alpha}(x)$, i.e.,  $$\hat{\alpha} := \inf\{\alpha \in (0, 1): T_{\alpha}(x) = 1\}.$$ 
>
>Such an $\hat{\alpha}$, which *depends* on $x$ and the *chosen test* and is a *statistic*, is called the **p-value** *for the test* $T_{\alpha}$.

^ce7424

- [[p-Value of Test]]




-----------
##  Recommended Notes and References


- [[Randomized Controlled Trial or RCT]]
- [[Probability Distribution of Random Variable]]
- [[Probability Space]]


- [[All of Statistics A Concise Course by Wasserman]]
- [[Testing Statistical Hypotheses by Lehmann]]
- [[Mathematical Statistics by Shao]] pp 140