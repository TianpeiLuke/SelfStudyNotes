---
tags:
  - concept
  - meta_learning
  - prototypical_network
keywords:
  - meta_learning
  - prototypical_network
topics:
  - machine_learning_paradigm
name: Prototypical Networks for Meta Learning
date of note: 2025-04-21
---

## Concept Definition

>[!important]
>**Name**: Prototypical Networks for Meta Learning

>[!important] Definition
>The *training algorithm* for **Prototypical Networks** can be described as below
>- *Require*: 
>	- *Task distribution* $p(\mathcal T)$; 
>	- *Encoder* $f_{\boldsymbol\phi}$; 
>	- Outer learning rate $\beta$; 
>	- Distance metric $d(\cdot,\cdot)$
>- While not converged
>	- **Sample episode** $\mathcal T \sim p(\mathcal T)$ 
>		- For $N$‑way, $K$‑shot, $Q$ queries per class
>			- **Support set** $S=\{(x_s^{(c,j)},y_s^{(c,j)}=c)\}_{c=1..N,\,j=1..K}$
>			- **Query set**   $Q=\{(x_q^{(c,m)},y_q^{(c,m)}=c)\}_{c=1..N,\,m=1..Q}$
>	- **Prototype construction**
>	- For $c=1\,{,}\ldots{,}\,N$
>		-  compute the **class prototype** $$\displaystyle \mathbf p_c \gets \frac{1}{K}\sum_{j=1}^{K} f_{\boldsymbol\phi}\!\bigl(x_s^{(c,j)}\bigr)$$
>	- $\mathcal L \gets 0$  initialise episodic loss
>	- For $\forall (x_q,y_q)\in Q$:
>		- generate *query embedding* $$\mathbf z \gets f_{\boldsymbol\phi}(x_q)$$
>		- *identify the class* to which the query belongs $$\displaystyle P_{\boldsymbol\phi}(y=c\mid x_q)\gets \frac{\exp[-\,d(\mathbf z,\mathbf p_c)]}{\sum_{c'=1}^{N}\exp[-\,d(\mathbf z,\mathbf p_{c'})]}$$
>		-  Update loss via *gradient descent* $$\mathcal L \gets \mathcal L -\log P_{\boldsymbol\phi}\!\bigl(y_q\mid x_q\bigr)$$
>	- **Meta‑update** $$\displaystyle \boldsymbol\phi \gets \boldsymbol\phi - \beta\,\nabla_{\!\boldsymbol\phi}\mathcal L$$
>- *Return*
>	- the trained encoder parameters $\boldsymbol\phi^\star$

>[!important] Definition
>The **inference algorithm** is described as
>- *Require*
>	- Trained encoder $f_{\boldsymbol\phi^\star}$; 
>	- support set $S$; 
>	- distance $d$
>- Compute **prototypes** $\mathbf p_c$ for each class $c$ as in training algorithm above
>- For $\forall\,$ query example $x_{q}$:
>	- Generate *query embedding*  $$\mathbf z \gets f_{\boldsymbol\phi^\star}(x_q)$$
>	- Predict class $$\displaystyle \hat{y} \gets \arg\min_{c} d(\mathbf z,\mathbf p_c)$$




### Episodic Few‑Shot Setting

>[!info]
>Each training  *episode* samples a few‑shot classification task
>$$
>\begin{align*}
> \mathcal T &= \bigl\{(x_s^{(c,j)},\;y_s^{(c,j)}\!=c)\bigr\}_{\substack{c=1,\dots,N\\ j=1,\dots,K}} \\
> &\;\cup\; \\
> &\; \bigl\{(x_q^{(c,m)},\;y_q^{(c,m)}\!=c)\bigr\}_{\substack{c=1,\dots,N\\ m=1,\dots,Q}},
> \end{align*}
>$$
> an **$N$-way, $K$-shot task** with **$Q$ query points** *per class*.

### Shared Encoder

>[!important]
>A learnable feature extractor
> $$f_{\boldsymbol\phi} : \mathcal X \!\to\! \mathbb R^{d}$$
> maps an input $x$ to an *embedding vector*
> $$\mathbf z \;=\; f_{\boldsymbol\phi}(x).$$

### Class Prototypes

>[!important] Definition
>For each class $c$ the **prototype** (*class representative*) is the mean of its $K$ *support embeddings*:
>$$\mathbf p_c = \frac{1}{K}\sum_{j=1}^{K}f_{\boldsymbol\phi}\bigl(x_s^{(c,j)}\bigr).$$

### Distance-based Classification

>[!important] 
>With a distance metric $$d(\mathbf z,\mathbf p),$$ the probability that query $x_q^{(c,m)}$ belongs to class $c$ is
>$$
>P_{\phi}\bigl(y=c \mid x_q\bigr) =  \frac{\exp\bigl[-\,d\bigl(f_{\boldsymbol\phi}(x_q),\,\mathbf{p}_c\bigr)\bigr]}{\sum_{c'=1}^{N}\exp\bigl[-\,d\bigl(f_{\boldsymbol\phi}(x_q),\,\mathbf{p}_{c'}\bigr)\bigr]}.
>$$

### Episodic Loss

>[!important] 
>*Cross‑entropy* over the query set of the episode:
> $$\mathcal L_{\mathcal T}(\boldsymbol\phi)\;=\;-\,\sum_{c=1}^{N}\sum_{m=1}^{Q}\log P_{\boldsymbol\phi}\!\bigl(y_q^{(c,m)}\!=c \mid x_q^{(c,m)}\bigr).$$

- [[Cross-Entropy Loss Function]]

### Meta‑Update

>[!important]
>Update encoder parameters with SGD/Adam using the outer learning rate $\beta$:
> 
> $$\boldsymbol\phi\;\leftarrow\;\boldsymbol\phi- \beta\, \nabla_{\!\boldsymbol\phi}\, \mathcal L_{\mathcal T}(\boldsymbol\phi).$$
> 

- [[Stochastic Gradient Descent Algorithm]]
- [[Adam Algorithm]]


## Explanation

>[!quote]
>**Intuition:** meta‑training shapes the embedding so that each class forms a _tight, convex cluster_; the cluster mean becomes a _sufficient statistic_ for classifying new points with minimal data.


### Key properties

|Trait|Explanation|
|---|---|
|**Model‑agnostic encoder**|Any differentiable backbone works.|
|**Fast at test time**|Only averaging + distance; no fine‑tuning loop.|
|**Distance metric matters**|Euclidean in feature space often outperforms cosine when the encoder is trained accordingly.|
|**Extensible**|Works with variable N,KN, KN,K; supports semi‑supervised, domain‑a|



-----------
##  Recommended Notes and References


- [[Meta Learning]]
- [[Model-Agnostic Meta Learning]]