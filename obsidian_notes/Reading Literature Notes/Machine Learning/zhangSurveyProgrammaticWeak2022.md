---
tags:
  - "#paper"
  - programmatic_weak_supervision
aliases:
  - zhangSurveyProgrammaticWeak2022
year: 2022
name: A Survey on Programmatic Weak Supervision
authors: Jieyu Zhang, Cheng-Yu Hsieh, Yue Yu, Chao Zhang, Alexander Ratner
publication: ArXiv
type: preprint
DOI: 10.48550/arXiv.2202.05433
date of note: 2024-03-08
---

## A Survey on Programmatic Weak Supervision 
> [!info] 
> - **Abstract:** Labeling training data has become one of the major roadblocks to using machine learning. Among various weak supervision paradigms, programmatic weak supervision (PWS) has achieved remarkable success in easing the manual labeling bottleneck by programmatically synthesizing training labels from multiple potentially noisy supervision sources. This paper presents a comprehensive survey of recent advances in PWS. In particular, we give a brief introduction of the PWS learning paradigm, and review representative approaches for each component within PWS's learning workflow. In addition, we discuss complementary learning paradigms for tackling limited labeled data scenarios and how these related approaches can be used in conjunction with PWS. Finally, we identify several critical challenges that remain under-explored in the area to hopefully inspire future research directions in the field. 
> - **Sources**: [online](http://zotero.org/users/13492210/items/LDVMQN8D) [local](zotero://select/library/items/LDVMQN8D) [pdf](file:////Users/lukexie/Zotero/storage/LACFAQWR/Zhang%20et%20al.%20-%202022%20-%20A%20Survey%20on%20Programmatic%20Weak%20Supervision.pdf) 
> - **Bibliography**: Zhang, J., Hsieh, C.-Y., Yu, Y., Zhang, C., & Ratner, A. (2022). _A Survey on Programmatic Weak Supervision_ (arXiv:2202.05433). arXiv. [https://doi.org/10.48550/arXiv.2202.05433](https://doi.org/10.48550/arXiv.2202.05433)
> - **Cite Key:** [[@zhangSurveyProgrammaticWeak2022]]
> - **Tags:** #Computer-Science---Artificial-Intelligence, #Computer-Science---Machine-Learning, #Statistics---Applications
> - **Conclusion**: Manual annotations are always of great importance to training machine learning models, but usually expensive and timeconsuming. Programmatic weak supervision (PWS) offers a promising direction to achieve large-scale annotations with minimal human efforts. In this article, we review the PWS area by introducing existing approaches for each component inside a PWS workflow. We also describe how PWS could interact with methods from related fields for better performance on downstream applications. Then, we list existing datasets and recent applications of PWS in the literature. Finally, we discuss current challenges and future directions in the PWS area, hoping to inspire future research advances in PWS.

>[!Personal Summary] 


## Questions regarding This Paper


>[! question] 
> What are the primary assumptions behind this paper?

- Deep Learning algorithms requires massive amount of annotated training samples. 
- Label Scarcity. Labeling is expensive. 
- Clean Label Scarcity. A set of clean labeled data is required to achieve good performance.
- Multiple Sources to obtain weak supervision. 
- Each weak supervision source is noisy. 


>[! question] 
>What are the major common problem of concern behind this paper? If i had to guess, what does the author seems to be concerned 

- The author concerns about learning a data-hungry model under limited clean labeled data.
- This paper is a tutorial on *the Programmatic Weak Supervision (PWS)* frameworks. 
- This paper has several tasks:
	- introduce basic concepts and formulation in PWS including
		- **Labeling Functions**: produce weak labels
		- **Label Model**: model that aggregate votes from multiple label functions
		- **End Model**: noise-tolerate models build from weak label aggregation.
		- **PWS workflow**: a pipeline that build end models using multiple weak supervision label functions 
	- introduce and discussed various methods used in each component of the PWS workflow. Provide reader entry point to reference. 
	- group existing methods in two categories: *two-stage method* or *one-stage method*. 
	- compare with related frameworks such as *Active Learning, Semi-supervised Learning and Transfer Learning*. 

![[PWS pipeline.png]]



>[! question] 
> What is the specific case that the study focus on?

- This tutorial focus on *the Programmatic Weak Supervision (PWS)* frameworks which aggregates votes based on noisy labeling functions from multiple weak supervision sources to build a reliable model for the downstream task. 



>[! question] 
> What are the models and methods discussed in this tutorial?

- **Labeling Function Types**:
	- **User Heuristics**: *labeling rule-based* such as *keyword-* or *regex-based LFs*; In CV, object detector is used to define heuristics. 
	- **Knowledge Base**: *distant learning approach*, using external knowledge base to provide weak supervision. e.g. *distance supervision approach* in *relation extraction task*. 
	- **Pre-trained Models**: using existing models from a related tasks to provide weak labels.  e.g. Google using existing *semantic topic model* to identify contents irrelevant to the product categories. Use pre-trained image classification model with different output label space as LFs. 
	- **Third party tools**: e.g. *NLTK*, *spaCy* for *NER* task. *TextBlob* for label assignment for sentiment analysis review. 
	- **Crowd-sourced labels**: each crowd-sourcing contributor can be represented as an LF. *Snorkel* used crowd-sourcing label as one of LFs. 
	  
- Normally LFs are developed by domain expert who used a small development set of samples to derive rules and models. 
  
- Label functions are generalization of the *views* in *co-training framework*. Unlike co-training, the generation of label functions are independent from the learning of label models which combines label functions.
  
- **Labeling function generation**: 
	- **Automatic Generation**: need some minimum supervision, seed LFs. 
		- *Snuba* generate LF by learning weak classification models on a small set of labeled datasets
		- *TALLOR*: input *seed LFs* and learn more *compound LFs* from multiple simple labeling rules
		- *GLaRA*: augment seed LFs, exploit semantic relationships between candidate and seed LFs via *graphical model*
	- **Interactive Generation**: use *interactively queries* to ask user to select LFs from a large pool of candidates. 
		- This is different from AL which relies on instance level annotation not rule-level. 
		- *Darwin*: candidate generated using n-gram or context-free grammar information. Each iteration, query user to annotate if a pre-selected LF is useful. (Note: similar to human-in-the-loop fine-tuning of LLM such as *RLHF*). System adapt at each iteration based on selection. (Multi-arm Bandit?)
		- *IWS*: 
	- **Guided Generation**: select *development set* to *guide* SME to generate LFs. Similar to AL, but annotation in LF level instead of individual label.
	  
- **Label models**: 
	- Multiple LFs would have conflict, overlap with each other. 
	- Label models are used to integrate predictions of LFs into probabilistic labels. They are also critical to resolve disagreements between multiple LFs
	- LFs have statistical dependency; Label Model may want to account for the dependency information
	- Most methods are based on probabilistic graphical models (PGMs) to model dependencies among labeling functions. 
	- Label Model for *Classification*: 
		- **Majority Vote**
		- *Data Programming* use factor graph
		- *MeTal* use *Markov Network* and recover parameters via *matrix completion*
		- *FlyingSquid* use a *binary Ising model*, where each LF is represented by two random variables, and a *Triplet Method* is used to recover the parameters and therefore no learning is needed.
		- *CAGE* extends LF to continuous LFs
		- *NPLM* use partial LFs that output a subset of possible class labels
		- *PLRM* allow indirect LFs that only predict unseen but related classes.
	- Label Model for *Sequence Tagging*: 
		- additional dependency between successive tokens. 
		- *Linked-HMM* for *Name Entity Recognition (NER)* use additional linking rules as adjunct supervion;
		- *Conditional hidden Markov model (CHMM)* learn transition and emission matrices using BERT embeddings. 
		- *Dugong* combines tags at different solutions (frames, window, scene) 
	- Label model for general tasks
		- *Universalizing weak supervision (UWS)* generalize PWS to ranking, regression, learning on manifold. 
- Label models are the *key* for PWS framework. This framework emphasize the existence of dependencies among labeling functions. The graph structure of labeling functions reflect the reasoning behind decision making using multiple sources. 
  
- **End Model**:
	- End model use probabilistic labels to train discriminative downstream tasks
	- Noise may still exist in probabilistic labels. So may need the *noise-tolerate* model.
	- *COSINE* use self-training method to generate pseudo-labels for unlabeled data. 
	- Other methods for *learning with noisy labels* can be used as end models.
	  
- **Joint Model**:
	- train label model and end model in an end-to-end manner
	- use neural networks instead of PGM.
	- design to facilitate co-training of both label model and end model
	- instance-dependent label model. 
	- can implicitly capture dependencies from LFs
	- Joint Model for *Classification*:
		- *Denoise*: reparameterize prior probabilistic posteriors with a neural network; then assign scores for each PWS sources for aggregation. After that, posterior network and end network are jointly trained to maximize the agreement between them. 
		- *WeaSEL*: 
		- *constrained min-max optimization*
		- *ALL*: learn model with high expected accuracy w.r.t. adversarial labeling
		- *AMCL*: constraints based on expected loss within a small set of clean data.
		- *ImplyLoss* train a rule denoising network using exemplars from each label and a classification model with soft implication loss
		- *SPEAR*: extends ImplyLoss, design additional loss for both label and unlabel data. encourage two models match
		- *ASTRA*: adopt self-training for PFW with a teacher-student framework.
	- Joint Model for *Sequence Tagging*: 
		- *Consensus Network (ConNet)*: use *BiLSTM-CRF*. Each CRF for each labeling sources. aggregate CRF transitions with attention scores conditioned on quality of LFs and outputs of a unified label sequence. 
		- *DWS*: CRF layer to capture statistical dependencies among tokens, weak labels and latent true labels. It use hard EM for training, finding most probable labels at E-step and maximize the probability for corresponding labels in M-step. 
![[table 1.png]]




>[! question] 
> What technical terms it used?

- deep learning
- active learning (AL)
- semi-supervised learning (SSL)
- transfer learning (TL)
- distant supervision
- crown-sourcing
- feature annotation
- programmatic weak supervision
- weak supervision
- labeling functions (LFs)
- knowledge base
- subject matter expert (SME)
- development set
- label function generation
- automatic generation
- seed LFs
- Snuba
- TALLOR
- GLaRA
- interactive generation
- Darwin
- IWS
- guided generation
- label models
- probabilistic graphical models (PGMs)
- LF dependency structure
- $\ell_1$-regularized marginal pseudo-likelihood of a factor graph with high order dependencies
- sparsity
- robust PCA
- classification
- majority vote
- Expectation-Maximization (EM) algorithm
- Data programming (DP)
- SGD
- Gibbs sampling
- MeTaL
- Markov Network
- matrix completion
- FlyingSquid
- binary Ising model
- Triplet Method
- CAGE
- continuous LFs
- NPLM
- partial LFs
- a subset of possible class labels
- PLRM
- sequence tagging
- Hidden Markov Models (HMM)
- Linked-HMM
- Conditional hidden Markov model (CHMM)
- transition and emission matrices
- the BERT embeddings
- context-dependent manner
- Dugong
- UWS
- generalizes PWS frameworks
- end models
- COSINE
- joint models
- neural network
- co-training of label model and end model
- instance-dependent label model
- Denoise
- WeaSEL
- reparameterize prior probabilistic posteriors
- the posterior network
- maximize the agreement
- constrained min-max optimization problem
- ALL
- adversarial labeling
- AMCL
- ImplyLoss
- a rule denoising network
- soft implication loss
- SPEAR
- ASTRA
- self-training
- teacher-student framework
- Consensus Network (ConNet)
- BiLSTM-CRF
- DWS

>[!question]
>- What vocabulary does this author, who clearly seems to be kept awake at night by the same gnawing question as I am, use to describe themself, whether professionally, intellectually, or otherwise?

- The term *the Programmatic Weak Supervision (PWS)*. It emphasize the importance of creating multiple simple programmable labeling functions that capture one aspect of the ground truth. 



>[!question]
>What are the major challenges in this domain? 

- **Extension of Task**: Currently PWS mainly used in *classification and sequence tagging*. On the other hand, tasks that requires high level of reasoning such as *question answering* also face the same issues in the assumption. Also these applications have *multi-modal* use case.
  
- **Extension on Label Functions**: for instance, physical rules, 
  
- **Ethical and Trustworthy AI**: to make sure training data which informs models is ethically labeled and managed, transparent, auditable, and bias-free.


## Questions related to me

>[!question]
>Is the problem behind this paper related to problem of mine?

Yes. Check details in [[RnR via Weak Supervision]]


>[!question]
>What impact does this paper have on me?

This paper introduce me the concept of programmatic weak supervision, a new paradigm to create large new training sets with weak supervision. 

>[!question]
>How does the author call my problem of concern?

The problem of RnR can be interpreted using **Programmatic Weak Supervision (PWS)**


>[!question]
>What aspects of the paper that excite me the most? Why, if i have to guess?

Learning robust models based on multiple weak label sources and domain expertise is the critical problem behind most of abuse prevention methods. 

The exciting part for PWS is that this framework has potential to combine all existing weak labeling strategies and to balance their impact in the final solution. We have many way to provide abuse labels but none of them are fully applicable to all datasets. There are subset of samples that these heuristics, rules and models are of high accuracy but not every one of them. 

This framework provide solution that can be used in the following tasks:
- build robust ML model given the existing discrepancy between ARI decisions and WBR abuse definitions.
- develop solutions that combine *multiple decision policies* at the planning phase of *the Action Taking System (ATS)*. This can be part of the tasks in post-investigation workflow. 
- explore the interpretability of labeling logic using multiple labeling sources;
- apply *in-context learning of LLMs* to create multiple query-based labeling function. 
- make use of many rules in RMP to support a better models.


>[!question]
>What aspects of the paper that are boring for me? Why, if i have to guess?

1. The learning of label model, which is the key of the PWS, relies on the dependency graph defined by domain expert. The inference of labels from multiple label functions are based on *Probabilistic Graphical Model (PGM)*. It aims at maximizing the probability of observing the outputs of LFs. 
   
	A major issue for PGM is that the underlying graph is user-defined and thus it is not fully automated and is not very adaptive to different use cases. Also the identification and verification of statistical dependencies between labeling functions is very challenging. If not to do conditional dependency verification, the validity of PGM is not guaranteed. 
	
	The inference via PGM is not very efficient. The current solution is based on Gibbs sampling which is time consuming. 
	
	The joint model solution which do not learn two models separately would be a good choice. But most of joint model solution is based on PGM too. A typical example is HMM-CRF model. 
	
2. For classification models, *majority votes* would be the major way to combine outputs of the labeling functions. Majority vote has no parameters and are too simple to use. Then program labeling functions + majority vote + noise-tolerate model = programmatic weak supervision?

3. Why do we still need to use robust noise-tolerate models as end model? This seems to defeat the purpose of using weak supervision. Can we just use noise tolerate model on existing labels without combining labeling functions from multiple sources? 
   
   Seems that the major selling point of PWS is that there are *multiple sources of weak labels*. Each output label space that covers the ground truth but has high false positives. To learn a robust model, we still need to search for noise tolerate model


---

## Related Papers

- **Data Programming**, basis for *Programmatic Weak Supervision (PWS)*. [[ratnerDataProgrammingCreating2016]]
- **Snorkel**, weakly supervised learning framework:  [[ratnerSnorkelRapidTraining2020]]
- [https://snorkel.ai/weak-supervision-modeling/](https://snorkel.ai/weak-supervision-modeling/)