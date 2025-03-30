---
tags:
- '#paper'
aliases: "smithLanguageModelsLoop2024"
year: 2024
name: "Language Models in the Loop: Incorporating Prompting into Weak Supervision"
authors: "Ryan Smith, Jason A. Fries, Braden Hancock, Stephen H. Bach"
publication: "ACM / IMS J. Data Sci."
type: "journalArticle"
DOI: "10.1145/3617130"
date of note: 2025-03-27 
---
# Descriptions

## Language Models in the Loop: Incorporating Prompting into Weak Supervision 
> [!info] 
> - **Abstract:** We propose a new strategy for applying large pre-trained language models to novel tasks when labeled training data is limited. Rather than apply the model in a typical zero-shot or few-shot fashion, we treat the model as the basis for labeling functions in a weak supervision framework. To create a classifier, we first prompt the model to answer multiple distinct queries about an example and define how the possible responses should be mapped to votes for labels and abstentions. We then denoise these noisy label sources using the Snorkel system and train an end classifier with the resulting training data. Our experimental evaluation shows that prompting large language models within a weak supervision framework can provide significant gains in accuracy. On the WRENCH weak supervision benchmark, this approach can significantly improve over zero-shot performance, an average 19.5% reduction in errors. We also find that this approach produces classifiers with comparable or superior accuracy to those trained from hand-engineered rules.Problem statementThe goal of this paper is to use large language models to create smaller, specialized models. These specialized models can be better suited to specific tasks because they are tuned for them and are less expensive to serve in production. Existing approaches create training data for specialized models by prompting large language models in a zero-shot fashion, i.e., they instruct the language model to solve the task of interest and treat the responses as ground truth. This approach can be unreliable when the language model has noisy outputs and is sensitive to the wording of the prompt.MethodsWe address the problems of noisy outputs and prompt sensitivity by proposing a new strategy. We treat large language models as the basis for labeling functions in a weak supervision framework. To create a classifier, we first prompt the model to answer multiple distinct queries about an example and define how the possible responses should be mapped to votes for labels and abstentions. We then denoise these noisy label sources using the Snorkel system and train an end classifier with the resulting training data.ResultsOur experimental evaluation shows that prompting large language models within a weak supervision framework can provide significant gains in accuracy. On the WRENCH weak supervision benchmark, this approach can significantly improve over zero-shot performance, an average 19.5% reduction in errors. We also find that this approach produces classifiers with comparable or superior accuracy to those trained from hand-engineered rules.SignificanceLarge language models are increasingly the starting point in many areas of machine learning. Incorporating prompting into weak supervision can enable users to more easily and accurately adapt them to specialized tasks. 
> - **Sources**: [online](http://zotero.org/users/13492210/items/FVJAKI72) [local](zotero://select/library/items/FVJAKI72) [pdf](file:////Users/lukexie/Zotero/storage/RP25YYCZ/Smith%20et%20al.%20-%202024%20-%20Language%20Models%20in%20the%20Loop%20Incorporating%20Prompting%20into%20Weak%20Supervision.pdf) 
> - **Bibliography**: Smith, R., Fries, J. A., Hancock, B., & Bach, S. H. (2024). Language Models in the Loop: Incorporating Prompting into Weak Supervision. _ACM / IMS J. Data Sci._, _1_(2), 7:1-7:30. [https://doi.org/10.1145/3617130](https://doi.org/10.1145/3617130)
> - **Cite Key:** @smithLanguageModelsLoop2024
> - **Conclusion**:


>[!note] Highlights:
>
>-
>-
>-



# Questions
## Questions Regarding to This Paper


>[!question] 
>What are the *primary assumptions* behind this paper?



>[!question]
>What are the major *problems of concern* behind this paper? If i had to guess, what does the author seems to be concerned. 




>[!question]
>What are *the main contributions* of the paper?



## Highlight of Technical Details


>[!todo]
>Highlight the main techniques proposed in this paper. Also highlight the performance comparison to state-of-the-art.



## Questions Related to Me


> [!question] 
> Is the problem behind this paper related to problem of mine?



> [!question] 
> What impact does this paper have on me?




----

## Reference and Related Notes