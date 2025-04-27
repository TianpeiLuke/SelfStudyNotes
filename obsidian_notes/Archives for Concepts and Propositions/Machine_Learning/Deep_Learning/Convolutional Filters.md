---
tags:
  - concept
  - machine_learning/models
  - deep_learning/discriminative_models
  - deep_learning/architecture
  - deep_learning/models
  - convolutional_filters
  - convolutional_neural_network
keywords:
  - convolutional_filter
  - translation_invariance
  - equivarience
topics:
  - deep_learning/network_block
  - deep_learning/algorithm
  - deep_learning/discriminative_models
name: Convolutional Filters
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Convolutional Filters

### Convolution Operation

 ![[Convolution Operation#^a2007d]]
- [[Convolution Operation]]

>[!important] Definition
>The **convolution** between $f$ and $K$ is given by $$s(t) = (f*K)(t) = \int f(x)\,K(t - x)\,dx$$
>- The first argument $f$ is called the **input** of convolution
>- The *second argument* $K$ is called the **kernel** of convolution. It is also called a **filter**.
>- The *output* is referred as the **feature map.**

- [[Reproducing Kernel of RKHS]]

### Digital Convolution

>[!important] Definition
>Let $I[j, k]$ be $(j,k)$ position of image and $K$ be a **filter** with values $K(l,m)$.
>
>The **feature map** $C$ has values given by 
>$$
>C[j, k] = \sum_{l}\sum_{m}I[j+l-1, k+m-1]\,K[l, m]
>$$
>- This feature map is the result of **convolution**, referred as $$C = I * K.$$
>- Strictly speaking, this is actually **cross-correlation operation.** In deep learning, the cross-correlation and convolution operations are not distinguished.

![[convolution_operation.png]]


>[!important] Definition
>The **two-dimensional convolution operation** between $I$ and $K$ is given by 
>$$
>C[j,k] = (I*K)[j,k] = \sum_{l}\sum_{m}\,I[l, m]\,K[j - l, k - m]
>$$
>or equivalently,
>$$
>C[j,k] = (K*I)[j,k] = \sum_{l}\sum_{m}\,I[j - l, k - m]\,K[l, m]
>$$

>[!info]
>For $K \in \mathbb{R}^{m_{k}\times m_{k}}$, the convolution is given by
>$$
>C[j,k] =  \sum_{l =0}^{m_{k}-1}\sum_{m= 0}^{m_{k}-1}I[j+l-1, k+m-1]\,K[l, m]
>$$

- Wikipedia [Multidimensional_discrete_convolution](https://en.wikipedia.org/wiki/Multidimensional_discrete_convolution)

>[!important] Definition
>In convolution layer, each unit output depends on a small patch neighborhood, called the **receptive field** of that unit.

![[convolution_filter.png]]

### Translation Equivariance

>[!quote]
> The units of the hidden layer form a **feature map** in which all the units *share the same weights*. Consequently if a *local patch* of an image produces a particular response in the unit connected to that patch, then the *same set* of pixel values at a different location will produce the *same response* in the corresponding **translated location** in the feature map. 
> - This is an example of **equivariance**. 
> 
>We see that the connections in this network are **sparse** in that most connections are absent. Also, the values of the weights are **shared** by *all the hidden units*, as indicated by the colours of the connections. This transformation is an example of a **convolution**.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 292

>[!quote]
>The **advantage** of a convolutional layer compared to using a linear layer is that the *weights of the kernel* are **shared** *across locations* in the input. Thus if a pattern in the input shifts locations, the corresponding output activation will also shift. This is called **shift equivariance**. 
> 
> In some cases, we want the output to be the same, no matter where the input pattern occurs; this is called **shift invariance**, and can be obtained by using a **pooling layer**, which computes the maximum or average value in each local patch of the input. (Note that pooling layers have no free (learnable) parameters.) Other forms of invariance can also be captured by neural networks (see e.g., [CW16; FWW21]).
>
>-- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 626


![[convolution_image.png]]

### Padding and Strided Convolutions

>[!important] Definition
>Given an image $I \in \mathbb{R}^{n\times m}$ and we convolve it with a kernel $K\in \mathbb{R}^{k\times k}$, the *dimensionality* of output *feature map* is given by 
>$$
> \left( n - k + 1 \right) \times \left( m - k + 1 \right)
>$$
>
>In order to obtain the feature map of *same dimensionality* of input, we use **padding technique** by adding additional zeros *around the outside*. 
>- If we pad with $p$ pixels,  then the output feature map has *dimensionality* $$\left( n + 2p - k + 1 \right) \times \left( m + 2p - k + 1 \right)$$
>- If there is *no padding*, so that $p = 0$, this is called a **valid convolution**.
>- When the value of $p$ is chosen such that the *output* array has *the same size* as the *input*, corresponding to $$p = \frac{k − 1}{2},$$ this is called a **same convolution**.
>- In computer vision, we usually choose $k$ as *odd number* so that the padding can be *symmetric* on both sides of image.



![[zero_padding.png]]

>[!important] Definition
>When we want to the *dimensionality* of feature map to be *significantly smaller* than the original image, we can achieve this by **strided convolutions**.
>- In **strided convolution**, instead of stepping the filter over the image *one pixel at a time*, it is moved in *larger steps* of size $s$, called the **stride**.
>- $$C[j, k] = \sum_{s}\sum_{l}\sum_{m}I[(j-1)\times s + l, (k-1)\times s +m, s]\,K[l, m, s]$$
>- If we use same stride horizontally and vertically, the *output feature map dimension* is $$ \left( \left\lfloor \frac{n + 2p - k}{s} \right\rfloor + 1 \right)   \times  \left( \left\lfloor  \frac{m + 2p - k}{s} \right\rfloor + 1 \right)$$

![[strided_convolutions.png]]

### Multi-dimensional Convolutions

>[!important] Definition
>Consider an image with $c$ *channels* $I\in \mathbb{R}^{n\times m\times c}$ which is described as a **tensor**. 
>
>We can introduce a **filter (kernel)** by a *tensor* $K \in \mathbb{R}^{k\times k\times c}$ which consists of $c$ channels, each representing a separate $k\times k$ **filter**
>
>The **feature map** between **multi-channel** input $I$ and kernel $K$ is given by the *sum of feature maps* of each channel
>$$
>C[j, k] = \sum_{s}\sum_{l}\sum_{m}I[j+l-1, k+m-1, s]\,K[l, m, s]
>$$
>- We may add a bias term to each feature map as $$\tilde{C}[j, k] = C[j, k] + \beta$$



![[multidim_convolution_layer.png]]


>[!important] Definition
>We can extend single feature maps to **multiple feature maps**.
>- We include $c_{out}$ *different filters*;
>- Each filter is of dimension $k\times k\times c$
>- Each filter corresponds to a *feature map*.
>- These feature maps are referred to as the **channels.**
>  
>Thus a **multi-dimensional convolution operation** between
>- an **image tensor**  $I\in \mathbb{R}^{n\times m\times c}$
>- a **filter tensor** i.e. $c_{out}$ *channels* of filters, $K \in \mathbb{R}^{k\times k\times c\times c_{out}}$ 
>
>is given by
>$$
>C[j, k, h] = \sum_{s}\sum_{l}\sum_{m}I[j+l-1, k+m-1, s]\,K[l, m, s, h], \quad h=1\,{,}\ldots{,}\,c_{out}
>$$
>or
>$$
>C \in \mathbb{R}^{n_{c} \times m_{c} \times c_{out}}
>$$
>where 
>$$
>n_{c} =  \left\lfloor \frac{n + 2p - k}{s} \right\rfloor + 1, \quad m_{c} = \left\lfloor  \frac{m + 2p - k}{s} \right\rfloor + 1 
>$$

^e74827

- [[Multilinear Function]]
- [[Tensor Product]]
- [[Tensor Field on Manifold]]

>[!info]
>For a *multi-dimensional convolution layer*, **each filter** $K[\cdot,\cdot,\cdot,h]$ is similar to a **hidden unit** in a feedforward network, which only detect one kind of feature.
>
>With a **filter tensor** of $c_{out}$ filters, we can simultaneously detect $c_{out}$ features.
>
>The total parameter size for each **filter tensor** $K \in \mathbb{R}^{k\times k\times c\times c_{out}}$  is $$(k^2\,c + 1)\,c_{out}$$

- [[Multi-Layer Perceptron and Feed-Forward Network]]

![[multidim_convolution_layer_mutichannel.png]]

>[!important] Definition
>One useful design concept is the **$1\times 1$ convolution** with $$K \in \mathbb{R}^{1\times 1\times c\times c_{out}}.$$
>- This allows us to change the *number of  channels* from $c$ to $c_{out}$  without changing the size of the feature maps $$I \in \mathbb{R}^{m\times n\times c}  \implies C = I*K \in \mathbb{R}^{m\times n\times c_{out}}$$

### Pooling

![[Pooling for Deep Learning#^f4bdf0]]

- [[Pooling for Deep Learning]]


## Explanation

### Motivations

>[!quote]
>One **motivation** for the introduction of convolutional networks is that for *image data*, which is the modality for which CNNs were designed, a standard fully connected architecture would **require vast numbers of parameters** due to the *high-dimensional nature of images*. To see this, consider a colour image with $103 \times 103$ pixels, each with three values corresponding to red, green, and blue intensities. If the first hidden layer of the network has, say, $1,000$ hidden units, then we already have $3 \times 109$ weights in the first layer. Furthermore, such a network would have to learn any **invariances** and **equivariances** by example, which would require huge data sets. By designing an architecture that incorporates our *inductive bias* about the *structure of images*, we can reduce the data set requirements dramatically and also improve generalization with respect to **symmetries in the image space**.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 290

- [[Equivariance of Estimator]]
- [[Invariance under Linear Transformation]]
- [[Inductive Bias in Machine Learning]]

>[!important]
>Convolution leverages **three important ideas** that can help improve a machine learning system: 
>
>- **Sparse Interactions** (also referred to as **sparse connectivity** or **sparse weights**): Instead of allowing every output unit interacts with every input unit, *Convolutional networks*, typically have *sparse interactions*. 
>	- This is accomplished by making the **kernel** *smaller* than the *input*. 
>	- This means that we store *fewer parameters*, which both reduces the *memory requirements* of the model and improves its statistical efficiency. 
>	- It also means that computing the output requires *fewer operations*. These improvements in efficiency are usually quite large. 
>	- If we limit the *number of connections* each output may have to $k$, then the *sparsely connected* approach requires only $k \times n$ parameters and $$O(m \times n) \to O(k \times n)$$ runtime.
>- **Parameter sharing**:  refers to using the *same parameter* for more than one function in a model. 
>	- In a *traditional neural net*, each element of the weight matrix is used *exactly once* when computing the output of a layer. 
>	- As a synonym for parameter sharing, one can say that a network has **tied weights**, because the value of the weight applied to *one input* is *tied* to the value of a *weight* applied elsewhere.
>	- In a *convolutional neural net*, each member of the **kernel** is used at *every position* of the input. 
>	- The parameter sharing used by the convolution operation means that rather than learning a *separate set of parameters* for *every location*, we **learn only one set**. 
>	- This does not affect the runtime of forward propagation—it is still $O(k \times n)$ —but it does further **reduce the storage requirements** of the model to $k$ parameters.
>- **Equivariant representations**. 
>	- To say a function is equivariant means that if the *input changes*, the *output changes in the same way*. 
>	- Specifically, a function $f(x)$ is *equivariant* to a function $g$ if $$f(g(x)) = g(f(x)).$$
>	- The **convolution** is *equivalent* to **translation (shift) operation.**
>	- Convolution is *not naturally equivariant* to some other transformations, such as **changes in the scale** or **rotation of an image**. 
>
>-- [[Deep Learning by Goodfellow]] pp 325

>[!quote]
>Comparing this convolutional structure with a standard fully connected network, we see several advantages: 
>- the connections are **sparse**, leading to far fewer weights even with large images, 
>- the **weight values** are **shared**, greatly reducing the number of independent parameters and consequently reducing the required size of the training set needed to learn those parameters, 
>- and the same network can be applied to images of **different sizes** without the need for retraining.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 293 - 294






-----------
##  Recommended Notes and References


- [[Convolutional Neural Network]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 625
- [[Deep Learning by Goodfellow]] pp 321
- [[Deep Learning Foundations and Concepts by Bishop]] pp 290
- [[Foundations of Computer Vision by Torralba]]  pp 335 - 342