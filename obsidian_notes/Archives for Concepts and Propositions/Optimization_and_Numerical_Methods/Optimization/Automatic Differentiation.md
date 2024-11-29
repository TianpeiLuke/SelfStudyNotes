---
tags:
  - concept
  - optimization/algorithm
  - machine_learning/algorithms
keywords:
  - automatic_differentiation
  - machine_learning_algorithm
topics:
  - optimization
name: Automatic Differentiation
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Automatic Differentiation

>[!quote]
>**Automatic differentiation** is the generic name for techniques that use the *computational representation* of a function to produce *analytic values* for the **derivatives**. Some techniques produce *code for the derivatives* at a general point x by manipulating the *function code* directly. Other techniques keep a *record of the computations* made during the *evaluation* of the function at a specific point $x$ and then *review* this information to *produce* a set of derivatives at $x$.
>
>-- [[Numerical Optimization by Nocedal]] pp 204

## Basic Principles

>[!quote]
>Automatic differentiation techniques are founded on the *observation* that **any function**, no matter how complicated, is evaluated by **performing a sequence of simple elementary operations** involving just **one or two arguments** *at a time*.
>
>-- [[Numerical Optimization by Nocedal]] pp 204

>[!important]
>**One argument operations** include
>- **trigonometric**: $\sin(x)$, $\cos(x)$, $\tan(x)$, $\csc(x)$,  $\sec(x)$, $\cot(x)$,  $\arcsin(x)$, $\arccos(x)$, $\arctan(x)$,
>- **exponential**: $\exp(x)$
>- **logarithmic**: $\log(x)$

>[!important]
>**Two arguments operations** include
>- **addition**: $x + y$
>- **subtraction**: $x - y$
>- **multiplication**: $x \times y$
>- **division**: $x / y$
>- **power**: $x^{y}$

>[!quote]
>Another common *ingredient* of the various automatic differentiation tools is their use of **the chain rule**.
>
>-- [[Numerical Optimization by Nocedal]] pp 204

>[!important] Chain Rule
>For $h: \mathbb{R}^{m} \to \mathbb{R}$ and $g: \mathbb{R}^{n} \to \mathbb{R}^{m}$, we have
>$$
>\nabla_{x}h\left(g(x)\right) = \sum_{i=1}^{m}\frac{ \partial h}{ \partial g_{i} }\nabla_{x}g_{i}(x) 
>$$

^fedbc0

## Computational Graph

>[!example]
>Compute gradient of $f(x)$ 
>$$
>f(x) = (x_{1}x_{2} \sin(x_{3}) + e^{x_{1} x_{2}}) / x_{3}
>$$
>We can decompose it into simple operations by introducing **intermediate variables**
>$$
>\begin{align*}
> x_{4} &= x_{1}\,x_{2}\\
> x_{5} &= \sin(x_{3})\\
> x_{6} &= e^{x_{4}}\\
> x_{7} &= x_{4}\,x_{5} \\
> x_{8} &= x_{6} + x_{7} \\
> x_{9} &= x_{8} / x_{3}
>\end{align*}
>$$
>and $x_{9}$ is the output final node. 


![[computation_graph_auto_diff.png]]

>[!important] Definition
>A **computational graph** $\mathcal{G} := (\mathcal{V}, \mathcal{E})$ is a *directed graph* that shows how the evaluation of a function $f(x)$ can be *broken down* into its elementary operations, and also indicates the *partial ordering* associated with these operations.
>- Each node $v\in \mathcal{V}$ represents a **variable**. There are three types of nodes:
>	- the *root nodes*, i.e. nodes with *no parents* represent **input variables**
>	- the *intermediate nodes* represent **intermediate variables**
>	- the *leaf nodes*, i.e. nodes with no children represent **output variables**, indicating the output value of the function. For a function $f(x)$, there exists *only one output node*.
>- Each directed edge $(u, v) \in \mathcal{E}$ represents a **input-output dependency relation** between parent node and children node. In particular, there are two types of connections:
>	- the **link structure** $(u, v) \in \mathcal{E}$ and $(w, v) \not\in \mathcal{E}$ for all $w \in \mathcal{V} \setminus \{ v \}$ represents an *one-argument function* $u \to v$.
>	- the **fork structure** $(u_{1}, v) \in \mathcal{E}$ and $(u_{2}, v) \in \mathcal{E}$ represents a *two-argument function* $(u_{1}, u_{2}) \to v$.
>- The **topological (partial) ordering** of the graph indicates the ordering of *evaluation* of the function $f$. The values in *all of* parent nodes need to be ready *before* the calculation of the children nodes
>  
>The *flow of computation* according to the direction of partial ordering in computational graph is called a **forward sweep**. 

