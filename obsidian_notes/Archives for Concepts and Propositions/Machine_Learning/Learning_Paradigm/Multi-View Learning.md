---
tags:
  - concept
  - machine_learning/paradigm
  - multi-view_learning
keywords:
  - multi-view_learning
topics:
  - machine_learning_paradigm
name: Multi-View Learning
date of note: 2024-09-09
---

## Concept Definition

>[!important]
>**Name**: Multi-View Learning

>[!important] Definition
>**Multi-View Learning** is a machine learning paradigm where the model learns from *multiple distinct but complementary views* of the same data, aiming to *exploit the redundancy* and *diversity* across views to improve learning performance. 
>- Each *view* represents a different feature set or *modality* that provides unique information about the underlying entity. 
>- Multi-view learning methods are designed to *align*, *integrate*, or jointly optimize these views to build more *robust* and generalizable models.



## Explanation

>[!info]
>Techniques in multi-view learning include 
>- **co-training**, 
>- **canonical correlation analysis**, 
>- and **multi-view deep networks**

- [[Canonical Correlation Analysis]]

>[!info]
>it has applications in fields like natural language processing, computer vision, and bioinformatics, where data naturally comes from multiple perspectives or feature spaces.

### Compare Multi-view and Multi-modal Learning

| Aspect                 | **Multi-View Learning**                                                                                | **Multi-Modal Learning**                                                                       |
| ---------------------- | ------------------------------------------------------------------------------------------------------ | ---------------------------------------------------------------------------------------------- |
| **Definition**         | Learning from multiple _feature sets_ (views) that describe the same instance                          | Learning from multiple _modalities_ (different data types) that together describe the instance |
| **Nature of Input**    | Different *representations* of the *same* data type                                                    | Different types of data (e.g., image, text, audio)                                             |
| **Example**            | Two sets of handcrafted features extracted from the same image                                         | An image and its associated text description                                                   |
| **Goal**               | Exploit *redundancy* and *complementary* information among views to improve learning                   | *Fuse heterogeneous signals* to capture richer representations across modalities               |
| **Typical Assumption** | All views describe the *same underlying object* and are aligned (e.g., co-occurring)                   | Modalities may vary widely in structure, scale, and semantic meaning                           |
| **Common Techniques**  | Co-training, Canonical Correlation Analysis (CCA), multi-view deep networks                            | Cross-modal transformers, multi-modal fusion, attention over modalities                        |
| **Challenges**         | *Aligning* feature spaces, handling missing views                                                      | *Bridging* modality gaps, balancing contributions from heterogeneous modalities                |
| **Applications**       | Web page classification (text + link graph view), sensor fusion with multiple sensors of the same type | Visual question answering (image + text), video understanding (audio + video frames)           |

- [[Multi-Modal Learning]]



-----------
##  Recommended Notes and References


- [[Representation Learning]]

- [[Multi-Modal Learning]]
- [[Transfer Learning]]

- [[Elements of Statistical Learning by Hastie]]
- [[Probabilistic Machine Learning Advanced Topics by Murphy]] pp 1054
