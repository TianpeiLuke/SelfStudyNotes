---
tags:
  - concept
  - machine_learning/models
  - machine_learning/boosting
  - machine_learning/ensemble_methods
keywords:
  - gradient_boost
  - tree_based_classifier
topics:
  - boosting
  - machine_learning_algorithm
name: Gradient Boosting Trees
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Gradient Boosting Trees

![[Gradient Boosting Algorithm#^dad77c]]

- [[Decision Tree Model for Classification and Regression]]
- [[Forward Stagewise Additive Modeling]]


>[!important]
>Consider the problem of estimation of an **ensemble of tree-based models**
>$$
>f(x) = \sum_{t=1}^{T}\beta_{t}\,\mathcal{T}_{t}(x; \gamma_{t})
>$$
>where
>- $\beta_{t}, t=1 \,{,}\ldots{,}\,T$ are the *expansion coefficients*, and 
>- $\mathcal{T}_{t}(x; \gamma_{t}) \in \mathcal{Y}$ is a *tree-based model*. $$\mathcal{T}_{t}(x; \gamma_{t}) := \sum_{s=1}^{k_{t}}\gamma_{t,s}\,\mathbb{1}\left\{ x \in R_{s}^{(t)} \right\} $$
>- Define the *regularization* for *complexity* of tree based on number of terminate nodes  $$\Omega(\mathcal{T}_{t}) := k_{t} := \#\left\{R_{1}^{(t)} \,{,}\ldots{,}\, R_{k_{t}}^{(t)} \right\} $$
>
>The goal is to *minimize* the **regularized loss function** given $\mathcal{D} := \left\{ (x_{i}, y_{i}) \right\}_{i=1}^{n}$
>$$
> \begin{align*}
> L(f) &:= \sum_{i=1}^{n}L\left( y_i, f(x_{i})\right) + \lambda  \sum_{t=1}^{T}\Omega(\mathcal{T}_{t}) + \frac{\alpha}{2} \sum_{t=1}^{T}\lVert \gamma_{t} \rVert_{2}^2 \\
> &= \sum_{i=1}^{n}L\left(y_{i}\,,\,\sum_{t=1}^{T}\beta_{t}\,\mathcal{T}_{t}(x_{i}; \gamma_{t})  \right) + \lambda  \sum_{t=1}^{T}\Omega(\mathcal{T}_{t}) + \frac{\alpha}{2} \sum_{t=1}^{T}\lVert \gamma_{t} \rVert_{2}^2
> \end{align*}
>$$

- [[Regularized Loss Minimization]]
- [[Decision Tree Model for Classification and Regression#Tree Pruning]]

### Taylor Expansion Approximation of Conditional Loss

>[!important]
>Define **stagewise conditional loss function** at time $T$ given the *ensemble from previous iteration*
>$$
> \begin{align*}
> &L_{T}(f_{T}\;|\;f^{(T-1)}) \\[6pt]
> &:= L(f\;|\;f^{(T-1)}) \\[6pt]
> &:= \sum_{i=1}^{n}L\left(y_{i}\,,\, \mathcal{T}_{T}(x_{i}; \gamma_{T}) + \sum_{t=1}^{T-1}\mathcal{T}_{t}(x_{i}; \gamma_{t}) \;|\; f^{(T-1)} \right) + \lambda  \sum_{t=1}^{T-1}\Omega(\mathcal{T}_{t}) + \frac{\alpha}{2} \sum_{t=1}^{T-1}\lVert \gamma_{t} \rVert_{2}^2 \\[6pt]
> &= \sum_{i=1}^{n}L\left(y_{i}\,,\, \mathcal{T}_{T}(x_{i}; \gamma_{T}) + f^{(T-1)}(x_{i}) \;|\; f^{(T-1)} \right) + \lambda  \sum_{t=1}^{T-1}\Omega(\mathcal{T}_{t}) + \frac{\alpha}{2} \sum_{t=1}^{T-1}\lVert \gamma_{t} \rVert_{2}^2 
> \end{align*}
>$$
>where $f_{T} = \mathcal{T}_{T}$ and the ensemble from previous iteration is given by $$f^{(T-1)} := \sum_{t=1}^{T-1}\mathcal{T}_{t}(\cdot; \gamma_{t}).$$
>- Assuming $\beta_{t} = 1$ for all $t$.

>[!info] Definition
>In **gradient boosting**, we *approximate* the stagewise conditional loss via its *second-order Taylor expansion* (in functional form)
>$$
>\begin{align}
> &L_{T}(f_{T} | f^{(T-1)})  \\[5pt]
>&\approx  L_{T}(f^{(T-1)}) + \left( \nabla L(f^{(T-1)}) \right)^{T}\,\Delta f + \frac{1}{2} \Delta f^{T} H_{L}|_{f^{(T-1)}} \Delta f \nonumber\\[5pt]
> &=  \sum_{i=1}^{n}L\left( y_i, f^{(T-1)}(x_{i}) \right) + \sum_{i=1}^{n}g_{i,T} f_{T}(x_{i}) + \frac{1}{2}\sum_{i}h_{i,T} f_{T}^2(x_{i}) \nonumber\\[5pt]
> &= const. +  \sum_{i=1}^{n}g_{i,T} f_{T}(x_{i}) + \frac{1}{2}\sum_{i}h_{i,T} f_{T}^2(x_{i})  \\[5pt]
> &= const. + \frac{1}{2} \sum_{i=1}^{n}h_{i,T}\left( f_{T}(x_{i}) + \frac{g_{i,T}}{h_{i,T}} \right)^{2} 
> \end{align} 
>$$
>where
>- $$\Delta f := f_{T}$$
>- And the *gradient* and *the diagonal part of Hessian matrix* is give by $$\begin{align*} g_{i,k} &:= \left[ \frac{\partial L(y_i, f(x_{i}))}{\partial f(x_{i})} \right]_{f=f^{k-1}(x_{i})} \\[5pt] h_{i,k} &=  \left[ \frac{\partial^2 L(y_i, f(x_{i}))}{\partial^{2} f(x_{i})} \right]_{f=f^{k-1}(x_{i})} \end{align*}$$ thus $$\nabla L(f^{(T-1)})  = (g_{1,T} \,{,}\ldots{,}\,g_{n,T})^{T}$$ and $$\text{vec}(\text{diag}(H_{L}|_{f^{(T-1)}})) := (h_{1,T} \,{,}\ldots{,}\,h_{n,T})^{T}.$$

>[!important] Definition
>The objective function for **gradient boost tree** at iteration $T$ is approximated by a **weighted regression loss**
>$$
>L_{T}(f_{T} | f^{(T-1)}) \approx \frac{1}{2} \sum_{i=1}^{n}h_{i,T}\left( f_{T}(x_{i}) + \frac{g_{i,T}}{h_{i,T}} \right)^{2} 
>$$  
>where 
>- the *weight* is determined by the *diagonal term of Hessian* of loss function;
>- the *response* is given by the *Newton's like update* $$r_{i} := [H_{T}^{-1}g_{T}]_{i} \approx \frac{g_{i,T}}{h_{i,T}} := [\text{diag}(H_{T})^{-1}g_{T}]_{i}$$ This term is sometimes called **influence function** in *active learning.*

>[!info]
>Note $$f_{T}(x) := \mathcal{T}_{T}(x) := \sum_{s=1}^{k_{T}}\gamma_{T,s}\,\mathbb{1}\left\{ x \in R_{s}^{(t)} \right\} $$ 
> so the loss function becomes
>$$
>\begin{align*}
>&L_{T}(f_{T} | f^{(T-1)})  \\[5pt]
>&\approx \sum_{s=1}^{k_{T}}\sum_{i:\,x_{i} \in R_{s}^{(t)}}\left( g_{i,T} \,\gamma_{T,s} + \frac{1}{2}h_{i,T}\,\gamma_{T,s}^2 \right) + \frac{1}{2}\alpha\, \sum_{s=1}^{k_{T}}\sum_{i:\,x_{i} \in R_{s}^{(t)}}\gamma_{T,s}^2 + \lambda |\mathcal{T}_{T}| \\[5pt]
>&= \sum_{s=1}^{k_{T}}\sum_{i:\,x_{i} \in R_{s}^{(t)}}\left(   g_{i,T} \,\gamma_{T,s} + \frac{1}{2}(h_{i,T} + \alpha)\,\gamma_{T,s}^2 \right) + \lambda k_{T}
>\end{align*}
>$$
>
>For fixed tree-partition $R_{s}$, we can find the corresponding *optimal estimate of response* $\gamma_{T,s}$ as
>$$
>\begin{align*}
>\gamma_{T,s}^{*} &= \arg\min_{\gamma_{s,T}} \sum_{i: x_{i} \in R_{s}}\left(   g_{i,T} \,\gamma_{T,s} + \frac{1}{2}(h_{i,T} + \alpha)\,\gamma_{T,s}^2 \right) \\[5pt]
>&= \arg\min_{\gamma_{s,T}} \left\{ \left(\sum_{i: x_{i} \in R_{s}}\,g_{i,T}\right) \gamma_{T,s} + \frac{1}{2}\left(\sum_{i: x_{i} \in R_{s}}\,(h_{i,T} + \alpha)  \right) \gamma_{T,s}^2 \right\} \\[5pt]
>&= - \frac{\sum_{i: x_{i} \in R_{s}}\,g_{i,T}}{\sum_{i: x_{i} \in R_{s}}\,(h_{i,T} + \alpha)}
>\end{align*}
>$$


- [[Taylor Series for Local Polynomial Approximation of Smooth Function]]
- [[Newton Method]]

>[!important] Definition
>The **optimal estimate** of parameter for each node $R_{s}$ is given by $$\gamma_{T,s}^{*} = - \frac{\sum_{i: x_{i} \in R_{s}}\,g_{i,T}}{\sum_{i: x_{i} \in R_{s}}\,(h_{i,T} + \alpha)}.$$
>and the corresponding **minimal loss** is 
>$$
>L_{T}(R_{s}) := L^{*}_{T}(f_{T} | f^{(T-1)}) = -\frac{1}{2}\sum_{s=1}^{k_{T}}\,\frac{\left[ \sum_{i: x_{i} \in R_{s}}\,g_{i,T} \right]^2 }{\sum_{i: x_{i} \in R_{s}}\,(h_{i,T} + \alpha)} + \lambda\,k_{T}
>$$

### Impurity Measure for Tree Splitting

>[!important] Definition
>Given a **split** with *threshold* $\theta^{(T)}$, we have 
>$$
>R_{s} := R_{s,-}(\theta^{(T)}) \cup R_{s,+}(\theta^{(T)})
>$$
>
>Define the **impurity measure** for *tree split* as the **difference of minimal loss**
>$$
>\begin{align}
>L(\theta^{T}; R_{s}) &:= L_{T}(R_{s}) - \left[ L_{T}(R_{s,-}(\theta^{T})) +   L_{T}(R_{s,+}(\theta^{T})) \right] \\[5pt]
>&= \frac{1}{2}\left[ \frac{\left( \sum_{i: \, x_{i} \in R_{s,-}(\theta^{(T)})}g_{i,T} \right)^2}{\sum_{i: \, x_{i} \in R_{s,-}(\theta^{(T)})}(h_{i,T}+\alpha)}  + \frac{\left( \sum_{i: \, x_{i} \in R_{s,+}(\theta^{(T)})}g_{i,T} \right)^2}{\sum_{i: \, x_{i} \in R_{s,+}(\theta^{(T)})}(h_{i,T}+\alpha)} - \frac{\left( \sum_{i: \, x_{i} \in R_{s}(\theta^{(T)})}g_{i,T} \right)^2}{\sum_{i: \, x_{i} \in R_{s}(\theta^{(T)})}(h_{i,T}+\alpha)} \right]  - \gamma k_{T}. 
>\end{align} 
>$$
>
>We can choose a split candidate that *maximized *the improvement of impurity of split. 

- [[Decision Tree Model for Classification and Regression#Classification Tree]]

### Split Finding Algorithm 

>[!info]
>One of the key problems in tree learning is to find the best split as indicated in $L(\theta^{T}; R_{s})$. 
>
>There are *two ways* to find it: 
>- the **exact greedy search**: 
>	- In exact greedy search, one **enumerates** *all possible split* for all continous features. 
>	- In order to do so efficiently, the algorithm must first **sort** the data according to *feature values* and 
>	- **visit** the data in *sorted order* to **accumulate** the *gradient statistics* for the structure score in $L(\theta^{T}; R_{s})$. 
>	- The **drawbacks** for exact greedy search is that it needs to *fit all data* into the memory. It is not efficient for distributed computing as well. 

>[!important] Definition
>The **exact greedy split finding** algorithm is described as below:
>- *Require*: the instance set of current node $$I := \left\{i: x_{i} \in R_{s} \right\}$$
>- *Require*: the feature dimension $d$
>- Set gain $gain = 0$
>- **Accumulate** *gradient values* and *Hessian values* $$G = \sum_{i\in I}g_{i}, \quad H = \sum_{i\in I}h_{i}$$
>- For $j=1\,{,}\ldots{,}\,d$:
>	- Initialize $$G_{L} \leftarrow 0, \quad H_{L} \leftarrow 0$$
>	- For $i$ in **sorted**$(I, by=x_{i}^{j})$:
>		- Update **left-partition minimum loss**  $$G_{L} \leftarrow G_{L} + g_{i}, \quad H_{L} \leftarrow H_{L} + h_{i}$$
>		- Update **right-partition minimum loss**  $$G_{R} \leftarrow G -  G_{L}, \quad H_{R} \leftarrow H - H_{L}$$
>		- Update **impurity score** $$\text{score } \leftarrow \max\left\{  \text{score }, \frac{G_{L}^2}{H_{L} + \alpha} + \frac{G_{R}^2}{H_{R} + \alpha} - \frac{G^2}{H + \alpha} \right\}  $$
>- *Return*: **split** $x_{i}^{j}$ by choosing the **maximum score.**


>[!info]
>In order to support these two settings, the **approximate greedy search** is proposed. See below for descriptions of the algorithms.
>- The approximate greedy search first propose *a set of candidate splitting points* based on the **percentiles** of *feature distribution*. 
>- The algorithm then 
>	- maps the *continuous features* into the **buckets** defined by these splitting point, 
>	- **aggregates statistics** and 
>	- find the *optimal solution* based on the aggregated statistics. 
>- There are two **variants**: **global approximate** or **local approximate**. 
>	- The *global approximate* proposes all candidates **at the initial step** of **tree construction** and uses the **same proposal** for split finding for *all levels below*. 
>	- The *local approximate* **re-proposes** candidates **after each split**. 
>	- The global method requires *less proposal steps* than the local method. 
>	- However, usually *more candidate points* are needed for the global proposal because candidates are not refined after each split. 
>	- The local proposal *refines the candidates after splits*, and can potentially be more appropriate for deeper trees. [[XGBoost and LightGBM]]

>[!important] Definition
>The **approximate greedy search** for **tree spliting** is described as follows
>- *Require*: the instance set of current node $$I := \left\{i: x_{i} \in R_{s} \right\}$$
>- *Require*: the feature dimension $d$
>- For $j=1\,{,}\ldots{,}\,d$
>	- Propose **candidate splits** $$S_{j} := \left\{ s_{j,1} \,{,}\ldots{,}\,s_{j,l} \right\}$$ by **percentiles** on feature $x^{j}$
>		- The proposal can be done **per tree (global)**, or **per split (local)**
>- For $j=1\,{,}\ldots{,}\,d$
>	- Update gradient in each dimension for each **bucket** over *candidate split* $$G_{j,v} = \sum_{i}\mathbb{1}\left\{  x_{i}^{j} \in [s_{j,v-1}, s_{j,v}] \right\}\,g_{i}  $$
>	- Update Hessian in each dimension for each **bucket** over *candidate split* $$H_{j,v} = \sum_{i}\mathbb{1}\left\{  x_{i}^{j} \in [s_{j,v-1}, s_{j,v}] \right\}\,h_{i}  $$
>- Call the **exact greedy split finding** to find *max score* only among **proposed splits.**
>	- For $j=1\,{,}\ldots{,}\,d$
>		- For $v=1\,{,}\ldots{,}\,l$
>			- Compute the **impurity score** based on $G_{j,v}$ and $H_{j,v}$.
>- *Return*: Find the **split** for some $j$ and bucket $v$ based on the maximum score. 

- [[XGBoost and LightGBM]]



## Explanation

>[!info]
>Gradient boost methods can be seen as searching for **gradient descent in functional space** $\mathcal{F}$, since the the optimal solution for a new model $f_{T}$  should fit the **negative gradient values** of the ensemble $$-g = -\nabla L_{T}(f).$$ 
>
>- For instance, when the loss function is squared loss, one fits the tree $\mathcal{T}$ according to the  **residual** of the ensemble in *previous iterations* via *least square*. 
>- Both gradient boost methods and the **recursive greedy algorithm** to fit the tree are appoximation procedures. 
>
>We can see that, similar to AdaBoost, the gradient boost method also reweights samples. 
>- Adaboost use the mis-classification error to upweight/downweight samples, 
>- Gradient boosting uses the **curvature of error surface** to *upweight/downweight* samples.  
>	- It **downweight** samples located in **flat surface** 
>	- and **upweight** the samples reside in **steep curvature** of the *error surface*, which would lead to significant change in error. 

- [[Gradient Boosting Algorithm]]




## Bagging and Random Forest

- [[Bagging and Model Averaging]]

- [[Random Forest Algorithm]]



-----------
##  Recommended Notes and References

- [[Gradient Boosting Algorithm]]
- [[chenXGBoostScalableTree2016]]
- [[keLightGBMHighlyEfficient2017]]

- [What makes LightGBM lightning fast?](https://towardsdatascience.com/what-makes-lightgbm-lightning-fast-a27cf0d9785e)

- [[Boosting Foundations and Algorithms by Schapire]]
- [[Elements of Statistical Learning by Hastie]]
- [[Understanding Machine Learning by Shalev-Shwartz]]
- [[Elements of Information Theory by Cover]]