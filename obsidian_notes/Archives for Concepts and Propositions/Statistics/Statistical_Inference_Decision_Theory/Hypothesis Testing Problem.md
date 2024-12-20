---
tags:
  - concept
  - math/probability
  - statistics/decision_theory
  - statistics/hypothesis_testing
keywords:
  - hypothesis_testing
  - type_I_error
  - type_II_error
topics:
  - statistics/decision_theory
  - statistics/hypothesis_testing
name: Hypothesis Testing Problem
date of note: 2024-06-08
---

## Concept Definition

>[!important]
>**Name**: Hypothesis Testing Problem

![[Statistical Decision Problem#^1e4cc1]]

![[Statistical Decision Problem#^e4b559]]

![[Statistical Decision Problem#^36cede]]

>[!important] Definition
>Let $\mathscr{P}$ be a family of distributions, $\mathscr{P}_{0} \subset \mathscr{P}$, and $\mathscr{P}_{1} = \left\{ \mathcal{P} \in \mathscr{P}: \mathcal{P} \not\in \mathscr{P}_{0}  \right\}.$
>
>A **hypothesis testing problem** can be formulated as that of *deciding which of the following two statements is true*:
>$$
>H_{0}: \mathcal{P} \in \mathscr{P}_{0} \quad \text{ versus} \quad H_{1}: \mathcal{P} \in \mathscr{P}_{1}.
>$$
>
>- $H_{0}$ is called the **null hypothesis.**
>- $H_{1}$ is called the **alternative hypothesis.**
>- The **action space** for this problem contains only two elements, i.e $\mathcal{A} := \left\{ 0, 1 \right\}$ where 
>	- $a=0$ is the action of **accepting** $H_{0}$
>	- $a=1$ is the action of **rejecting** $H_{0}$
>-  A *decision rule* is called a **test** $$T: (\mathcal{X}, \mathscr{F}_{\mathcal{X}}) \to (\left\{0, 1\right\}, 2^{\left\{ 0, 1 \right\}})$$  It is a *binary function* and can be represented as $$T(X) = \chi_{C}(X) \equiv \mathbb{1}\left\{ X \in C \right\}.$$
>	- The set $C \in \mathscr{F}_{\mathcal{X}}$ is called the **rejection region**, or **critical region** for testing $H_{0}$ versus $H_{1}$.
>  
>- Define the **loss function** as 
>  $$L(\mathcal{P}, a) = \left\{
>  \begin{array}{cc} 
> 0 & \text{if }\left( a = 0 \land \mathcal{P} \in \mathscr{P}_{0} \right)\text{ or }\left( a = 1 \land \mathcal{P} \in \mathscr{P}_{1} \right)\\
> 1 & \text{ otherwise.}
>\end{array} \right. 
>$$
>That is, the loss is zero if $a$ is the correct decision, otherwise the losss is $1$.  $$L(\mathcal{P}, j) =0 \quad \text{ for } \mathcal{P} \in \mathscr{P}_{j},\; j=0,1.$$
>- Define the **risk function** as 
>  $$
>  \begin{align*}
>  R_{T}(\mathcal{P}) &:= \mathbb{E}_{ \mathcal{P} }\left[ L(\mathcal{P}, T(X)) \right] \\[10pt]
>  &= 
> \left\{
> \begin{array}{cc} 
> \mathcal{P}\left( T(X) = 0 \right) = \mathcal{P}\left( X \in C \right) &  \mathcal{P} \in \mathscr{P}_{0}\\
> \mathcal{P}\left( T(X) = 1 \right) = \mathcal{P}\left( X \not\in C \right) &  \mathcal{P} \in \mathscr{P}_{1}
>\end{array} \right. 
\end{align*}
> $$

^14f68d

- [[Randomized Controlled Trial or RCT]]
- [[Population and Sample and Statistical Problem]]
- [[Statistical Decision Problem]]
- [[Statistics]]
- [[Characteristic Function of Set]]

- [[Mathematical Statistics by Shao]] pp 115

### Type I and Type II Error

>[!important] Definition
>For a *hypothesis testing problem* 
>$$
>H_{0}: \mathcal{P} \in \mathscr{P}_{0} \quad \text{ versus} \quad H_{1}: \mathcal{P} \in \mathscr{P}_{1},
>$$
>there are two types of **statistical errors**:
>- The error of *rejecting* $H_{0}$ when $H_{0}$ is *true*, i.e. $$a = 1 \land \mathcal{P} \in \mathscr{P}_{0},$$ is called the **Type-I error**, or the **false positives**.
>- The error of *accepting* $H_{0}$ when $H_{0}$ is *wrong*, i.e. $$a = 0 \land \mathcal{P} \in \mathscr{P}_{1},$$ is called the **Type-II error**, or the **false negatives.**

^1194ca

- [[Confusion Table]]
- [[True or False Positive Rate and True or False Negative Rate]]
- [[Mathematical Statistics by Shao]] pp 140
- [[Power and Size of Test]]

>[!important] Definition
>The **Type I error rate** or **false positive rate** is the probability of making Type-I error
>$$
>\beta_{T}(\mathcal{P}) = \mathcal{P}\left( T(X) = 1 \right) \quad \mathcal{P}\in \mathscr{P}_{0}
>$$
>
>The **Type II error rate** or **false negative rate** is the probability of making Type-II error
>$$
>1 - \beta_{T}(\mathcal{P}) = \mathcal{P}\left( T(X) = 0 \right) \quad \mathcal{P}\in \mathscr{P}_{1}
>$$

^178dfc



## Explanation



## Examples









-----------
##  Recommended Notes and References



- [[Population and Sample and Statistical Problem]]

- [[All of Statistics A Concise Course by Wasserman]] pp 195
- [[Mathematical Statistics by Shao]] pp 113 - 116

