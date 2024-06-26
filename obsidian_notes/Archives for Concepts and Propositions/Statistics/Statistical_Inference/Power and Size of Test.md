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

>[!info]
>Consider the following *hypothesis testing problem*, 
>$$
>\begin{align*}
>H_{0}: \theta \in \Theta_{0} \text{ versus } H_{1}: \theta \in \Theta_{1} 
\end{align*}
>$$
>where the partition of parameter space $\Theta = \Theta_{0} \cup \Theta_{1}$. 
>
>We call $H_{0}$ the **null hypothesis** and $H_{1}$ the **alternative hypothesis**.

>[!info]
>Suppose a random variable $X$ taking values in $\mathcal{X}$, the **rejection region** of a *test* is a subset $R \subset \mathcal{X}$ within which **the null hypothesis is rejected**: 
>$$
>X \in R \implies H_{0} \text{ is rejected.}
>$$



>[!important] Definition
>The **power function** of a test with *rejection region* $R$ is defined by
>$$
>\beta(\theta) := \mathcal{P}_{\theta}\left[ X \in R  \right] 
>$$

>[!important] Definition
>The **size** of a test is defined by
>$$
>\alpha := \sup\left\{ \beta(\theta): \theta \in \Theta_{0} \right\} := \sup_{\theta \in \Theta_{0}} \mathcal{P}_{\theta}\left[ X \in R \right] .
>$$
>
>A *test* is said to have **level $\alpha$** if its size is less than or equal to $\alpha$.
>$$
>\sup\left\{ \beta(\theta): \theta \in \Theta_{0} \right\} \le \alpha
>$$

>[!info]
>For $\Theta_{0} = \left\{ \theta_{0} \right\}$, the test at $\alpha$ level  with rejection region $R$ has
>$$
>\mathcal{P}_{\theta_{0}}\left[ X \in R \right] \le \alpha
>$$


## Explanation

>[!info]
>The level $\alpha$ is the *probability* of a test to *reject the null hypothesis* **when the null hypothesis is true**.

>[!info]
>Recall that the isometric isomorphism $\mathcal{P} \mapsto \int \cdot d\mathcal{P}$, thus $\mathcal{P}_{\theta}$ is a functional indexed by $\theta$ on $\mathcal{C}(\Omega)$. Thus we can define the **power function** as evaluation functional acts on $\mathcal{P}_{\theta}$:
>$$
>\beta(\theta) = I_{R}( \mathcal{P}_{\theta})  := \mathcal{P}_{\theta}\,\chi_{R}
>$$
>
>
>The **size** of test is the obtained by evaluating a sequence of functionals $\mathcal{P}_{\theta}$ on the function $\chi_{R}$, where $\theta\in \Theta_{0}$.
>$$
>\sup_{\mathcal{P}_{\theta} \in \mathcal{M}(\Theta_{0})}I_{R}(\mathcal{P}_{\theta})
>$$
>where $\mathcal{M}(\Theta_{0}) = \left\{ \mathcal{P}_{\theta} \in \mathcal{M}(\Omega): \theta \in \Theta_{0} \right\}$

- [[Characteristic Function of Set]]
- [[Evaluation Functional]]
- [[Expectation of Random Variable]]


-----------
##  Recommended Notes and References



- [[Probability Distribution of Random Variable]]
- [[Probability Space]]


- [[All of Statistics A Concise Course by Wasserman]]
- [[Testing Statistical Hypotheses by Lehmann]]