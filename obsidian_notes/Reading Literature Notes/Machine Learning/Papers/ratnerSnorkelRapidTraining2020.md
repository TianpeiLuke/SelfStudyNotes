---
tags:
  - "#paper"
  - programmatic_weak_supervision
aliases:
  - ratnerSnorkelRapidTraining2020
year: 2020
name: "Snorkel: rapid training data creation with weak supervision"
authors: Alexander Ratner, Stephen H. Bach, Henry Ehrenberg, Jason Fries, Sen Wu, Christopher Ré
publication: The VLDB Journal
type: journalArticle
DOI: 10.1007/s00778-019-00552-1
date of note: 2024-03-07
---

## Snorkel: rapid training data creation with weak supervision 
> [!info] 
> - **Abstract:** Labeling training data is increasingly the largest bottleneck in deploying machine learning systems. We present Snorkel, a first-of-its-kind system that enables users to train state-of-the-art models without hand labeling any training data. Instead, users write labeling functions that express arbitrary heuristics, which can have unknown accuracies and correlations. Snorkel denoises their outputs without access to ground truth by incorporating the first end-to-end implementation of our recently proposed machine learning paradigm, data programming. We present a flexible interface layer for writing labeling functions based on our experience over the past year collaborating with companies, agencies, and research laboratories. In a user study, subject matter experts build models $2.8\times$ faster and increase predictive performance an average $45.5\%$ versus seven hours of hand labeling. We study the modeling trade-offs in this new setting and propose an optimizer for automating trade-off decisions that gives up to $1.8\times$ speedup per pipeline execution. In two collaborations, with the US Department of Veterans Affairs and the US Food and Drug Administration, and on four open-source text and image data sets representative of other deployments, Snorkel provides $132\%$$ average improvements to predictive performance over prior heuristic approaches and comes within an average $3.60\%$$ of the predictive performance of large hand-curated training sets. 
> - **Sources**: [online](http://zotero.org/users/13492210/items/QCWL6BFW) [local](zotero://select/library/items/QCWL6BFW) [pdf](file:////home/lukexie/Documents/Papers/storage/AWKESA6Z/Ratner%20et%20al.%20-%202020%20-%20Snorkel%20rapid%20training%20data%20creation%20with%20weak%20su.pdf) 
> - **Bibliography**: Ratner, A., Bach, S. H., Ehrenberg, H., Fries, J., Wu, S., & Ré, C. (2020). Snorkel: Rapid training data creation with weak supervision. _The VLDB Journal_, _29_(2), 709–730. [https://doi.org/10.1007/s00778-019-00552-1](https://doi.org/10.1007/s00778-019-00552-1)
> - **Cite Key:** @ratnerSnorkelRapidTraining2020
> - **Tags:** #Machine-learning, #Training-data, #Weak-supervision
> - **Github**:  [https://github.com/snorkel-team/snorkel](https://github.com/snorkel-team/snorkel)
> - **Conclusion**: Snorkel provides a new paradigm for soliciting and managing weak supervision to create training data sets. In Snorkel, users provide higher-level supervision in the form of labeling functions that capture domain knowledge and resources, without having to carefully manage the noise and conflicts inherent in combining weak supervision sources. Our evaluations demonstrate that Snorkel significantly reduces the cost and difficulty of training powerful machine learning models while exceeding prior weak supervision methods and approaching the quality of large, hand-labeled training sets. Snorkel’s deployments in industry, research laboratories, and government agencies show that it has real-world impact, offering developers an improved way to build models.

>[!Personal Summary] 



## Questions

>[!question]
>What are the major problem of concern behind this paper?








>[!question]
>How the output of label functions are combined?







>[!question]
>How the end model uses the output of label functions?





>[! Questions Regarding to This Paper] 
>- What are the primary assumptions behind this paper?
> - What are the major problem of concern behind this paper? If i had to guess, what does the author seems to be concerned 
> - What is the specific case that the study focus on?
> - What is the argument in this paper?
> - What is the specific questions posed by the study of the paper?
> - What is the conclusion of the paper?
> - What are the primary sources to the problem of this paper? data, code, literature
> - How is the source _primary_ to the problem of this paper?
> - What is the flow where this paper lies in? What is before this paper? What may be after this paper? What excites you and why?
> - What success criteria are used in this paper?  What are the evaluation results?
> - What technical terms it used?


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