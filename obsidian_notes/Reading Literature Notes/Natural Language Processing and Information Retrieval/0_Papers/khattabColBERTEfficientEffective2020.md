---
tags:
- '#paper'
aliases: "khattabColBERTEfficientEffective2020"
year: 2020
name: "ColBERT: Efficient and Effective Passage Search via Contextualized Late Interaction over BERT"
authors: "Omar Khattab, Matei Zaharia"
publication: ""
type: "conferencePaper"
DOI: "10.1145/3397271.3401075"
date of note: 2024-12-31 
---
# Descriptions

## ColBERT: Efficient and Effective Passage Search via Contextualized Late Interaction over BERT 
> [!info] 
> - **Abstract:** Recent progress in Natural Language Understanding (NLU) is driving fast-paced advances in Information Retrieval (IR), largely owed to fine-tuning deep language models (LMs) for document ranking. While remarkably effective, the ranking models based on these LMs increase computational cost by orders of magnitude over prior approaches, particularly as they must feed each query-document pair through a massive neural network to compute a single relevance score. To tackle this, we present ColBERT, a novel ranking model that adapts deep LMs (in particular, BERT) for efficient retrieval. ColBERT introduces a late interaction architecture that independently encodes the query and the document using BERT and then employs a cheap yet powerful interaction step that models their fine-grained similarity. By delaying and yet retaining this fine-granular interaction, ColBERT can leverage the expressiveness of deep LMs while simultaneously gaining the ability to pre-compute document representations offline, considerably speeding up query processing. Crucially, ColBERT's pruning-friendly interaction mechanism enables leveraging vector-similarity indexes for end-to-end retrieval directly from millions of documents. We extensively evaluate ColBERT using two recent passage search datasets. Results show that ColBERT's effectiveness is competitive with existing BERT-based models (and outperforms every non-BERT baseline), while executing two orders-of-magnitude faster and requiring up to four orders-of-magnitude fewer FLOPs per query. 
> - **Sources**: [online](http://zotero.org/users/13492210/items/CCTBD7LB) [local](zotero://select/library/items/CCTBD7LB) [pdf](file:////home/lukexie/Documents/Papers/storage/RS6HL9GD/Khattab%20and%20Zaharia%20-%202020%20-%20ColBERT%20Efficient%20and%20Effective%20Passage%20Search%20via%20Contextualized%20Late%20Interaction%20over%20BERT.pdf) 
> - **Bibliography**: Khattab, O., & Zaharia, M. (2020). ColBERT: Efficient and Effective Passage Search via Contextualized Late Interaction over BERT. _Proceedings of the 43rd International ACM SIGIR Conference on Research and Development in Information Retrieval_, 39–48. [https://doi.org/10.1145/3397271.3401075](https://doi.org/10.1145/3397271.3401075)
> - **Cite Key:** [[@khattabColBERTEfficientEffective2020]] 
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