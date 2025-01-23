---
tags:
  - "#paper"
  - programmatic_weak_supervision
aliases:
  - yuAlfredSystemPrompted2023
year: 2023
name: "Alfred: A System for Prompted Weak Supervision"
authors: Peilin Yu, Stephen Bach
publication: "Proceedings of the 61st Annual Meeting of the Association for Computational Linguistics (ACL 2023 - Volume 3: System Demonstrations)"
type: conferencePaper
DOI: 10.18653/v1/2023.acl-demo.46
date of note: 2024-03-11
---
# Descriptions

## Alfred: A System for Prompted Weak Supervision 
> [!info] 
> - **Abstract:** Alfred is the first system for programmatic weak supervision (PWS) that creates training data for machine learning by prompting. In contrast to typical PWS systems where weak supervision sources are programs coded by experts, Alfred enables users to encode their subject matter expertise via natural language prompts for language and vision-language models. Alfred provides a simple Python interface for the key steps of this emerging paradigm, with a high-throughput backend for large-scale data labeling. Users can quickly create, evaluate, and refine their prompt-based weak supervision sources; map the results to weak labels; and resolve their disagreements with a label model. Alfred enables a seamless local development experience backed by models served from self-managed computing clusters. It automatically optimizes the execution of prompts with optimized batching mechanisms. We find that this optimization improves query throughput by 2.9x versus a naive approach. We present two example use cases demonstrating Alfred on YouTube comment spam detection and pet breeds classification. Alfred is open source, available at https://github.com/BatsResearch/alfred. 
> - **Sources**: [online](http://zotero.org/users/13492210/items/MEAZBY84) [local](zotero://select/library/items/MEAZBY84) [pdf](file:////Users/lukexie/Zotero/storage/AI8MMZRI/Yu%20and%20Bach%20-%202023%20-%20Alfred%20A%20System%20for%20Prompted%20Weak%20Supervision.pdf) 
> - **Bibliography**: Yu, P., & Bach, S. (2023). Alfred: A System for Prompted Weak Supervision. In D. Bollegala, R. Huang, & A. Ritter (Eds.), _Proceedings of the 61st Annual Meeting of the Association for Computational Linguistics (Volume 3: System Demonstrations)_ (pp. 479–488). Association for Computational Linguistics. [https://doi.org/10.18653/v1/2023.acl-demo.46](https://doi.org/10.18653/v1/2023.acl-demo.46)
> - **Cite Key:** @yuAlfredSystemPrompted2023
> - **Conclusion**: This paper introduces Alfred, a prototype for the next generation of programmatic weak supervision systems that leverage the potential of large pretrained models. Alfred complements the existing ecosystem of large-pretrained-model toolkits, offering optimized inference throughput, a smooth local development experience, and compatibility with vision-language models to support image annotation tasks. Alfred represents a notable advancement in the domain of programmatic weak supervision, as it enables users to express their domain-specific knowledge and heuristics with flexible natural language prompts for language and vision-language models. This approach can be more user-friendly than conventional PWS systems, which requires expert programming of weak supervision sources. Our objective is for Alfred to serve as the infrastructure and experimentation platform for many future weak supervision research projects and applications. Furthermore, we plan to extend Alfred’s capabilities to accommodate a wider range of multimodal large pre-trained models, such as Whisper (Radford et al., 2022) and LayoutLMs (Xu et al., 2020b,a; Huang et al., 2022).


>[!Personal Summary] 


# Questions
## Questions Regarding to This Paper


>[!question] 
>What are the *primary assumptions* behind this paper?

[[Weak Supervision Basic Problem and Assumptions]]


>[!question]
>What is the argument in this paper?

- Traditional PWS using heuristic rules, human domain expertise to design labeling function (LF). 
- Using LLM to create LF attracts attention
- **Prompted LFs** use prompts with natural languages to replace coded LFs. The benefits of using Prompted LFs are:
	- Prompted Models can replace human experts;
	- Prompted Models can use easy human language expression to represent complex rule logics and functions that are hard to code. 
	- They can "potentially elevating the quality of the annotation"
	- Prompted Models can be multi-modal. They can handle both NLP and CV tasks. 
	- Prompts are easy to generate. Thus they allow users to conduct experiments easily. 



>[!question]
>What are the major *problems of concern* behind this paper? If i had to guess, what does the author seems to be concerned. 

- In typical PWS, LF are cheap but LLM based LFs are expensive to execute.
- PWS using prompted models requires us to rethink the **workflow** and **abstractions**:
	- User need to manage *a library of prompts* instead of a library of functions; 
	- LLM demands high computational resources; The **throughput** of models is the bottleneck.
- There lacks open source solutions for prompt-based PWS
	- Existing ones focus on prompt engineering, prompt-chains, soft prompt tuning
	- Lack of Vision-Language support
- This paper concerns about a software infrastructure that facilitates efficient development. 



>[!question]
>What are *related publications* before this paper? What may be *after* this paper? What excites you and why?

- Original paper for PWS [[ratnerDataProgrammingCreating2016]]
- Survey [[zhangSurveyProgrammaticWeak2022]]
- Creating LFs using LLM
	- Smith, Ryan, Jason A. Fries, Braden Hancock, and Stephen H. Bach. “Language Models in the Loop: Incorporating Prompting into Weak Supervision.” _ACM / IMS Journal of Data Science_, November 16, 2023. [https://doi.org/10.1145/3617130](https://doi.org/10.1145/3617130).
	- Arora, Simran, Avanika Narayan, Mayee F. Chen, Laurel Orr, Neel Guha, Kush Bhatia, Ines Chami, and Christopher Re. “Ask Me Anything: A Simple Strategy for Prompting Language Models.” In _The Eleventh International Conference on Learning Representations_, 2023. [https://openreview.net/forum?id=bhUPJnS2g0X](https://openreview.net/forum?id=bhUPJnS2g0X).
	- Zhang, Rongzhi, Yue Yu, Pranav Shetty, Le Song, and Chao Zhang. “Prompt-Based Rule Discovery and Boosting for Interactive Weakly-Supervised Learning.” In _Proceedings of the 60th Annual Meeting of the Association for Computational Linguistics (Volume 1: Long Papers)_, edited by Smaranda Muresan, Preslav Nakov, and Aline Villavicencio, 745–58. Dublin, Ireland: Association for Computational Linguistics, 2022. [https://doi.org/10.18653/v1/2022.acl-long.55](https://doi.org/10.18653/v1/2022.acl-long.55).
	- Chen, Mayee F., Daniel Y. Fu, Dyah Adila, Michael Zhang, Frederic Sala, Kayvon Fatahalian, and Christopher Ré. “Shoring up the Foundations: Fusing Model Embeddings and Weak Supervision.” In _Proceedings of the Thirty-Eighth Conference on Uncertainty in Artificial Intelligence_, 357–67. PMLR, 2022. [https://proceedings.mlr.press/v180/chen22e.html](https://proceedings.mlr.press/v180/chen22e.html).
- Prompting LLMs
- System that facilitate prompt development 
	- **PromptSource**: environment for creating and archiving prompts
	- **OpenPrompt**: prompt tuning
	- **Manifest**: unified front-end with different API
	- **LangChain**: provides convenient utilities for building applications that chain together multiple prompts and outputs.



>[!question]
>What are *the main contributions* of the paper?

>[!quote]
>We present Alfred, a versatile PWS system that leverages large pre-trained models for image and text annotations. Alfred aims to provide an environment for the rapid development of prompt-based supervision, while maintaining a consistent development experience similar to established PWS systems.

- **Alfred**,  a Python interface for key steps in PWS
- **Alfred** allow users to encode *subject mater expertise* into prompts and using prompts to generate Labeling Functions based on LLMs
	- Support popular LLMs
	- Support local models and API-based models
	- Support multi-modal
	- Easy Template for Prompt
	- Interactive Prompt LF development
	- Manage prompts, track their outputs from multiple datasets
	- Manage Label models that distill output of prompted LFs into final training datasets
	- Easy Inference Server Deployment
	- Optimize Throughput of Models
- The authors said that **Alfred** is the 2nd generation PWS


>[!question]
>What is the *major workflow* it proposed?

![[pws_alfred_workflow.png]]
1. **Task Setup**: For a large model to be used in the development loop, developers can elect to use either self-hosted models or API-based models. `AlfredServer`: host for model. `Client`: specify the type of model. User interacts with `Client` for experiments on labeling. `Dataset` class for fast data access.  
2. **Interactive Prompt Development**: `Template` define LFs, output `Query` objects. For each `Query`, `Client` generate `Response`. User define `Voter` that maps response to votes. We can define different matching functions that specify how `Voter` determine a match. Evaluation can be done using additional `Dataset`. 
3. **Aggregate Prompt Responses**: Finally, the votes are aggregated from each `Voter` with a `LabelModel` to produce probabilistic estimates of the true labels. Alfred implements the following LabelModel
	1. `MajorityVote`
	2. `NaiveBayes`
	3. `NPLM`: noisy partial label model
	4. `FlyingSquid`: recommended when `MajorityVote` is not accurate enough but `NaiveBayes` is too slow. 


>[!question]
>What *technical terms and vocabulary* it used?

- **Programmatic Weak Supervision** (PWS)
- Large Language Model (LLM)
- **Prompted Models**
- Labeling Functions
- Label Model
- End Model


## Primary Sources


>[!question]
>What are the *primary sources* to the problem of this paper? list important the datasets, code repositories, literature citations

- **YouTube spam detection dataset** 
  Alberto, Túlio C., Johannes V. Lochter, and Tiago A. Almeida. “TubeSpam: Comment Spam Filtering on YouTube.” In _2015 IEEE 14th International Conference on Machine Learning and Applications (ICMLA)_, 138–43, 2015. [https://doi.org/10.1109/ICMLA.2015.37](https://doi.org/10.1109/ICMLA.2015.37).
- The prompts are translated from the code-based labeling functions provided by the **WRENCH benchmark** (Zhang, Jieyu, Yue Yu, Yinghao Li, Yujing Wang, Yaming Yang, Mao Yang, and Alexander Ratner. “WRENCH: A Comprehensive Benchmark for Weak Supervision.” arXiv, October 11, 2021. [https://doi.org/10.48550/arXiv.2109.11377](https://doi.org/10.48550/arXiv.2109.11377).)
- Pet Breed Classification
	- **Oxford-IIIT Pet dataset**
	- 



>[!question]
>*How* is the source _primary_ to the problem of this paper? List major results from *literary, theoretical and experimental perspectives* that support the conclusion of the paper. Also explain the success criteria that are used in this paper.






> [!question]
> What do I notice about the source (data, theory, reference)? list feature-question pair from the sources






>[!question] 
>Which of the feature-question in this paper lights my fire?





>[!question]
>What is the *very next primary source* that the author might want to find?


## Questions Related to Me


> [!question] 
> Is the problem behind this paper related to problem of mine?



> [!question] 
> What impact does this paper have on me?



> [!question] 
> How does the author call my problem of concern?



>[!question]
>What aspects of the paper that *excite* me the most? Why, if i have to guess?



>[!question]
>What aspects of the paper that are *boring* to me? Why, if i have to guess?




>[!question]
  What vocabulary does this author, who clearly seems to be kept awake at night by the same gnawing question as I am, use to describe themself, whether professionally, intellectually, or otherwise?



## Advanced Questions

### Limitations and Restrictions


>[!question]
>What are the *limitations* of this paper? What criticism towards the perspective of this paper?
>> [!question] Follow-Up Questions
>> - What question the author did not ask? but for me they should.
>> - What are the limitations on the assumptions of the paper?
>> - What are the limitations and restrictions for primary sources in the paper? 
>> - Are there untold tricks to achieve the results?
>> - Are we satisfied with the conclusion of the paper? why or why not?
>> - Under what situation the conclusion of this paper do not hold?
>> - Under what condition the major argument do not hold? 
>> - How much resources do we need to replicate the results?
>> - Can we use this paper in real world applications?
>> - What are the costs to use this paper in real life applications?

>[!quote]
>Alfred is a prototype for the second generation of PWS systems, which incorporate large pre-trained models. However, there are some potential limitations to consider. As with all PWS approaches, application quality is limited by *the quality of the weak supervision sources* used to vote on the labels. In this case of prompted labeling functions, this depends on *how well suited the prompts and model are to the task and domain*. If they are not well suited, then additional fine-tuning of the prompted models will be necessary. Compared with traditional labeling functions written in code, *understanding when and why labeling functions fail on certain examples can be particularly challenging.* Methods for *explanations* such as minimal contrastive edits (Ross et al., 2021) can potentially help address this limitation. We plan to explore incorporating such methods into Alfred.



> [!question] 
> What questions and concerns that i might have after reading the paper?
> 


### Connection, Expansion and Generalization


>[!todo] Connect More Papers
>- What are related genres of questions that might related to the author's problem?
>- Listed all the author's questions, connected to other papers. Identify as many questions as possible.



>[!todo] Problem Summarization and Expansion
>
>- Identity patterns among these questions of the author. What does this author seem to be concerned about or preoccupied with? 
>- try to identify a common theme that connect different author's problems; 
>- see past the author’s case study, and identify the deeper-seated problem



> [!question]
> Change one variable regarding the features of the problem behind this paper. What new problem do you see? Could you find related papers? 





>[!todo]
> Try to group papers of different author together




----

## Reference and Related Notes
- Tutorial:  [[zhangSurveyProgrammaticWeak2022]]
- Stephen Bach is an advisor to Snorkel AI, a company that provides software and services for weakly supervised machine learning. [[ratnerSnorkelRapidTraining2020]]
- 