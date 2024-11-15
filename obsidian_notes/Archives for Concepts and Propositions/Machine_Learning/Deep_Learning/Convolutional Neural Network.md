---
tags:
  - concept
  - machine_learning/models
  - deep_learning/discriminative_models
  - deep_learning/architecture
keywords:
  - convolutional_neural_network
  - convolutional_filter
topics:
  - deep_learning/network_block
  - deep_learning/models
  - deep_learning/discriminative_models
name: Convolutional Neural Network
date of note: 2024-05-12
---

## Concept Definition

>[!important]
>**Name**: Convolutional Neural Network

### Convolutions

![[Convolutional Filters#^e74827]]

- [[Convolutional Filters]]

### Multi-Layer Convolution Neural Network

>[!important] Definition
>The **convolutional neural network (CNN)** usually consists of a *stack of blocks*, each containing
>- several **convolutional layers**, with *activations* which are *interspersed* by
>- a **max pooling layer** taking input from feature maps of convolutional layer
>
>In **CNN**, each unit in a feature map in one layer only takes **local information** from a **receptive field** of previous layer. $$Z^{(l+1)} = \text{max-pool}\left( \sigma\left(Z^{(l)} * K^{(l)}\right) \right)$$
>
>For *classification task*, CNN would add a subnetwork on the top, which consists of 
>- a stack of **feedforward layers (MLP)** and
>- a **softmax activation function** as the final activation before the loss functions.
>- This subnetwork is for a simple nonlinear classification model. $$P = \text{softmax}\left( \text{MLP}\left( Z^{(L)} \right) \right)$$

- [[Convolutional Filters]]
- [[Pooling for Deep Learning]]
- [[Multi-Layer Perceptron and Feed-Forward Network]]
- [[Activation Functions for Deep Learning]]
- [[Softmax Function and Log-Sum-Exp Function]]

![[pooling_cnn.png]]





## Explanation

>[!quote]
>A **key property** that we built into the convolutional framework is that of **locality**, in which a given unit in a feature map takes information only from a small patch, the **receptive field**, in the previous layer. When we construct a deep neural network in which each layer is convolutional then the effective receptive field of a unit in later layers in the network becomes much larger than those in earlier layers.
>
>-- [[Deep Learning Foundations and Concepts by Bishop]] pp 298

- [[Equivariance of Estimator]]

## Examples of CNN

>[!example]
>The **Alexnet**
>
>-- Krizhevsky, A., Sutskever, I., & Hinton, G. E. (2012). Imagenet classification with deep convolutional neural networks. _Advances in neural information processing systems_, _25_.



>[!example]
>The **VGG-16** model from *Visual Geometry Group* is a simple CNN model with *$16$ layers*.
>- It takes an input image having $224 \times 224$ pixels and *three colour channels*, followed by sets of **convolutional layers** interspersed with **down-sampling**.
>- All **convolutional layers** have *filters* of size $3 \times 3$ with a *stride* of 1, same *padding*, and a **ReLU activation** function, 
>- whereas the **max-pooling** operations all use *stride* $2$ and *filter size* $2 \times 2$ thereby **down-sampling** the number of units by a factor of $4$.
>- The first learnable layer is a convolutional layer in which each unit takes input from a $3 \times 3 \times 3$ ‘cube’ from the stack of input channels and so has $28$ parameters including the bias. These parameters are shared across all units in the feature map for that channel.
>- There are **$64$ such feature channels** in the *first layer*, giving an output tensor of size $224 \times 224 \times 64$.
>- The 2nd layer has $64$ channels, followed by a max-pooling of size $112 \times 112$
>- The 3rd, 4th layer has $128$ channels, with dimension  $112 \times 112$.
>- The *increase in channels* is to account for *downsampling*.
>- Again, this is followed by a *max-pooling* operation to give a feature map size of $56 \times 56$.
>- The next $3$ layers are convolutional, each with *$256$ channels*. 
>- This is followed by a *max-pooling* to give feature maps of size $28 \times 28$
>- They are followed by $3$ more convolutional layers, each *having $512$ channels*.
>- Followed by another *max-pooling* to bring down the feature maps to $7 \times 7$
>- Finally, we have $3$ layers of *fully connected layers*
>- The final *max-pooling layer* has *$512$ channels*, each of size $7 \times 7$, with $25,088$ units in total.
>- a third fully connected layer with $1000$ units so that the network can be applied to a **classification problem involving $1,000$ classes**. 
>- All the learnable layers in the network have nonlinear **ReLU activation** functions, except for the output layer, which has a softmax activation function.
>- In total there are roughly **$138$ million** independently learnable parameters in VGG-16, the **majority** of which (nearly **$103$ million**) are in the first fully connected layer, whereas most of the connections are in the first convolutional layer.  
>  
>-- Karen Simonyan, Andrew Zisserman, Very Deep Convolutional Networks for Large-Scale Image Recognition. *ICLR 2015*  

![[cnn_example.png]]


## Variants

### Encoder-Decoder Architecture

- [[U-Net as Convolutional Autoencoder with Skip Connections]]
- [[Auto-Encoder and Stochastic Auto-Encoder]]

### Causal CNN

- [[Causal Convolutional Neural Network]]




-----------
##  Recommended Notes and References



- [[Artificial Neural Network and Deep Learning]]

- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 634
- [[Deep Learning by Goodfellow]] pp 321
- [[Deep Learning Foundations and Concepts by Bishop]] pp 287
- [[Foundations of Computer Vision by Torralba]] pp 335 - 354
