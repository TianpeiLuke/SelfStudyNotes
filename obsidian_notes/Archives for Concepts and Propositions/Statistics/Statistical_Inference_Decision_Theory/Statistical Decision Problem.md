---
tags:
  - concept
  - statistics/estimation
  - math/probability
  - statistics/decision_theory
keywords:
  - statistical_decision_theory
topics:
  - statistics/decision_theory
name: Statistical Decision Problem
date of note: 2024-06-08
---

## Concept Definition

>[!important]
>**Name**: Statistical Decision Problem

![[Population and Sample and Statistical Problem#^86cfde]]


>[!important] Definition
>Let $X$ be a *sample* from a *population* $\mathcal{P} \in \mathscr{P}$. 
>
>A **statistical decision** is an **action** that we take after we *observe* $X$, for example, a *conclusion* about $\mathcal{P}$ or a *characteristic* of $\mathcal{P}$. 
>
>- Throughout this section, we use $\mathcal{A}$ to denote the **set of allowable actions**. Let $\mathscr{F}_{\mathcal{A}}$ be a **$\sigma$-field** on $\mathcal{A}$. 
>- Then the *measurable space* $(\mathcal{A}, \mathscr{F}_{\mathcal{A}})$ is called the **action space**. 
>- Let $\mathcal{X}$ be the *range* of $X$ and $\mathscr{F}_{\mathcal{X}}$ be a *$\sigma$-field* on $\mathcal{X}$. 
>- A **decision rule** is a *measurable function* (a *statistic*) $$T: (\mathcal{X}, \mathscr{F}_{\mathcal{X}}) \to (\mathcal{A}, \mathscr{F}_{\mathcal{A}})$$  
>- If a decision rule $T$ is chosen, then we take the **action** $$T(X) \in \mathcal{A}$$ whence $X$ is *observed*.

^1e4cc1

- [[Probability Space]]
- [[Measure Space and Countably Additive Measure]]
- [[Random Element and Random Variable]]
- [[Probability Distribution of Random Variable]]
- [[Measurable Function]]
- [[Statistics]]
- [[Mathematical Statistics by Shao]] pp 113

### Loss and Risk

>[!important] Definition
>In *statistical decision theory*, we set a *criterion* using a **loss function** $L$, which is a function $$L: \mathscr{P} \times \mathcal{A} \to [0, \infty)$$ and 
>- is **Borel** on $(\mathcal{A}, \mathscr{F}_{\mathcal{A}})$ for each *fixed* $\mathcal{P} \in \mathscr{P}.$ 
>
 >If $X = x$ is *observed* and our *decision rule* is $T$, then our **“loss”** (in making a decision) is $$L(\mathcal{P}, T(x)).$$

^e4b559

 
- [[Measurable Function]]
- [[Borel sigma Field]]

>[!important] Definition
>The *average loss* for the decision rule $T$, which is called the **risk of $T$**, is defined to be
>$$
>R_{T}\left(\mathcal{P}\right) := \mathbb{E}_{ \mathcal{P} }\left[ L(\mathcal{P}, T(X)) \right] = \int_{\Omega}\,L(\mathcal{P}, T(x))\,d\mathcal{P}_{X}(x)
>$$
>where $\mathcal{P}_{X} = X_{*}\,\mathcal{P}$ is the distribution of $X$.

^36cede

### Parametric Family

>[!important] Definition
>The **loss** and **risk** functions are denoted by $$L(\theta, a)$$ and $$R_{T}(\theta)$$ if $\mathscr{P}$ is a **parametric family** *indexed by* $\theta$.

- [[Parametric Models]]

>[!info]
>Consider point estimator $T(X) = \hat{\theta}(X) = a$, the loss and risk are denoted as
>$$
>L(\theta, \hat{\theta})
>$$
>and
>$$
>R(\theta, \hat{\theta})
>$$

- [[Point Estimator]]
- [[All of Statistics A Concise Course by Wasserman]] pp 195

### Comparison of Decision Rules

>[!important] Definition
>We compare two *statistical decisions* by their **risks**:
>- A rule $T_{1}$ is **as good as** another rule $T_{2}$ *if and only if* $$R_{T_{1}}\left(\mathcal{P}\right) \le R_{T_{2}}\left(\mathcal{P}\right), \quad \forall \mathcal{P} \in \mathscr{P}.$$ 
>- A rule $T_{1}$ is **better than** another rule $T_{2}$ *if and only if* $$R_{T_{1}}\left(\mathcal{P}\right) \le R_{T_{2}}\left(\mathcal{P}\right), \quad \forall \mathcal{P} \in \mathscr{P}$$ holds, and $$R_{T_{1}}\left(\mathcal{P}\right) < R_{T_{2}}\left(\mathcal{P}\right)$$ for *at least one* $\mathcal{P} \in \mathscr{P}.$ 
>- Two rules are **equivalent** if and only if $$R_{T_{1}}\left(\mathcal{P}\right) = R_{T_{2}}\left(\mathcal{P}\right), \quad \forall \mathcal{P} \in \mathscr{P}.$$
>- If there exists a rule $T^{*}$ that is *as good as* **any other rule** in $\mathcal{R}$, a *class of allowable decision rules*, then $T^{*}$ is said to be **$\mathcal{R}$-optimal.**

^a44cc3

### Randomized Rules

>[!important] Definition
>Sometimes it is useful to consider **randomized decision rules**.
>
>A **randomized decision rule** is a function $$\delta: \mathcal{X} \times \mathscr{F}_{\mathcal{A}} \to [0, \infty)$$ such that, 
>- for *every* $A \in \mathscr{F}_{\mathcal{A}}$,  $\delta(\cdot, A)$ is a **Borel function** and, 
>- for *every* $x \in \mathcal{X}$, $\delta(x, \cdot)$ is a **probability measure** on $(\mathcal{A}, \mathscr{F}_{\mathcal{A}})$.

- [[Conditional Probability]]


>[!important] Definition
>The **loss function** for a *randomized rule* $\delta$ is defined as
>$$
>L(\mathcal{P}, \delta, x) = \mathbb{E}_{\delta }\left[ L(\mathcal{P}, a) \right] = \int_{\mathcal{A}}L(\mathcal{P}, a)\;\delta(x, da) 
>$$


>[!important] Definition
>The **risk function** for a *randomized rule* $\delta$ is defined as
>$$
>R_{\delta}(\mathcal{P}) = \mathbb{E}_{\mathcal{P} }\left[ L(\mathcal{P}, \delta,  X) \right] = \int_{\mathcal{X}} \int_{\mathcal{A}}L(\mathcal{P}, a)\;\delta(x, da)\;d\mathcal{P}_{X}(x). 
>$$


## Explanation

>[!info]
>A randomized rule is a **conditional probability** on action space $(\mathcal{A}, \mathscr{F}_{A})$
>$$
>\delta(x, A) := \mathcal{P}\left[A \,|\, \mathscr{F}_{\mathcal{X}}\right](x)
>$$
>which replaces the **deterministic rule** $T$ as
>$$
>\delta(x, \{ a \}) = \chi_{\{ a \}}\left(T(x)\right) = \mathbb{1}\left\{ T(x) = a \right\}\quad \forall a\in \mathcal{A},\, x\in \mathcal{X} 
>$$

- [[Conditional Probability]]
- [[Characteristic Function of Set]]



## Examples

### Statistical Estimation

>[!example]
>Assume that the sample $X = (X_{1} \,{,}\ldots{,}\, X_{n})$ is from a *parametric model* $\{\mathcal{P}_{\theta}: \theta \in \Theta\}.$
>
>Suppose that we need a **decision on the value** of $\theta \in \Theta$, based on the sample $X$.
>
>- Consider the **action space** $(\Theta, \mathcal{B}(\Theta))$ be the Borel measurable space of $\Theta$
>-  A **decision rule** is a **point estimator** $$T: (\mathcal{X}, \mathscr{F}_{\mathcal{X}}) \to (\Theta, \mathcal{B}(\Theta))$$  We denote $\hat{\theta}(X) := T(X).$
>- Define the **loss function** as $$L(\theta, \hat{\theta})$$
>- Define the **risk function** as $$R(\theta, \hat{\theta}) := \mathbb{E}_{ \mathcal{P}_{\theta} }\left[ L(\theta, \hat{\theta}(X)) \right] = \int_{\Omega}\,L(\theta, \hat{\theta}(x))\,d\mathcal{P}_{\theta}(x)$$
>
>The decision problem as described above is called the **statistical estimation** problem.
>- The decision rule in statistical estimation problem is called an **estimator**. 

- [[Statistical Estimation Problem]]
- [[Point Estimator]]
- [[Minimum Mean Square Estimation]]

### Hypothesis Testing

>[!example] 
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

- [[Hypothesis Testing Problem]]

### Empirical Risk Minimization

>[!example]
>Let $X$ be a sample taking values in $\mathcal{X}$ from *nonparametric model* $\mathcal{P} \in \mathscr{P}$. Suppose that there exists some *unknown* Borel measurable function $f\in \mathcal{F}$ such that $$Y = f(X) \in \mathcal{Y}, \quad \forall X\in \mathcal{X}.$$ Let $\mathcal{H}$ be a family of *Borel measurable functions* from $\mathcal{X}$ to $\mathcal{Y}$. 
>
>A **statistical learning problem** can be formulated as that of *deciding which function* $h \in \mathcal{H}$ based on sample $(X, Y)$ where $X$ is from $\mathcal{P}$.
>- Consider the **action space** $(\mathcal{H}, \mathcal{B}(\mathcal{H}))$ be the Borel measurable space of $\mathcal{H}$. The space $\mathcal{H}$ is called a **hypothesis class**.
>- $f\in \mathcal{F}$ is called a **concept** and $\mathcal{F}$ is called a **concept class.**
>-  A **classification (learning)  rule** is $$T: (\mathcal{X}, \mathscr{F}_{\mathcal{X}}) \to (\mathcal{H}, \mathcal{B}(\mathcal{H}))$$  Denote $h:=T(X)$.
>- Define the **loss function** as $$L_{f}(X, h)$$
>- Define the **risk function** as $$R_{T, f}(\mathcal{P}) := \mathbb{E}_{ \mathcal{P}}\left[ L_{f}(X, T(X)) \right]$$ The risk function is called the **generalization error** of $h.$

- [[Statistical Learning via Statistical Decision Theory]]





-----------
##  Recommended Notes and References


- [[Concepts and Theorems in Statistical Inference and Decision Theory]]
- [[Concepts and Theorems in Hypothesis Testing]]

- [[Population and Sample and Statistical Problem]]

- [[All of Statistics A Concise Course by Wasserman]] pp 195
- [[Mathematical Statistics by Shao]] pp 113 - 116
- [[]]

