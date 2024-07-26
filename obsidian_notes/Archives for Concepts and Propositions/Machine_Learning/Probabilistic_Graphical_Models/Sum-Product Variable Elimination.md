---
tags:
  - concept
  - machine_learning/algorithms
  - probabilistic_graphical_models/algorithm
keywords:
  - sum_product
  - probabilistic_graphical_model
  - variable_elimination
topics:
  - machine_learning_models
  - probabilistic_graphical_model
name: Sum-Product Variable Elimination
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Sum-Product Variable Elimination

![[Markov Network on Undirected Graph#^421079]]

### Marginalization

>[!important] Definition
>Let $X$ be a set of variables, and $Y \not\in X$ a variable. Let $\phi(X, Y)$ be a *factor*. 
>
>We define the **factor marginalization** of $Y$ in $\phi$ to be a factor $\psi$ over $X$ such that
>$$
>\psi(X) = \sum_{Y}\phi(X, Y).
>$$
>This operation is called **summing out** of $Y$ in $\psi$.

>[!info]
>The key point in this definition is that we **only** *sum up entries* in the table where the *values* of $X$ **match** up.

>[!info]
>For Bayes Net, $$\mathcal{P}(X) = \sum_{Y}\mathcal{P}(X, Y).$$

### Sum-Product Inference

>[!important] Definition
>Computing the **marginalization** of a **factorized distribution** can be seen as computing the value of an expression of the form
>$$
>\sum_{Z}\,\prod_{\phi \in \Phi}\phi
>$$
>We call this task the **sum-product inference** task.

>[!info]
>$$
>\sum_{x_{v},\, v\in \mathcal{Z}}P(x_{\mathcal{V}}\,,\, x_{\mathcal{Z}}) = \sum_{x_{v},\, v \in \mathcal{Z}}\prod_{v\in \mathcal{V}}P(x_{v}\,|\, x_{Pa(v)})
>$$



### Sum-Product Variable Elimination Algorithm

>[!quote]
>The **key insight** that allows the *effective sum-product computation* of this expression is the fact that the **scope** of the *factors* is **limited**, allowing us to “*push in*” some of the *summations*, performing them over the *product* of *only a subset of factors*. One simple instantiation of this algorithm is a procedure called **sum-product variable elimination (VE)**.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 299


>[!important] Algorithm
>The sub-procedure **Sum-Product-Elimination-Var** is described as below:
>
>- *Require*: $\Phi$, a set of *factors*
>- *Require*: $Z$, a variable to be *eliminated*
>- *Collect* the set of factors whose scopes *include* $Z$: $$\Phi_{Z} = \left\{ \phi\in \Phi: Z \in \text{scope}[\phi] \right\} $$
>- *Collect* the set of factors whose scopes *do not include* $Z$: $$\Phi_{-Z} = \Phi \setminus \Phi_{Z}.$$
>- Compute the **product** *of factors* whose scopes *include* $Z$: $$\psi = \prod_{\phi \in \Phi_{Z}}\phi$$
>- Compute the **sum** of *product factors* over $Z$: $$\tau = \sum_{Z}\psi$$
>- *Output*: $$\Phi_{-Z}\,\cup \,\tau.$$

>[!important] Algorithm
>The **Sum-Product-VE algorithm** is described as below:
>
>- *Require*: $\Phi_{0} := \Phi$, a set of *factors*
>- *Require*: $\mathcal{Z}$, a set of variables to be *eliminated*
>- *Require*: $\prec$, an *ordering* on $\mathcal{Z}$ such that $Z_{i} \prec Z_{j}$ if $i < j$ for any pair $Z_{i}, Z_{j} \in \mathcal{Z}.$
>- For $i=1 \,{,}\ldots{,}\,k$:
>	- *Eliminate* one variable $Z_{i}\in \mathcal{Z}$ by calling the **Sum-Product-Elimination-Var** *sub-procedure* $$\Phi_{i} = \text{Sum-Product-Elimination-Var}(\Phi_{i-1}, Z_{i}).$$
>- Compute the  **product** of *all factors* that have *eliminated all variables* in $\mathcal{Z}$: $$\phi^{*} = \prod_{\phi \in \Phi_{k}}\phi$$
>- *Output*: $\phi^{*}$.


>[!important] Theorem
>Let $\mathcal{X}$ be some set of variables, and let $\Phi$ be a set of *factors* such that for each $\phi\in \Phi$, $$\text{scope}[\phi] \subseteq \mathcal{X}.$$
>
>Let $\mathcal{Y} \subset \mathcal{X}$ be a set of *query variables*, and let $\mathcal{Z} = \mathcal{X} \setminus \mathcal{Y}$. 
>
>Then for any **ordering** $\prec$ over $\mathcal{Z}$, the **Sum-Product-VE algorithm**$(\Phi, \mathcal{Z}, \prec)$ described above *returns a factor* $\phi^{*}(\mathcal{Y})$ such that 
>$$
>\phi^{*}(\mathcal{Y}) = \sum_{\mathcal{Z}}\,\prod_{\phi\in \Phi}\phi.
>$$ 

- [[Strict Partial Order Relation]]

### Sum Product with Evidence

>[!info]
>Given *evidence* $E=e$ where $E \subset \mathcal{X}$, our goal is to compute **conditional probability** $$\mathcal{P}(X | E=e)$$
>
>- First, we reduce the problem to computing the **unnormalized probability** $$\mathcal{P}(X, E=e)$$
>- Then we can compute the *condition probability* $$\mathcal{P}(X | E =e) = \frac{\mathcal{P}(X, E=e)}{\mathcal{P}(E=e)}$$

>[!important] Algorithm
>The **Cond-Prob-VE algorithm** is described as below:
>
>- *Require*: $\mathcal{K}$, a *Bayesian* or *Markov network* over $\mathcal{X}$
>- *Require*: $\mathcal{Y}$, a set of *query* variables
>- *Require*: $E =e$, **evidence**
>- Collect the set $\Phi$ as all *factors* that *parameterize* $\mathcal{K}$
>- *Replace / Reduce* each factor $\phi \in \Phi$ by setting $$\phi[E=e]$$
>- Select an **elimination ordering** $\prec$
>- Set $\mathcal{Z} = \mathcal{X} \setminus \left\{ \mathcal{Y}, E \right\}$
>- Call **Sum-Product-VE algorithm** to compute $\mathcal{P}(Y, E=e)$, i.e. $$\phi^{*} = \text{Sum-Product-VE}(\Phi, \mathcal{Z}, \prec)$$
>- Compute the  **marginalized factor** over $\mathcal{Y}$: $$\alpha = \sum_{Y\in \mathcal{Y}}\phi^{*}(\mathcal{Y})$$
>- *Output*: $\phi^{*}, \alpha$.

>[!important]
>The conditional probability $\mathcal{Y}$ given $E=e$ can be 
>$$
>\mathcal{P}(\mathcal{Y} | E=e) = \frac{\phi^{*}}{\alpha}
>$$


## Explanation

>[!important]
>A **key observation** used in performing *inference in graphical models* is that the **operations of factor product** and **summation** behave precisely as do *product* and *summation* over *numbers*.
>
>Specifically, $$\phi_{1}\cdot \phi_{2} = \phi_{2}\cdot \phi_{1}$$ and $$\sum_{X}\sum_{Y}\phi = \sum_{Y}\sum_{X}\phi.$$ And the associativity rule $$\left(\phi_{1} \cdot \phi_{2}\right)\cdot \phi_{3} = \phi_{1} \cdot \left(\phi_{2}\cdot \phi_{3}\right)$$
>
>If $X\not\in \text{scope}[\phi_{1}],$
>$$
>\sum_{X}\left(\phi_{1} \cdot \phi_{2}\right) = \phi_{1} \cdot \left(\sum_{X}\phi_{2}\right)
>$$



>[!quote]
>To summarize, the **two ideas** that help us address the **exponential blowup** of the *joint distribution* are: 
>- Because of the structure of the *Bayesian network*, *some* subexpressions in the joint *depend only* on a **small number of variables**.
>- By **computing** these expressions **once** and **caching** the results, we can *avoid generating* them *exponentially many times*.
>
>  
>-- [[Probabilistic Graphical Models by Koller]] pp 296  

## Dynamic Programming Algorithms

- [[Sum-Product Message Passing Algorithm for Clique Tree]]
- [[Belief-Update Message Passing Algorithm for Clique Tree]]
- [[Belief Propagation and Belief Update Equivalence for Clique Tree]]



-----------
##  Recommended Notes and References

- [[Clique Tree and Graph and Running Intersection Property]]
- [[Max-Product Variable Elimination]]
- [[Gibbs Distribution]]

- [[Conditional Probability Query of Graphical Model]]

- [[Markov Network on Undirected Graph]]
- [[Bayesian Network on Directed Acyclic Graph]]

- [[Probabilistic Graphical Models by Koller]] pp 297 - 303
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
