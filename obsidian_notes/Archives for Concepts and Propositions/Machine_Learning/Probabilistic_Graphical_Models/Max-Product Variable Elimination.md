---
tags:
  - concept
  - machine_learning/algorithms
  - probabilistic_graphical_models/algorithm
  - probabilistic_graphical_models/theory
keywords:
  - max_product
  - variable_elimination
  - max_marginal
topics:
  - probabilistic_graphical_model
name: Max-Product Variable Elimination
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Max-Product Variable Elimination

### Reformulation

>[!important]
>Finding MAP assignment for a *probability graphical model* can be reformulated as finding maximum assignment for *product of factors*
>$$
>\xi^{MAP} = \arg\max_{\xi} \mathcal{P}_{\Phi}(\xi) = \arg\max_{\xi} \frac{1}{Z}\hat{\mathcal{P}}_{\Phi}(\xi) = \arg\max_{\xi} \hat{\mathcal{P}}_{\Phi}(\xi)
>$$
>That is, the task is often called the **max-product inference**.
>$$
>\xi^{MAP} = \arg\max_{\xi} \prod_{\phi \in \Phi}\phi(\xi)
>$$
>- We often convert this problem in *log-space* $$\xi^{MAP} = \arg\max_{\xi} \sum_{\phi \in \Phi}\log\phi(\xi)$$ Hence this version of the problem is often called the **max-sum problem.**
>- It is also common to *negate* the factors and minimize the sum of the *energies* for the different potentials; this version is generally called an **energy minimization problem.**

- [[Maximum A Posteriori Probability Query of Graphical Model]]

>[!quote]
> The transformation **energy minimization** into *log-space* has several significant **advantages**. First, it avoids the *numerical issues* associated with multiplying many small numbers together. More importantly, it transforms the problem into a **linear one**; as we will see, this transformation allows certain valuable tools to be brought to bear. For consistency with the rest of the book, we mostly use the *max-product* variant of the problem in the remainder of this chapter. However, all of our discussion carries over with minimal changes to the analogous *max-sum (or min-sum) problem*: we simply take the logarithm of all factors, and replace factor product steps with factor additions.
> 
> -- [[Probabilistic Graphical Models by Koller]] pp 553


### Max Marginal

>[!important] Definition
>The **max-marginal** of a function $$f: \mathcal{X}\times \mathcal{Y} \to \mathbb{R}, \quad (x,y)  \mapsto f(x,y)$$ *relative* to a set of variables $y$ is
>$$
>\text{MaxMarg}_{f}(y) = \max_{x \in \mathcal{X}}f(x, y), \quad \forall y\in \mathcal{Y}.
>$$

>[!quote]
>As we show, the *computation of (approximate) max-marginals* allows us to solve a *global optimization problem* as **a set of local optimization problems** for individual variables. This task, known as **decoding**, is to construct a joint assignment that *locally* optimizes each of the beliefs. If we can construct such an assignment, we will see that we can provide guarantees on its (strong local or even global) optimality.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 553

>[!important] Definition
>A *max-marginal* of $f$ is **unambiguous** if for each variable $x_{i}$ there exists a *unique* $x_{i}^{*}$  that maximizes $$x_{i}^{*} = \arg\max_{x_{i}\in \mathcal{X}_{i}}\text{MaxMarg}_{f}(x_{i})$$

^ad6150

### Marginal MAP problem

>[!important] Definition
>For a probability model $\mathcal{P}_{\Phi}$ where the domain is partitioned into two parts $\mathcal{X} := \mathcal{Y} \cup \mathcal{W}$, the **marginal MAP inference** aims at computing
>$$
>y^{M-MAP} = \arg\max_{y}\mathcal{P}_{\Phi}(y) = \arg\max_{y}\sum_{\mathcal{W}}\hat{\mathcal{P}}_{\Phi}(y, \mathcal{W})
>$$

>[!quote]
>Thus, the marginal MAP problem involves both **multiplication** and **summation**, a combination that makes the task much more difficult, both theoretically and in practice. In particular, exact inference methods such as *variable elimination* can be *intractable*, even in simple networks.


### Factor Maximization

>[!important] Definition
>Let $X$ be a set of variables, $Y\not\in X$ a variable. Let $\phi(X, Y)$ be a *factor*.
>
>We define the **factor maximization** of $Y$ in $\phi$ to be *factor* $\psi$ over $X$ such that 
>$$
>\psi(X) := \max_{Y}\phi(X, Y)
>$$


### Max-Product Variable Elimination Algorithm

>[!info]
>A key observation is that we can **exchange the order** of *maximization and product*: if $X\not\in \text{scope}[\phi_{1}]$, then $$\max_{X}(\phi_{1} \cdot \phi_{2}) = \phi_{1} \cdot \max_{X}(\phi_{2}).$$

>[!important] Algorithm
>The sub-procedure **Max-Product-Elimination-Var** is described as below:
>
>- *Require*: $\Phi$, a set of *factors*
>- *Require*: $Z$, a variable to be *eliminated*
>- *Collect* the set of factors whose scopes *include* $Z$: $$\Phi_{Z} = \left\{ \phi\in \Phi: Z \in \text{scope}[\phi] \right\} $$
>- *Collect* the set of factors whose scopes *do not include* $Z$: $$\Phi_{-Z} = \Phi \setminus \Phi_{Z}.$$
>- Compute the **product** *of factors* whose scopes *include* $Z$: $$\psi = \prod_{\phi \in \Phi_{Z}}\phi$$
>- Compute the **maximization** of *product factors* over $Z$: $$\tau = \max_{Z}\psi$$
>- *Output*: $$\Phi_{-Z}\,\cup \,\tau \; \text{ and } \; \psi$$

