---
tags:
  - concept
  - machine_learning/models
  - probabilistic_graphical_models/models
keywords:
  - probabilistic_graphical_model
topics:
  - machine_learning_models
  - probabilistic_graphical_model
name: Probabilistic Graphical Models
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Probabilistic Graphical Models

>[!important] Definition
>Let $G = (V, E)$ be a *graph* and $P$ be the *joint probability distribution* of a random vector $X = (X_{1} \,{,}\ldots{,}\, X_{d}) \in \mathcal{X} \subset \mathbb{R}^{d}$ where $d = |V|$. 
>
>$P$ is a **probabilistic graphical model** *associated with* $G$ if $G$ is the *graphical representation* of $P$ where 
>- each node $v\in V$ is associated with one random variable $X_{v}\in X$ and 
>- each edge $uv\in E$ represents the *direct probabilistic relation* between two end variables $X_{u}, X_{v}\in X$. 
>  
>A **probabilistic graphical model** consists of a collection of probability distributions (or *probability density functions* $p$ with respect to some measure $\nu$) that **factorize** according to the structure of *underlying graph*. 

- [[Graph]]
- [[Probability Distribution of Random Variable]]
- [[Probability Density Function of Random Variable]]
- [[Product Measure]]


>[!important] Definition
>Let $P$ be a  *joint probability distribution* of a random vector $X = (X_{1} \,{,}\ldots{,}\, X_{d}) \in \mathbb{R}^{d}$. Let $I(P)$ be the set of *independence assertions* of the form $$P \vDash\; X \perp Y \,|\, Z$$ that holds in $P$.
>
>Let $G = (V, E)$. The distribution $P$ is a **probabilistic graphical model** *associated with* $G$ if $P$ satisfies the *local independencies* associated with $G$, i.e. $$I(G) \subseteq I(P).$$ 
>
>

- [[Conditional Independence]]
- [[I-Map and Independence Assertion]]


## Explanation

>[!quote]
>**Probabilistic graphical models** use a **graph-based representation** as the basis for *compactly encoding* a complex distribution over a *high-dimensional space.* In this graphical representation, illustrated in figure 1.1, the **nodes** (or ovals) correspond to the **variables** in our domain, and the **edges** correspond to **direct probabilistic interactions** between them.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 3

>[!quote]
>There is a **dual perspective** that one can use to interpret the structure of this graph. From one perspective, the graph is a **compact representation** of a set of **independencies** that hold in the distribution;
>
>-- [[Probabilistic Graphical Models by Koller]] pp 4

>[!quote]
>It turns out that these two perspectives — the graph as a representation of a set of **independencies**, and the graph as a skeleton for **factorizing a distribution** — are, in a deep sense, **equivalent**. The independence properties of the distribution are precisely what allow it to be represented compactly in a factorized form. Conversely, a particular factorization of the distribution guarantees that certain independencies hold.
>
>-- [[Probabilistic Graphical Models by Koller]] pp 4

>[!quote]
>Deep learning draws on many modeling formalisms that researchers can use to guide their design efforts and describe their algorithms. One of these *formalisms* is the idea of **structured probabilistic models**. ...
>
>A structured probabilistic model is a way of **describing** a *probability distribution*, using a **graph** to describe which random variables in the probability distribution *interact with each other directly*. Here we use “graph” in the graph theory sense—a set of vertices connected to one another by a set of edges. Because the structure of the model is defined by a graph, these models are often also referred to as **graphical models.**
>
>... While this approach allows us to overcome many challenges, it is not without its own **complications**. One of the **major difficulties** in *graphical modeling* is *understanding* **which variables** need to be able to **interact directly**, that is, **which graph structures** are **most suitable** for a given problem.... 
>
>-- [[Deep Learning by Goodfellow]] pp 549