>[!info]
>For automatic differentiation software, the identification of *intermediate quantities* and *construction of the computational graph* is carried out, explicitly or implicitly, by the software tool itself.

## Forward Mode

>[!important] Definition
>In the **forward mode** of automatic differentiation, we evaluate and carry forward a **directional derivative** of *each* *intermediate variable* $x_i$ in a given direction $p \in \mathbb{R}^n$, **simultaneously** with the **evaluation** of $x_{i}$ itself.

>[!info] Definition
>Note that the *directional derivative* of node $x_{i}$ along a direction $p$ can be computed by
>$$
>D_{p}x_{i} := \left\langle  p\,,\,\nabla x_{i} \right\rangle = \sum_{j}\frac{ \partial x_{i} }{ \partial x_{j} } p_{j}
>$$
>and $D_{p}f = D_{p}x_{final}$. The direction $p$ is called the **seed vector**. By chain rule,
>$$
>D_{p} h\left(g(x)\right) = \sum_{i=1}^{m}\frac{ \partial h}{ \partial g_{i} }D_{p} g_{i}(x) 
>$$

>[!important] 
>The key of **forward mode** is to observe that as soon as the *value* of $x_{i}$ at *any node is known*, we can **immediately compute** $D_{p}x_{i}$. This is because $$\frac{ \partial x_{i} }{ \partial x_{j} } := \frac{ \partial x_{i} }{ \partial x_{j} }(\text{Pa}(x_{i}))$$ is associated with the *local computational graph* and the *value of parent nodes* only. 
>- The value of $x_{i}$ is available *only if* *all* of its parents $\text{Par}(x_{i})$ are available. 
>- When the *local computational graph* is known, we can find *partial derivatives* of elementary operations analytically. 
>
>
>The directional derivatives $D_{p}x_{i}$ are therefore **evaluated side by side** *with* the **intermediate results**.

- [[Jacobian Matrix and Jacobian Determinant]]

>[!important] Forward Mode
>The **forward mode** of **automatic differentiation** is described as 
>- For $k=1 \,{,}\ldots{,}\,m$ according to *topological ordering*:
>	- If $x_{k}$ is not a *root node*: 
>		- Gather the values of all *parent nodes*  $x_{Pa(k)}:=(x_{j}, j\in \text{Pa}(k))$ and the corresponding directional derivatives $(d_{j}, j\in \text{Pa}(k))$
>		- For each $j \in Pa(k)$:
>			- Evaluate and store partial derivatives $$g[k, j] := \frac{ \partial x_{k} }{ \partial x_{j} }(x_{Pa(k)})$$ 
>		- Compute *directional derivative* $$d_{k}:= D_{v}x_{k} = \sum_{j \in \text{Pa}(k)}g[k, j]\,d_{j}$$
>		- Evaluate $$x_{k} = x_{k}(x_{Pa(k)})$$ using the values of all *parent nodes*  $Pa(k)$.
>		- Store and overwrite value $x_{k}$ and $d_{k}$
>-  Output the directional derivative $d_{m}$ as $D_{v}f := \left\langle  v\,,\,  \nabla f  \right\rangle.$

