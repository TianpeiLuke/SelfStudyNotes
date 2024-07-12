---
tags:
  - concept
  - machine_learning/algorithms
  - deep_learning/algorithms
keywords:
  - back_propagation_algorithm
  - deep_learning/algorithm
topics:
  - machine_learning_algorithm
name: Back-Propagation Algorithm
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Back-Propagation Algorithm

>[!quote]
>When we use a feedforward neural network to accept an input $x$ and produce an output $y$, information *flows forward* through the network. The input $x$ provides the initial information that then *propagates up* to the hidden units at each layer and finally produces $y$. This is called **forward propagation**. During *training*, forward propagation can *continue onward* until it produces a *scalar cost* $J(\theta)$.
>
>The **back-propagation algorithm** (Rumelhart et al., 1986a), often simply called **backprop**, allows the information *from the cost* to then *flow backward* through the network in order to *compute the gradient*.
>
>-- [[Deep Learning by Goodfellow]] pp 197

![[Automatic Differentiation#^fedbc0]]

>[!important] 
>The key ideas behind **back-propagation** are
>- the concept of **computational graph** which are directed acyclic graph (DAG) where 
>	- each *node* $i\in \mathcal{V}$ represents *input/intermediate/output variable* and 
>	- each *edge* represents the *input-output function dependency* between variables and
>	- each edge $(j, i) \in \mathcal{E}$ is associated with a *partial derivatives* $\partial x_{i} / \partial x_{j}$ 
>- the chain rule of gradient $$\nabla_{x} h = \left(\frac{ \partial y }{ \partial x } \right)^T \nabla_{y}\,h$$ where $$\frac{ \partial y }{ \partial x } = \left[\frac{ \partial y_{i} }{ \partial x_{j} }\right]_{i,j} $$ is the **Jacobian matrix**.
>  
> In computational graph, the functions are simple operations with one or two input variables.  

### Backpropagation as Reverse Mode Automatic Differentiation


>[!important]
>Backpropagation is a variant of the **reverse mode** of **automatic differentiation**.

- [[Automatic Differentiation]]

>[!quote]
>The deep learning community has been somewhat isolated from the broader computer science community and has largely developed its own cultural attitudes concerning how to perform differentiation. More generally, the field of **automatic differentiation** is concerned with how to compute derivatives algorithmically. The back-propagation algorithm described here is only one approach to automatic differentiation. It is a special case of a broader class of techniques called **reverse mode accumulation.** Other approaches evaluate the subexpressions of the chain rule in different orders. In general, *determining the order of evaluation* that results in the *lowest computational cost* is a difficult problem. **Finding the optimal sequence of operations** to compute the gradient is **NP-complete** (Naumann, 2008), in the sense that it may require simplifying algebraic expressions into their least expensive form.
>
>-- [[Deep Learning by Goodfellow]] pp 215



![[Automatic Differentiation#^0382e1]]

![[Automatic Differentiation#^52d1dd]]

- We can **compute the Jacobian** during *the reverse sweep* instead of forward sweep. This way, we do not need to keep the Jacobian in memory for too long.

### General Back-propagation

>[!quote]
>More formally, each node in the graph $G$ corresponds to a *variable*. To achieve maximum generality, we describe this *variable* as being a *tensor* $V$. Tensors in general can have any number of dimensions. They subsume *scalars*, *vectors*, and *matrices*.
>
>We assume that each variable $V$ is associated with the following *subroutines*:
>- **$\text{get\_operation}(V)$**: This returns the **operation that computes** $V$, represented by the *edges coming into* V in the computational graph. For example, there may be a Python or C++ class representing the matrix multiplication operation, and the $\text{get\_operation}$ function. Suppose we have a variable that is created by *matrix multiplication*, $C = AB$. Then $\text{get\_operation}(V)$ returns a *pointer* to an instance of the corresponding C++ class. 
>- **$\text{get\_consumers}(V, G)$**: This returns the list of *variables* that are **children** of V in the computational graph $G$. 
>- **$\text{get\_inputs}(V, G)$**: This returns the list of *variables* that are **parents** of $V$ in the computational graph $G$.
>
>Each **operation** $op$ is also associated with a $\text{bprop}$ *operation*. This $\text{bprop}$ operation can compute a **Jacobian-vector product** as described by equation  
>$$
>\nabla_{\boldsymbol{X}}z = \sum_{j}\;\left(\nabla_{\boldsymbol{X}}Y_{j}\right)\;\frac{ \partial  z}{ \partial Y_{j} } 
>$$
>Each operation is *responsible* for knowing *how to back-propagate* through the edges in the graph that it participates in. ... The back-propagation algorithm itself *does not need to know any differentiation rules*. It only needs to call *each operation’s $\text{bprop}$  rules* with the right arguments. 
>
>Formally, $\text{op.bprop }(\text{inputs}, X, G)$ must return $$\sum_{i}\left(\nabla_{X}\; \text{op.f }(\text{input})_{i}\right)\,G_{i}$$ which is just an implementation of the chain rule. 
>
>Here, 
>- $\text{inputs}$ is a list of *inputs* that are supplied to the operation, 
>- $op.f$ is the *mathematical function* that the operation implements, 
>- $X$ is the input whose *gradient* we wish to compute, and 
>- $G$ is the *gradient on the output* of the operation.



![[backprop_outer_loop.png]]

![[backprop_inner_loop.png]]

## Explanation

>[!quote]
>The **back-propagation algorithm** is designed to **reduce the number of common subexpressions** without regard to memory. Specifically, it performs on the order of **one Jacobian product per node** in the graph. This can be seen from the fact that backprop (algorithm 6.2) visits **each edge from node** $u(j)$ to node $u(i)$ of the graph **exactly once** in order to obtain the associated partial derivative $\partial u(i) / \partial u(j)$ . Backpropagation thus *avoids the exponential explosion* in **repeated subexpressions**. Other algorithms may be able to avoid more subexpressions by performing *simplifications on the computational graph*, or may be able to *conserve memory* by **recomputing** rather than storing some subexpressions. We revisit these ideas after describing the back-propagation algorithm itself.
>
>--  [[Deep Learning by Goodfellow]] pp 202



>[!quote]
>When the **forward graph** $\mathcal{G}$ has a *single output node* and each partial derivative $\partial u(i) / \partial u(j)$ can be computed with a **constant amount of computation**, back-propagation guarantees that the **number of computations for the gradient computation** is of the **same order** as the **number of computations for the forward computation**: this can be seen in algorithm 6.2, because each local partial derivative $\partial u(i) / \partial u(j)$ needs to be computed **only once** along with an associated multiplication and addition for the recursive chain-rule formulation (equation 6.49). The overall computation is therefore $\mathcal{O}(\# edges)$.
>
>--  [[Deep Learning by Goodfellow]] pp 215

>[!quote]
>We defined back-propagation only for computing a scalar output gradient, but back-propagation can be *extended* to **compute a Jacobian** (either of $k$ *different scalar nodes* in the graph, or of a *tensor-valued* node containing $k$ values). A naive implementation may then *need $k$ times more computation*: for each scalar internal node in the original forward graph, the naive implementation computes $k$ gradients instead of a single gradient. When **the number of outputs of the graph** is **larger** than **the number of inputs**, it is sometimes *preferable* to use another form of automatic differentiation called **forward mode accumulation.** *Forward mode accumulation* has been proposed for obtaining *real-time computation* of gradients in *recurrent networks*, for example (Williams and Zipser, 1989). This approach also **avoids** the need to *store the values and gradients* for the *whole graph*, trading off computational efficiency for memory.
>
>--  [[Deep Learning by Goodfellow]] pp 215

- [[Automatic Differentiation#Forward Mode]]

## Complexity

>[!quote]
>Computing a gradient in a graph with $n$ nodes will **never execute more than** $O(n^2)$ operations or **store** the output of **more than** $O(n^2)$ *operations*. Here we are counting operations in the computational graph, not individual operations executed by the underlying hardware, so it is important to remember that the runtime of each operation may be highly variable.... We can see that **computing the gradient** requires **at most $O(n^2)$ operations** because the *forward propagation* stage will *at worst execute all $n$ nodes* in the original graph (depending on which values we want to compute, we may not need to execute the entire graph). The *back-propagation algorithm* adds **one Jacobian-vector product**, which should be expressed with $O(1)$ nodes, per edge in the original graph. Because the computational graph is a *directed acyclic graph* it has **at most $O(n^2)$ edges**. ... Most neural network **cost functions** are roughly **chain-structured**, causing back-propagation to have $O(n)$ **cost**.
>
>--  [[Deep Learning by Goodfellow]] pp 209


## Dynamic Programming

>[!info]
>A naive approach to compute gradient of loss function with respect to input need to **account for all paths** 
>$$
>\frac{ \partial f }{ \partial x_{j} } = \sum_{\text{path }\gamma: \gamma(0)=j, \gamma(t) = f } \prod_{k=2}^{t}\frac{ \partial x_{\gamma(k)} }{ \partial x_{\gamma(k-1)} } 
>$$
>
>Since the number of paths from node $j$ to node $n$ can **grow exponentially** in the length of these paths, the number of terms in the above sum, which is the number of such paths, can grow exponentially *with the* **depth** of the *forward propagation* graph.
>
>This large cost would be incurred because the **same computation** for $$\frac{ \partial x_{k} }{ \partial x_{i} } $$  would be redone many times. 


>[!info]
>To **avoid such recomputation**, we can think of back-propagation as a *table-filling algorithm* that takes advantage of *storing intermediate results*. Each node in the graph has a corresponding slot in a table to *store the gradient* for that node. By filling in these table entries in order, back-propagation avoids repeating many common subexpressions.
>
>In other word, back-propagation is a **dynamic programming algorithm**. It use additional memory (via the **computational graph**) to reduce the repeated computation of *partial derivatives* and *intermediate evaluations*.

- [[Dynamic Programming on Markov Decision Process]]

## Symbol-to-Number Differentiation vs. Symbol-to-Symbol Differentiation

>[!important] Definition
>Algebraic expressions and *computational graphs* both operate on **symbols**, or *variables* that do not have specific values. These **algebraic** and **graph-based representations** are called **symbolic representations**.
>
>When training or evaluation, we replace the symbols with corresponding **numerical** values.

>[!important] Definition
>Some approaches to back-propagation take a *computational graph* and a set of *numerical values* for the inputs to the graph, then *return a set of numerical values* describing the gradient at those input values. We call this approach **symbol-to-number differentiation**. This is the approach used by libraries such as **Torch** (Collobert et al., 2011b) and **Caffe**.

>[!important] Definition
>Another approach is to take a *computational graph* and **add additional nodes** *to the graph* that provide a **symbolic description** of the *desired derivatives*. This is the approach taken by **Theano** (Bergstra et al., 2010; Bastien et al., 2012) and **TensorFlow** (Abadi et al., 2015).

![[backprop_symbol_symbol.png]]






-----------
##  Recommended Notes and References

- [[Gradient Descent Algorithm]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 264
- [[Deep Learning by Goodfellow]] pp 197 - 216
- [[Deep Learning Foundations and Concepts by Bishop]] pp 233

- [[Numerical Optimization by Nocedal]]