>[!quote]
>Probability theory can be expressed in terms of *two simple equations* known as the **sum rule** and the **product rule**. .... In principle, we could therefore formulate and use *complex probabilistic models* purely by using algebraic manipulation. However, we will find it *advantageous* to augment the analysis using **diagrammatic representations** of **probability distributions**, as these offer several useful properties: 
>1. They provide a simple way to **visualize the structure** of a probabilistic model and can be used to design and motivate new models.
>2. Insights into the **properties** of the model, including **conditional independence properties**, can be obtained by inspecting the graph.
>3. The complex **computations** required to perform **inference** and **learning** in sophisticated models can be expressed in terms of **graphical operations**, such as *message-passing*, in which the underlying mathematical operations are carried out implicitly.
>
>Although such graphical models have nodes and edges much like neural network diagrams, their **interpretation** is specifically **probabilistic** and carries a **richer semantics**.
>   
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 326

- [[Probability Space]]

>[!info]
>A **probabilistic graphical model** is a *distributed system* 
>- each **local model (factors)** maintain the *probabilistic knowledge* between a few variables
>- each edge encodes the direct probabilistic dependency (i.e. **conditional dependency**) between factors
>- graph provides a **partial ordering** so that the **communication** and **transfer** of *new information* can be completed in order. 
>- the **consistency** between **global** and **local system** via graph operation such as message-passing.



## Challenges for Probability Distribution in High Dimensional Space

>[!quote]
>Modeling a rich distribution over *thousands or millions of random variables* is a challenging task, both computationally and statistically. Suppose we wanted to model only binary variables.
>
>...
>
>This is **not feasible** for several reasons:
>- **Memory**—the cost of *storing the representation*: For all but very small values of $n$ and $k$, representing the distribution *as a table* will require too many values to store.
>- **Statistical efficiency**: As the number of *parameters* in a *model* increases, so does the *amount of training data needed* to choose the values of those parameters using a statistical estimator. Because the table-based model has an **astronomical number of parameters**, it will require an **astronomically large training set** to fit accurately. Any such model will overfit the training set very badly unless additional assumptions are made linking the different entries in the table (as in back-off or smoothed n-gram models; section 12.4.1).
>- **Runtime**—the **cost of inference**: Suppose we want to perform an inference task where we use our model of the joint distribution $P(x)$ to compute some other distribution, such as the *marginal distribution* $P(x_{1})$ or the *conditional distribution* $P (x_{2} | x_{1})$. Computing these distributions will require *summing across the entire table*, so the *runtime of these operations* is as high as the *intractable memory cost* of storing the model.
>- **Runtime**—the **cost of sampling**: Likewise, suppose we want to draw a sample from the model. The naive way to do this is to sample some value $u \sim U(0, 1)$, then iterate through the table, adding up the probability values until they exceed u and return the outcome corresponding to that position in the table. This requires *reading through the whole table* in the worst case, so it has the same exponential cost as the other operations.
>
>...
>
>The problem with the table-based approach is that we are *explicitly modeling* **every possible kind of interaction** between every possible subset of variables. The probability distributions we encounter in real tasks are much simpler than this. Usually, most variables influence each other only indirectly. ...
>
>...
>Structured probabilistic models provide a formal framework for **modeling only direct interactions** between random variables. This allows the models to have **significantly fewer parameters** and therefore be estimated reliably from less data. These *smaller models* also have dramatically **reduced computational cost** in terms of *storing the model*, *performing inference* in the model, and *drawing samples* from the model.
>
>
>-- [[Deep Learning by Goodfellow]] pp 551





## Bayesian Network

- [[Bayesian Network on Directed Acyclic Graph]]\


## Markov Network

- [[Markov Network on Undirected Graph]]





-----------
##  Recommended Notes and References


- [[Graph]]
- [[Probability Space]]

- [[Probability Density Function of Random Variable]]
- [[Probability Distribution of Random Variable]]



- [[Probabilistic Graphical Models by Koller]] pp 3
- [[Graphical Models Exponential Families and Variational Inference by Wainwright and Jordan]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 765
- [[Deep Learning by Goodfellow]] pp 74, 549
- [[Deep Learning Foundations and Concepts by Bishop]] pp 325