- Wikipedia [Topological sorting](https://en.wikipedia.org/wiki/Topological_sorting)
- [[Topological Sorting]]

>[!info]
>Several things to note
>- No need for users to construct *computational graph* and to identify *intermediate variables*
>- It is **not necessary to store** information $x_{i}$ and $D_{p}x_{i}$ for **every node** of *the computation graph* at once.
>	- Once all the children of any node have been *evaluated*, its associated values $x_{i}$ and $D_{p}x_{i}$  are **not needed further** and may be **overwritten in storage**.

>[!info]
>The key to **practical implementation** is the **side-by-side evaluation** of $x_{i}$ and $D_{p}x_{i}$. The automatic differentiation software associates a scalar $D_{p}w$ with *any scalar* $w$ that appears in the evaluation code. Whenever $w$ is used in an arithmetic computation, the software performs an *associated operation* (based on the chain rule) with the gradient vector $D_{p}w$.


>[!info]
>The forward mode of automatic differentiation can be implemented by means of a **precompiler**, which transforms *function evaluation code* into *extended code* that *evaluates the derivative vectors* as well.

## Reverse Mode

>[!important] Definition
>The **reverse mode** of *automatic differentiation* does **not** perform *function and gradient evaluations* **concurrently**. Instead, **after** the evaluation of $f$ is *complete*, it **recovers the partial derivatives** of $f$ with respect to each variable $x_{i}$ —independent and intermediate variables alike—by performing a **reverse sweep** of the computational graph.

^344a4a

>[!important] Definition
>Instead of keeping *gradient vectors* $g^{k}$ for intermediate variables, the **reverse mode** associates **scalar variable** $\bar{x}_{i}$ with *each node* in the graph; information about the *partial derivative* $\partial f / \partial x_{i}$ is **accumulated** in  $\bar{x}_{i}$ during the reverse sweep. The scalar $\bar{x}_{i}$ is called the **adjoint variables.**

>[!important]
>The **key observation** for the **reverse sweep** is that, for any node $i$, the partial derivative $\partial f / \partial x_{i}$  can be *build up* from the *partial derivatives* of its **children** $\partial f / \partial x_{j}$. 
>
>That is, by **chain rule**
>$$
> \frac{ \partial f }{ \partial x_{i} } = \sum_{j \in \text{Ch}(i)}  \frac{ \partial f }{ \partial x_{j} }\;\frac{ \partial x_{j} }{ \partial x_{i} }
>$$  
>
>For each node $i$, we *add the RHS to the scalar* $\bar{x}_{i}$ as soon as it becomes known.
>$$
> \bar{x}_{i} \leftarrow \bar{x}_{i} + \frac{ \partial f }{ \partial x_{j} }\;\frac{ \partial x_{j} }{ \partial x_{i} }
>$$
>Once contributions have been received from all the **child nodes** of $i$,
>$$
>\bar{x}_{i} = \frac{ \partial f }{ \partial x_{i} }(x) 
>$$
>so we declare node $i$ to be “**finalized.**” At this point, node $i$ is *ready* to contribute *a term to the summation* for each of its **parent nodes** according to the formula.
>$$
> \frac{ \partial f }{ \partial x_{i} } = \sum_{j \in \text{Ch}(i)}  \bar{x}_{j} \;\frac{ \partial x_{j} }{ \partial x_{i} }
>$$  
>
>Note that for **derivative evaluation**, the *flow* of computation in the graph is **from children to parents**—the *opposite direction* to the computation flow for **function evaluation**.

![[computation_graph_auto_diff_reverse.png]]

>[!important] Reverse Mode (Forward Sweep)
>- Input  the evaluation point $x_{i}, i\in [n]$
>- Initialize the computational graph $(\mathcal{V}, \mathcal{E})$
>- For $k= 1, \,{,}\ldots{,}\,m$ in *topological ordering*:
>	- Evaluate and store $$x_{k} = x_{k}(x_{Pa(k)})$$ into the node $k\in \mathcal{V}$ using the values of all *parent nodes*  $Pa(k)$.
>- Output the computational graph with node value and graph topology

^0382e1


>[!important] Reverse Mode (Reverse Sweep)
>- Input  the evaluation point $x_{i}, i\in [n]$
>- Initialize all adjoint variables $\bar{x}_{k} = 1, \; \forall k$ 
>- Run **forward sweep** to obtain computational graph $\mathcal{G}$ and $(x_{i}, i\in [m])$
>- For $k= m, m-1 \,{,}\ldots{,}\, 1$ in *reverse topological ordering*:
>	- If $\text{Ch}(k) = \emptyset$, i.e. node $k$ is *leaf node*:
>		- the node $k$ is marked as **finalized**
>		- *continue*
>	- For all $j \in \text{Ch}(k)$: 
>		- If $j$ is **finalized**
>			- gather node values for *all parent nodes* of $j$ as $x_{Pa(j)}$
>			- evaluate the *derivative* $$g[j, k] = \frac{ \partial x_{j} }{ \partial x_{k} }(x_{Pa(j)}) $$
>			- update **adjoint variable** $$\bar{x}_{k} \leftarrow \bar{x}_{k}  + \, \bar{x}_{j}\;g[j, k]$$
>	- If **all of children** $j \in \text{Ch}(k)$ are finalized, then node $k$ is marked as **finalized**
>- Output $$\nabla f(x) =  (\bar{x}_{i}, i\in [n])$$

^52d1dd

>[!info]
>[[Back-Propagation Algorithm]] is a version of **reverse mode** of **automatic differentiation**.

>[!info]
>This algorithm is close to the **Sum-Product Message Passing Algorithm** in graphical model

- [[Sum-Product Belief Propagation Algorithm for Clique Tree]]

## Explanation

>[!info]
>This is a version of dynamic programming.

- [[Dynamic Programming Algorithms]]

## Automatic Differentiation of Vector-valued Function

>[!important]
>Consider $f: \mathbb{R}^{n} \to \mathbb{R}^{m}$, the goal is to compute the Jacobian matrix
>$$
>\frac{ \partial f }{ \partial x } = \left[ \frac{ \partial f_{i} }{ \partial x_{j} }  \right]_{i,j}  \in \mathbb{R}^{m \times n}
>$$

- [[Jacobian Matrix and Jacobian Determinant]]

>[!important]
>For the **forward mode**, it is the same as the scalar function for the intermediate nodes. For the output nodes, since there are total of $m$ output nodes, we can find the directional derivative for each component
>$$
>D_{v}f_{i} = \left\langle  v \,,\, \nabla f_{i}   \right\rangle, \quad i = 1 \,{,}\ldots{,}\, m
>$$
>then
>$$
> \frac{ \partial f }{ \partial x }\;p = [D_{v}f_{1} \,{,}\ldots{,}\,D_{v}f_{m}]^T
>$$

>[!important]
>The key to applying the **reverse mode** to a vector function is to choose a **seed vector** $w \in \mathbb{R}^{m}$, and to apply the **reverse mode** for a *scalar function*
>$$
>f_{w}(x) := \left\langle  w\,,\, f(x)   \right\rangle
>$$
>then the result of the reverse mode is the vector
>$$
>\nabla_{x} f_{w} = \nabla_{x} \left(\sum_{j=1}^{m}w_{j} f_{j}(x)\right) = \sum_{j=1}^{m}w_{j} \nabla_{x}f_{j} = \left(\frac{ \partial f }{ \partial x }\right)^T \,w
>$$
>The technique can be implemented by **seeding the adjoint variables** $\bar{x}_{i}$ in the $m$ dependent nodes that contain $f_{1} \,{,}\ldots{,}\,f_{m}$, with the components $w_{1} \,{,}\ldots{,}\,w_{m}$ of the vector $w$. At the end of the *reverse sweep*, the node for independent variables $x_{1} \,{,}\ldots{,}\,x_{n}$ will contain
>$$
>\frac{d}{dx_{i}}\left\langle  w\,,\,f(x) \right\rangle, \quad i= 1 \,{,}\ldots{,}\,n
>$$
>which are simply the components of $\left(\frac{ \partial f }{ \partial x }\right)^T \,w.$

>[!quote]
>The factor of **increase** in the number of **arithmetic operations** required, in comparison to an evaluation of $r$ alone, is **no more than 5 times** the **number of seed vectors**. (The factor of 5 is the usual overhead from the reverse mode for a scalar function.) The space required for **storage** of the computational graph is **no greater than in the scalar case**. As before, we need **only store the graph topology** information together with the **partial derivative** *associated with each arc*.
>
>-- [[Numerical Optimization by Nocedal]] pp 213


## Comparison between Forward and Reverse Mode

>[!quote]
>During the **reverse sweep**, we work with **numerical values**, *not with formulae or computer code* involving the variables $x_{i}$ or the *partial derivatives* $\partial f / \partial x_{i}$. 
>
>During the **forward sweep**—the *evaluation* of $f$ —we **not only calculate the values** of each variable $x_{i}$ , but we also **calculate and store** the *numerical values* of **each partial derivative** $\partial f / \partial x_{i}$. Each of these partial derivatives is associated with *a particular arc* of the computational graph. 
>
>The numerical values of $\partial x_{j} / \partial x_{i}$ **computed during the forward sweep** are then used in the formula (8.32) during the **reverse sweep**.
>
>-- [[Numerical Optimization by Nocedal]] pp 208

>[!quote]
>The main **appeal** of the *reverse mode* is that its **computational complexity is low** for the *scalar functions* $f: \mathbb{R}^n \to \mathbb{R}$. 
>
>The extra arithmetic associated with the *gradient computation* is **at most four or five times** the arithmetic needed to *evaluate the function* alone.
>
>As we noted above, the **forward mode** may require up to **$n$ times more arithmetic** to compute the *gradient* $\nabla f$ than to *compute the function* $f$ alone, making it appear **uncompetitive** with the **reverse mode**. When we consider vector functions $r: \mathbb{R}^n \to \mathbb{R}^m$, the relative costs of the forward and reverse modes become more similar as m increases

>[!quote]
>An apparent **drawback** of the **reverse mode** is the need to **store the entire computational graph**, which is needed for the reverse sweep. In principle, storage of this graph is not too difficult to implement. Whenever an elementary operation is performed, we can *form and store* a **new node** containing the intermediate result, **pointers** to the (one or two) parent nodes, and the **partial derivatives** associated with these arcs. During the reverse sweep, the nodes can be *read in the reverse order* to that in which they were written, giving a particularly simple access pattern. The process of forming and writing the graph can be implemented as a straightforward extension to the elementary operations via **operator overloading**. The reverse sweep/gradient evaluation can be invoked as a *simple function call*.
>
>Unfortunately, the computational graph may require a *huge amount of storage*. ... The storage requirements can be reduced, at the cost of *some extra arithmetic*, by performing **partial forward and reverse sweeps** on *pieces* of the *computational graph*, **reevaluating** portions of the graph *as needed* rather than storing the whole structure. Descriptions of this approach, sometimes known as **checkpointing**, can be found in Griewank ...
>
>-- [[Numerical Optimization by Nocedal]] pp 210

### Analogy using Matrix Multiplication

>[!quote]
>The relationship between **forward mode** and **backward mode** is analogous to the relationship between **left-multiplying** *versus* **right-multiplying** a sequence of matrices, such as $$ABCD, \quad (6.58)$$ where the matrices can be thought of as *Jacobian*. For example, if $D$ is a *column vector* while $A$ has many rows, the graph will have a *single output* and *many inputs*, and *starting* the multiplications *from the end* and going **backward** *requires only* **matrix-vector products**. This order corresponds to the **backward mode**. Instead, starting to multiply from the left would involve a series of matrix-matrix products, which makes the whole computation much more expensive. If $A$ has *fewer rows* than $D$ has *columns*, however, it is **cheaper** to run the multiplications left-to-right, corresponding to the forward mode.
>
>-- [[Deep Learning by Goodfellow]] pp 216



### Table Comparison

|                                         | **forward mode**                                                                                                                                                                                 | **reverse mode**                                                                                                                                                                                                         |
| --------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| objective function                      | $f: \mathbb{R}^{n} \to \mathbb{R}$                                                                                                                                                               | $f: \mathbb{R}^{n} \to \mathbb{R}$                                                                                                                                                                                       |
| input variables                         | $x = (x_{1} \,{,}\ldots{,}\,x_{n})$                                                                                                                                                              | $x = (x_{1} \,{,}\ldots{,}\,x_{n})$                                                                                                                                                                                      |
| objective                               | compute **gradient** $$\nabla f(x) = \left(\frac{ \partial f }{ \partial x_{i} }, i \in [n]\right)$$                                                                                             | compute **gradient**  $$\nabla f(x) = \left(\frac{ \partial f }{ \partial x_{i} }, i \in [n]\right)$$                                                                                                                    |
| intermediate variables                  | $(x_{n+1} \,{,}\ldots{,}\,x_{m})$, where $x_{m}$ corresponds to $f(x)$                                                                                                                           | $(x_{n+1} \,{,}\ldots{,}\,x_{m})$, where $x_{m}$ corresponds to $f(x)$                                                                                                                                                   |
| **computational graph**                 | $\mathcal{G} := (\mathcal{V}, \mathcal{E})$ with $\lvert\mathcal{V}\rvert = m.$                                                                                                                  | $\mathcal{G} := (\mathcal{V}, \mathcal{E})$ with $\lvert\mathcal{V}\rvert = m.$                                                                                                                                          |
| notations                               | $\text{Pa}(i) = \{ j\in \mathcal{V}: (j, i) \in \mathcal{E} \}$                                                                                                                                  | $\text{Ch}(i) = \{ j\in \mathcal{V}: (i, j) \in \mathcal{E} \}$                                                                                                                                                          |
| **sweep ordering**                      | **forward topological ordering**, i.e. a node is ranked after all of its parent nodes                                                                                                            | **reverse topological ordering**, i.e. the reverse ranking of forward sort                                                                                                                                               |
| procedures                              | 1. **function evaluation**; <br>2. **gradient computation**                                                                                                                                      | 1. **function evaluation**; <br>2. **gradient computation**                                                                                                                                                              |
| sync of procedures                      | **concurrent** <br>- **forward sweep**: function evaluation<br>- **forward sweep**: derivative evaluation<br>                                                                                    | **sequential** <br>- **forward sweep**: function evaluation<br>- **reverse sweep**: derivative evaluation                                                                                                                |
| **formula**                             | $$D_{v}x_{i} = \sum_{j \in \text{Pa}(i)}\frac{ \partial x_{i} }{ \partial x_{j} }(x_{Pa(i)})\;D_{v}x_{j}$$                                                                                       | $$\frac{ \partial f }{ \partial x_{i} }  = \sum_{j \in \text{Ch}(i)}  \frac{ \partial f }{ \partial x_{j} }(x_{Ch(i)})\;\frac{ \partial x_{j} }{ \partial x_{i} }(x_{Pa(j)})$$                                           |
| output                                  | $$D_{v}f(x) := \left\langle v\,,\,\nabla f(x) \right\rangle = D_{v}x_{m}$$                                                                                                                       | $$\nabla f(x) = \left(\frac{ \partial f }{ \partial x_{i} }, i \in [m]\right)$$                                                                                                                                          |
| **auxiliary variable**                  | **seed vector** $v:=(v_{i}, i\in [m])$                                                                                                                                                           | **adjoint variables** $(\bar{x}_{i}, i\in [m])$                                                                                                                                                                          |
| **update formula**                      | $$d_{i} = \sum_{j \in \text{Pa}(i)}\frac{ \partial x_{i} }{ \partial x_{j} }(x_{Pa(i)})\;d_{j}$$ and  $$x_{Pa(j)},\, \frac{ \partial x_{j} }{ \partial x_{i} } $$ are evaluated at the same time | $$\bar{x}_{i} \leftarrow \bar{x}_{i} + \bar{x}_{j}\;\frac{ \partial x_{j} }{ \partial x_{i} }(x_{Pa(j)})$$ where $$x_{Pa(j)},\, \frac{ \partial x_{j} }{ \partial x_{i} } $$ comes from *forward loop*                   |
| **triggering** condition for update     | the values of **all parent nodes** are updated                                                                                                                                                   | the adjoint variable $\bar{x}_{i}$ is **finalized**, i.e. $$\bar{x}_{i} = \frac{ \partial f }{ \partial x_{i} }$$                                                                                                        |
| intermediate **storage**                | 1. the **directional derivative** $d_{i}$<br>2. the **value of intermediate nodes** $x_{i}$ <br>                                                                                                 | 1. the **adjoint variables** $\bar{x}_{i}$<br>2. the **value of intermediate nodes** $x_{i}$<br>3. all **partial derivatives** with respect to its parent nodes $$\frac{ \partial x_{i} }{ \partial x_{j} }(x_{Pa(i)})$$ |
| need to **store** *computational graph* | No                                                                                                                                                                                               | Yes, including *graph topology*, *node value* ($x_{i}$) and *edge value* $\partial x_{i} / \partial x_{j}$                                                                                                               |






-----------
##  Recommended Notes and References


- [[Back-Propagation Algorithm]]
- [[Newton Method]]
- [[Newton-Conjugate Gradient and Inexact Newton Method]]
- [[Newton-Lanczos Method for Large Scale Optimization]]
- [[Conjugate Gradient Algorithm Nonlinear]]


- [[Numerical Optimization by Nocedal]] pp 204
- [[Nonlinear Programming by Bertsekas]]


- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 255 - 260
- [[Deep Learning Foundations and Concepts by Bishop]] pp 233 - 252
- [[Deep Learning by Goodfellow]] pp 214 - 216
- [[Foundations of Computer Vision by Torralba]] pp 166 - 178