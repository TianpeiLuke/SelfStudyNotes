---
tags:
  - concept
  - machine_learning/models
  - math/probability
  - probabilistic_graphical_models/models
keywords:
  - local_probabilistic_models
  - bayesian_network
topics:
  - probabilistic_graphical_model
name: Local Probabilistic Models
date of note: 2024-07-09
---

## Concept Definition

>[!important]
>**Name**: Local Probabilistic Models

![[Bayesian Network on Directed Acyclic Graph#^9d991d]]

- [[Bayesian Network on Directed Acyclic Graph]]

### Tabular CPD

>[!important] Definition
>If $X_{i}$ are all discrete random variables, then we can resort to the **tabular representation of local probability model**, where we encode $$P(X_{i} | X_{Pa(i)})$$ as a table with columns as $(X_{Pa_{i}}, X_{i})$. Each entry in the table represent a *joint assignment*. 
>
>For the CPD to be regular, we requires $$\sum_{a\in \mathcal{X}_{i}}P(X_{i} = a | X_{Pa(i)}) = 1, \quad \forall X_{Pa(i)} \in \prod_{k \in Pa(i)} \mathcal{X}_{k}$$
>
>Note that the *number of total assignments* for the **tabular CPD** is $$|\mathcal{X}_{i}| \times \prod_{k \in Pa(i)} | \mathcal{X}_{k}|,$$ which is exponentially increase as the number of variables increase.


### Deterministic CPD

>[!important] Definition
>Note that each local probability model is a function of $X_{Pa(i)}$. The simplest non-tabular representation of local probabilistic model is a **deterministic function**, i.e. 
>$$
>P(X_{i} = x | X_{Pa(i)}) = \mathbb{1}\left\{ f(X_{Pa(i)}) = x \right\}.
>$$
>for some function $f: \prod_{k\in Pa(i)}\mathcal{X}_{k} \to \mathcal{X}_{i}.$

>[!example]
>The most common application for **deterministic CPD** is the **logical deduction**. 

- [[Context-Specific Conditional Independence]]
- [[Characteristic Function of Set]]


### Tree-CPDs

>[!important] Definition
>A **tree-CPD** is a **decision tree representation** of a *local probabilistic model*
>$$
>P(X_{i} | X_{Pa_{i}}) = K(X_{Pa_{i}}, X_{i})
>$$
>
>In particular, [[Probabilistic Graphical Models by Koller]] calls the internal decision node as *$t$-node*. Then the structure of the decision tree is as below
>- Each $t$-node in the tree is either a **leaf node** or an **interior node**.
>- Each *leaf* is labeled with a distribution $P(X_{i})$
>- Each *interior $t$-node* is labeled with some variable $X_{k}$ where $k \in Pa(0)$
>- Each *interior $t$-node* has a set of **outgoing arcs** to its *children*
>- Each *interior $t$-node* is associated with a **unique variable assignment** $X_{k}= x_{k}$ for $x_{k} \in \mathcal{X}_{k}$
>  
>A **branch** $\beta$ through a *tree-CPD* is a path beginning at the root and preceeding to a leaf node. We assume that *no branch* contains *two interior nodes labeled by the same variable*. 
>
>The **parent context** induced by branch $\beta$ is the set of variable assignment $X_{k} = x_{k}$ encountered on the *arcs along the branch*.
>

- [[Probabilistic Graphical Models by Koller]] pp 164, 1083

>[!info]
>A branch in tree-CPD is a path $(X_{k}, \, k\in Pa(i))$ to the leaf $X_{i}$. 
>
>Each variable in the branch has a *unique assignment*, i.e. $X_{k} = x_{k}, \, k\in Pa(i)$. Thus the decision tree **represent a kernel** $K$
>
>- For each **branch** of *the decision tree*, which assigns $X_{k} = x_{k}, \, k\in Pa(i)$ for some value $x_{k}\in \mathcal{X}_{k}$, the output of the tree-CPD is a probability on $X_{i}$
>$$
>K(x_{Pa(i)}, A) = P(X_{i} \in A).
>$$

- [[Markov Transition Kernel and Transition Function]]

>[!important] Definition
>A CPD $$P(X | A, Z_{1} \,{,}\ldots{,}\,Z_{k})$$ is said to be a **multiplexer CPD** if $A \in \{ 1 \,{,}\ldots{,}\, k\}$, and 
>$$
>P(X | A = i, Z_{1} \,{,}\ldots{,}\,Z_{k} ) = \mathbb{1}\{ X = Z_{i} \}
>$$
>where $i \in \{ 1 \,{,}\ldots{,}\, k\}$. The variable $A$ is called the **selector variable** for the CPD.


### Rule CPDs

>[!important] Definition
>A **rule** $\rho$ is a pair $<c; p >$ where $c$ is an *assignment* to some subset of variables $C$, and $p\in [0,1].$
>
>We define $C$ to be the **scope** of $\rho$, denoted $\text{Scope}[\rho].$


>[!info]
>The *rule-based* representation and the *decision-tree-based* representation are **equivalent** in that each *branch* corresponds to an *assignment in the rule*, and each $p$ corresponds to the *probability* $P(X_{i})$ in the output node.
>
>For each *assignment* $X_{Pa(i)} = x_{Pa(i)}$, 
>$$K(x_{Pa(i)}, A) = P(X_{i} \in A) \implies <x_{Pa(i)}\,,\,  p>, \;\; p =P(X_{i} \in A).$$


>[!important] Definition
>A **rule-based CPD** $P(X_{i} | X_{Pa_{i}})$ is a set of *rules* $\mathcal{R}$ such that 
>- For each *rule* $\rho \in \mathcal{R}$, we have the $$\text{scope}[\rho] \subset \{ X_{i}, X_{Pa_{i}} \}$$
>- For each *assignment* $(x, u) \in \{ X_{i}, X_{Pa_{i}} \}$, we have **precisely one rule** $<c; p>$ where $c$ is the assignment on rule condition and $p\in [0,1]$, such that $c$ is *compatible* with $(x,u)$. In this case, we say $$P(X_{i} = x | X_{Pa(i)} = u) = p$$
>- The resulting CPD $P(X | U)$ is *legal CPD* in that $$\sum_{x}P(X_{i} = x | X_{Pa(i)} = u) = 1, \;\;\forall \text{ assignment }u.$$


- [[Probabilistic Graphical Models by Koller]] pp 168

### Generalized Linear Models

![[Generalized Linear Models#^16bb2c]]

>[!info]
>With GLM as local probabilistic models, we have **GLM-CPD**
>$$
>P(X_{i} | X_{Pa(i)}) = \exp \left( \left\langle \eta , X_{i} \right\rangle - A(\eta) \right)
>$$
>where the conditional mean $$ \mathbb{E}_{ \eta }\left[ X_{i} | X_{Pa(i)} \right] = (\nabla A)(\eta) = g^{-1}\left( \beta^{T}\,X_{Pa(i)} \right).$$

- [[Generalized Linear Models]]
- [[Probabilistic Graphical Models by Koller]] pp 178

>[!important] Definition
>Let $Y$ be a *continuous random variable* with *continuous parents* $X_{1} \,{,}\ldots{,}\,X_{k}$. We say that $Y$ has a **linear Gaussian model** with parameters $\beta_{0}, \beta_{1} \,{,}\ldots{,}\,\beta_{k}$ and $\sigma^2$ if 
>$$
>P(Y | X_{1} \,{,}\ldots{,}\,X_{k}) = \mathcal{N}\left(Y; f(X_{1} \,{,}\ldots{,}\,X_{k}), \sigma^2\right)
>$$
>where 
>$$
>f(X_{1} \,{,}\ldots{,}\,X_{k}) = \beta_{0} + \sum_{i=1}^{k}\beta_{i}\,X_{i}
>$$
>In other word, the local probability model is a *linear regression model*
>$$
>Y =  \beta_{0} + \sum_{i=1}^{k}\beta_{i}\,X_{i} + \sigma\, \xi
>$$
>where $\xi \sim \mathcal{N}(0,I)$.

- [[Linear Regression]]



## Explanation





-----------
##  Recommended Notes and References

- [[Bayesian Network on Directed Acyclic Graph]]
- [[Conditional Probability]]



- [[Probabilistic Graphical Models by Koller]] pp 158 - 195