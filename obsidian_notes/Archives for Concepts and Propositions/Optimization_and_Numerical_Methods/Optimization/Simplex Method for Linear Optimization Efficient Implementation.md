---
tags:
  - concept
  - optimization/algorithm
keywords:
  - simplex_method_linear
topics:
  - optimization/algorithm
name: Simplex Method for Linear Optimization Efficient Implementation
date of note: 2024-08-18
---

## Concept Definition

>[!important]
>**Name**: Simplex Method for Linear Optimization Efficient Implementation

![[Simplex Method for Linear Optimization#^933ad4]]

### Naive Implementation

>[!info]
>In naive implementation, given the basis matrix $B$, we compute two quantities
>- We need to compute $p^{T} = c_{B}^{T}\,B^{-1}$ by solving the *linear system of equations* $$B^{T}\,p = c_{B}$$ The vector $p$ is called the **vector of simplex multipliers** associated with the basis $B$.
>- The reduced cost of any variable $x_{j}$ is $$\bar{c}_{j} = c_{j} - \left\langle p , A_{j} \right\rangle$$
>- Once a column $A_{j}$ is *selected* to **enter the basis**, we solve the *linear system* $$B\,d_{B} = - A_{j}$$ in order to determine **the $j$-th basic direction** $$d_{B} = - B^{-1}\,A_{j}.$$

>[!important]
>In **naive implementation**, 
>- we need $O(m^{3})$ *arithmetic operations* to **solve the sys­tems** $$p^{T}B = c_{B}^{T} \;\;\text{ and }\;\; B\,d = -A_{j}.$$
>- In addition, **computing the reduced costs** of all variables requires $O(mn)$ *arithmetic operations*, because we need to form the inner product of the vector $p$ with each one of the nonbasic columns $A_{j}$.
>- Thus, the **total computational effort** per iteration is $O(m^{3} + mn)$.

### Revised Implementation

>[!info]
>Let the *basis matrix* at the beginning of iteration be $$B = [A_{B(1)} \ldots A_{B(m)}].$$ 
>And let the *basis matrix* at the beginning of *next iteration* be $$\overline{B} = [A_{B(1)}\; \ldots \;A_{B(l-1)}\; A_{j}\;  A_{B(l+1)}\; \ldots \;A_{B(m)}].$$ 
>

>[!info]
>These two basis matrices have the *same columns* **except** that the $l$-th column $A_{B(l)}$ (the one that **exits the basis**) has been replaced by $A_{j}$.
>
>It is then reasonable to expect that $B^{-1}$ contains information that can be exploited in the computation of $\overline{B}^{-1}$.

>[!important] Definition
>Given a matrix, not necessarily square, the operation of *adding a constant multiple* of one row to *the same* or to *another row* is called an **elementary row operation**.

>[!info]
>**Multiplying the jth row** by $\beta$ and adding it to the $i$-th row (for $i\neq j$) is the same as **left-multiplying** by the matrix $$Q = I + D_{i,j},$$ where $D_{i,j}$ is a matrix with all entries equal to zero, except for the $(i,j)$-th entry which is equal to $\beta$. The determinant of such a matrix $Q$ is equal to $1$ and, therefore, $Q$ is *invertible*.
>
>Suppose now that we apply a **sequence of $K$ elementary row oper­ations** and that the $k$-th such operation corresponds to *left-multiplication* by a certain invertible matrix $Q_{k}$. Then, the sequence of these elementary row operations is the same as left-multiplication by the invertible matrix $$Q_{K} Q_{K-1} \ldots Q_{2}Q_{1}.$$

>[!info]
>Since $B^{-1}B= I$, thus $B^{-1}A_{B(i)} = e_{i}$. 
>
>Thus 
>$$
>B^{-1}\overline{B} = \left[ e_{1} \,{,}\ldots{,}\, e_{l-1},\,(-d_{B}),  \,e_{l+1} \,{,}\ldots{,}\,  e_{m} \right] 
>$$
>where $$-d_{B} = B^{-1}\,A_{j}.$$ and $d_{B} = (d_{B(1)} \,{,}\ldots{,}\,d_{B(l-1)},\, d_{B(l)}, \,d_{B(l+1)} \,{,}\ldots{,}\,d_{B(m)})$

>[!important]
>Consider the following **sequence** of **elementary row operations**. 
>- For each $i\neq l$, we **add** the $l$-th row **times** $$-\frac{d_{B(i)}}{d_{B(l)}}$$ to the $i$-th row. (Recall that $d_{B(l)} < 0$.) This *replaces* $d_{B(i)}$ by **zero**. 
>- We **divide** the $l$-th row by $-d_{B(l)}$. This *replaces* $-d_{B(l)}$ by **one**.
>  
>In words , we are **adding** to *each row* a **multiple** of the $l$-th row to **replace** the $l$-th column $-d_{B}$ by the $l$-th **unit vector** $e_{l}$.  

>[!info]
>This sequence of *ele­mentary row operations* is **equivalent** to left-multiplying $B^{-1}\overline{B}$ by a certain *invertible matrix* $Q$. We have
>$$
>QB^{-1}\overline{B} = I.
>$$
>This yields
>$$
>QB^{-1} = \overline{B}^{-1}.
>$$
>We conclude that all it takes to generate $\overline{B}^{-1}$, is to start with $B^{-1}$ and apply the *sequence* of **elementary row oper­ations** described above.

#### Revised Simplex Method

>[!important] Definition
>Consider the linear optimization problem in *standard form*
>$$
>\begin{align*}
>\min_{x}\; & \left\langle c ,  x\right\rangle\\
>\text{s.t.}\;& Ax = b\\
>\;&x \succeq 0\\
\end{align*}
>$$
>
>The **revised simplex method** for solving above problem is described as below:
>- *Initialize* at an arbitrary **basic feasible solution** $x$ and the inverse basis matrix $B^{-1}$
>- While optimality condition not met:
>	- Collect the following
>		- A set of **basis columns**  $$A_{B(1)} \,{,}\ldots{,}\,A_{B(m)}$$ and 
>		- the associated **basic feasible solution** $x$. Note that $x_{i} =0$ for all $i \not\in \{ B(1) \,{,}\ldots{,}\, B(m)\}$
>		- The **inverse basis matrix** $B^{-1}$ where $$B = [A_{B(1)} \ldots A_{B(m)}]$$
>	- Compute the **vector $p$ of simplex multipliers** associated with the **basis matrix** $B$ as  $$p^{T} = c_{B}^{T}\,B^{-1}$$
>	- Compute the **reduced costs** for all $j \not\in \{ B(1) \,{,}\ldots{,}\,B(m)\}$ $$\bar{c}_{j} = c_{j}  - \left\langle  p\,,\,A_{j} \right\rangle,$$ 
>	- If $\bar{c}_{j} \ge 0$ for all non-basic indices
>		- the current basic solution $x$ is **optimal**; 
>		- *Return* $x$ and the **optimal cost** $\left\langle  c\,,\,x    \right\rangle$
>	- Else:
>		- Find $j$ such that $\bar{c}_{j} < 0$
>		- Compute the $j$-th **basic direction** $$d_{B} = -B^{-1}A_{j}$$
>		- If **no** component in $d$ is **negative**, i.e. $$d_{B} \succeq 0$$
>			- *Return* with **optimal cost** $-\infty$; set $\theta^{*} = \infty$
>		- Else, i.e. there exists some component $i\in [m]$ in $d_{B}$ that is $d_{B(i)} <0$  *negative*
>			- Compute $$\theta^{*} = \min_{\{ i=1 \,{,}\ldots{,}\,m:\; d_{B(i)} < 0 \}}\; \left(-\frac{x_{B(i)}}{d_{B(i)}}\right)$$ Let $l$ be the index that attains the minimum $$\theta^{*} = -\frac{x_{B(l)}}{d_{B(l)}}$$
>			- Form a **new basis** by *replacing* $A_{B(l)}$ with $A_{j}$.
>			- Update a **new basic feasible solution** $y$ based on $x$, where the value of new basic variable are $$ y_{k} = \left\{\begin{array}{lc}\theta^{*} & k=j\\ x_{k} + \theta^{*}\;d_{k} & k \in \left\{ B(1) \,{,}\ldots{,}\, B(m) \right\}  \setminus \{ B(l) \} \\0 & \text{otherwise} \end{array} \right.$$
>			- Form a **new inverse matrix matrix** $\overline{B}^{-1}$ according to the following
>				- Collect a matrix $$\left[ B^{-1},\, (-d_{B})\right] \in \mathbb{R}^{m\times (m+1)} $$
>				- **Add** to each one of its rows a **multiple** of the $l$-th row to make the *last column* equal to the **unit vector** $e_{l}$.
>				- The *first $m$ columns* is equal to $\overline{B}^{-1}$

#### Complexity

>[!important]
>In **revised implementation**
>- since, only $O(m^2)$ entries are updated when updating $B^{-1}$ and $c_{B}^T\,B^{-1}$,  the **compu­tational requirements** *per iteration* are $O(m^2)$.
>- In addition, the **reduced cost** of each variable $x_{i}$ can be computed by forming the *inner product* $p^{T}A_{j}$, which requires $O(m)$ operations. In the worst case, the reduced cost of *every variable* is computed, for a *total of $O(mn)$ computations* per iteration.
>- Since $m \ll n$, the **worst-case computational effort** per iteration is $O(mn + m^2) = O(mn)$.
>- On the other hand, if we consider a **pivoting rule** that evaluates one reduced cost at a time, until a negative reduced cost is found, a typical iteration of the revised simplex method might *require a lot less work*. 
>- In the **best case**, if the **first** reduced cost computed is *negative*, and the corresponding variable is chosen to en­ter the basis , the total computational effort is only $O(m^2)$.

>[!important]
>Another important element in favor of the revised simplex method is that **memory requirements** are *reduced* from $O(mn)$ to $O(m^2)$.

|                         | **naive** implementation | **revised** implementation |
| ----------------------- | ------------------------ | -------------------------- |
| **memory**              | $O(mn)$                  | $O(m^2)$                   |
| **worst-case run-time** | $O(m^3 + mn)$            | $O(mn)$                    |
| **best-case run-time**  | $O(m^3)$                 | $O(m^2)$                   |

## Explanation

>[!quote]
>It should be clear from the statement of the algorithm that the vectors $B^{-1}A_{j}$ play a **key role**. If these vectors are available, the **reduced costs**, the **direction** of motion, and the **stepsize** $\theta^{*}$ are easily computed. Thus , the **main difference** between alternative implementations lies in **the way** that the vectors $B^{-1}A_{j}$ are **computed** and on the amount of related information that is carried from one iteration to the next.
>
>-- [[Introduction to Linear Optimization by Bertsimas]] pp 94



-----------
##  Recommended Notes and References

- [[Simplex Method for Linear Optimization]]
- [[Feasible Direction and Reduced Cost for Linear Optimization]]
- [[Optimality Condition for Linear Optimization]]


- [[Polyhedron and Polytope]]
- [[Generalized Simplex]]
- [[Linear Optimization Problem]]


- [[Introduction to Linear Optimization by Bertsimas]] pp 94 - 101