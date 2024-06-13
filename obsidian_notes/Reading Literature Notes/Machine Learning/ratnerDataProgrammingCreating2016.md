---
tags:
  - "#paper"
  - programmatic_weak_supervision
aliases:
  - ratnerDataProgrammingCreating2016
year: 2016
name: "Data Programming: Creating Large Training Sets, Quickly"
authors: Alexander J Ratner, Christopher M De Sa, Sen Wu, Daniel Selsam, Christopher Ré
publication: Advances in Neural Information Processing Systems
type: conferencePaper
DOI: ""
date of note: 2024-03-06
---
# Descriptions
## Data Programming: Creating Large Training Sets, Quickly 
> [!info] 
> - **Abstract:** Large labeled training sets are the critical building blocks of supervised learning methods and are key enablers of deep learning techniques. For some applications, creating labeled training sets is the most time-consuming and expensive part of applying machine learning. We therefore propose a paradigm for the programmatic creation of training sets called data programming in which users provide a set of labeling functions, which are programs that heuristically label subsets of the data, but that are noisy and may conflict. By viewing these labeling functions as implicitly describing a generative model for this noise, we show that we can recover the parameters of this model to "denoise" the generated training set, and establish theoretically that we can recover the parameters of these generative models in a handful of settings. We then show how to modify a discriminative loss function to make it noise-aware, and demonstrate our method over a range of discriminative models including logistic regression and LSTMs. Experimentally, on the 2014 TAC-KBP Slot Filling challenge, we show that data programming would have led to a new winning score, and also show that applying data programming to an LSTM model leads to a TAC-KBP score almost 6 F1 points over a state-of-the-art LSTM baseline (and into second place in the competition). Additionally, in initial user studies we observed that data programming may be an easier way for non-experts to create machine learning models when training data is limited or unavailable. 
> - **Sources**: [online](http://zotero.org/users/13492210/items/FI5I6UGN) [local](zotero://select/library/items/FI5I6UGN) [pdf](file:////home/lukexie/Documents/Papers/storage/Y6DSBKFF/data_programming_cameraready_with_appendix.pdf)  [pdf](file:////home/lukexie/Documents/Papers/storage/LWYWCN44/Ratner%20et%20al.%20-%202016%20-%20Data%20Programming%20Creating%20Large%20Training%20Sets,%20Qu.pdf) 
> - **Bibliography**: Ratner, A. J., De Sa, C. M., Wu, S., Selsam, D., & Ré, C. (2016). Data Programming: Creating Large Training Sets, Quickly. _Advances in Neural Information Processing Systems_, _29_. [https://proceedings.neurips.cc/paper/2016/hash/6709e8d64a5f47269ed5cea9f625f7ab-Abstract.html](https://proceedings.neurips.cc/paper/2016/hash/6709e8d64a5f47269ed5cea9f625f7ab-Abstract.html)
> - **Cite Key:** [[@ratnerDataProgrammingCreating2016]]
> - **Conclusion**: We introduced data programming, a new approach to generating large labeled training sets. We demonstrated that our approach can be used with automatic feature generation techniques to achieve high quality results. We also provided anecdotal evidence that our methods may be easier for domain experts to use. We hope to explore the limits of our approach on other machine learning tasks that have been held back by the lack of high-quality supervised datasets, including those in other domains such imaging and structured prediction.

>[!Personal Summary] 


# Questions
## Questions Regarding to This Paper

>[!question]
>What are the major problem of concern behind this paper?

- Common Problem for Weak Supervision [[Weak Supervision Basic Problem and Assumptions]]



>[!question]
>- What are the primary assumptions behind this paper?

- [[Weak Supervision Basic Problem and Assumptions]]: training labels are noisy and may be from multiple, potentially overlapping sources
- **Programmatic Weak Supervision**: there exist simple mechanisms that generate noisy labels for a large amount of data. These simple mechanisms are represented in forms of ***label functions (LFs)***.



>[!question]
>What is the conclusion of the paper?

- The authors introduced a *paradigm* called *Data Programming* which automatically generate large labeled training set using a set of simple mechanisms (called label functions). They show that Data Programming with automatic feature generation techniques can achieve high quality labels.  


>[!question]
>- What are the related previous work to this paper?
>- What is the flow where this paper lies in? What is before this paper? What may be after this paper? What excites you and why?

- **distant supervision**: use existing knowledge base
- **crowdsourcing**: 
- **co-training**: learning from small labeled set and large unlabeled set by selecting two *conditionally independent **views***. Then two models are trained collaboratively, each providing pseudo-labels to the other. 
- **boosting**: an ensemble learning method that learns and combines multiple *weak learners* sequentially to achieve good performance in joint model. Boosting can be used in semi-supervised setting with unlabelled data. It can set constrains on the accuracy of each weak learner on unlabeled set. 
- **learning with noisy labels**: 
- **adversarial learning**: Using adversarial learning instead of maximum likelihood estimation can provide strong theoretical guarantees without assumptions on the distribution of labels and labeling function outputs, but requires either a small amount of labeled data or other assumptions to constrain the accuracy of the labeling function
- Another line of work has extended the label modeling stage to incorporate features of the underlying data, in order to model *which types of examples each labeler is best at labeling*.  (instance-level LFs)
- 


>[!question]
>- What are the key characteristics for the method introduced in this paper?

**Data Programming**: 
- a paradigm for the programmatic creation of training sets
- user role: not label provider but provide *a description of labeling process* by a set of heuristic rules called **label functions**
- a *label model (e.g. probabilistic graphical model (PGM) )* that combines noisy label output from label functions. This model will encode the dependency relationship between label functions. 
	- The main role of Labeling functions is to *resolve the disagreements* of labels generated by multiple noisy labeling functions *without knowing the ground truth*.
	- In this work, the labeling functions are based on a *probabilistic generative model* that assumes the ground truth label for each example is *a latent random variable* that generates the outputs of the labeling functions. The parameters of the model are learned by *maximizing the likelihood of the observed outputs* of the labeling functions.
	- This model generalizes the classic ***Dawid-Skene model*** for **crowdsourcing**, i.e., learning from multiple human annotators.
	- In simplest form, we can assume conditional independence among labeling functions given true label. This often works well in practice.
	- Since labeling function exhibits systematic biases and correlations, we can also model their dependencies. 


>[!question]
>- What are the primary sources to the problem of this paper? theorem, data, code, literature


**Theory Settings**
- Symbols:
	- $\Lambda \in \{-1, 0, 1\}^m$ are pseudo-labels generated by labeling function;
	- $Y\in \{-1, 1\}$ is the predicted class
	  
- Assumption: *Independent labeling function*. The formulation of *label model* with two parameters $(\alpha, \beta)$  is 
$$
\mu_{\alpha, \beta}(\Lambda, Y) = \frac{1}{2}\prod_{i=1}^{m}\left(\beta_i\,\alpha_i\,\mathbf{1}_{\{\Lambda_i = Y_i\}} + \beta_i\,(1-\alpha_i)\,\mathbf{1}_{\{\Lambda_i = -Y_i\}} + (1-\beta_i)\,\mathbf{1}_{\{\Lambda_i = 0\}}  \right)
$$
Under this model, each labeling function $\lambda_i$ has some probability $\beta_i$ of *labeling an object* and then some probability $\alpha_i$ of labeling the object *correctly*; Normally, it is expected that labeling function has coverage $\beta_i \in [0.3, 0.5]$ and $\alpha_i \in [0.8, 0.9]$. 

Label models is used to integrate the LFs’ output predictions into **probabilistic labels**, aiming to accurately recover the unobserved ground truth labels.

- We can relax independence assumption on labeling function. Instead, we can use a *factor graphical model* $$
  \mu_{\theta}(\Lambda, Y) = \frac{1}{Z_{\theta}}\exp\left(\theta^{T} h(\Lambda, Y) \right)
  $$ where $h$ consists of $M$ factors.

- Objective function for *label model*: Our first goal will be to learn which parameters $(\alpha, \beta)$ are most *consistent* with our observations—our *unlabeled training set*—using maximum likelihood estimation.

$$\begin{align}
(\widehat{\alpha}, \, \widehat{\beta}) &:= \arg\max_{\alpha, \beta} \sum_{x \in \mathcal{S}}\log \mathbf{P}_{(\Lambda, Y) \sim \mu_{\alpha, \beta}}(\Lambda = \lambda(x))\\
&= \arg\max_{\alpha, \beta} \sum_{x \in \mathcal{S}}\log \left[ \sum_{y' \in \{-1, +1\}}\mu_{\alpha, \beta}(\lambda(x), y')  \right]
\end{align}
$$
	- Learning parameters can be competed via *Stochastic Gradient Descent*. 
	- For factor graph formulation, we can use *Gibbs sampling* in gradient update step

- Objective function for *end model*: Given that our parameter learning phase has successfully found some $(\widehat{\alpha}, \, \widehat{\beta})$ that accurately describe the training set, we can now proceed to estimate the parameter $w$ which minimizes the expected risk of a linear model over our feature mapping $f$, given $(\widehat{\alpha}, \, \widehat{\beta})$. Here label model provides weights on pseudo-labels generated by each label function.
  
![[formula_3.png]]

- Assumption:
	- The underlying joint distribution $(x,y) \sim \pi$ can be modeled by some $\mu$ in the given family of distributions where we want to learn $$
	  \mathbf{P}_{(x,y) \sim \pi}(\lambda(x) = \Lambda, y = Y) = \mu_{\alpha^*, \beta^{*}}(\Lambda, Y)
	  $$
	- given sample  $(x,y) \sim \pi$, ***class label $y$ must be independent of the feature $f(x)$ given the label $\lambda(x)$*** $$ y \perp f(x) \;|\; \lambda(x). $$This assumption encodes the idea that *the labeling functions*, while they may be arbitrarily dependent on the features, provide *sufficient information* to accurately identify the class.
	  
	- The *noise-aware empirical loss* for *end-model* has *bounded generalization error*; 
	  
- **Main Theorem**: Proof of *PAC learnability of end-model* under settings above and the assumptions above. 


**Experiments**
- **Relation Mention Extraction Tasks**: In the relation mention extraction task, our objects are *relation mention candidates* $x = (e_1, e_2)$, which are pairs of entity mentions $e_1$, $e_2$ in unstructured text, and our goal is to learn a model that classifies each candidate as either a true *textual assertion of the relation* $R(e_1, e_2)$ or not. 
	- **Dataset**: *2014 TAC-KBP Slot Filling challenge.* extract relations between real-world entities from article
	- **Dataset**: a clinical genomics application. extract causal relations between genetic mutations and phenotypes from the scientific literature
	- **Dataset**: a pharmacogenomics application. extract interactions between genes, also from the scientific literature
	  
- **Automatically-generated Features**: compare both hand-tuned and automatically generated features, where the latter are learned via an LSTM recurrent neural network (RNN).



>[!question]
>How to combine multiple noisy untrustworthy label sources to boost the performance of supervised learning?

- Use a probabilistic graphical model (PGM) that encode dependency structure of the labeling function. 
- This PGM model is used to generate combined pseudo-labels for the end model
- Learn parameters of the label model (PGM) via SGD + Gibbs sampling
- Learn end-model with pseudo-labels using noise-aware empirical risk minimization 


>[!question]
>What are limitations of this paper?

- Requires separate modeling for label model and end-model
  
- Theoretical guarantee requires ***sufficiency** of the labeling function*: 
  conditioned on the label functions, the ground truth label $y$ is independent to the sample $x$.  
  
- Good labeling function is assumed. For this analysis, it is assumed that the labeling function covers at least $50\%$ of sample size and achieves $80\%$ of accuracy. 
  
- Require domain expertise in creating the dependency graph for the label model.
	- In practice, the estimation of dependency structure among labeling functions is hard. 
	- Learning of PGM depends on the dependency structure and can be slow. 
	  
- Inference using Label models would still generate noisy labels. Depending on the performance of labeling function. 



## Questions Related to Me

>[!question] 
>Is the problem behind this paper related to problem of mine?

Yes. See 



>[! Questions Related to Me] 
> - Is the problem behind this paper related to problem of mine?
> - What impact does this paper have on me?
> - How does the author call my problem of concern? 
> - What do I notice about the source (data, reference)?
> - What questions and concerns that i might have?
> - Which of the feature-question in this paper lights my fire?
> - What aspects of the paper that excite me the most? Why, if i have to guess?
> - What aspects of the paper that are boring for me? Why, if i have to guess?
> - What vocabulary does this author, who clearly seems to be kept awake at night by the same gnawing question as I am, use to describe themself, whether professionally, intellectually, or otherwise?


## Advanced Questions




>[! Advanced Questions]
> - Change one variable regarding the features of the problem behind this paper. What new problem do you see? Could you find related papers? 
> - What is the very next primary source that the author might want to find?
> - What are related genres of questions that might related to the author's problem?
> - Listed all the author's questions, connected to other papers. Identify as many questions as possible.
> - Identity patterns among these questions of the author. What does this author seem to be concerned about or preoccupied with? 
> - What question the author did not ask? but for me they should.
> - see past the author’s case study, and identify the deeper-seated problem
> - try to identify a common theme that connect different author's problems; 
> - try to group papers of different author together