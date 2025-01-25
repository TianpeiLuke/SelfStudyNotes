---
tags:
- '#paper'
aliases: "malkovEfficientRobustApproximate2020"
year: 2020
name: "Efficient and Robust Approximate Nearest Neighbor Search Using Hierarchical Navigable Small World Graphs"
authors: "Yu A. Malkov, D. A. Yashunin"
publication: "IEEE Transactions on Pattern Analysis and Machine Intelligence"
type: "journalArticle"
DOI: "10.1109/TPAMI.2018.2889473"
date of note: 2024-11-30 
---
# Descriptions

## Efficient and Robust Approximate Nearest Neighbor Search Using Hierarchical Navigable Small World Graphs 
> [!info] 
> - **Abstract:** We present a new approach for the approximate K-nearest neighbor search based on navigable small world graphs with controllable hierarchy (Hierarchical NSW, HNSW). The proposed solution is fully graph-based, without any need for additional search structures (typically used at the coarse search stage of the most proximity graph techniques). Hierarchical NSW incrementally builds a multi-layer structure consisting of a hierarchical set of proximity graphs (layers) for nested subsets of the stored elements. The maximum layer in which an element is present is selected randomly with an exponentially decaying probability distribution. This allows producing graphs similar to the previously studied Navigable Small World (NSW) structures while additionally having the links separated by their characteristic distance scales. Starting the search from the upper layer together with utilizing the scale separation boosts the performance compared to NSW and allows a logarithmic complexity scaling. Additional employment of a heuristic for selecting proximity graph neighbors significantly increases performance at high recall and in case of highly clustered data. Performance evaluation has demonstrated that the proposed general metric space search index is able to strongly outperform previous opensource state-of-the-art vector-only approaches. Similarity of the algorithm to the skip list structure allows straightforward balanced distributed implementation. 
> - **Sources**: [online](http://zotero.org/users/13492210/items/N4PLE2Y2) [local](zotero://select/library/items/N4PLE2Y2) [pdf](file:////home/lukexie/Documents/Papers/storage/699VWJZX/Malkov%20and%20Yashunin%20-%202020%20-%20Efficient%20and%20Robust%20Approximate%20Nearest%20Neighbor%20.pdf) 
> - **Bibliography**: Malkov, Y. A., & Yashunin, D. A. (2020). Efficient and Robust Approximate Nearest Neighbor Search Using Hierarchical Navigable Small World Graphs. _IEEE Transactions on Pattern Analysis and Machine Intelligence_, _42_(4), 824–836. IEEE Transactions on Pattern Analysis and Machine Intelligence; Date of Publication: 28 December 2018. [https://doi.org/10.1109/TPAMI.2018.2889473](https://doi.org/10.1109/TPAMI.2018.2889473)
> - **Cite Key:** @malkovEfficientRobustApproximate2020 
> - **Conclusion**:
> - **Tags:** #artificial-intelligence, #nearest-neighbor-search, #big-data, #data-structures, #Data-models, #approximate-search, #Approximation-algorithms, #Biological-system-modeling, #Brain-modeling, #Complexity-theory, #Graph-and-tree-search-strategies, #graphs-and-networks, #information-search-and-retrieval, #information-storage-and-retrieval, #information-technology-and-systems, #Routing, #Search-problems, #search-process, #similarity-search, #HNSW, #Hierarchical-Navigable-Small-World-Graphs


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