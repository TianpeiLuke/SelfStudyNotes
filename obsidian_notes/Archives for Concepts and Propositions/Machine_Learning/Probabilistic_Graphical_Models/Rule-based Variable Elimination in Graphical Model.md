---
tags:
  - concept
  - machine_learning/algorithms
  - probabilistic_graphical_models/algorithm
keywords:
  - rule_based_variable_elimination
  - rule_cpd
topics:
  - probabilistic_graphical_model
name: Rule-based Variable Elimination in Graphical Model
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Rule-based Variable Elimination in Graphical Model

![[Local Probabilistic Models#^8f6b15]]

![[Local Probabilistic Models#^98dd1f]]

### Basic Rule Transformation

>[!important] Definition
>Let $\rho_{1} = <c\,;\, p_{1}>$ and $\rho_{2} = <c\,;\, p_{2}>$ be two *rules*.
>
>Then the **product of rules** is defined as 
>$$
>\rho_{1} \cdot \rho_{2} = < c\,;\, p_{1} \cdot p_{2} >.
>$$

[[Local Probabilistic Models#Rule CPDs]]

>[!important] Definition
>Let $Y$ be a variable with value set $\mathcal{Y} = \left\{ y_{1} \,{,}\ldots{,}\,  y_{k}\right\}$ , and let $\rho_{i}$ for $i=1 \,{,}\ldots{,}\,k$ be a rule of the form $$\rho_{i} = < c\,,\, Y= y_{i} \,;\, p_{i}>.$$
>
>Then for rule set $\mathcal{R} := \left\{ \rho_{1} \,{,}\ldots{,}\, \rho_{k}\right\},$ the **sum of rules** $$\sum_{Y}\mathcal{R} \;:=\; <\,c\,; \sum_{i=1}^{k}p_{i} >.$$

>[!info]
>Note that all $Y$ relevant rules are merged and then the assignment on $Y$ is removed in the output of the **rule sum operation**

### Rule Split

>[!important] Definition
>Let $\rho = <c\,;\, p>$ be a rule, and let $Y\in \mathcal{Y}$ be a variable. 
>
>We define the **rule split** as follows
>- If $Y \in \text{scope}[c]$, then $$\text{Split}(\rho \,\angle\, Y) = \left\{ \rho \right\}.$$
>- Otherwise, 
>$$
>\text{Split}(\rho \,\angle\, Y) = \left\{ <\,c\,, Y=y \,;\, p >, \;\; y\in \mathcal{Y}  \right\}.
>$$

>[!info]
>In general, the **purpose** of **rule splitting** is to make the *context* of one rule $\rho = < c\,;\, p >$ *compatible* with the context $c'$ of *another rule* $\rho'$.

>[!info]
>Naively, we might take all the variables in $Scope[c'] − Scope[c]$ and **split** $\rho$ **recursively** on each one of them. However, this process creates **unnecessarily many rules.**

>[!info]
>Rule splitting gives us the tool to take a *set of rules* and **refine** them, allowing us to apply either the **rule-product** operation or the **rule-sum** operation.


### Rule Splitting Algorithm

>[!important] Definition
>The **Rule-Split Algorithm** is described as below
>- *Require*: rule to split $\rho = <\,c\,; p >$ 
>- *Require*: context to split $c'$ 
>- If $c$ and $c'$ is *not compatible* to each other, then **return** $\rho$.
>- If $\text{scope}[c] \subseteq \text{scope}[c']$ then **return** $\rho$.
>- Select $Y \in \text{scope}[c'] - \text{scope}[c]$
>- $\mathcal{R} = \text{Split}(\rho \,\angle\, Y)$
>- **Recursive** call **Rule-Split** algorithm $$\mathcal{R}' = \bigcup_{\rho'' \in \mathcal{R}}\text{Rule-Split}\,(\rho''\,,\, c'\,).$$
>- **Return** $\mathcal{R}'.$


### Sum-Product Variable Elimination for Rules

>[!important] Definition
>The **Rule-Sum-Product-Eliminate-Var** algorithm is described as below:
>- *Require*: the *set of rules* $\mathcal{R}$
>- *Require*: variable to be *eliminated* $Y$
>- Collect a set of rules that whose *scope contains* $Y$: $$\mathcal{R}^{+} = \left\{ \rho \in \mathcal{R}\,:\, \text{scope}[\rho] \ni Y \right\}.$$
>- The rest of rules $$\mathcal{R}^{-} = \mathcal{R} \setminus\, \mathcal{R}^{+}.$$
>- While $\mathcal{R}^{+} \neq \emptyset$:
>	- If applicable, call **Rule Sum** operation:
>		- Select $\mathcal{R}_{c} \subseteq \mathcal{R}^{+}$ such that $$\mathcal{R}_{c} = \left\{  <\,c,\,Y = y_{1}\,;\, p_{1}> \,{,}\ldots{,}\,  <\,c,\,Y = y_{k}\,;\, p_{k}> \right\}$$
>		- *Rule sum* over $\mathcal{R}_{c}$ and **add** to the irrelevant rule set $$\mathcal{R}^{-} \leftarrow \mathcal{R}^{-} \cup \sum_{Y}\mathcal{R}_{c} $$
>		- **Remove** $\mathcal{R}_{c}$ from $\mathcal{R}^{+}$ $$\mathcal{R}^{+} \leftarrow \mathcal{R}^{+} - \mathcal{R}_{c}.$$
>	- If applicable, call **Rule Product** operation:
>		- Select $\rho_{1} \in \mathcal{R}^{+}$, $\rho_{2} \in \mathcal{R}^{+}$ such that 
>			- $\rho_{1} = <c\,; p_{1} >$
>			-  $\rho_{2} = <c\,; p_{2} >$
>		- **Remove** $\rho_{1}$, $\rho_{2}$ and their *Rule Product* $\rho_{1}\cdot \rho_{2}$ from $\mathcal{R}^{+}$, $$\mathcal{R}^{+} \leftarrow \mathcal{R}^{+} - \left\{ \rho_{1},\, \rho_{2},\, \rho_{1} \cdot \rho_{2}  \right\}.$$
>	- If applicable, call **Rule Split for Rule Product** operation:
>		- Select $\rho_{1} \in \mathcal{R}^{+}$, $\rho_{2} \in \mathcal{R}^{+}$ such that 
>			- $\rho_{1} = <c_{1}\,; p_{1} >$
>			-  $\rho_{2} = <c_{2}\,; p_{2} >$
>			- $c_{1}$ is *compatible* with $c_{2}$
>		- Call the **Rule Split** for
>			- $\rho_{1}$ with context $c_{2}$, i.e. $$\text{Rule-Split}(\rho_{1}, c_{2})$$
>			- $\rho_{2}$ with context $c_{1}$, i.e. $$\text{Rule-Split}(\rho_{2}, c_{1})$$
>		- **Remove**  $$\mathcal{R}^{+} \leftarrow \mathcal{R}^{+} - \left\{ \rho_{1},\, \rho_{2},\, \text{Rule-Split}(\rho_{1}, c_{2}),\,  \text{Rule-Split}(\rho_{2}, c_{1}) \right\}.$$
>	- If applicable, call **Rule Split for Rule Sum** operation:
>		- Select $\rho_{1} \in \mathcal{R}^{+}$, $\rho_{2} \in \mathcal{R}^{+}$ such that 
>			- $\rho_{1} = <c_{1},\,Y = y_{i}\,; p_{1} >$
>			-  $\rho_{2} = <c_{2},\,Y = y_{j}\,; p_{2} >$ where $i\neq j$
>			- $c_{1}$ is *compatible* with $c_{2}$,
>		- Call the **Rule Split** for
>			- $\rho_{1}$ with context $c_{2}$, i.e. $$\text{Rule-Split}(\rho_{1}, c_{2})$$
>			- $\rho_{2}$ with context $c_{1}$, i.e. $$\text{Rule-Split}(\rho_{2}, c_{1})$$
>		- **Remove** $$\mathcal{R}^{+} \leftarrow \mathcal{R}^{+} - \left\{ \rho_{1},\, \rho_{2},\, \text{Rule-Split}(\rho_{1}, c_{2}),\,  \text{Rule-Split}(\rho_{2}, c_{1}) \right\}.$$
>- *Return* the *ruleset* $\mathcal{R}^{-}$ 

>[!info]
>The above algorithm eliminate one variable. To eliminate all irrelevant variables, we apply the same **Sum-Product-VE** algorithm where the potential functions are replaced by rules.


![[Sum-Product Variable Elimination#^45fe7e]]


## Explanation





-----------
##  Recommended Notes and References


- [[Sum-Product Variable Elimination]]


- [[Local Probabilistic Models]]
- [[Bayesian Network on Directed Acyclic Graph]]


- [[Probabilistic Graphical Models by Koller]] pp 329 - 334

