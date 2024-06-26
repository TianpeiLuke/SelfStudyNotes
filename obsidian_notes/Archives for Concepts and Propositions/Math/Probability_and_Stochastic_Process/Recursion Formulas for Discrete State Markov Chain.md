---
tags:
  - concept
  - math/stochastic_process
keywords:
  - Markov_Chain
  - first_hitting_time
  - number_of_returns
  - finite_return_probability
  - kernel_recursion
  - hitting_time_recursion
topics:
  - stochastic_process
name: Formulas for Computation in Discrete State Markov Chain
date of note: 2024-06-22
---

## Concept Definition

>[!important]
>**Name**: Formulas for Computation in Discrete State Markov Chain


![[Stopping Time of Markov Chain#^61fb49]]

![[Number of Passages and Probability of Finite Return#^830eef]]

![[Number of Passages and Probability of Finite Return#^3ca5c2]]


>[!important] Definition
>Assume in this note $(X_{n})$ is a **discrete-time** Markov chain with **discrete state** space $\mathcal{X} := \{ 0, 1, \,{,}\ldots{,}\, \}$
>
>- Denote  $$f_{x,y} \equiv P(\tau_{y} < \infty | X_{0} = x)\, \quad \forall x, y \in \mathcal{X}$$ as **the probability of ever visiting** state $y$ starting at state $x$
>- Denote  $$f_{x,y}^{m} \equiv P(\tau_{y} = m | X_{0} = x)\, \quad \forall x, y \in \mathcal{X}$$ as **the probability of  visiting** state $y$ **at time $m$**  starting at state $x$
>- Denote $$\eta_{x} \equiv \sum_{n=1}^{\infty}\mathbb{1}\left(X_{n} = x\right) \quad \forall x\in \mathcal{X}$$ as the **total number of passages** of $(X_{n})$ at state $x$ 

- [[Number of Passages and Probability of Finite Return]]
- [[Stopping Time of Markov Chain]]
- [[Markov Chain and Markov Process]]

### Kernel Recursion Formula

>[!important] Kernel Recursion Formula
>Let $K$ be the transition kernel of Markov chain,.
>
>For any two states $x, y \in \mathcal{X}$
>$$
>\begin{align}
> K^{m}(x, y)&= \sum_{n=1}^{m} P(\tau_{y} = n | X_{0} = x)K^{m-n}(y, y)\\
> &:= \sum_{n=1}^{m}f_{x,y}^{n}\;\,K^{m-n}(y, y). \nonumber 
> \end{align}
>$$
>
>That is, we *categorize* **all possible $m$-step path** from $x\rightarrow y$ according to the **first time** *the path visiting* $y$. 
>
>This is called the **First-Step analysis.**
>
>This is also a **greedy algorithm**.

- [[Dynamic Programming for Optimal Stopping]]

### Stopping Time Recursion Formula

>[!important] Stopping Time Recursion Formula
> **The probability of  visiting** state $y$ **at time $m$**  starting at state $x$ can be computed recursively via
>$$
>\begin{align}
> f_{x,y}^{m} &:= P(\tau_{y} = m | X_{0} = x)\\ \\
>&= \sum_{z \neq i}\,P(\tau_{y} = m - 1 | X_{0} = z)\,K(x, z)  \\
> &:= \sum_{z \neq i}\,f_{z,y}^{m-1}\,K(x, z).\nonumber
> \end{align}
>$$  
>
>This formula **break down** **the $m$-step path** from $x\rightarrow y$ into **two parts**: 
>- a path from $x\rightarrow z$ and 
>- a **$(m-1)$-step path** from intermediate state $z\rightarrow y$ 
>  
>This is also the **First-Step analysis**.

>[!info]
>This probability is used to identify if the state is **recurrent**.

![[Classification of States of Markov Chain#^8a85fa]]

- [[Classification of States of Markov Chain]]


### Mean Hitting Time Formula




- [[Resolvent associated with Transition Kernel]]

###  Total Number of Passages 

>[!important] Recursion for Total Number of Passages
>Note that 
>$$
>\begin{align}
> P(\eta_{y} \ge 1 |\, X_{0} = x) &= P(\tau_{y} < \infty | X_{0} = x) = f_{x,y}  \\
> \end{align}
>$$
> 
>Thus from **Stopping Time Recursion formula** above, the probability of **total number of passage** $y$ greater than $m$ times can be decomposed into two parts
>$$
>\begin{align}
> P(\eta_{y} \ge m |\, X_{0} = x) &= P(\eta_{y} \ge 1 |\, X_{0} = x)\;P^{m-1}(\eta_{y} \ge 1 |\, X_{0} = y) \\
> &=f_{x,y}\,\; f^{m-1}_{y,y}
> \end{align}
>$$  
>This is because in order to visit $y$ **at least $m$ times**, we need to 
>- **visit $y$ first time** and 
>- stating from $y$ **recurrently visit** $y$ **$(m-1)$ times**.

>[!important] 
>The *random variable* $\eta_{x}$ follows a **geometric distribution** with **mean** $$\mu := \mathbb{E}_{ p }\left[  \eta_{x} | X_{0} = x \right] = \frac{1}{1- f_{x,x}} \equiv \frac{1}{1- \mathcal{P}\left(\tau_{x} < \infty | X_{0}= x\right)}.$$
>
>And the **probability mass function**
>$$
> \begin{align}
> P(\eta_{x} = m |\, X_{0} = x) &= (1- f_{x,x})\;f^{m-1}_{x,x} 
> \end{align}
>$$ 


>[!info]
>The mean of this random variable is used to identify if the state is **recurrent**

![[Classification of States of Markov Chain#^4e0184]]


- [[Classification of States of Markov Chain]]

>[!info]
>This probability is used to identify if the state is **Harris recurrent**

![[Harris Recurrent Set and Harris Recurrent Markov Chain#^f40444]]

- [[Harris Recurrent Set and Harris Recurrent Markov Chain]]

### Expected Number of Passages

>[!important]
>Given kernel $K$, the **expected number of passages** of $(X_{n})$ *at state $y$* starting from state $x$ is computed via
>$$
>\begin{align}
> \mathbb{E}\left[  \eta_{y} | X_{0} = x \right] &= \mathbb{E}\left[  \sum_{n=0}^{\infty}\mathbb{1}\left\{ X_{n} = y \right\}  \;\Big|\; X_{0} = x \right]\\
> &= \sum_{n=0}^{\infty}\mathbb{E}\left[\mathbb{1}\left\{ X_{n} = y \right\}  \;\Big|\; X_{0} = x \right]  \\
> &=\sum_{n=0}^{\infty}K^{n}(x, y)
> \end{align}
>$$ 


## Explanation











-----------
##  Recommended Notes and References

- [[Number of Passages and Probability of Finite Return]]
- [[Stopping Time of Markov Chain]]
- [[Markov Transition Kernel and Transition Function]]
- [[Markov Chain and Markov Process]]