>[!info]
>$\psi$ above is the **max-marginal** over $Z$


>[!important] Algorithm
>The **Max-Product-VE algorithm** is described as below:
>
>- *Require*: $\Phi_{0} := \Phi$, a set of *factors*
>- *Require*: $\prec$, an *ordering* on $\mathcal{X}$ such that $X_{i} \prec X_{j}$ if $i < j$ for any pair $X_{i}, X_{j} \in \mathcal{X}.$
>- For $i=1 \,{,}\ldots{,}\,k$:
>	- *Eliminate* one variable $X_{i}\in \mathcal{X}$ by calling the **Max-Product-Elimination-Var** sub-procedure $$(\Phi_{i}, \phi_{X_{i}}) = \text{Max-Product-Elimination-Var}(\Phi_{i-1}, X_{i}).$$
>- $\Phi_{k}$ contains the *probability of MAP*.
>- **Trace back** the *MAP assignment* based on a list of factors that contain the *eliminated variables*: $$x^{*} = \text{Traceback-MAP}(\left\{ \phi_{X_{i}}:\, i=1\,{,}\ldots{,}\,k \right\})$$
>- *Output*: the MAP assignment and the corresponding probability $$x^{*},\, \Phi_{k}$$

>[!info]
>If $X_i$ is the *final variable* in this *elimination process*, we have maximized all variables *other than* $X_i$, so that the resulting factor $$\phi_{X_{i}}$$ is the **max-marginal** over $X_i$.

### Decoding and Traceback

>[!important] Definition
>Given a set of *max-marginals*, the process of finding *global optimal* can be solved by a set of *local optimization problems* for individual variables. 
>
>The task of constructing a joint assignment that *locally optimizes* each of the beliefs is called the **decoding task**.


>[!important] Algorithm
>The sub-procedure **Traceback-MAP** is described as below:
>
>- *Require*: $\phi_{X_{i}}$, a set of *max-marginals* over $X_{i}$, $i=1\,{,}\ldots{,}\,k$
>- For $i= k \,{,}\ldots{,}\,1$:
>	- collect the *maximizing assignment* to the variables **eliminated after** $X_{i}$ $$u_{i} = (x_{i+1}^{*} \,{,}\ldots{,}\,x_{k}^{*})$$
>	- choose $x_{i}^{*}$ that **maximizes** the corresponding query, given the *previous choice* $u_{i}$ (restricted to $\text{scope}[\phi_{X_{i}}] - \left\{ X_{i} \right\}$ ) $$x_{i}^{*} = \arg\max_{x_{i}}\phi_{X_{i}}(x_{i}, u_{i})$$
>- *Output*: $$x^{*} = (x_{1}^{*} \,{,}\ldots{,}\,x_{k}^{*})$$

- [[Hidden Markov Model MAP Inference via Viterbi Algorithm]]

>[!info]
>The key intuition in this computation is that, as we *eliminate variables*, we cannot determine their maximizing value.  However, we can determine a **“conditional” maximizing value** — their maximizing value **given** the values of the variables that *have not yet been eliminated*. 
>- When we pick the value of the final variable, we can then **go back** and *pick the values* of the other variables accordingly. 
>- For the last variable eliminated, say $X$, the factor for the value $x$ contains the probability of the most likely assignment that contains $X = x$. 
>	- Thus, we correctly select the *most likely assignment to* $X$, and therefore *to all the other* variables. 
>
>This process is called **traceback** of the *solution.*

>[!important] Theorem
>Let $\mathcal{X}$ be some set of variables, and let $\Phi$ be a set of *factors* such that for each $\phi\in \Phi$, $$\text{scope}[\phi] \subseteq \mathcal{X}.$$
>
>Then for any **ordering** $\prec$ over $\mathcal{X}$, the **Max-Product-VE algorithm**$(\Phi, \prec)$ described above *returns*
>$$
>x^{*}  = \arg\max_{x}\,\prod_{\phi\in \Phi}\phi.
>$$ 
>and $\Phi^{*}$, which contain a single factor of *empty scope* whose **value** is $$\Phi^{*} = \max_{x}\,\prod_{\phi\in \Phi}\phi.$$


## Explanation

>[!quote]
>The factors generated by **max-product variable elimination** have an **identical structure** to those generated by the **sum-product algorithm** using the same ordering. Thus, our entire analysis of the computational complexity of variable elimination, which we performed for sumproduct in section 9.4, applies unchanged. In particular, we can use the same algorithms for finding elimination orderings, and the complexity of the execution is precisely the same induced width as in the sum-product case.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 556




-----------
##  Recommended Notes and References

- [[Sum-Product Variable Elimination]]

- [[Tree-Order Relation]]
- [[Root and Rooted Tree]]
- [[Tree Graph and Forest]]


- [[Probabilistic Graphical Models by Koller]] pp 552- 557
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]]
